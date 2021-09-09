---
title: Anotações sobre Recuperação de banco de dados e segurança
author: João F. F. Nogueira
date: 2020-12-11 09:00:00 -0300
categories: [Português, Estudos]
tags: [data]
toc: true
---

## Estratégias de recuperação:

1.	Se houver dano extensivo a uma grande parte do banco de dados devido a uma falha catastrófica, como uma falha de disco, o método de recuperação restaura uma cópia antiga do banco de dados que teve backup para o arquivamento (normalmente, fita ou outro meio de armazenamento off-line de grande capacidade) e reconstrói um estado mais recente, reaplicando ou refazendo as operações das transações confirmadas do log em backup, até o momento da falha. 

2.	Quando o banco de dados no disco não está danificado fisicamente, por conta de uma falha não catastrófica, a estratégia de recuperação é identificar quaisquer mudanças que possam causar uma inconsistência no banco de dados. Por exemplo, uma transação que atualizou alguns itens do banco de dados no disco, mas não confirmou as necessidades de ter suas mudanças revertidas ao desfazer suas operações de gravação. Pode também ser preciso refazer algumas operações a fim de restaurar um estado consistente do banco de dados; por exemplo, se uma transação tiver sido confirmada, mas algumas de suas operações de gravação ainda não tiverem sido gravadas em disco. Para a falha não catastrófica, o protocolo de recuperação não precisa de uma cópia de arquivamento completa do banco de dados. Em vez disso, as entradas mantidas no log do sistema on-line no disco são analisadas para determinar as ações apropriadas para recuperação.

## Técnicas de atualização:

### Atualização adiada

Não atualizam fisicamente o banco de dados no disco até que uma transação atinja seu ponto de confirmação; então as atualizações são registradas no banco de dados. Antes de atingir a confirmação, todas as atualizações de transação são registradas no espaço de trabalho de transação local ou nos buffers da memória principal que o SGBD mantém (o cachê da memória principal do SGBD). Antes da confirmação, as atualizações são gravadas persistentemente no log e, após a confirmação, elas são gravadas no banco de dados no disco. Se uma transação falhar antes de atingir seu ponto de confirmação, ela não terá alterado o banco de dados de forma alguma, de modo que o UNDO não é necessário. Pode ser preciso um REDO para desfazer o efeito das operações de uma transação confirmada com base no log, pois seu efeito pode ainda não ter sido registrado no banco de dados em disco. Assim, a atualização adiada também é conhecida como algoritmo NO-UNDO/REDO.

### Atualização imediata

O banco de dados pode ser atualizado por algumas operações de uma transação antes que a transação alcance seu ponto de confirmação. Porém essas operações também precisam ser registradas no log no disco ao forçar a gravação antes que elas sejam aplicadas ao banco de dados no disco, tornando a recuperação ainda possível. Se uma transação falhar depois de gravadas algumas mudanças no disco, mas antes de atingir seu ponto de confirmação, o efeito de suas operações no banco de dados precisa ser desfeito; ou seja, a transação deve ser revertida. 
No caso geral da atualização imediata, tanto UNDO quanto REDO podem ser exigidos durante a recuperação. Essa técnica, conhecida como algoritmo UNDO/REDO, requer as duas operações durante a recuperação, e é usada na prática. Uma variação do algoritmo, em que todas as atualizações precisam ser registradas no banco de dados em disco antes que a transação se confirme, requer apenas UNDO, de modo que é conhecido como algoritmo UNDO/NOREDO.

Não atualizam fisicamente o banco de dados no disco até que uma transação atinja seu ponto de confirmação; então as atualizações são registradas no banco de dados. Antes de atingir a confirmação, todas as atualizações de transação são registradas no espaço de trabalho de transação local ou nos buffers da memória principal que o SGBD mantém (o cachê da memória principal do SGBD). Antes da confirmação, as atualizações são gravadas persistentemente no log e, após a confirmação, elas são gravadas no banco de dados no disco. Se uma transação falhar antes de atingir seu ponto de confirmação, ela não terá alterado o banco de dados de forma alguma, de modo que o UNDO não é necessário. Pode ser preciso um REDO para desfazer o efeito das operações de uma transação confirmada com base no log, pois seu efeito pode ainda não ter sido registrado no banco de dados em disco. Assim, a atualização adiada também é conhecida como algoritmo NO-UNDO/REDO.	O banco de dados pode ser atualizado por algumas operações de uma transação antes que a transação alcance seu ponto de confirmação. Porém essas operações também precisam ser registradas no log no disco ao forçar a gravação antes que elas sejam aplicadas ao banco de dados no disco, tornando a recuperação ainda possível. Se uma transação falhar depois de gravadas algumas mudanças no disco, mas antes de atingir seu ponto de confirmação, o efeito de suas operações no banco de dados precisa ser desfeito; ou seja, a transação deve ser revertida. 
No caso geral da atualização imediata, tanto UNDO quanto REDO podem ser exigidos durante a recuperação. Essa técnica, conhecida como algoritmo UNDO/REDO, requer as duas operações durante a recuperação, e é usada na prática. Uma variação do algoritmo, em que todas as atualizações precisam ser registradas no banco de dados em disco antes que a transação se confirme, requer apenas UNDO, de modo que é conhecido como algoritmo UNDO/NOREDO.

Algoritmo de recuperação ARIES: o ARIES é um algoritmo de recuperação projetado para trabalhar com uma estratégia de roubo, sem imposição. Quando o gerenciador de recuperação é ativado após uma falha, o reinício ocorre em três fases:
1. Análise: Identifica as páginas sujas no pool de buffers (isto é, alterações que não foram gravadas no disco) e as transações ativas no momento da falha.
2. Refazer: Repete todas as ações, partindo de um ponto apropriado no log, e restaura o banco de dados para o estado em que ele estava no momento da falha.
3. Desfazer: Desfaz as ações das transações que não foram efetivadas, para que o banco de dados reflita apenas as ações das transações efetivadas. Princípios do algoritmo de recuperação ARIES:
1. Gravação antecipada do Log (Write-Ahead Logging, WAL): Qualquer alteração em um objeto de banco de dados é primeiramente gravada no log; o registro que está no log deve ser gravado em um meio de armazenamento estável, antes que a alteração no objeto de banco de dados seja gravada no disco.
2. Repetição do Histórico durante a fase Refazer: Na inicialização após uma falha, o ARIES refaz todas as ações do SGBD antes da falha e coloca o sistema de volta no estado exato em que se encontrava no momento da falha. Ele então desfaz as ações das transações que ainda estavam ativas no momento da falha (cancelando-as efetivamente).
3. Registro das alterações durante a fase Desfazer: As alterações feitas no banco de dados, enquanto uma transação é desfeita, são registradas para garantir que essa ação não seja repetida no caso de reinícios (causando falhas) repetidos.
A parte mais recente do log, chamada de cauda do log, é mantida na memória principal, e é periodicamente gravada no armazenamento estável. Desse modo, os registros do log e os registros dos dados são gravados no disco com a mesma granularidade (páginas ou conjuntos de páginas). Todo registro de log recebe um id exclusivo, chamado de número de sequência de log (NSL).
Tabelas relacionadas à recuperação:
Tabela de transações: Essa tabela contém uma entrada para cada transação ativa. A entrada contém (dentre outras coisas) o id da transação, o status e um campo chamado último NSL, que é o NSL do registro de log mais recente dessa transação. O status de uma transação pode indicar que ela está em andamento, foi efetivada ou foi cancelada. (Nos dois últimos casos, a transação será removida da tabela quando certas etapas de ‘limpeza’ forem completadas.) 
Tabela de páginas sujas: Essa tabela contém uma entrada para cada página suja no pool de buffers; isto é, cada página com alterações ainda não refletidas no disco. A entrada contém um campo NSLreg, que é o NSL do primeiro registro de log que fez a página tornar-se suja. Note que esse NSL identifica o registro de log mais recente que talvez tenha que ser refeito para essa página durante o reinício a partir de uma falha.
Discos rígidos espelhados – arquitetura RAID - (Redundant Array Inexpensive/Independent Disk, ou “Conjunto Redundante de Discos Econômicos/Independentes”).

## Controle de concorrência

Aplicação de diversas técnicas que são usadas para garantir a propriedade de não interferência ou isolamento das transações executadas simultaneamente.
O protocolo de bloqueio mais amplamente usado é o bloqueio de duas fases restrito, ou Strict 2PL (do inglês, Strict Two-Phase Locking).

1. Se uma transação T quer ler (respectivamente, modificar) um objeto, ela primeiro solicita um bloqueio compartilhado (respectivamente, exclusivo) sobre o objeto.
2. Todos os bloqueios mantidos por uma transação são liberados quando a transação termina.

1. Uma transação que tenha um bloqueio exclusivo também pode ler o objeto; não é exigido um bloqueio compartilhado adicional. Uma transação que solicita um bloqueio é suspensa até que o SGBD seja capaz de garantir-lhe o bloqueio solicitado. O SGBD monitora os bloqueios que concedeu e garante que, se uma transação mantiver um bloqueio exclusivo sobre um objeto, nenhuma outra transação manterá um bloqueio compartilhado ou exclusivo sobre o mesmo objeto.
2. Os pedidos para adquirir e liberar bloqueios podem ser inseridos automaticamente nas transações pelo SGBD; os usuários não precisam se preocupar com esses detalhes. Na verdade, o protocolo de bloqueio só permite intercalações “seguras” de transações. Se duas transações acessam partes completamente independentes do banco de dados, elas obtêm concorrentemente os bloqueios que precisam e seguem seu caminho normalmente. Por outro lado, se duas transações acessam o mesmo objeto e uma quer modificá-lo, suas ações são efetivamente ordenadas em série – todas as ações de uma dessas transações (aquela que recebe primeiro o bloqueio sobre o objeto comum) são concluídas antes (que esse bloqueio seja liberado) e que a outra transação possa prosseguir.

Outro conjunto de protocolos de controle de concorrência, utiliza rótulos de tempo (timestamp). Um rótulo de tempo é um identificador exclusivo para cada transação gerado pelo sistema. Os valores de rótulo de tempo são gerados na mesma ordem que os tempos de início de transação.

## Performance – conhecer técnicas de otimização de consultas (consultas, índices)

*	Enumerar planos alternativos para avaliar a expressão. Normalmente, o otimizador considera um subconjunto de todos os planos possíveis, pois o número deles é muito grande. 
*	Estimar o custo de cada plano enumerado e escolher o plano com o custo estimado mais baixo.
Para serem realizadas, as consultas SQL são otimizadas pela sua decomposição em um conjunto de unidades menores chamadas blocos. Um otimizador de consultas relacional típico se concentra na otimização de um único bloco por vez. Para isso, uma consulta é decomposta em blocos, e a otimização de um único bloco pode ser compreendida em termos de planos constituídos de operadores da álgebra relacional.
Para cada nó na árvore, devemos estimar o custo da execução da operação 
correspondente. Os custos são afetados significativamente pelo fato de se usar pipelining ou se relações temporárias são criadas para passar a saída de um operador para seu ascendente. 
Para cada nó na árvore, devemos estimar o tamanho do resultado e verificar se ele está ordenado. Esse resultado é a entrada para a operação que corresponde ao ascendente do nó corrente e, por sua vez, o tamanho e a ordem afetam a estimativa de tamanho, o custo e a ordem do ascendente.
Utilização de índices nos SGBDRs:

IBM DB2: Ao criar um índice, o usuário pode especificar um conjunto de colunas ‘de inclusão’ que devem ser mantidas no índice, mas que não fazem parte da chave do índice. Isso possibilita que um conjunto mais rico de consultas somente de índice seja manipulado, pois as colunas acessadas frequentemente são incluídas no índice, mesmo que não façam parte da chave.

Microsoft SQL Server: Considerada uma classe interessante de planos somente de índice, suponha uma consulta que seleciona atributos salário e idade a partir de uma tabela, dado um índice em salário e outro em idade.

SQL Server: Associando as entradas por junção no rid dos registros de dados para identificar os pares (salário, idade) que aparecem na tabela.

Representação de índice:
1. Caminho de acesso com um único índice: Se vários índices correspondem às condições de seleção na cláusula WHERE, cada índice correspondente oferece um caminho de acesso alternativo. Um otimizador pode escolher o caminho de acesso que, segundo sua estimativa, vai resultar na recuperação do menor número de páginas, e pode aplicar projeções e termos de seleção não primários (isto é, partes da condição de seleção que não correspondem ao índice), e pode passar a calcular as operações de agrupamento e agregação (ordenando nos atributos de GROUP BY).

2. Caminho de acesso com vários índices: Se vários índices usando as alternativas (2) ou (3) para entradas de dados corresponderem à condição de seleção, cada índice poderá ser usado para recuperar um conjunto de rids. Podemos fazer a intersecção desses conjuntos de rids e, depois, ordenar o resultado pelo id da página (supondo que a representação de rid inclua o id da página) e recuperar as tuplas que satisfazem os termos da seleção primária de todos os índices correspondentes. Todas as projeções e termos de seleção não primários podem, então, ser aplicados, seguidos das operações de agrupamento e agregação.

3. Caminho de acesso com índice ordenado: Se a lista de atributos de agrupamento for um prefixo de um índice de árvore, o índice pode ser usado para recuperar as tuplas na ordem exigida pela cláusula GROUP BY. Todas as condições de seleção podem ser aplicadas em cada tupla recuperada, os campos indesejados podem ser removidos e as operações agregadas podem ser calculadas para cada grupo. Essa estratégia funciona bem para índices agrupados.

4. Caminho de acesso somente de índice: Se todos os atributos mencionados na consulta (nas cláusulas SELECT, WHERE, GROUP BY ou HAVING) estiverem incluídos na chave de pesquisa para algum índice denso na relação da cláusula FROM, uma varredura somente de índice poderá ser usada para calcular as respostas. Como as entradas de dados no índice contêm todos os atributos de uma tupla necessários para essa consulta e há apenas uma entrada de índice por tupla, nunca precisamos recuperar tuplas reais da relação. Usando apenas as entradas de dados do índice, podemos executar os passos a seguir, conforme for necessário, em determinada consulta: aplicar as condições de seleção, remover os atributos indesejados, ordenar o resultado para obter agrupamento e calcular as funções agregadas dentro de cada grupo. Essa estratégia somente de índice funciona mesmo que o índice não corresponda às seleções da cláusula WHERE. Se o índice corresponder à seleção, precisamos examinar apenas um subconjunto das entradas de índice; caso contrário, devemos percorrer todas as entradas de índice. Em qualquer caso, podemos evitar a recuperação de registros de dados reais; portanto, o custo desta estratégia não depende de o índice ser agrupado. Além disso, se é um índice de árvore e a lista de atributos na cláusula GROUP BY forma um prefixo da chave do índice, podemos recuperar as entradas de dados na ordem necessária para a cláusula GROUP BY e, com isso, evitar a ordenação.

# Data warehouse

Um data warehouse tem a característica distintiva de servir principalmente para a aplicação de apoio à decisão, sendo utilizados para recuperar dados e não para processamento de transação de rotina, o que implica diretamente que os data warehouse são muito distintos dos bancos de dados tradicionais em sua estrutura, funcionamento, desempenho e finalidade.

OLAP – Processamento analítico on-line: É um termo usado para descrever a análise de dados complexos do data warehouse. Nas mãos de trabalhadores do conhecimento habilidoso, as ferramentas OLAP utilizam capacidades de computação 
distribuída para análises que exigem mais armazenamento e poder de processamento do que pode estar localizada econômica e eficientemente em um desktop individual.

DSS sistema de apoio à decisão: Também conhecido como sistema de informações executivas. Não confunda com sistemas de integração empresarial; ajudam os principais tomadores de decisões de uma organização com dados de nível mais alto em decisões complexas e importantes.

Mineração de dados: É usada para descoberta do conhecimento – o processo de procurar novo conhecimento imprevisto nos dados. Estudaremos sobre este assunto em breve.

Mineração de dados	É usada para descoberta do conhecimento – o processo de procurar novo conhecimento imprevisto nos dados. Estudaremos sobre este assunto em breve.
Banco de dados tradicionais versus data warehouse:
*	Banco de dados tradicionais: O suporte para processamento de transação on-line (OLTP) que lida com inserções, atualizações e exclusões, enquanto também tem suporte para requisitos de consulta de informação. Os bancos de dados relacionais tradicionais são utilizados para processar consultas que podem tocar em uma pequena parte do banco de dados e transações que lidam com inserções ou atualizações no processo de algumas duplas por relação, assim eles não podem ser utilizados para OLPA, DSS ou mineração de dados.
*	Data warehouses: São projetados exatamente para dar suporte à extração, processamento e apresentação eficiente para fins analíticos e de tomada de decisão. Em comparação com os bancos de dados tradicionais, os data warehouses em geral contêm quantidades muito grandes de dados de várias fontes, que podem incluir bancos de dados de diferentes modelos de dados, e às vezes arquivos adquiridos de sistemas e plataformas independentes.

## Modelagem de dados para data warehouse

Para modelagem de dados deve ser levada em consideração a tipologia. Em modelos multidimensionais ocorre o relacionamento dos dados em matrizes multidimensionais, que são chamadas de cubo de dados. Também pode ocorrer de haver mais de três dimensões e, nesse caso, a nominação é hipercubo.
A mudança de hierarquia de uma orientação unidimensional para outra é algo feito com facilidade em um cubo de dados com uma técnica chamada de giro, que também pode ser chamada de rotação. Nessa técnica, o cubo de dados pode ser imaginado girando para mostrar uma orientação diferente dos eixos.
Modelos multidimensionais atendem prontamente a visões hierárquicas, conhecidas como exibição roll-up ou exibição drill-down. Uma exibição roll-up sobe na hierarquia, agrupando em unidades maiores ao longo de uma dimensão. Uma exibição drill-down oferece a capacidade oposta, fornecendo uma visão mais detalhada.
O modelo de armazenamento multidimensional envolve dois tipos de tabelas: a tabela de dimensão, que consiste em tuplas de atributos da dimensão, e a tabela de fatos, que pode ser imaginada como sendo tuplas, uma para cada fato registrado. Esse fato contém alguma variável observada e a identifica com ponteiros para tabelas de dimensão, podendo ser uma ou várias variáveis. A tabela de fatos contém os dados, e as dimensões identificam cada tupla nesses dados.
Dois esquemas multidimensionais comuns são o esquema estrela e o esquema floco de neve. O esquema estrela consiste em uma tabela de fatos com uma única tabela para cada dimensão. O esquema floco de neve é uma variação do esquema estrela, em que as tabelas dimensões de um esquema estrela são organizadas em uma hierarquia ao normalizá-las.

## Projeto de data warehouse

1.	Os dados precisam ser extraídos de várias fontes heterogêneas. Por exemplo, banco de dados ou outras entradas de dados, como aquelas que contêm dados do mercado financeiro ou dados ambientais.
2.	Os dados precisam ser formatados por coerência dentro do data warehouse. Nomes, significados e domínios de dados de fontes não relacionadas precisam ser reconciliados. Por exemplo, empresas subsidiárias de grandes corporações podem ter diferentes calendários fiscais com trimestres terminados em datas diferentes, tornando difícil agregar dados financeiros por trimestre.
3.	Os dados precisam ser limpos para garantir a validade. A limpeza de dados é um processo complicado e complexo, que tem sido identificado como componente que mais exige trabalho na construção do data warehouse. A entrada de dados precisa ser examinada e formatada de modo consistente, sendo verificada a validade e a qualidade. Reconhecer dados errôneos e incompletos é difícil de automatizar, e a limpeza que requer correção de erro automática pode ser ainda mais complicada. Por exemplo, pode-se exigir que "Cidade=Campinas" junto com o "Estado=RJ" seja reconhecido como uma combinação incorreta. Depois que tais problemas tiverem sido resolvidos, dados semelhantes de fontes diferentes precisam ser coordenados para carregar no data warehouse. O processo de retornar dados limpos para origem é chamado de fluxo reverso.
4.	Os dados precisam ser ajustados ao modelo de dados do armazém. Baixar os dados de várias fontes que devem ser instalados no modelo de dados no data warehouse. Eles podem ter que ser convertidos de banco de dados relacionais, orientados a objetos ou legados (em rede e/ou hierárquico) para um modelo multidimensional.
5.	Os dados precisam ser carregados no data warehouse. O grande volume de dados torna a carga dos dados uma tarefa significativa; são necessárias ferramentas de monitoramento para cargas, bem como métodos para recuperação de cargas incompletas ou incorretas. Com o imenso volume de dados no data warehouse, a atualização incremental normalmente é a única técnica viável.
Processos armazenamento de dados:
* Armazenamento dos dados de acordo com o modelo de dados do armazém; * Criação e manutenção das estruturas de dados exigidas; 
* Criação e manutenção dos caminhos de acesso apropriados; 
* Fornecimento de dados variáveis no tempo à medida que novos dados são incluídos; 
* Suporte e atualização dos dados do data warehouse; 
* Atualização dos dados; 
* Eliminação dos dados.
Elementos para projeto do data warehouse:
* Projeções de uso; 
* O ajuste de modelo de dados; 
* Características das fontes disponíveis; 
* Projeto do componente de metadados; 
* Projeto de componente modular; 
* Projeto de facilidade de gerenciamento de mudança; 
* Considerações de arquitetura distribuída e paralela.
Existem duas arquiteturas distribuídas básicas: o data warehouse distribuídos e o data warehouse federado.

Data warehouses em nível empresarial: São imensos projetos que exigem investimento maciço de tempo e recursos.

Data warehouses virtuais: Oferecem visões de banco de dados operacionais que são materializadas para acesso eficiente

Data marts: Em geral são voltados para um subconjunto da organização como um departamento e possuem um foco mais estreito.

Funcionalidades pré-programadas:

Roll-up: Os dados são resumidos com generalização cada vez maior, por exemplo: semanal para trimestral para anual.

Drill-down: Níveis cada vez maiores de detalhes são revelados (complemento de roll-up).

Giro: É realizada a tabulação cruzada, também conhecida como rotação.

Slice e dice: Operações de projeção são realizadas nas dimensões.

Ordenação: Os dados são ordenados por valor ordinal.

Seleção: Os dados estão disponíveis por valor ou intervalo.

Atributos derivados (calculados): Atributos são calculados por operações sobre valores armazenados e derivados.

# Data Mining

Consiste em encontrar tendências ou padrões interessantes em grandes conjuntos de dados para orientar decisões sobre atividades futuras. Há uma expectativa geral de que as ferramentas de mineração de dados deverão identificar esses padrões nos dados com entrada de usuário mínima. Os padrões identificados por essas ferramentas podem fornecer ao analista de dados ideias úteis e inesperadas que podem ser melhor investigadas subsequentemente, talvez se usando outras ferramentas de apoio à decisão.
Objetivos da mineração de dados: previsão, identificação, classificação, otimização.
Está relacionada à subárea da estatística chamada análise de dados exploratória, que tem objetivos semelhantes e conta com medidas estatísticas.
Fases da descoberta de conhecimento nos bancos de dados (KDD -  Knowledge Discovery in Database): Seleção dos dados, limpeza, mineração (enriquecimento e transformação), avaliação (limpeza).
Nova informação gerada: regras de associação, padrões sequenciais e árvores de classificação.
Conhecimento descoberto na mineração de dados: regras de associação, hierarquia de classificação, padrões sequenciais, padrões dentro da série temporal e agrupamento.

# Banco de dados distribuídos

Uma coleção de múltiplos bancos de dados logicamente interrelacionados, distribuídos por uma rede de computadores, e um sistema de gerenciamento de banco de dados distribuído – SGBDD.
Fatores para distribuição dos dados: Maior disponibilidade, Acesso distribuído aos dados, Análise de dados distribuídos.
Propriedade esperada de um SGBDD: Independência dos dados distribuídos e Atomicidade da transação distribuída.
Condições mínimas para um BDD: Conexões de nós de banco de dados por uma rede de computadores, Inter-relação lógica dos bancos de dados conectados e Ausência de restrição de homogeneidade entre os nós conectados.
Problemas abordados no controle de usuário e recuperação de dados: Manipulação de várias cópias de itens de dados, Falhas em pontos da rede, Falhas na comunicação, Falha em commit e Deadlock.
Funções adicionais dos bancos de dados distribuídos: Acompanhar a distribuição de dados, Processamento de consulta distribuído, Gerenciamento de transação distribuído, Gerenciamento de dados replicado, Recuperação de banco de dados distribuído, Segurança e Gerenciamento de diretório (catálogo) distribuído.
Vantagens dos bancos de dados distribuídos: Maior facilidade e flexibilidade de desenvolvimento da aplicação, Maior confiabilidade e disponibilidade, Maior desempenho e Expansão mais fácil.
Funções necessárias de um BDD: 
*	Controle de distribuição, fragmentação e replicação dos dados por meio de extensão no catálogo do SGBDD.
*	Capacidade de processar consultas distribuídas, acessando, por meio de uma rede de comunicação, localizações remotas para extrair os dados.
*	Gerenciamento de consultas e transações que acessam dados a partir de vários locais, ao mesmo tempo em que mantém o acesso sincronizado e a integridade do próprio banco de dados. 
*	Capacidade de decidir qual cópia de um item de dado que se encontra replicado deve ser considerada. 
*	Recuperação do banco de dados distribuído quando houver alguma falha ou colapso do sistema (os comumente denominados crashs). 
*	Segurança na execução de transações distribuídas e gerenciamento de privilégios de autorização/acesso por parte dos usuários.
*	Gerenciamento do catálogo do banco de dados distribuído, de forma que contenha informação referente às localizações dos bancos. Esse catálogo pode ser geral a todo o banco ou local para cada nó da rede envolvida do processo.
Desvantagens causadas por problemas com sistemas de gerenciamentos de bancos de dados federados: Diferenças nos modelos de dados, Diferenças nas restrições, Diferenças nas linguagens de consulta, Heterogeneidade semântica, Autonomia de projeto do sistema de bancos de dados.
Desvantagens causadas por problemas encontrados no controle de concorrência e recuperação de um BDD: Lidar com múltiplas cópias dos itens de dados, Falha de sites individuais, Falha dos links de comunicação, Confirmação distribuída e Deadlock distribuído.
Dois tipos de arquiteturas de sistema multiprocessador: Arquitetura de memória compartilhada (altamente acoplada) e Arquitetura de disco compartilhado (livremente acoplada).

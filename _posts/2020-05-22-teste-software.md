---
title: Anotações sobre Teste de Software
author: João F. F. Nogueira
date: 2020-05-22 08:00:00 -0300
categories: [Português, Estudos]
tags: [test]
toc: true
---

# Introdução

Danos dos Bugs :

Prejuízos Financeiros e de Imagem

| **Empresas / Organizações**      | **Pessoas**                    |
| -------------------------------- | ------------------------------ |
| Atrasos                          | Constrangimentos               |
| Perda de Confiança / Vendas      | Perda ou Supressão de Direitos |
|                                  | Risco de Vida e Acidentes      |
| **Governos**                     | **Meio Ambiente**              |
| Vulnerabilidade de Informações   | Alertas Atrasados              |
| Decisões Estratégicas Incorretas | Desperdício de Recursos        |
| Derrotas Militares               | Poluição                       |

**Os 7 fundamentos do Teste (ISTQB):**

1.  Teste Demonstra a Presença de Defeitos, Mas Nunca a Sua Ausência;

2.  Teste exaustivo não é possível (é necessário avaliar riscos e prioridades);

3.  Teste antecipado;

4.  Agrupamento de defeitos (os bugs estão distribuídos de forma heterogênea);

5.  Paradoxo do pesticida (quanto mais realiza o mesmo conjunto de testes, menos defeitos; inove regularmente os testes);

6.  Teste depende do contexto;

7.  A ilusão da ausência de erros (o foco é atender a necessidade do usuário).

A tolerância a falhas muda em razão do meio.

Regra 10 de Myers: Quanto mais cedo encontrarmos um defeito, mais barata será sua identificação e correção.

Diferença entre teste (produto) e QA (processo): Testes devem ser integrados como uma das atividades de garantia da qualidade.

Softwares são feitos por pessoas para pessoas. Pessoas cometem erros (enganos), que produzem defeitos (bugs) no código, em um software ou sistema ou em um documento. Devem ser chamados de ocorrência, ou incidente, para evitar atritos com as pessoas.

Se um defeito no código for executado, o sistema falhará ao tentar fazer o que deveria (ou, em algumas vezes, o que não deveria), causando uma falha.

Nem todos os defeitos causam falhas (a falha só existe quando o defeito é executado). Falhas geram insatisfação com a qualidade.

**Tipos de testes baseados na IEC/ISO 25010 (Substitui a ISO 9126; conhecida como SQuaRE):**

1.  Adequação funcional (funcionalidade);

    a.  Completude funcional;

    b.  Correção funcional;

    c.  Apropriado a funcionalidade;

1.  Usabilidade;

    a.  Reconhecibilidade: facilitar que o usuário reconheça elementos e componentes;

    b.  Aprendizibilidade: facilitar o aprendizado do usuário;

    c.  Operabilidade: facilitar a operação e navegação;

    d.  Proteção contra erro do usuário;

    e.  Estética (da interface do usuário);

    f.  Acessibilidade: facilitar o acesso a todas as pessoas;

1.  Compatibilidade:

    a.  Coexistência: facilidade de coexistir;

    b.  Interoperabilidade: facilidade de comunicar;

1.  Confiança/confiabilidade:

    a.  Maturidade: perceber e prevenir a falha antes que aconteça;

    b.  Disponibilidade: manter-se a disposição de usuários e sistemas;

    c.  Tolerância a falhas: perceber e compensar as falhas em tempo real;

    d.  Recuperabilidade: recuperar-se de falhas e travamentos;

1.  Eficiência de desempenho:

    a.  Comportamento em relação ao tempo;

    b.  Utilização de recursos;

    c.  Capacidade: de atender transações e usuários;

1.  Manutenibilidade:

    a.  Modularidade: organizado em módulos;

    b.  Reusabilidade: facilidade em reutilizar;

    c.  Analisabilidade: facilidade de analisar;

    d.  Modificabilidade: facilidade de modificar;

    e.  Testabilidade: facilidade de testar;

1.  Portabilidade:

    a.  Adaptabilidade: facilidade de adaptar;

    b.  Instalabilidade: facilidade de instalar e desinstalar;

    c.  Substituibilidade: facilidade de substituir;

1.  Segurança:

    a.  Confidencialidade;

    b.  Integridade (modificações apenas por usuário autorizado);

    c.  Não repúdio (garantir a identidade do usuário);

    d.  Responsabilidade: Auditável e prestação de contas;

    e.  Autenticidade;

Testes de regressão automatizados: garantir que correções e alterações não estão quebrando outras funções que já existiam.

# Planejamento de Testes

Dimensões do planejamento: Escopo, Cronograma, Qualidade, Custo, Pessoas, Riscos, Comunicação, Aquisições, Fornecedores.

MVP: Mínimo Produto Viável. MVQ: Mínima Qualidade Viável.

Princípio de Pareto.

Gráficos de Pareto para Testes: reclamações por módulo; módulos mais usados; análise de risco; falhas por módulo; defeitos por módulo (averiguados por você).

Produtos cabeça (hits/populares) e cauda longa (produtos de nicho). Testes combinatoriais - Pairwise [pairwise.yuuniworks.com](http://pairwise.yuuniworks.com)

Quadrantes de teste:

Pirâmide de teste: Testes unitários \> teste de serviços \> testes de UI

Negociando um acordo flexível e de valor: valor para os negócios; antecipar mudanças; acordar as trocas (trade off).

Plano de teste: IEC/ISO 29119-3 Padrão de Documentação de Teste.

Estória dos usuários: independente; negociável; valioso; estimável; pequeno; testável (critérios de aceite; mensurável).

Pre-game: inception; planejamento do produto; Sprint do planejamento; reuniões de grooming.

Épicos: estória grande - longa duração - grande entrega.

Features: momento intermediário entre estória e épico. Funcionalidades mais visíveis, que podem depender de várias estorias.

Análise de riscos: feita com o time; Identificação - Análise - Priorização (probabilidade x impacto) - Estratégia de tratamento - Acompanhamento.

Matriz de risco: Nome do risco - Probabilidade - Impacto - R=PxI - Estratégia - Como? - Responsável - Reavaliar

Planning Poker: Dinâmica de grupo com cartas. Facilita discussões e votações.

Histórico dos Riscos: ajuda a tomar boas decisões e cria uma cultura de preservar.

Análise de Pareto: Priorizações. Baseia-se na existência de restrições.

Priorização por Impulso: Seguir a ordem do maior para o menor.

Priorização por Atração: Um item priorizado atrai menos priorizados que podem ser resolvidos juntos.

Análise da cauda longa: Pairwise e Matriz Ortogonal.
 

# Análise, Modelagem e Implementação

Análise: Conjunto de testes - Suite de teste ou cenário

Modelagem: Casos de teste são caros e demorados; indicados apenas para funções críticas e complexas. Mapas mentais para mapear as funcionalidades pode ser mais agil. BDD; Fichas de teste e diagramas.

# Testes Web

Três maiores problemas da testagem web: identificação dos elementos; sincronismo; programação exótica.

Tipos de aplicações web: site, web app.

Responsividade; Performance; Acessibilidade; Informação para tomada de decisão.

Ferramentas: Google Analytics, Crazy Egg (mapa de calor e teste A/B). [seositecheckup.com](http://seositecheckup.com)

|  Prioridade|  Fluxo                       Cenários
|------------|---------------------------|------------------------------------|
|  1         |  Validações básicas       |  Lista produtos na página principal|
|  2         |  Validações básicas       |  Validar carrinho vazio            |
|  3         |  Fluxo padrão             |  Compra de um produto              |
|  4         |  Funcionalidade adicionais|  Contate-nos                       |

Java JDK + Eclipse + Browser + WebDriver do Browser

Maven + Selenium

1.  Criar um novo Maven project no Eclipse, verificar a configuração do compilador e do jdk do projeto;

2.  Editar o arquivo pom.xml (properties, dependencies, build);

3.  Dependencies:

    a.  JUnit (JUnit Jupiter (Aggregator));

    b.  Hamcrest;

    c.  Selenium (Selenium Java);

1.  Criar pacotes de teste em src/test/java;

2.  Criar os testes em classes dentro dos pacotes;

O Selenium permite capturar a tela para registrar os testes.

Cucumber: ferramenta voltada para BDD (Behavior Driven Development);

Utiliza a linguagem Gherkin, que suporta inclusive o português. Viabiliza a execução automatizada das especificações.

Plug-in do Eclipse.

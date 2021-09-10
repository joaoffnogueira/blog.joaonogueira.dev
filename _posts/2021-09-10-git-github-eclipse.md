---
title: Anotações sobre Git/GitHub no Eclipse
author: João F. F. Nogueira
date: 2021-09-10 09:00:00 -0300
categories: [Português, Estudos]
tags: [git, java]
toc: true
---

> Baseadas nos cursos da Softblue

No Eclipse não é recomendado criar o projeto dentro do Workspace para integrar com o Git. Escolha outro diretório.

Nas configurações do projeto, inclua user.name e user.email para identificação nos commits

Clique com o botão direito no projeto - Opção Team - Opção Share Project

Marque a opção: Use or create repository in parent folder of project

Utilize a Perspective Git do Eclipse

Commit: enviar um snapshot do projeto para o repositório.

Head: commit ativo

Check-out para voltar aos commits anteriores, para consulta, sem alterar (ou pra criar outro branch para alteração)

Git Staging para adicionar os arquivos do projeto ao controle de gestão. Desnecessário adicionar arquivos .class, pois eles são compilados a partir dos códigos fonte .java. Você pode incluir na pasta bin um arquivo .gitignore para que a pasta com todos os arquivos compilados seja ignorada.

Operação clean: limpar alterações que ainda não foram enviados para commit.

Nomear commits especiais: tags - #

Operação revert: para eliminar alterações que já haviam sido consolidadas em commit, reverte para o commit anterior, mas não apaga o commit revertido, ele é mantido. O git apenas cria uma cópia da versão anterior e a marca como Head.

Operação stash changes: O commit pressupõe o snapshot de uma funcionalidade pronta, então se você quiser guardar um trabalho em andamento, pode utilizar o stash changes. As alterações são removidas projeto principal, mas podem ser recuperadas no stashed commits.

Recurso compare: compara arquivo alterado com a versão de algum commit.

Recurso replace: substitui o arquivo alterado por um de algum commit.

## Linhas de desenvolvimento independentes com o uso de branches

Galhos ou ramos. O branch principal é chamado de Master.

Juntando branches com o fast-forward merge: fazer check-out no commit que vai receber o merge.

Excluindo branches que não são mais necessários: delete branches

Usando 3-way merge e resolvendo conflitos manualmente: fazer check-out no commit que vai receber o merge. Fazer o merge; resolver manualmente os conflitos sinalizados; fazer novo commit.

## Alterando a estrutura dos branches com o uso do rebase

Usando o rebase pra mover um branch para outro local - mudar o commit pai. Ajuda a limpar a estrutura dos commits

Importante manter o histórico do Master organizado

Operações mais comuns do interactive rebase (permite fazer uma limpeza no histórico): permite eliminar commits, fundir, pular, renomear, mudar o comentário etc.

## Trabalhando com repositórios remotos

Adicionando repositórios remotos e realizando o fetch: Repositório clonado - cópia. Fetch - buscar do repositório remoto alguma alteração. Push - enviar alterações feitas para o repositório remoto.

Ao receber um push, você pode substituir seu arquivo que foi alterado ou forçar um commit que mantem a sua versão.

Não é recomendado fazer push em um repositório remoto local. Você deve avisar as pessoas para que elas façam fetch.

## Repositório central no GitHub

Elimine repositórios remotos locais do Eclipse, e trabalhe apenas com o central. Adicionar Remotes incorpora configuração automática com o GitHub.

No repositório central você pode fazer push.

Integrator Workflow: push bloqueado no repositório central. Desenvolvedores fazem pull request para o integrator aprovar as alterações para inclusão no repositório central.
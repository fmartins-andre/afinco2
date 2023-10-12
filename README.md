# AFINCO 2

Este é um trabalho de atualização do app AFINCO, feito anteriormente em Python/Django.
O objetivo é criar uma base de código mais limpa e simples, além de melhorar os recursos
existentes no app original e adicionar outros.

## Apps

O projeto conta com dois apps:

### API

A API é uma aplicação em NodeJS utilizando o framework NestJS para facilitar na organização e gestão arquitetura.

### Web

O cliente Web é uma aplicação em React consumindo a API.

### Core

Além dos dois apps supracitados, o projeto terá em separado um pacote chamado `core` quer compartilha os casos de uso comuns à API e ao client Web.

## Monorepo com NPM

Todo o projeto está contido neste monorepo.

Não foi utilizado nenhum pacote externo para criar/gerir o monorepo além do próprio NPM.

### Criando novos pacotes (workspaces)

Para criar um outro workspace utilize o comando:

```bash
# npm init -y --scope @afinco2 -w <workspace_dir>/<workspace_name>
npm init -y --scope @afinco2 -w apps/cli
```

E referencie tal workspace no arquivo `tsconfig.json`:

```json
{
    ...
    "references": [
        { "path": "packages/core" },
        { "path": "apps/api" },
        { "path": "<workspace_dir>/<workspace_name>" }
    ]
}
```

### Executando comando NPM nos workspaces

Para executar um comando npm em algum workspace em específico, utilize o comando:

```bash
# npm install <npm_package> -w <workspace>
npm install json -w @afinco2/web
```

## Execução

O arquivo `package.json` da raiz do projeto conta com scripts gestão básicos para iniciar as aplicações em modo de desenvolvimento e produção.

Para iniciar o projeto basta executar o comando:

```bash
# em modo de desenvolvimento
npm run start:dev

# em modo de produção
npm run build
npm run start:prod
```

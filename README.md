# Simple Workflow Node.js Boilerplate

Este projeto tem como objetivo centralizar e reutilizar workflows do GitHub Actions para projetos Node.js, evitando a duplicação de código e a necessidade de criar múltiplos repositórios com configurações semelhantes.

## Motivação

Ao trabalhar com diversos projetos Node.js, é comum replicar arquivos de workflow para CI/CD, testes, lint, build, etc. Isso gera retrabalho e dificulta a manutenção. Com este boilerplate, você pode aninhar (reusar) workflows, mantendo-os padronizados e fáceis de atualizar.

## Como funciona

- Os workflows são definidos em `.github/workflows/`.
- Utiliza o recurso de [Reusable Workflows](https://docs.github.com/pt/actions/using-workflows/reusing-workflows) do GitHub Actions.
- Outros projetos podem chamar estes workflows via `workflow_call`.
- Permite centralizar lógica de CI/CD, testes, lint, build, deploy, etc.

## Como reutilizar

1. No seu projeto, crie um workflow que chame o workflow deste repositório:

```yaml
name: CI
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  call-reusable:
    uses: usuario/simple-workflow-nodejs-boilerplate/.github/workflows/nodejs-reusable.yml@main
    with:
      # parâmetros opcionais
    secrets: inherit
```

2. Adapte os parâmetros conforme necessário.

## Benefícios

- **Padronização:** Todos os projetos seguem o mesmo fluxo de CI/CD.
- **Manutenção centralizada:** Atualize o workflow em um só lugar.
- **Redução de código duplicado:** Menos arquivos para manter em múltiplos repositórios.

## Estrutura

```
.github/
  workflows/
    nodejs-reusable.yml
README.md
```

## Contribuindo

Sinta-se à vontade para abrir issues ou pull requests para sugerir melhorias ou reportar problemas.

## Licença

MIT

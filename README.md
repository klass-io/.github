# .github

Arquivos padrão da organização **klass-io** no GitHub.

O GitHub usa os arquivos deste repositório em **todo** repositório da organização que não tiver o seu próprio arquivo do mesmo tipo, seja ele público ou privado. Se um repositório criar o próprio `CONTRIBUTING.md`, por exemplo, ele substitui o daqui só naquele repositório.

> ⚠️ Este repositório é **público**, porque o GitHub exige isso. Nada de segredo, arquitetura interna, endereço de ambiente de homologação ou dado pessoal de clientes e usuários aqui. Esse conteúdo fica no `docs-klass-hub`.

## O que tem aqui

| Arquivo | Para que serve |
|---|---|
| `profile/README.md` | Página pública da organização em github.com/klass-io |
| `CONTRIBUTING.md` | Guia do time: branches, commits, PRs e revisão |
| `SECURITY.md` | Como reportar uma vulnerabilidade |
| `SUPPORT.md` | Onde pedir ajuda (clientes, usuários e time) |
| `ISSUE_TEMPLATE/` | Formulários de issue: bug, melhoria e tarefa técnica |
| `pull_request_template.md` | Modelo padrão de PR (`feature/*` → `homolog`) |
| `PULL_REQUEST_TEMPLATE/` | Modelos de PR para release (`homolog` → `production`) e hotfix |
| `.github/workflows/` | CI central, chamado pelos repositórios: `node-ci.yml` (API, apps e `lib-klass-design`), `vault-check.yml` (cofre) e `terraform-check.yml` (infra) |
| `workflow-templates/` | Atalho em **Actions → New workflow** que cria o `ci.yml` de cada repositório já chamando o `node-ci.yml` |

## O que **não** dá para definir aqui

Estes arquivos precisam existir em cada repositório, porque o GitHub não aceita um padrão da organização para eles:

- `LICENSE`
- `CODEOWNERS`
- `.github/dependabot.yml`
- `.github/workflows/ci.yml`: cada repositório precisa do seu, mesmo que só chame o CI central daqui. O deploy também fica nele, porque usa os secrets de cada repositório

A proteção das branches `production` e `homolog` é configurada pelo Terraform no `tool-klass-infra`.

## Como um repositório usa o CI central

O CI roda em **todo push, em qualquer branch**. O `ci.yml` de cada repositório chama o central:

```yaml
jobs:
  ci:
    uses: klass-io/.github/.github/workflows/node-ci.yml@main
```

Mudou o CI aqui, muda em todos os repositórios no próximo push. Este repositório precisa continuar **público** para os repositórios privados conseguirem chamar esses workflows.

## Página só para membros

Para mostrar uma página interna a quem é membro da organização (links do cofre, Penpot, ambientes), crie um repositório **privado** chamado `.github-private` com um `profile/README.md`.

# .github

Arquivos padrão da organização **klass-io** no GitHub.

O GitHub usa os arquivos deste repositório em **todo** repositório da organização que não tiver o seu próprio arquivo do mesmo tipo, seja ele público ou privado. Se um repositório criar o próprio `CONTRIBUTING.md`, por exemplo, ele substitui o daqui só naquele repositório.

> ⚠️ Este repositório é **público**: o GitHub só aplica os arquivos padrão e mostra o `profile/README.md` da organização se ele for público. Qualquer pessoa na internet lê o que estiver aqui. Nada de segredo, nome de repositório interno, arquitetura, fornecedores, endereço de homologação ou do backoffice, nem dado pessoal de clientes e usuários. Esse conteúdo fica no `docs-klass-hub`.

## O que tem aqui

| Arquivo | Para que serve |
|---|---|
| `profile/README.md` | Página pública da organização em github.com/klass-io |
| `CONTRIBUTING.md` | Regras básicas de contribuição; o guia completo do time fica no cofre |
| `SECURITY.md` | Como reportar uma vulnerabilidade |
| `SUPPORT.md` | Onde pedir ajuda (clientes, usuários e time) |
| `ISSUE_TEMPLATE/` | Formulários de issue: bug, melhoria e tarefa técnica |
| `pull_request_template.md` | Modelo padrão de PR (`feature/*` → `homolog`) |
| `PULL_REQUEST_TEMPLATE/` | Modelos de PR para release (`homolog` → `production`) e hotfix |
| `.github/workflows/` | CI central, chamado pelos repositórios: `node-ci.yml` (projetos Node), `vault-check.yml` (cofre) e `terraform-check.yml` (infra) |
| `.github/dependabot.yml` | Atualização semanal das actions usadas pelo CI central |
| `workflow-templates/` | Atalho em **Actions → New workflow** que cria o `ci.yml` de cada repositório já chamando o `node-ci.yml` |

## O que **não** dá para definir aqui

Estes arquivos precisam existir em cada repositório, porque o GitHub não aceita um padrão da organização para eles:

- `LICENSE`: nos repositórios privados, uma licença proprietária ("Todos os direitos reservados")
- `CODEOWNERS`
- `.github/dependabot.yml`
- `.github/workflows/ci.yml`: cada repositório precisa do seu, mesmo que só chame o CI central daqui. O deploy também fica nele, porque usa os secrets de cada repositório

## Como um repositório usa o CI central

O CI roda em **todo push, em qualquer branch**. O `ci.yml` de cada repositório chama o central:

```yaml
jobs:
  ci:
    uses: klass-io/.github/.github/workflows/node-ci.yml@main
```

Mudou o CI aqui, muda em todos os repositórios no próximo push. Por isso a `main` deste repositório precisa ser protegida (sem push direto, PR com aprovação) e as actions de terceiros ficam fixadas por SHA, com o Dependabot propondo as atualizações.

## Página só para membros

Para mostrar uma página interna a quem é membro da organização (links do cofre, ferramentas, ambientes), crie um repositório **privado** chamado `.github-private` com um `profile/README.md`.

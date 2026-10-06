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
| `pull_request_template.md` | Modelo padrão de PR, para **homologação** (`feature/*` → `homolog`) |
| `PULL_REQUEST_TEMPLATE/production.md` | Modelo de PR para **produção** (`homolog` → `production`) |
| `PULL_REQUEST_TEMPLATE/hotfix.md` | Modelo de PR para **hotfix** (`hotfix/*` → `production`) |

## O que **não** dá para definir aqui

Estes arquivos precisam existir em cada repositório, porque o GitHub não aceita um padrão da organização para eles:

- `LICENSE`: nos repositórios privados, uma licença proprietária ("Todos os direitos reservados")
- `CODEOWNERS`
- `.github/dependabot.yml`, incluindo o ecossistema `github-actions`
- `.github/workflows/`: cada repositório tem o próprio CI/CD, completo, sem depender de nenhum workflow daqui

## Templates de PR

O GitHub não escolhe o template pelo branch de destino: o padrão (homologação) aparece sozinho, e os outros são abertos acrescentando ao endereço de criação do PR:

- `?template=production.md` para levar `homolog` a produção
- `?template=hotfix.md` para uma correção urgente em produção

A `main` deste repositório precisa ser protegida (sem push direto, PR com aprovação), configurada pelo Terraform como a dos outros repositórios.

## Página só para membros

Para mostrar uma página interna a quem é membro da organização (links do cofre, ferramentas, ambientes), crie um repositório **privado** chamado `.github-private` com um `profile/README.md`.

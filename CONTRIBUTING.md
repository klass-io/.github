# Guia do time Klass

Este é o guia de trabalho de quem faz parte do time do Klass. Os repositórios da organização **klass-io** são privados: só membros do time abrem issues e pull requests. As regras valem para todos eles, a não ser que o repositório tenha o seu próprio `CONTRIBUTING.md`.

O passo a passo de cada repositório (instalação, variáveis de ambiente, comandos) fica no `README.md` dele. As decisões de produto e de arquitetura ficam no cofre de documentação (`docs-klass-hub`), que é a fonte única da verdade.

## Antes de começar

1. Todo trabalho nasce de um **card** no Kanban Klass. Feature nasce de uma **spec aprovada** (passou pelo DoR).
2. Termo novo do domínio entra primeiro no Glossário, depois no código.
3. Decisão cara de reverter, que afeta várias features ou que envolve segurança, LGPD ou dinheiro pede uma **ADR** antes do código.

## Repositórios

O nome segue o padrão `<tipo>-<produto>-<escopo>`:

| Repositório | Conteúdo |
|---|---|
| `api-klass-api` | API (backend) |
| `lib-klass-design` | Componentes e tokens do Design System |
| `mobile-klass-familia` | App dos responsáveis e alunos |
| `mobile-klass-professor` | App do professor |
| `web-klass-gestor` | Portal do gestor da escola |
| `web-klass-admin` | Backoffice do time Klass |
| `tool-klass-bruno` | Coleções do Bruno para testar a API |
| `tool-klass-infra` | Infraestrutura como código (Terraform) |

## Branches

Usamos um Git Flow simplificado:

| Branch | Para quê | Sai de | Entra em |
|---|---|---|---|
| `production` | O que está em produção | — | — |
| `homolog` | Integração e homologação | — | `production` |
| `feature/*` | Trabalho novo | `homolog` | `homolog` |
| `hotfix/*` | Correção urgente em produção | `production` | `production` **e** `homolog` |

Nome da branch: `tipo/<card_id>-descricao-curta`, por exemplo `feature/42-diario-fotos` ou `hotfix/57-corrige-push-duplicado`. O nome do repositório fica fora da branch.

`production` e `homolog` são protegidas: não aceitam push direto, exigem CI verde, e `production` só recebe PR de `homolog` ou de `hotfix/*`.

Repositórios que não têm deploy (`docs-klass-hub`, `tool-klass-bruno`) usam só a `main`.

## Commits

Seguimos o [Conventional Commits](https://www.conventionalcommits.org/pt-br/v1.0.0/). O commitlint confere a mensagem no pre-commit e no CI.

```
<tipo>(<escopo>): <resumo no imperativo, minúsculo, sem ponto final>
```

| Tipo | Quando usar |
|---|---|
| `feat` | Funcionalidade nova |
| `fix` | Correção de bug |
| `refactor` | Mudança de código sem mudar comportamento |
| `perf` | Melhoria de desempenho |
| `test` | Testes |
| `docs` | Documentação |
| `build` | Dependências, build, Docker |
| `ci` | Pipelines do GitHub Actions |
| `chore` | Manutenção que não entra em nenhum dos outros |

O escopo é o módulo ou contexto do domínio: `feat(attendance): ...`, `fix(grades): ...`.

Mudança que quebra contrato (API, pacote do `lib-klass-design`) leva `!` depois do tipo e um rodapé `BREAKING CHANGE:` explicando o impacto.

## Pull requests

- Um PR = um card. PR pequeno é revisado mais rápido e com mais cuidado.
- Preencha o modelo de PR: ele traz o checklist da Definition of Done.
- Título no mesmo formato dos commits: `feat(attendance): finaliza a chamada da aula`.
- Link para o card e para a spec no corpo do PR.
- O merge só acontece com CI verde e pelo menos uma aprovação.
- Para abrir um PR de release ou de hotfix, acrescente `?template=release.md` ou `?template=hotfix.md` ao endereço de criação do PR.

## Padrões de código

- **Código em inglês**, com os nomes do Glossário (`Person`, `Guardian`, `Enrollment`, `Attendance`…). Nenhum texto em português no código: tudo que o usuário vê passa pelo i18n (pt-BR padrão; en e es com a estrutura pronta).
- ESLint + Prettier rodam no pre-commit e no CI. Não desligue regra sem explicar o porquê no próprio código.
- Parâmetros de função sempre nomeados (objeto desestruturado).
- Valor de um conjunto fixo e conhecido vira enum, no código e no banco.
- Datas em UTC no banco; `America/Sao_Paulo` só na apresentação.
- Comentário explica o **porquê**, não o quê.
- Teste citando a regra de negócio: `describe('RN03 - ...')` e `it('dado X, quando Y, então Z')`.

## Segurança e privacidade

O Klass lida com dados de crianças e adolescentes. Segurança e privacidade vêm antes de prazo, simplicidade e UX.

- Nunca faça commit de `.env`, chave, token ou dado real de escola, aluno ou família. Use o `.env.example` e os dados de exemplo.
- CPF nunca aparece completo na interface.
- Dado de menor e dado pessoal nunca vão para log.
- Encontrou uma vulnerabilidade? **Não abra issue.** Siga o [SECURITY.md](SECURITY.md).

## Revisão de código

Quem revisa olha, nesta ordem:

1. A mudança faz o que a spec pede, citando as RNs?
2. Nenhum dado atravessa escolas, e a autorização por vínculo continua garantida (responsável só vê os próprios dependentes, professor só as próprias turmas)?
3. Há testes para o caminho feliz e para os caminhos tristes da spec?
4. O código segue as convenções e as ADRs vigentes?

Comentário de revisão é sobre o código, nunca sobre a pessoa. Use os prefixos `bloqueante:`, `sugestão:` e `dúvida:` para deixar claro o peso de cada comentário.

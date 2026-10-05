<!-- Release: homolog → production -->

## Release

**Data prevista:**

## O que entra

| Card | Título | Tipo |
|---|---|---|
| # | | feat / fix / chore |

## Antes do merge

- [ ] Todos os cards da lista estão verificados (DoD completo)
- [ ] Testado em homologação, incluindo os e2e obrigatórios
- [ ] Migrations conferidas: compatíveis com a versão anterior ou com plano de janela
- [ ] Variáveis de ambiente novas já criadas em produção
- [ ] Nenhuma mudança que quebra contrato sem versão nova da API ou do `lib-klass-design`
- [ ] Release fora do horário de aula, se mexe em chamada, notas ou push

## Plano de volta

<!-- O que fazer se der errado: reverter o deploy, desligar a feature, rodar a migration de volta. -->

## Depois do merge

- [ ] Deploy de produção concluído
- [ ] Health check e painéis do SigNoz sem erro novo
- [ ] Cards movidos no Kanban

<!--
  HOMOLOGAÇÃO: feature/* → homolog
  Produção: ?template=production.md · Hotfix: ?template=hotfix.md
  Pergunta deste PR: "está pronto para ser testado em homologação?"
-->

## O que muda

<!-- 2 ou 3 frases. O porquê importa mais que o quê. -->

## Card e spec

- Card: #
- Spec:
- RNs cobertas:
- ADRs aplicadas:

## Como testar em homologação

<!-- Roteiro que outra pessoa consegue seguir sem te perguntar nada. -->

- **Perfil e escola de teste:**
- **Dados de exemplo necessários:**

1.
2.

**Resultado esperado:**

## Prints

<!-- Obrigatório se mexe em tela. Sem dado real de aluno ou família. -->

## Mudanças de dados e configuração

- [ ] Não há migration, seed ou variável de ambiente nova
- [ ] Migration revisada e compatível com a versão anterior (o deploy não quebra quem ainda roda o código antigo)
- [ ] Seed atualizado para entidade nova (idempotente, travado contra produção)
- [ ] Variável de ambiente nova criada em homologação e listada no `.env.example`
- [ ] Atrás de feature flag: `nome-da-flag` (estado em homologação: ligada / desligada)

## Checklist (DoD)

**Escola, segurança e LGPD**
- [ ] Toda consulta e escrita está escopada à escola do contexto: nenhum dado atravessa escolas
- [ ] Autorização por vínculo conferida (responsável só os próprios dependentes, professor só as próprias turmas, aluno só a si)
- [ ] CPF sempre mascarado na interface
- [ ] Nenhum dado de menor ou dado pessoal vai para log
- [ ] Acesso a dado sensível ou ação irreversível coberto pela auditoria

**Modelo temporal**
- [ ] Dado acadêmico pendurado em matrícula ou enturmação, nunca direto na pessoa
- [ ] Toda referência a turma considera o ano letivo

**Produto**
- [ ] Comunicação continua só da escola para a família
- [ ] Push enviado quando a spec pede, para os responsáveis certos
- [ ] Ação destrutiva ou irreversível tem modal explicando a consequência
- [ ] Textos passam pelo i18n

**Técnico**
- [ ] Testes unitários do caminho feliz e dos caminhos tristes da spec
- [ ] E2E, quando o fluxo exige
- [ ] Contrato da API (OpenAPI) atualizado para rota criada, alterada ou removida
- [ ] Modelo de Dados, Contratos e Glossário atualizados, se mudaram

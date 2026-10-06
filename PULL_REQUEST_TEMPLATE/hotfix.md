<!--
  HOTFIX: hotfix/* → production
  Correção urgente de um problema que já está em produção. Mínima, revisada e com volta rápida.
  Depois do merge, abra o mesmo hotfix para homolog.
-->

## Problema em produção

<!-- O que quebrou, desde quando e quais escolas ou perfis são afetados. -->

- Card ou issue: #
- **Gravidade:** crítica / alta / média
- **Começou em:**
- **Escolas ou perfis afetados:**

## Correção

<!-- O que muda e por que é a menor correção segura. -->

## Como foi verificado

1.

## Risco e volta

- **O que pode dar errado com esta correção:**
- **Como voltar:** <!-- reverter o deploy para a versão anterior / desligar a flag -->

## Checklist

- [ ] A correção é mínima: nada além do necessário para resolver o problema
- [ ] Teste que reproduz o bug e passa com a correção
- [ ] Sem migration, ou migration compatível com a versão anterior
- [ ] Revisado por pelo menos uma pessoa além de quem escreveu
- [ ] Se houve exposição de dado pessoal, o plano de incidente (LGPD) foi acionado e as escolas afetadas avisadas
- [ ] Quem acompanha depois do deploy: @
- [ ] PR do mesmo hotfix para `homolog` aberto: #

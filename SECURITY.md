# Política de segurança

O Klass guarda dados de escolas, famílias, crianças e adolescentes. Se você encontrou uma vulnerabilidade, agradecemos por nos avisar de forma responsável.

## Como reportar

**Não abra uma issue pública, não comente em PR e não divulgue a falha** antes de ela ser corrigida.

Reporte pelo **GitHub Private Vulnerability Reporting**, neste link: [github.com/klass-io/.github/security/advisories/new](https://github.com/klass-io/.github/security/advisories/new). O relatório chega só ao time, nunca fica público. Use esse mesmo link para qualquer parte do produto: os outros repositórios da organização são privados.

Inclua, se possível:

- o que a falha permite fazer e qual o impacto;
- o passo a passo para reproduzir (endereço, requisição, payload);
- a versão, o navegador ou o aparelho usados;
- como você sugere corrigir, se tiver uma ideia.

## O que esperar de nós

| Etapa | Prazo |
|---|---|
| Confirmação de recebimento | até 2 dias úteis |
| Avaliação inicial e classificação de gravidade | até 5 dias úteis |
| Atualizações sobre a correção | pelo menos a cada 7 dias |

Quando a falha envolver dados pessoais, seguimos o nosso plano de resposta a incidentes e as obrigações da LGPD. Avisamos as escolas afetadas, que são as controladoras dos dados, e apoiamos a comunicação à ANPD e aos titulares quando for o caso.

Com a sua autorização, damos o crédito pela descoberta quando a correção for publicada.

## Escopo

**Dentro do escopo:**

- `klass.com.br` e os subdomínios dele
- o código dos repositórios da organização **klass-io**

**Fora do escopo:**

- ataques de negação de serviço (DoS/DDoS) e testes de carga;
- engenharia social, phishing ou ataque físico contra o time, as escolas ou as famílias;
- falhas em serviços de terceiros que usamos (reporte direto ao fornecedor);
- relatórios automáticos de scanners sem prova de impacto;
- ausência de cabeçalhos ou boas práticas sem uma exploração concreta.

## Regras para pesquisa de boa-fé

- Use apenas contas suas ou de teste. Nunca acesse, altere ou apague dados de outras pessoas.
- Se encontrar dados pessoais por acidente, principalmente de crianças e adolescentes, pare, não guarde cópia e nos avise.
- Não degrade o serviço para os usuários.

Quem seguir estas regras agindo de boa-fé não sofrerá nenhuma ação nossa por causa da pesquisa.

No momento, o Klass não tem programa de recompensa (bug bounty).

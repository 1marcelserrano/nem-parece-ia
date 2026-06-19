# CLAUDE.md — nem-parece-ia

## O que é este repo

Uma skill do Claude distribuída como repositório público no GitHub. A única
fonte de verdade do comportamento é `skills/nem-parece-ia/SKILL.md`. Toda
mudança de comportamento começa por lá.

A skill faz revisão editorial em PT-BR: detecta marcas de escrita artificial
por camadas (frases, estruturas, ritmo, registro) e reescreve com agente, ação
e consequência. O repo é uma vitrine — o README é uma landing page, não só
documentação.

## O que editar

| Arquivo | O que controla |
|---------|----------------|
| `skills/nem-parece-ia/SKILL.md` | Comportamento — triggers, fluxo, regras, rubrica. PT-BR, canônico. |
| `skills/nem-parece-ia/references/*.md` | Taxonomias por camada (frases, estruturas, ritmo, metáforas, formatação, hermetismo, registros, exemplos, checklist). |
| `skills/nem-parece-ia/README.md` | Resumo por-skill voltado pra humano. |
| `README.md` (raiz) | Porta de entrada do produto. Otimizar pra quem tem rascunho com cara de IA. |
| `assets/social-preview.html` | Instância do gabarito DS V3.0 (motivo cleanup) do social card. |
| `page/index.html` | Página-vitrine interativa publicada na Vercel. |

## O que NÃO editar

- Não edite a skill canônica no monorepo privado `mscs-skills` a partir daqui —
  este repo é um espelho publicado. Mudanças de comportamento fluem pelo `skills-sync`.
- Mantenha o frontmatter do SKILL.md (`name`, `description`) intacto.
- Não fabrique números de eficácia. O valor vem do método, não de marketing.
- Nunca commite `.env`, tokens ou credenciais.

## Convenções

- Idioma: README/skill em PT-BR; voz Tradutor, frases curtas, voz ativa, zero floreio.
  (A própria skill caça os vícios — a documentação tem que ser exemplar.)
- Commits: Conventional Commits. Push só com SHA verificado (local = remote).

## Licença

MIT. Inspirada em `hardikpandya/stop-slop` (MIT), recriada pra PT-BR.
Contribuições bem-vindas. Ver CONTRIBUTING.md.

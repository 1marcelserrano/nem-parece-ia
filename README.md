# nem-parece-ia

**Tira a cara de IA do texto. Sem matar a voz.**

Uma skill do Claude que revisa textos em português do Brasil que soam artificiais, genéricos, inflados ou com cheiro de LLM. Ela corta o que anuncia, infla ou teatraliza, e preserva o que informa, situa, prova ou move o texto. Um arquivo markdown. Sem servidor, sem dependência.

[Instalar](#instalar) · [O que ela corrige](#o-que-ela-corrige) · [Quando usar](#quando-usar) · [Exemplo](#exemplo) · [FAQ](#faq) · [Página](https://nem-parece-ia-page.vercel.app)

---

Texto de IA chega certo, mas sem vida. Claro, mas genérico. Bem formatado, mas previsível. Abre com "é importante destacar que", promete "impacto significativo" sem dizer qual, fecha cada parágrafo numa frase de efeito. Você sente que tem algo errado antes de saber nomear o quê.

A skill nomeia. Ela separa o problema em camadas — frases prontas, estruturas artificiais, ritmo robótico, registro errado — e ataca cada uma com uma regra concreta. O objetivo não é enganar detector nem simular imperfeição. É melhorar texto ruim: mais direto, mais específico, com agente, ação e consequência no lugar de abstração.

## O problema

Um rascunho de IA acerta a gramática e erra a voz. Os tells são previsíveis: abertura vazia, sujeito abstrato fazendo ação humana ("o mercado exige"), contraste fabricado ("não é sobre X, é sobre Y"), tríade automática, cópula inflada ("serve como" em vez de "é"), gerúndio decorativo colado no fim da frase. Sozinho, cada um é pequeno. Juntos, denunciam a origem.

Trocar palavra por sinônimo não resolve — mantém a mesma estrutura robótica por baixo. Por isso a revisão é por camadas, da frase à arquitetura do parágrafo.

## O que ela corrige

A skill divide o texto em cinco camadas. Cada uma tem um arquivo de referência carregado só quando a tarefa precisa.

| Camada | O que procura | Correção típica |
|--------|---------------|-----------------|
| **Frases** | Abertura vazia, conector morto, intensificador, jargão | "É importante destacar que" → começa direto |
| **Estruturas** | Contraste fabricado, falsa agência, passiva evasiva, cópula inflada | "O mercado exige" → "clientes B2B recusam contrato sem SLA" |
| **Ritmo** | Tríade previsível, punchline automática, cadência de metrônomo | "Clareza. Consistência. Presença." → relação causal |
| **Registro** | Ajuste por canal e gênero | E-mail preserva cortesia; documentação preserva passiva útil |
| **Exemplos** | Modelos antes/depois | Guia de reescrita, sem aplicar regra cega |

O passo que separa a skill de um "deixa mais natural" genérico é a **auto-auditoria final**: depois de reescrever, ela relê e pergunta "o que ainda denuncia origem artificial aqui?", lista os tells restantes em uma linha e corrige antes de entregar.

## Quando usar

**Use quando:**
- O rascunho parece correto, mas sem vida; claro, mas genérico
- O texto está cheio de jargão corporativo e promessa vaga
- O post tem "não é sobre X, é sobre Y" usado como efeito
- Você quer naturalizar post, artigo, e-mail, institucional, landing, proposta ou relatório em PT-BR

**Não use quando:**
- O pedido é burlar detector de IA ou ocultar autoria → não é isso que ela faz
- O texto está em outro idioma sem adaptação pra PT-BR
- A artificialidade é intencional (texto literário, paródia)
- O problema é gramática pura, sem questão de voz

A skill não esteriliza. Ela calibra por registro: um e-mail mantém cortesia, um acadêmico mantém cautela, uma documentação mantém passiva quando a passiva carrega precisão. Texto limpo sem opinião nem ritmo denuncia tanto quanto slop.

## Exemplo

**Antes** — abertura de um institucional:

> *No cenário atual, é fundamental destacar que a inovação tem desempenhado um papel cada vez mais relevante. Não se trata apenas de tecnologia, mas de pessoas. Nossa solução serve como um catalisador, impulsionando resultados e refletindo nosso compromisso com a excelência.*

Os tells: abertura vazia ("no cenário atual", "é fundamental destacar que"), falsa agência ("a inovação tem desempenhado"), contraste fabricado ("não se trata apenas de X, mas de Y"), cópula inflada ("serve como"), gerúndio decorativo ("impulsionando", "refletindo"), abstração sem prova ("excelência").

**Depois:**

> *Reduzimos o tempo de implantação de seis semanas para nove dias. O time do cliente parou de abrir chamado pra tarefa que agora roda sozinha. É isso que a gente entrega.*

Mesma intenção. Agente nomeado, número concreto, consequência verificável. Sem floreio.

Método completo em [`skills/nem-parece-ia/SKILL.md`](./skills/nem-parece-ia/SKILL.md) e nas [referências](./skills/nem-parece-ia/references/).

## Instalar

```bash
# Via skills CLI (recomendado)
npx skills add 1marcelserrano/nem-parece-ia

# Ou manualmente — faça backup antes se a pasta já existir:
# mv ~/.claude/skills/nem-parece-ia ~/.claude/skills/nem-parece-ia.backup
git clone https://github.com/1marcelserrano/nem-parece-ia.git
cp -r nem-parece-ia/skills/nem-parece-ia ~/.claude/skills/
```

**Verifique:** abra uma sessão nova do Claude e rode `/skills` (ou pergunte "que skills você tem?"). `nem-parece-ia` deve aparecer. Se não, confira que `~/.claude/skills/nem-parece-ia/SKILL.md` existe e reinicie a sessão.

**Sem terminal?** Baixe [`nem-parece-ia.skill`](./nem-parece-ia.skill) e suba no Claude (Cowork / claude.ai → Skills).

**Testar sem instalar:** abra [`SKILL.md`](./skills/nem-parece-ia/SKILL.md), copie o conteúdo inteiro, cole numa conversa nova e em seguida cole o texto a revisar.

## FAQ

**Isso burla detector de IA?** Não, e não é o objetivo. A skill melhora clareza, especificidade e ritmo. Quem só quer enganar detector está pedindo a coisa errada.

**Precisa de API key, conta paga ou servidor?** Não. É um arquivo markdown que o Claude carrega. Roda onde o Claude roda.

**Vai deixar meu texto seco e sem alma?** Não deve. A skill calibra por registro e tem uma dimensão de avaliação só pra isso ("Vida"): texto limpo sem opinião nem ritmo perde tanto ponto quanto texto inflado.

**Funciona em qualquer gênero?** Funciona melhor em PT-BR: post, artigo, e-mail, institucional, landing, proposta, relatório, trecho acadêmico. Ela detecta o registro antes de editar e ajusta a agressividade do corte.

**Por que é em português, e não tradução do inglês?** Os tells de IA em PT-BR são próprios: jargão de LinkedIn local, ritmo traduzido do inglês, fórmulas de thought leadership brasileiras. A taxonomia foi reconstruída pra isso, não traduzida.

---

Uma skill do **[MSCREATIVE.SYSTEMS™](https://fronteirista.substack.com)**. Inspirada no projeto público [`hardikpandya/stop-slop`](https://github.com/hardikpandya/stop-slop) (MIT), recriada pra padrões do português brasileiro. Licença MIT — use, modifique, redistribua. Mantenha os créditos.

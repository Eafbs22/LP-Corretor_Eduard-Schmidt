# [Nome Profissional] — Kit Imobiliário

## O que é esse workspace
Workspace de criação de conteúdo e automação de [Nome] — corretor autônomo focado em [foco] na região de [cidade/bairros].

**Estrutura de pastas:**
- `conteudo/carrosseis/` — carrosséis gerados pra Instagram/TikTok
- `conteudo/roteiros/` — roteiros de vídeo e posts
- `conteudo/ideias/` — banco de ideias e pautas
- `clientes/` — informações e histórico de clientes
- `imoveis/` — fichas e materiais de imóveis em carteira
- `dados/` — arquivos pra análise (CSV, XLSX, PDF)
- `templates/skills/` — templates de skills prontos pra personalizar com /mapear
- `templates/ferramentas/catalogo.md` — APIs e ferramentas disponíveis pra usar em skills

## Sobre o profissional
[Nome completo], corretor autônomo com CRECI [número se mencionou].
Foco em [residencial/comercial/lançamentos/aluguel] na região de [cidade — bairros].
Atende principalmente [perfil do público-alvo].

## Plataformas de conteúdo
[Instagram / TikTok / ambas] — formatos prioritários: [carrossel / reels / stories]

## Clientes e contexto
Atende clientes diretamente, sem intermediação de imobiliária.
Perfil principal: [compradores de primeira moradia / investidores / famílias / locatários].

## Tom de voz
[como escrever, o que evitar, exemplos se mencionou]

## Ferramentas conectadas
[lista das ferramentas que usa — atualizar conforme MCPs forem instalados]

---

## Contexto do negócio

No início de toda conversa, ler os seguintes arquivos (se existirem e estiverem configurados):

1. `_contexto/empresa.md` — quem é o corretor, como atua, foco e público
2. `_contexto/preferencias.md` — tom de voz, estilo de escrita, o que evitar
3. `_contexto/estrategia.md` — foco atual de conteúdo, prioridades, o que pode esperar

Usar essas informações como base pra qualquer resposta ou decisão. Ao sugerir temas, formatos ou abordagens de conteúdo, considerar o foco atual descrito em `estrategia.md`.

Para qualquer tarefa visual (carrossel, slide, post), consultar `marca/design-guide.md` como referência de estilo.

Não é necessário listar o que foi lido nem confirmar a leitura. Apenas usar o contexto naturalmente.

---

## Fluxo de trabalho

Antes de executar qualquer tarefa, verificar se existe uma skill relevante em `.claude/skills/` ou `.claude/commands/`.
Se encontrar, seguir as instruções da skill.
Se não encontrar, executar a tarefa normalmente.

Ao concluir uma tarefa que não tinha skill mas parece repetível, perguntar:

> "Isso pode virar uma skill pra próxima vez. Quer que eu crie?"

---

## Aprender com correções

Quando o usuário corrigir algo ou dar instrução permanente, perguntar:

> "Quer que eu salve isso pra não precisar repetir?"

- **Sobre o negócio** → `_contexto/empresa.md`
- **Sobre preferências e estilo** → `_contexto/preferencias.md`
- **Sobre prioridades e foco** → `_contexto/estrategia.md`
- **Regra de comportamento** → `CLAUDE.md`

---

## Manter contexto atualizado

Ao terminar tarefa que mudou algo relevante, perguntar:

> "Isso mudou algo no teu contexto. Quer que eu atualize os arquivos de memória?"

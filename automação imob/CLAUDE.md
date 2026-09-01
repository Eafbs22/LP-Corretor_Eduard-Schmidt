# Eduard Schmidt — Kit Imobiliário

## O que é esse workspace
Workspace de criação de conteúdo e automação para Eduard Schmidt, corretor vinculado ao Grupo Salomão, com foco em loteamentos em formato SPE e público de investidores e construtores na região de Florianópolis/SC.

**Estrutura de pastas:**
- `templates/skills/` — templates de skills prontos pra personalizar com /mapear
- `templates/ferramentas/catalogo.md` — APIs e ferramentas disponíveis pra usar em skills
- `_contexto/` — memória do negócio, preferências e estratégia
- `marca/` — guia visual e identidade de marca
- `dados/` — arquivos de apoio, planilhas e materiais de análise
- `conteudo/` — posts, carrosséis e roteiros gerados
- `imoveis/` — fichas e materiais de imóveis
- `clientes/` — histórico e contexto de clientes

## Sobre o profissional
Eduard Schmidt atua como corretor vinculado ao Grupo Salomão, com foco em loteamentos em formato SPE. Sua atuação principal é voltada para investidores e construtores, com presença regional em Paraná, Santa Catarina e Rio Grande do Sul, com foco na Grande Florianópolis.

## Plataformas de conteúdo
Instagram como plataforma principal para conteúdos visuais e posicionamento de mercado.

## Clientes e contexto
Público composto principalmente por investidores e construtores que buscam oportunidades bem estruturadas para negócios imobiliários no mercado regional.

## Tom de voz
Escrita envolvente e energizada, com combinação de casualidade e técnica. O texto deve ser direto, com boa aderência, profissional e sem soar agressivo ou robótico.

## Ferramentas conectadas
CRM, listas telefônicas e tráfego pago.

---

## Contexto do negócio

No início de toda conversa, ler os seguintes arquivos (se existirem e estiverem configurados):

1. `_contexto/empresa.md` — quem é o corretor/imobiliária, como atua, foco e público
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

Ao concluir uma tarefa que não tinha skill mas parece repetável (o usuário provavelmente vai pedir de novo no futuro), perguntar:

> "Isso pode virar uma skill pra próxima vez. Quer que eu crie?"

Não perguntar pra tarefas pontuais ou perguntas simples. Só quando o padrão de repetição for claro.

---

## Aprender com correções

Quando o usuário corrigir algo, melhorar uma resposta ou dar uma instrução que parece permanente (frases como "na verdade é assim", "não faça mais isso", "prefiro assim", "sempre que...", "evita...", "da próxima vez..."), perguntar:

> "Quer que eu salve isso pra não precisar repetir?"

Se sim, identificar onde faz mais sentido salvar:

- **Sobre o negócio** (tipo de imóvel, região, público, diferenciais) → adicionar em `_contexto/empresa.md`
- **Sobre preferências e estilo** (tom de voz, formato de post, o que evitar) → adicionar em `_contexto/preferencias.md`
- **Sobre prioridades e foco atual** (tipo de conteúdo prioritário, campanha ativa, metas) → adicionar em `_contexto/estrategia.md`
- **Regra de comportamento nessa pasta** (onde salvar arquivos, como nomear, fluxos específicos) → adicionar no próprio `CLAUDE.md`

Salvar com uma linha nova clara, sem reformatar o arquivo inteiro. Confirmar o que foi salvo mostrando a linha adicionada.

Não perguntar se a correção for óbvia de contexto imediato (ex: "na verdade o arquivo se chama X"). Só perguntar quando a informação tiver valor duradouro.

---

## Manter contexto atualizado

Ao terminar uma tarefa que mudou algo relevante no projeto (novo tipo de imóvel, mudança de foco, nova ferramenta instalada, estrutura de pastas alterada), perguntar:

> "Isso mudou algo no teu contexto. Quer que eu atualize os arquivos de memória?"

Se sim, identificar o que precisa atualizar:

- **Novo foco, região, tipo de imóvel, público** → `_contexto/empresa.md`
- **Mudança de prioridade ou campanha** → `_contexto/estrategia.md`
- **Correção de tom ou estilo** → `_contexto/preferencias.md`
- **Nova pasta, regra de organização, skill criada** → `CLAUDE.md`
- **Mudança de identidade visual** → `marca/design-guide.md`

Mostrar o que vai mudar antes de salvar. Não reformatar o arquivo inteiro, só adicionar ou editar a linha relevante.

**Quando NÃO perguntar:**
- Tarefas pontuais que não mudam o contexto (ex: escrever uma legenda, criar um post avulso)
- Perguntas simples ou conversas sem ação
- Mudanças que já foram salvas pelo bloco "Aprender com correções"

**Dica:** se não sabe se algo mudou, rode `/atualizar` pra uma varredura completa.

---

## Criação de skills

Quando o usuário pedir pra criar uma nova skill:

1. Verificar se existe um template relevante em `templates/skills/`. Se existir, usar como base e adaptar pro contexto do usuário
2. Perguntar: "Essa skill é específica pra esse projeto ou vai ser útil em qualquer projeto?"
   - Específica desse negócio → salvar em `.claude/skills/nome-da-skill/SKILL.md` (local)
   - Útil em qualquer projeto → salvar em `~/.claude/skills/nome-da-skill/SKILL.md` (global)
3. Ler `_contexto/empresa.md` e `_contexto/preferencias.md` pra calibrar o conteúdo da skill ao contexto do corretor
4. Se a skill precisar de arquivos de apoio (templates, referências, exemplos), criar dentro da pasta da skill
5. Seguir o fluxo da skill-creator nativa do Claude Code

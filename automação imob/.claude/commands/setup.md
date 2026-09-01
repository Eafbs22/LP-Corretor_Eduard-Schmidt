---
name: setup
description: >
  Configura o kit imobiliário pro seu negócio. Faz perguntas sobre quem você é,
  como atua e como trabalha, e gera CLAUDE.md, memória, estrutura de pastas e
  lista de MCPs personalizados pro seu perfil de corretor ou imobiliária.
  Use quando o usuário chamar /setup, quando _contexto/empresa.md estiver vazio
  ou ausente, ou quando disser "configurar o sistema", "primeira vez", "setup".
---

# /setup — Configuração do Sistema

## Verificação inicial

Antes de qualquer coisa, verifique se `_contexto/empresa.md` existe e tem conteúdo real (não apenas o template).

- Se **não existe ou está vazio**: inicia o fluxo de onboarding abaixo.
- Se **já tem conteúdo**: informa ao usuário que o setup já foi feito e pergunta se quer refazer ou apenas atualizar alguma parte.

---

## Onboarding (primeira vez)

Comece com uma mensagem curta de boas-vindas:

> "Boa. Vou te fazer algumas perguntas pra configurar o sistema pro seu negócio. Responde com calma — quanto mais específico, melhor o sistema vai trabalhar pra ti."

Faça as perguntas em sequência, uma por vez, em conversa natural. Não liste todas de uma vez. Espere a resposta de cada uma antes de ir pra próxima.

### Pergunta 1

"Qual é o seu nome completo? E como você se identifica como corretor — o nome que você usa no Instagram, no cartão, quando se apresenta pras pessoas?"

*(Pode ser o nome completo, só o primeiro nome, apelido profissional — o que você usa no dia a dia)*

### Pergunta 2 — Verificação de histórico

"Você já usa o Claude Code há algum tempo, ou é a primeira vez?"

**Se já usa há algum tempo:** perguntar:

> "Quer que eu tente carregar o que você já tem configurado em outros projetos, ou prefere configurar do zero aqui?"

- **Se quiser carregar:** executar o bloco **"Carregamento de contexto existente"** abaixo antes de continuar.
- **Se preferir do zero:** continua normalmente pra Pergunta 3.

**Se for a primeira vez:** perguntar:

> "Você usa outro assistente de IA com frequência — ChatGPT, Claude na web, Gemini? Se sim, consigo pegar o contexto de lá pra não precisar responder tudo do zero."

- **Se não usa outro assistente:** continua normalmente pra Pergunta 3.
- **Se usa:** executar o bloco **"Importação de contexto de outro assistente"** abaixo antes de continuar.

---

#### Bloco: Carregamento de contexto existente (Claude Code anterior)

Tentar ler, nessa ordem:
1. `~/.claude/CLAUDE.md` — CLAUDE.md global (se existir)
2. Arquivos de memória em `~/.claude/projects/` — procurar por arquivos relevantes (empresa, preferências, contexto)

Com o que encontrar, montar um resumo e apresentar ao usuário:

> "Encontrei isso no que você já tem configurado:
>
> - **Nome / como atua:** [extraído]
> - **Foco e região:** [extraído]
> - **Tom de voz:** [extraído]
> - **Ferramentas:** [extraído]
> - *(... outras informações encontradas)*
>
> Está correto? Quer ajustar alguma coisa ou completar o que faltou?"

Aguardar confirmação ou correções do usuário. Após confirmar, **pular as perguntas já respondidas** e continuar apenas com o que ficou em aberto.

Se não encontrar nada relevante, informar:

> "Não encontrei contexto salvo de outros projetos. Vamos configurar do zero — leva poucos minutos."

E continuar normalmente pra Pergunta 3.

---

#### Bloco: Importação de contexto de outro assistente (ChatGPT, Claude web, Gemini, etc.)

Mostrar ao usuário o seguinte prompt pra copiar e colar no assistente que ele usa:

---

> **Copia esse prompt e cola no seu assistente de IA:**
>
> ```
> Preciso exportar o contexto do meu negócio das nossas conversas para configurar uma nova ferramenta. Por favor, responda com o que sabe sobre mim nas seguintes categorias — se não souber algo, deixe em branco:
>
> NOME: [seu nome completo e como se identifica profissionalmente]
> TIPO DE ATUAÇÃO: [corretor autônomo, vinculado a imobiliária, imobiliária própria, equipe]
> IMOBILIÁRIA: [nome da imobiliária se vinculado — ou "própria" se for sua]
> FOCO: [residencial, comercial, lançamentos, aluguel, misto]
> REGIÃO: [cidade e bairros onde atua]
> PÚBLICO: [perfil dos clientes que atende]
> PLATAFORMAS: [Instagram, TikTok, outros canais de conteúdo]
> FERRAMENTAS: [CRM, portais, WhatsApp Business, Canva etc]
> IDENTIDADE VISUAL: [cores, fontes, estilo da marca]
> TOM DE VOZ: [como prefere se comunicar e escrever]
> O QUE EVITAR: [o que te incomoda em textos gerados por IA]
> OUTROS DETALHES: [qualquer outro contexto relevante]
> ```

---

Após mostrar o prompt, dizer:

> "Cola isso no [nome do assistente que o usuário mencionou] e traz a resposta aqui."

Aguardar o usuário colar a resposta. Com o que vier:

1. Extrair todas as informações da resposta
2. Montar um resumo e apresentar pro usuário confirmar
3. Aguardar confirmação ou ajustes
4. **Pular as perguntas já respondidas** e continuar apenas com o que ficou em branco ou incerto

---

### Pergunta 3 — Tipo de atuação

"Você trabalha como corretor de que forma?"

Apresentar as opções de forma natural, não como lista formal:

> "É autônomo puro (sem imobiliária vinculada), autônomo mas com sua própria imobiliária, corretor vinculado a uma imobiliária, ou você representa uma imobiliária com equipe de corretores?"

**Se corretor vinculado a imobiliária:** fazer a pergunta complementar antes de continuar:

> "Qual é o nome da imobiliária? E como é essa relação — você é parceiro, funcionário, franqueado?"

*(Guardar essa informação — vai influenciar a identidade visual e o tipo de conteúdo gerado)*

### Pergunta 4 — Foco do negócio

"Qual é o seu foco principal — residencial, comercial, lançamentos, aluguel, ou você trabalha com mais de um?"

*(Pode ser combinação — ex: residencial + lançamentos. Detalhar se mencionar mais de um)*

### Pergunta 4.5 — Região de atuação

"Em que cidade e região você atua? Pode citar os bairros ou zonas principais se quiser."

*(Essa informação vai aparecer no conteúdo — posts, carrosséis, bio)*

### Pergunta 5 — Público-alvo

"Quem é o cliente que você mais atende?"

*(Exemplos: compradores de primeira moradia, famílias buscando upgrade, investidores, empresas em busca de espaço comercial, locatários — pode ser mais de um)*

### Pergunta 6 — Plataformas de conteúdo

"Em quais plataformas você quer criar conteúdo — Instagram, TikTok, as duas, ou outra?"

*(Isso vai definir os formatos dos carrosséis e roteiros gerados pelo sistema)*

### Pergunta 7 — Ferramentas

"Quais ferramentas você usa no dia a dia? Cita as principais."

*(Exemplos: WhatsApp Business, CRM — qual?, Zap Imóveis, Viva Real, OLX, Canva, Google Drive, planilhas — qualquer uma que use com frequência)*

### Pergunta 8 — Identidade visual

"Pra criar carrosséis e posts, preciso entender qual marca vamos usar como base."

Apresentar as opções de forma natural:

> "Você usa uma marca própria (seu nome ou marca pessoal), usa a marca da imobiliária para qual trabalha, ou ainda não tem uma identidade visual definida?"

**Se marca própria:**
- Perguntar: "Tem um site, Instagram ou material visual que eu possa analisar? Ou prefere descrever as cores e estilo em texto?"
- **Se compartilhar URL:** buscar o conteúdo com WebFetch, analisar cores, tipografia e estilo geral, apresentar o que foi detectado antes de preencher o design-guide:
  > "Vi no seu [site/Instagram]: fundo [cor], destaque em [cor], tipografia [descrição], estilo [adjetivo]. Bate com a sua marca?"
- **Se compartilhar imagens:** pedir pra jogar na pasta `dados/` e informar os nomes dos arquivos, ler como imagem e analisar
- **Se descrever em texto:** usar a descrição diretamente pra preencher `marca/design-guide.md`

**Se marca da imobiliária:**
- Perguntar: "Tem o site da imobiliária ou algum material visual pra eu analisar? Ou consegue descrever as cores e estilo deles?"
- Seguir o mesmo fluxo de análise (URL → imagem → texto)
- No `marca/design-guide.md`, registrar que é a identidade da imobiliária e o nome dela

**Se ainda não tem marca definida:**
- Preencher o `marca/design-guide.md` com campos em branco e orientações pra preencher depois
- Mencionar: "Sem problema — vou usar um visual clean e profissional até você definir. Quando tiver, é só me dizer que atualizo."

**Logo (perguntar em todos os casos acima):**

Após resolver cores e estilo, perguntar:

> "Tem o logo em PNG ou SVG? Se tiver, joga na pasta `marca/` e me diz o nome do arquivo. Se tiver versão pra fundo escuro e pra fundo claro, manda as duas."

- Se fornecer: preencher a seção **Logo** do `marca/design-guide.md` com o caminho e as variações
- Se não tiver: deixar a seção Logo em branco no design-guide

### Pergunta 9 — Tom de voz

"Como você prefere que o Claude escreva? O que mais incomoda em textos gerados por IA?"

*(Exemplos: "direto, sem enrolação, sem bullet points" / "odeio travessão e linguagem corporativa" / "pode ser informal, falo gíria com clientes" / "profissional mas próximo, não quero parecer robô")*

### Pergunta 10 — Equipe

"Você trabalha solo ou tem equipe? Se tiver imobiliária, quantos corretores na equipe?"

*(Pode mencionar parceiros, assistentes, sócios se tiver)*

---

## Processamento das respostas

Com todas as respostas, detecte o perfil principal:

**Perfis possíveis:**
- `corretor-autonomo` — corretor solo, sem imobiliária própria, atua de forma independente
- `corretor-imobiliaria-propria` — corretor autônomo que tem sua própria imobiliária (mesmo que pequena)
- `corretor-vinculado` — corretor que trabalha vinculado a uma imobiliária de terceiros
- `imobiliaria` — imobiliária com equipe de corretores, múltiplos profissionais

*(Um perfil pode ter características de outro — use o que melhor descreve o uso principal)*

---

## O que gerar

### 1. Atualizar `CLAUDE.md` na raiz

Substitua o conteúdo placeholder pelo CLAUDE.md real do usuário:

```markdown
# [Nome Profissional] — Kit Imobiliário

## O que é esse workspace
[uma ou duas frases descrevendo o que essa pasta representa — ex: "Workspace de criação de conteúdo e automação de [Nome] — corretor focado em [foco] na região de [cidade]."]

**Estrutura de pastas:**
[lista das pastas criadas e o que vai em cada uma — gerada conforme o perfil detectado]
- `templates/skills/` — templates de skills prontos pra personalizar com /mapear
- `templates/ferramentas/catalogo.md` — APIs e ferramentas disponíveis pra usar em skills

## Sobre o profissional
[descrição em 2-4 linhas com o que foi dito: tipo de atuação, foco, região, público]

## Plataformas de conteúdo
[Instagram, TikTok ou ambas — formatos prioritários pra esse profissional]

## Clientes e contexto
[perfil dos clientes que atende e região de atuação]

## Tom de voz
[como escrever, o que evitar, exemplos se mencionou]

## Ferramentas conectadas
[lista das ferramentas que usa — atualizar conforme MCPs forem instalados]

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

Ao concluir uma tarefa que não tinha skill mas parece repetível (o usuário provavelmente vai pedir de novo no futuro), perguntar:

> "Isso pode virar uma skill pra próxima vez. Quer que eu crie?"

Não perguntar pra tarefas pontuais ou perguntas simples. Só quando o padrão de repetição for claro.

---

## Aprender com correções

Quando o usuário corrigir algo, melhorar uma resposta ou dar uma instrução que parece permanente (frases como "na verdade é assim", "não faça mais isso", "prefiro assim", "sempre que...", "evita...", "da próxima vez..."), perguntar:

> "Quer que eu salve isso pra não precisar repetir?"

Se sim, identificar onde faz mais sentido salvar:

- **Sobre o negócio** (tipo de imóvel, região, público, diferenciais) → adicionar em `_contexto/empresa.md`
- **Sobre preferências e estilo** (tom, formato de post, o que evitar) → adicionar em `_contexto/preferencias.md`
- **Sobre prioridades e foco atual** (tipo de conteúdo prioritário, campanha ativa, metas) → adicionar em `_contexto/estrategia.md`
- **Regra de comportamento nessa pasta** (onde salvar arquivos, como nomear, fluxos específicos) → adicionar no próprio `CLAUDE.md`

Salvar com uma linha nova clara, sem reformatar o arquivo inteiro. Confirmar o que foi salvo mostrando a linha adicionada.

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
- Tarefas pontuais que não mudam o contexto (ex: criar um post avulso, gerar um roteiro)
- Perguntas simples ou conversas sem ação
- Mudanças que já foram salvas pelo bloco "Aprender com correções"

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
```

### 2. Criar `_contexto/empresa.md`

```markdown
# Contexto do Profissional — [Nome]

**Nome:** [nome completo]
**Nome profissional:** [como se identifica — nome que usa no Instagram, cartão, etc.]
**Tipo de atuação:** [corretor-autonomo / corretor-imobiliaria-propria / corretor-vinculado / imobiliaria]
**Imobiliária:** [nome da imobiliária — própria ou vinculada — ou "N/A" se autônomo puro]
**Relação com imobiliária:** [sócio / parceiro / funcionário / franqueado — se aplicável]
**Foco:** [residencial / comercial / lançamentos / aluguel / misto — detalhar]
**Região de atuação:** [cidade, bairros ou zonas onde atua]
**Público-alvo:** [perfil dos clientes — compradores de primeira moradia, investidores, famílias, locatários etc.]
**Plataformas de conteúdo:** [Instagram / TikTok / ambas]
**Ferramentas:** [lista das ferramentas usadas]
**Trabalha:** [solo / com equipe — quantas pessoas se mencionou]

## Contexto adicional
[qualquer informação relevante que surgiu nas respostas]
```

### 3. Criar `_contexto/estrategia.md`

```markdown
# Foco Atual — [Nome]

## Fase
[Em que momento está o profissional agora — começando no digital, crescendo canal, gerando leads, organizando operação, etc.]

## Prioridade de conteúdo
[Que tipo de conteúdo quer priorizar — educativo, captação, apresentação de imóveis, autoridade, bastidores, etc.]

## Público em foco agora
[Se há um segmento específico sendo trabalhado com mais atenção no momento]

## O que pode esperar
[O que não é prioridade no momento — ajuda o Claude a não sugerir fora de hora]

## Contexto com prazo
[Campanhas ativas, lançamentos previstos, datas relevantes — se mencionou]

---
*Atualize esse arquivo quando suas prioridades mudarem.*
```

### 4. Criar `_contexto/preferencias.md`

```markdown
# Preferências de Comunicação

## Tom de voz
[como o Claude deve escrever nos posts, roteiros e carrosséis — ex: direto e próximo, consultivo, informal, especialista]

## O que evitar
[lista do que incomoda — palavras, construções, expressões proibidas em textos gerados por IA]

## Estilo geral
[formal/informal, curto/longo, com/sem emoji, como usar hashtags, etc.]

## Preferências adicionais
[qualquer outra preferência mencionada — ex: "não usar bullet point", "prefiro texto corrido"]
```

### 5. Pré-preencher `marca/design-guide.md`

Antes de preencher as cores e tipografia, adicionar no topo do arquivo (após o título e aviso):

```
**Marca em uso:** [própria — [nome] / imobiliária — [nome] / ainda não definida]
```

Se o usuário descreveu cores e estilo, preencha com o que foi dito.
Se não tem identidade definida, preencha com campos em branco e orientações pra preencher depois.

Em ambos os casos, manter este aviso no topo do arquivo (logo abaixo do título):

```
> Você pode editar esse arquivo a qualquer momento.
> As skills de carrossel e slide leem este arquivo antes de criar qualquer visual.
```

### 6. Escolher estrutura de pastas

Antes de criar qualquer pasta, **mostrar ao usuário o que você pensou** e deixar ele ajustar.

Ler os templates de perfil disponíveis em `templates/perfis/` pra saber quais opções existem. Depois apresentar:

> "Com base no que você me contou, acho que a estrutura de **[perfil detectado]** faz mais sentido pra você. Ficaria assim:
>
> ```
> [lista de pastas do perfil detectado]
> ```
>
> Quer usar essa, ajustar alguma pasta, ou montar uma estrutura diferente?"

**Se aceitar:** criar as pastas do perfil detectado.
**Se quiser ajustar:** perguntar quais pastas faz sentido ter e criar conforme ele descrever.

Estruturas padrão por perfil (referência):

**Corretor autônomo / corretor vinculado:**
```
conteudo/
  carrosseis/
  roteiros/
  ideias/
clientes/
imoveis/
dados/
tarefas.md
```

**Corretor com imobiliária própria / imobiliária:**
```
conteudo/
  carrosseis/
  roteiros/
  ideias/
captacoes/
clientes/
imoveis/
equipe/
dados/
tarefas.md
```

### 7. Recomendar MCPs e ferramentas

Ler `templates/ferramentas/catalogo.md` e cruzar com as ferramentas que o usuário citou na Pergunta 7.

Para cada ferramenta que o usuário usa e que tem um MCP ou conector disponível no catálogo:
- Mostrar o que o conector faz
- Mostrar o comando de instalação
- Perguntar se quer instalar agora

Se o usuário aceitar, rodar o comando de instalação do MCP.
Se preferir depois, anotar em `tarefas.md`:

```
## MCPs pra instalar depois
- [ ] [Ferramenta] — `[comando de instalação]`
```

---

## Mensagem final

Após gerar todos os arquivos, envie uma mensagem de encerramento:

> "[Nome profissional], seu sistema tá configurado.
>
> Aqui está o que foi criado:
> - CLAUDE.md — o Claude agora sabe quem você é, como atua e onde fica cada coisa
> - _contexto/ — perfil, preferências e foco atual salvos
> - marca/design-guide.md — identidade visual [preenchida / pronta pra preencher]
> - Estrutura de pastas pro seu perfil de [perfil detectado]
> - [N] MCPs instalados / [N] anotados pra instalar depois
>
> **Duas coisas importantes antes de continuar:**
>
> 1. Se você tiver chaves de API, guarde sempre num arquivo chamado `.env` — ele já está protegido e nunca vai pro GitHub por engano.
>
> 2. Para não perder seu trabalho, conecte esse workspace ao GitHub rodando `/syncar`. Leva 2 minutos e depois o sistema salva automaticamente.
>
> **Próximo passo:** rode `/mapear` pra eu entender suas tarefas repetitivas e criar skills personalizadas pra você."

---

## Regras

- Tom direto e humano, sem excesso de entusiasmo
- Não use listas com bullet points nas perguntas — faça em conversa
- Se o usuário der respostas vagas, faz uma pergunta de acompanhamento antes de continuar
- Gera os arquivos todos de uma vez no final, não um a um durante as perguntas
- Após gerar, mostra a mensagem final resumida — não lista cada linha de cada arquivo

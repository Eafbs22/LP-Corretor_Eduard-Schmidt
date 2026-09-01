# Kit Imobiliário — Claude Code OS

Automação de conteúdo para corretores autônomos e imobiliárias, rodando dentro do Claude Code.

---

## Como instalar

### Opção 1 — Via prompt (mais fácil)

Com o Claude Code aberto na pasta `automação imob/`, cole esse prompt:

```
Configura o sistema pra mim rodando /setup
```

### Opção 2 — Via terminal

**1. Abra no VS Code**
```bash
code .
```

**2. Abra o terminal integrado** (Ctrl+` no Windows / Cmd+` no Mac) e rode:
```bash
claude
```

**3. Chame o setup**
```
/setup
```

O Claude vai te fazer algumas perguntas sobre como você atua no mercado imobiliário e configurar o sistema pro seu perfil. Em 5 minutos você tem tudo pronto.

---

## O que vem no kit

**Skills prontas pra usar:**
- `/setup` — configura o sistema pro seu negócio (comece por aqui)
- `/iniciar` — carrega o contexto do negócio no começo de cada sessão
- `/syncar` — salva o trabalho no GitHub (commit + push)
- `/carrossel` — cria carrosséis pra Instagram e TikTok com a sua identidade visual
- `/roteiro-post` — transforma ideia ou imóvel em roteiro de post ou vídeo
- `/slide` — cria slide/card visual pra apresentação
- `/analisar-dados` — analisa planilhas e gera resumo executivo com insights
- `/publicar-site` — publica qualquer HTML no ar com um link compartilhável
- `/email-profissional` — rascunha email profissional a partir de contexto livre
- `/atualizar` — varre o projeto e atualiza arquivos de contexto desatualizados
- `/mapear` — entende suas tarefas repetitivas e cria skills personalizadas
- `/novo-projeto` — cria pasta de projeto novo com CLAUDE.md dedicado

---

## Estrutura do repositório

```
automação imob/
├── .claude/commands/     # skills do kit (atualizar, iniciar, mapear...)
├── _contexto/            # perfil, preferências e estratégia do negócio
├── marca/                # guia de identidade visual
├── dados/                # drop zone para arquivos de análise (CSV, XLSX, PDF)
├── templates/
│   ├── skills/           # código-fonte das skills (editável)
│   ├── perfis/           # modelos de CLAUDE.md por tipo de usuário
│   └── marca/            # exemplos de design-guide
├── CLAUDE.md             # instruções de comportamento da IA
└── README.md             # este arquivo
```

**Pastas geradas pelo `/setup`:**
- `_contexto/` — empresa.md, preferencias.md, estrategia.md
- `marca/design-guide.md` — identidade visual
- `conteudo/` — carrosséis, roteiros e ideias gerados
- `imoveis/` — fichas e materiais de imóveis
- `clientes/` — histórico de clientes

**Perfis suportados:**
- Corretor autônomo (sem imobiliária)
- Corretor autônomo com imobiliária própria
- Corretor vinculado a imobiliária
- Imobiliária com equipe de corretores

---



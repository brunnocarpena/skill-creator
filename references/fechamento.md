# Fechamento de skill nova (padrão da casa)

Faça na ordem. Cada passo tem o porquê: pular um deles já fez skill "sumir" em outra conta
ou ficar sem histórico.

## 1. Arquivos da skill
- `README.md`: o que faz (lista curta de passos), como instalar
  (`git clone ... ~/.claude/skills/<nome>`), requisitos e tabela de scripts.
- `.gitignore`: `.DS_Store`, `*.log`, `*.zip`, `node_modules/`, `__pycache__/`, `.env*`.
- Workspace dos evals fica no scratchpad da sessão, nunca dentro de `~/.claude/skills/`
  (uma pasta a mais ali vira lixo na lista de skills).

## 2. Git e GitHub
- `git init`, commit com mensagem em português com acentos, via `git commit -F` com
  heredoc entre aspas (o `-m` no shell às vezes come o acento).
- Se houve evals, registre o resultado na mensagem: "com skill 100% x sem skill 34%".
- Repo **privado** em `brunnocarpena/<nome>`, salvo outra resposta no briefing:
  `gh auth switch -u brunnocarpena` → `gh repo create brunnocarpena/<nome> --private --source . --push`
  → `gh auth switch -u dev-16pct` (a conta ativa padrão é a da 16pct; volte para ela).
- Atualizou a skill depois = commit + push no repo dela.

## 3. Conta da Mari
`ln -s ~/.claude/skills/<nome> ~/.claude-mari/skills/<nome>` - symlink, nunca cópia
(cópia não sincroniza e as duas versões se separam).

## 4. Roteador de skills
- `~/.claude/skills-routing/CATALOGO.md`: entrada `### <nome>` no formato das outras
  (Faz / Usar quando / Não usar / Sobreposição / Requisitos / Relevância p/ usuário).
- `~/.claude/skills-routing/ROTEADOR.md`: uma linha na situação certa, com a data e o repo.
  Se ela compete com outra skill, diga qual ganha em que caso.

## 5. Memória
`project_<nome>-skill.md` na pasta de memória do projeto (repo, commit, resultado dos evals,
o que falta testar) e uma linha no `MEMORY.md`.

## 6. Para o usuário
- Se a skill não aparecer na lista de skills, reiniciar o Claude Code.
- O que falta só ele fazer (login, chave no `.env.local`, primeiro teste real) em lista
  curta numerada, pronta para colar no WhatsApp.

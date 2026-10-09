# Briefing de skill nova

Mande as perguntas numa mensagem só, numeradas, com a sugestão padrão entre parênteses
para ele poder responder "padrão" ou "ok pros padrões". Pule o que a conversa ou a skill
existente já respondem - quem acabou de fazer o processo na conversa não quer contar de novo.

```
Pra começar, me responde (se o padrão servir, é só dizer "padrão"):
1. Em uma frase: o que a skill faz? (vira a primeira frase da description)
2. Quando ela deve entrar? Que frases você costuma falar quando precisa disso?
   (eu completo com variações em PT e EN)
3. Quando ela NÃO deve entrar? Tem skill parecida que deve ganhar nesses casos?
4. O que sai no fim: arquivos, um relatório, código, algo publicado, uma lista no chat?
5. Tem passo em que você precisa decidir ou aprovar no meio (escolher entre opções,
   dar ok antes de publicar)? (padrão: só antes de ação pública ou que gasta dinheiro)
6. Usa algum serviço, conta, login ou chave? (segredo vai em .env.local, nunca no chat)
7. Nome da skill. **Pergunta obrigatória**, mesmo se eu já tiver chamado de algum jeito.
   Levo 2 ou 3 sugestões em kebab-case e confiro se não colide com skill já instalada.
8. Fica nas duas contas (16pct e Mari)? (padrão: sim, por symlink)
9. Repo no GitHub? (padrão: privado em brunnocarpena/<nome>)
10. Quer que eu teste com e sem a skill e te mostre a diferença? (padrão: sim, 2 ou 3 casos;
    skill de gosto/estilo pode ficar só na avaliação visual)
```

## Como transformar as respostas em decisões

| Resposta | Decisão |
|---|---|
| Passo repetido e mecânico (gerar arquivo, conferir medida, empacotar) | `scripts/` com o script pronto e testado |
| Muito conhecimento que só vale numa etapa | `references/<etapa>.md`, lido só nela |
| Modelo de arquivo que a skill preenche | `assets/<nome>.template.*` |
| Ponto de decisão do usuário | checkpoint explícito, com o que fazer se ele não responder (seguir com padrão provisório e listar pendência) |
| Ação pública, irreversível ou paga | só com ok explícito naquele momento |
| Instala dependência, MCP ou roda `npx` | passar pela `supply-chain-guard` antes |
| Serviço externo no caminho crítico | escrever na skill o fallback e os limites do plano (regras globais) |
| Login, chave ou token | `.env.local` com a variável vazia e comentário de onde obter; conferir `.gitignore` |
| Abre navegador para testar | Chromium isolado com perfil temporário; nunca o Brave do usuário |
| Precisa de outra skill (logo, design, vídeo) | chamar a skill existente pelo nome, sem copiar o conteúdo dela |
| Tem ponto de falha em runtime no que a skill gera | `ERRORS.md` com códigos curtos (`XXX-001`) |

Feche o briefing com um resumo de 5 linhas (propósito, gatilhos, saída, checkpoints,
nome) e siga sem pedir confirmação de novo, a não ser que algo seja ambíguo.

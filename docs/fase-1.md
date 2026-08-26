# Fase 1 — Congelar a URL
Status: Em andamento (parte local concluída, aguardando criação do repositório)

---

## ⚠️ Antes de Começar — OBRIGATÓRIO

Ler o `plano-geral.md`. Verificar especificamente:

- "Estado Atual do Projeto": o que já foi feito e o que ficou definido
- "Decisões Tomadas": decisões que afetam esta fase
- "Onde Estão as Coisas": caminhos, URLs e serviços

---

## Contexto Herdado

Primeira fase. O que veio antes foi a leitura do PDF do convite
(`c:\Users\gabri\Downloads\CASAMENTO_.pdf`), que definiu toda a identidade visual: fontes, paleta,
tom editorial, dados do evento e formato.

---

## Escopo desta Fase

Objetivo único: existir uma URL viva e testada no celular. Já com a identidade final do jornal,
porque ela é conhecida. Só o conteúdo dos manuais fica pendente.

- Estrutura de arquivos do projeto
- Masthead "The Wedding Times" vetorizado, com a grafia corrigida
- CSS com o sistema visual completo, mobile-first
- Três páginas: índice, masculino e feminino
- Repositório público no GitHub e Pages ativo

## O que fica de fora

- QR Code (Fase 2)
- Conteúdo real dos dress codes (Fase 3)
- Imagens de referência de looks (Fase 3)

---

## Tarefas

**Feito**

- [x] Criar `c:\Users\gabri\Documents\dresscode` com a estrutura de pastas
- [x] Extrair a fonte Engravers Old English BT do FontFile2 do PDF
- [x] Vetorizar "The Wedding Times" em curvas para `assets/masthead.svg` (15 KB, grafia corrigida)
- [x] Confirmar que Anton, Lora e League Gothic existem no Google Fonts (HTTP 200 nas três)
- [x] `assets/style.css`: papel `#f2f1ec`, tinta preta, régua dupla, cintilha, manchete, chamadas
- [x] `index.html`: masthead, cintilha, manchete, deck e as duas chamadas (Caderno A e B)
- [x] `masculino/index.html` e `feminino/index.html` com selo "Matéria em fechamento"
- [x] `.nojekyll`, `robots.txt` (`Disallow: /`), `.gitignore`
- [x] `README.md` com a regra inegociável da URL em caixa alta
- [x] Meta `noindex, nofollow` nas três páginas
- [x] Verificar transbordo horizontal em 390px e 360px: nenhum
- [x] Verificar fallback com Google Fonts bloqueado: legível, sem transbordo
- [x] Medir peso da home: 105,6 KB sem compressão, sendo 71,2 KB de fontes
- [x] Verificar alvos de toque: 350 x 155 px, bem acima dos 44 px recomendados
- [x] Testar navegação real: índice → masculino → índice → feminino, todas OK
- [x] `git init`, branch `main` e commit inicial

**Pendente, depende do usuário**

- [ ] Criar o repositório **público** `dresscode` na conta `gabrielferreirab7-coder`
- [ ] `git remote add origin` e `git push -u origin main`
- [ ] Ativar Pages: Settings → Pages → Deploy from a branch → `main` → `/ (root)`
- [ ] Aguardar o build e confirmar HTTPS ativo
- [ ] Abrir a URL no celular, **no 4G e não no Wi-Fi de casa**

---

## Critério de Conclusão

`https://gabrielferreirab7-coder.github.io/dresscode/` abre no celular, no 4G, em menos de
2 segundos, e os dois botões navegam e voltam.

Verificação por linha de comando:

```bash
curl -sI https://gabrielferreirab7-coder.github.io/dresscode/ | head -1
curl -sI https://gabrielferreirab7-coder.github.io/dresscode/masculino/ | head -1
curl -sI https://gabrielferreirab7-coder.github.io/dresscode/feminino/ | head -1
```

As três precisam responder `HTTP/2 200`.

---

## ⚠️ Após Executar Esta Fase — OBRIGATÓRIO

**1. Neste arquivo:** marcar as tarefas pendentes, registrar o que ficou aberto e por quê, e
atualizar o status no topo para `Status: Concluído — [data]`.

**2. No `plano-geral.md`, seção "Estado Atual":** atualizar "Última fase concluída" e
"Próxima fase", registrar em "Onde Estão as Coisas" a URL real do repositório e do Pages, e
preencher o "Contexto Herdado" do `fase-2.md`.

Não avançar para a Fase 2 sem atualizar os dois arquivos.

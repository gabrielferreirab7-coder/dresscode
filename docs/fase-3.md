# Fase 3 — Conteúdo dos manuais
Status: Pendente

---

## ⚠️ Antes de Começar — OBRIGATÓRIO

Ler o `plano-geral.md`. Verificar especificamente:

- "Estado Atual do Projeto": confirmar que o QR já foi impresso e a URL está congelada
- "Identidade Visual": em especial o tom editorial do jornal
- "Riscos e Gaps": a regra editorial de não publicar endereço, horário nem telefone

Sem pressa nesta fase. O QR já está impresso, a URL não muda, e cada edição é um `git push` que
reflete em cerca de 1 minuto.

---

## Contexto Herdado da Fase 2

[Preencher ao concluir a Fase 2]

- Data em que o jornal foi liberado para a gráfica:
- Onde ficaram os arquivos do QR:

---

## Escopo desta Fase

Escrever as duas páginas de verdade, substituindo o selo "Matéria em fechamento".

**`masculino/index.html`**

- Traje esperado
- Cor do terno
- Camisa
- Gravata, se aplicável
- Sapato e acessórios
- O que evitar
- Referências visuais
- Observações específicas

**`feminino/index.html`**

- Tipo e comprimento do vestido
- Paleta ou direcionamento de cores
- Cores reservadas ou a evitar
- Sapatos e acessórios
- O que evitar
- Referências visuais
- Observações específicas

## O que fica de fora

- Endereço, horário e telefone. Essa informação fica no convite impresso, não no site público.
- Qualquer mudança de URL, nome de repositório ou username.

---

## Tarefas

- [ ] Definir com a Amanda o dress code masculino
- [ ] Definir com a Amanda o dress code feminino
- [ ] Escrever `masculino/index.html` no tom do jornal
- [ ] Escrever `feminino/index.html` no tom do jornal
- [ ] Selecionar referências visuais de looks
- [ ] Otimizar as imagens: WebP, largura máxima de 800 px, `loading="lazy"`
- [ ] Revisar em tela de 360 px de largura
- [ ] Commit e push

---

## Nota de tom

O jornal alterna humor íntimo e registro religioso. O quiz dos noivos, o "fato ou fake" e frases
como "acabou virando a nossa comédia romântica" convivem com Gl 6,2 e 1Ts 5,11 na missão dos
padrinhos.

Uma página de dress code em tom de manual corporativo destoa do material inteiro. O texto precisa
da mesma pegada: humor seco e instrução clara. "O que é melhor deixar no armário" funciona melhor
que "itens não recomendados".

---

## Critério de Conclusão

As duas páginas completas, peso total abaixo de 500 KB por página com imagens, e legíveis sem zoom
em tela de 360 px de largura.

Verificação de peso:

```bash
curl -so /dev/null -w "%{size_download} bytes\n" \
  https://gabrielferreirab7-coder.github.io/dresscode/masculino/
```

---

## ⚠️ Após Executar Esta Fase — OBRIGATÓRIO

**1. Neste arquivo:** marcar tarefas, registrar pendências e atualizar o status no topo.

**2. No `plano-geral.md`, seção "Estado Atual":** atualizar "Última fase concluída" e registrar
qualquer decisão que tenha divergido do plano original.

# Fase 2 — QR Code e liberação da gráfica
Status: Em andamento — arquivos gerados, aguardando montagem e teste impresso

---

## ⚠️ Antes de Começar — OBRIGATÓRIO

Ler o `plano-geral.md`. Verificar especificamente:

- "Estado Atual do Projeto": confirmar que a Fase 1 fechou e a URL está viva
- "Decisões Tomadas": em especial a decisão de não gerar o QR antes de a URL existir
- "Onde Estão as Coisas": a URL de produção real

**Não gerar o QR antes de a URL responder 200.** Gerar em cima de uma URL que ainda não existe é
gerar em cima de suposição, e o erro só aparece depois de impresso.

---

## Contexto Herdado da Fase 1

- URL de produção confirmada: `https://gabrielferreirab7-coder.github.io/dresscode/`
- Data em que o Pages entrou no ar: 27/08/2026
- Deploy confirmado com sucesso e as três rotas respondendo HTTP 200
- Resultado do teste no celular (4G):

---

## Escopo desta Fase

- Gerar o QR Code apontando para a URL de produção, **com barra final**
- Entregar a especificação de impressão junto do arquivo
- Testar o QR impresso em papel, não na tela
- Conferir a montagem dentro do Canva

## O que fica de fora

- Conteúdo dos manuais (Fase 3)

---

## Tarefas

- [x] Gerar `assets/qr/dresscode.svg` com correção de erro nível Q
- [x] Gerar `assets/qr/dresscode-2000.png` para quem não aceitar vetor
- [x] Escrever `assets/qr/README.md` com a spec de impressão abaixo
- [ ] Escanear o SVG na tela só para validar o destino (teste preliminar, não vale como aprovação)
- [ ] Substituir o placeholder do bloco DRESS CODE no Canva pelo QR mais uma linha curta
- [ ] Conferir no Canva: QR sobre retângulo branco liso, sem textura de papel por baixo
- [ ] Exportar o jornal em PDF de impressão
- [ ] **Imprimir em papel comum e escanear com câmera nativa de iPhone e de Android**
- [ ] Só então liberar a gráfica

---

## Especificação de impressão do QR

Vai junto do arquivo, para mandar à gráfica ou colar no Canva.

- Preto puro sobre **retângulo branco liso**. Sem textura de papel por baixo.
- Tamanho final mínimo: **2,5 cm** de lado
- Margem branca (quiet zone) de 4 módulos em volta. Não cortar, não encostar em régua nem em texto.
- Correção de erro **nível Q (25%)**, que tolera dobra e sujeira no papel
- Sem logo, sem gradiente, sem cantos arredondados, sem cor
- Usar o **SVG**, nunca o PNG, dentro do Canva

O erro clássico de convite é estilizar o QR em dourado ou cinza claro. Ele para de ler em luz de
festa e ninguém descobre até a semana do casamento.

---

## Sugestão de conteúdo para o bloco DRESS CODE do jornal

Substituindo o placeholder atual (`[ORIENTAÇÃO DE TRAJE] / EX.: ESPORTE FINO / SOCIAL...`):

```
DRESS CODE

SUA PRESENÇA É O MAIS IMPORTANTE.
AS ORIENTAÇÕES DE TRAJE ESTÃO AQUI:

        [ QR CODE ]

     APONTE A CÂMERA DO CELULAR
```

---

## Critério de Conclusão

O QR **impresso em papel comum** lê em dois celulares diferentes, um iPhone e um Android, com a
câmera nativa, em luz ambiente normal, à distância de leitura de convite, e cai em
`https://gabrielferreirab7-coder.github.io/dresscode/`.

Se um dos dois falhar, aumentar o tamanho e testar de novo. Não liberar a gráfica antes disso.

---

## ⚠️ Após Executar Esta Fase — OBRIGATÓRIO

**1. Neste arquivo:** marcar tarefas, registrar pendências e atualizar o status no topo.

**2. No `plano-geral.md`, seção "Estado Atual":** atualizar "Última fase concluída" e
"Próxima fase", registrar em "Onde Estão as Coisas" onde ficaram o SVG e o PNG do QR, e preencher
o "Contexto Herdado" do `fase-3.md`.

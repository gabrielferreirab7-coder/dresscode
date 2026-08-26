# Plano Geral — Manual de Vestimenta, Gabriel & Amanda

## Definição do Problema

O convite dos padrinhos é um jornal A3 paisagem diagramado no Canva, "The Wedding Times". O bloco
DRESS CODE dele está com o placeholder do template, porque a orientação de traje ainda não foi
decidida. Sem uma solução, a impressão fica travada esperando uma decisão de roupa.

O QR Code entra naquele bloco e destrava a gráfica: o conteúdo passa a viver numa página web
editável, e o QR aponta para uma URL que nunca muda.

**Para quem:** os padrinhos e madrinhas do casamento, escaneando um QR impresso, quase sempre no
celular e quase sempre longe do Wi-Fi.

**Objetivo prático:** mandar o jornal para a gráfica sem ter decidido o dress code.

---

## Arquitetura

Site estático puro. Sem build, sem framework, sem runtime.

```
dresscode/
├── index.html              /dresscode/            índice, destino do QR
├── masculino/index.html    /dresscode/masculino/
├── feminino/index.html     /dresscode/feminino/
├── assets/
│   ├── style.css           folha única compartilhada
│   ├── masthead.svg        "The Wedding Times" em curvas
│   ├── img/                referências visuais (Fase 3)
│   └── qr/                 QR Code + spec de impressão (Fase 2)
├── docs/                   este plano e as fases
├── .nojekyll
├── robots.txt
└── README.md               a regra inegociável da URL
```

Pastas com `index.html` em vez de `masculino.html` produzem URLs limpas sem precisar de servidor.
CSS externo compartilhado: custa um round-trip na primeira visita e economiza manutenção nas três
páginas.

---

## Stack Definida

| Camada | Escolha |
| --- | --- |
| Markup | HTML5 estático |
| Estilo | CSS puro, arquivo único |
| Tipografia | Anton, Lora, League Gothic (Google Fonts) com fallback Impact / Georgia / Arial Narrow |
| Masthead | SVG de curvas extraído da fonte embutida no PDF do convite |
| Hospedagem | GitHub Pages, branch `main`, pasta raiz |
| CI/CD | Nenhum |
| QR Code | Gerado localmente, saída SVG, correção de erro Q |

Fora: Tailwind, Bootstrap, Jekyll, Hugo, Astro, analytics e encurtadores de URL.

---

## Identidade Visual

Extraída do PDF do convite, não suposta.

**Fontes embutidas no PDF:** Anton (manchetes), Lora regular e itálico (corpo), League Gothic
(cintilha), Alice e Parisienne (descartadas para a web), Engravers Old English BT (masthead,
licença comercial, vetorizado em curvas).

**Cores nos content streams:** `#000000`, `#171717`, `#101010`, `#FFFFFF`, `#231815`. Zero cor
cromática. O site é monocromático como o convite.

**Tom editorial:** o jornal alterna humor íntimo (quiz, "fato ou fake", "acabou virando a nossa
comédia romântica") e registro religioso (Gl 6,2 e 1Ts 5,11). O texto das páginas segue o mesmo
registro, nunca tom de manual corporativo.

**Dados do evento:** 19/06/2027, 15:00, Paróquia Sagrada Família, Mendanha, Rio de Janeiro.
Ver Riscos antes de publicar qualquer parte disso na web.

---

## Riscos e Gaps

| Risco | Nível | Mitigação |
| --- | --- | --- |
| URL refém do username `gabrielferreirab7-coder` | Alto | Aviso em caixa alta no README. Não há mitigação técnica nesta configuração. |
| Repo público expõe data, horário e endereço | Médio | `robots.txt`, meta `noindex`, e regra editorial de não publicar endereço nem horário nas páginas |
| Comando `/github` do usuário cria repo privado e quebra o Pages | Médio | Este projeto não usa o `/github`. Repo criado manualmente como público. |
| QR ilegível na impressão | Médio | Spec obrigatória: preto puro, retângulo branco liso, 2,5 cm mínimo, ECC nível Q, quiet zone preservada |
| Jekyll ignorando arquivos com `_` | Baixo | `.nojekyll` na raiz |

**Gaps abertos**

1. Conteúdo real dos dress codes (Fase 3, não bloqueia a impressão)
2. Referências visuais de looks (Fase 3)
3. Confirmar 2FA e recuperação da conta GitHub
4. Se o jornal já foi para a gráfica ou ainda dá tempo de editar

**Pendências no Canva, fora do escopo técnico**

1. "The Weeding Times" nos quatro cabeçalhos. O correto é "Wedding". Corrigir antes da gráfica.
2. "SINTA SE À VONTADE" sem hífen no bloco DRESS CODE.
3. O bloco DRESS CODE ainda tem o placeholder do template e precisa receber o QR.
4. O link do Canva compartilhado é de edição, não de visualização.

---

## Fases

- Fase 1: Congelar a URL — Status: **Concluída localmente, aguardando criação do repo**
- Fase 2: QR Code e liberação da gráfica — Status: Pendente
- Fase 3: Conteúdo dos manuais — Status: Pendente

---

## 📍 Estado Atual do Projeto

> Esta seção é a fonte da verdade. Atualizar ao final de cada fase.
> Contexto novo, máquina nova: começar lendo aqui.

**Última fase concluída:** Fase 1, parte local (código pronto, testado e commitado)
**Próxima ação:** criar o repositório público `dresscode` no GitHub, dar push e ativar o Pages
**Depois disso:** Fase 2

### Decisões Tomadas Durante Execução

- **Masthead vetorizado a partir da fonte embutida no PDF.** A fonte Engravers Old English BT foi
  extraída do objeto FontFile2 do PDF, e o `cmap` do subset continha exatamente os glifos
  necessários (`T W d e g h i m n s` mais espaço). "The Wedding Times" saiu completo, com a grafia
  corrigida, convertido em curvas com fontTools. Curvas em vez de webfont resolve licença e
  fidelidade de uma vez.
- **Alice e Parisienne descartadas.** Anton, Lora e League Gothic cobrem manchete, corpo e cintilha,
  que é toda a hierarquia do jornal. Duas famílias a menos são dois requests a menos.
- **Papel `#f2f1ec`, levemente acinzentado.** Papel de jornal real não é creme quente. Branco puro
  cansa em tela de celular à noite.
- **Fallbacks escolhidos por peso, não por hábito:** Impact segura a manchete se Anton falhar,
  Georgia segura o corpo se Lora falhar. Testado bloqueando o Google Fonts: a página continua
  legível e sem transbordo.
- **Estrutura de índice em vez de botões genéricos.** A home é o índice do jornal, com as duas
  seções como chamadas rotuladas "Caderno A" e "Caderno B", vocabulário real de jornal brasileiro.
  A inversão preto/papel no toque é o único gesto de movimento da página.
- **QR não foi gerado ainda, de propósito.** Gerar antes de a URL existir é gerar em cima de
  suposição. Se algo mudar na criação do repo, o QR muda junto. Fase 2 depois da URL viva.

### Desvios do Plano Original

- A suposição inicial de que "The Wedding Times" era só referência estética estava errada. É um
  jornal A3 diagramado de verdade, e a direção visual foi corrigida antes de qualquer código.
- A Fase 2 original ("descobrir a identidade visual") deixou de existir. A leitura do PDF resolveu
  identidade, fontes, paleta, data, local e tom de uma vez, e a Fase 1 já saiu com a cara final.
  A Fase 2 virou só a geração e o teste do QR.

### Onde Estão as Coisas

- **Projeto local:** `c:\Users\gabri\Documents\dresscode`
- **Repositório:** ainda não criado. Precisa ser `dresscode`, **público**, na conta
  `gabrielferreirab7-coder`
- **Deploy:** GitHub Pages, branch `main`, pasta `/ (root)`. Ainda não ativado.
- **URL de produção (congelada):** `https://gabrielferreirab7-coder.github.io/dresscode/`
- **PDF do convite:** `c:\Users\gabri\Downloads\CASAMENTO_.pdf`
- **Convite no Canva:** `https://canva.link/s0u13lsk0ppuirn` (link de edição, trocar para visualização)
- **Variáveis de ambiente:** nenhuma. Site estático sem backend.
- **Preview local:** `cd c:\Users\gabri\Documents\dresscode && python -m http.server 8899`

# Manual de Vestimenta — Gabriel & Amanda

Site estático com as orientações de traje do casamento. Destino do QR Code impresso no convite
dos padrinhos ("The Wedding Times", edição especial).

**URL de produção:** https://gabrielferreirab7-coder.github.io/dresscode/

---

## ⚠️ NÃO MUDE ISSO NUNCA

O QR Code impresso nos convites aponta para a URL acima. Papel impresso não tem desfazer.
Se qualquer um destes três itens mudar, **todos os convites já impressos viram papel morto**:

1. **O username da conta GitHub:** `gabrielferreirab7-coder`
2. **O nome deste repositório:** `dresscode`
3. **O repositório precisa continuar PÚBLICO com GitHub Pages ativo**

Não renomeie a conta. Não renomeie o repo. Não torne privado. Não delete.

O conteúdo das páginas pode ser alterado à vontade. A URL, não.

---

## Como editar o conteúdo

As três páginas são HTML puro. Sem build, sem dependência, sem passo de compilação.

| Arquivo | URL |
| --- | --- |
| `index.html` | `/dresscode/` |
| `masculino/index.html` | `/dresscode/masculino/` |
| `feminino/index.html` | `/dresscode/feminino/` |
| `assets/style.css` | estilo compartilhado pelas três |

Edite, faça commit e push. O GitHub Pages republica sozinho em cerca de 1 minuto.

```bash
git add .
git commit -m "atualiza dress code masculino"
git push
```

Dá para editar direto pelo site do GitHub, inclusive pelo celular, sem precisar de computador.

---

## Identidade visual

Tudo extraído do PDF original do convite, não inventado.

**Tipografia**

| Uso | Fonte | Origem |
| --- | --- | --- |
| Masthead "The Wedding Times" | Engravers Old English BT | Vetorizado em `assets/masthead.svg`. A fonte é comercial (Bitstream), por isso vai como curvas e não como webfont. |
| Manchetes | Anton | Google Fonts |
| Corpo de texto | Lora (regular e itálico) | Google Fonts |
| Cintilha e rótulos | League Gothic | Google Fonts |

Fallback: `Georgia, serif`, nativa em praticamente todo celular. Se o Google Fonts falhar, a
página continua legível e sem salto de layout.

**Cores** (extraídas dos content streams do PDF)

| Token | Valor | Uso |
| --- | --- | --- |
| `--papel` | `#f2f1ec` | Fundo, papel de jornal |
| `--papel-bloco` | `#fbfaf7` | Fundo dos blocos de chamada |
| `--tinta-forte` | `#000000` | Manchetes e réguas |
| `--tinta` | `#101010` | Texto |
| `--tinta-suave` | `#171717` | Texto secundário |
| `--sepia` | `#231815` | Rótulos |

O convite é monocromático. O site também.

---

## Regra editorial

**Não publique endereço, horário nem telefone nestas páginas.**

O repositório é público porque o GitHub Pages gratuito exige. Data, horário e endereço juntos num
site aberto anunciam uma casa vazia num dia e hora específicos. Essa informação já está no convite
impresso, que é o canal certo para ela.

O `robots.txt` e a meta `noindex` reduzem a exposição, mas não são uma garantia. A garantia é não
publicar.

---

## Estrutura

```
dresscode/
├── index.html              índice, destino do QR
├── masculino/index.html
├── feminino/index.html
├── assets/
│   ├── style.css
│   ├── masthead.svg        "The Wedding Times" em curvas
│   ├── img/                referências visuais
│   └── qr/                 QR Code para impressão + spec da gráfica
├── docs/                   plano e fases do projeto
├── .nojekyll               impede o Jekyll de processar o site
└── robots.txt
```

---

## Publicação

GitHub Pages, branch `main`, pasta raiz. Sem GitHub Actions, sem build.

Settings → Pages → Source: **Deploy from a branch** → Branch: `main` → Folder: `/ (root)`

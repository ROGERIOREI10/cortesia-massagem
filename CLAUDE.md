# Balão Premiado — QR de cortesia por compra (Dia das Crianças)

App estático (um `index.html` só) que gera/lê QR codes de cortesia: funcionária digita o
valor da compra → cliente ganha o direito de estourar balão(ões) premiado(s) numa das lojas
do evento. Antes era o app "Cortesia Massagem" (poltrona Trono da Massagem) — reaproveitado
em outubro/2026 para o evento BALÃO PREMIADO.

- **Regras:** ≥ R$100 = 1 balão · ≥ R$200 = 2 balões · QR vale 24h
- **Onde estourar:** Centro Comercial da Onda (Princesinha Shop) · Shopping Praia do Morro
  (Princesinha Shop) · Shopping Mar (Reizinho Brinquedos, loja nova)
- **Produção:** https://rogeriorei10.github.io/cortesia-massagem/ (GitHub Pages, push em main = publica em ~1 min)
- Sem backend: payload do QR é a própria URL com query params (`?v=&b=&t=&id=` + `&brinde=1`).
  Libs via CDN (`qrcodejs` + `html5-qrcode` com fallback entre 3 CDNs).
- Admin escondido (link "🔐 admin" no rodapé, PIN `8110`, fica desbloqueado 24h) só com o
  **Brinde Expresso** (gera balão sem compra). Fidelidade por selos foi removida.
- Resgates ficam no `localStorage` do celular que leu (chave `baloes_resgatados`).
- **Contexto completo** nas memórias da pasta.

## Regras de ouro

1. Estética **festa de Dia das Crianças**: céu azul, balões coloridos flutuando, confete,
   fontes Baloo 2 + Nunito. (O tema madeira/dourado antigo foi aposentado.)
2. Câmera exige HTTPS (por isso GitHub Pages). Ícone da PWA só troca desinstalando/reinstalando.
3. `gh` CLI está instalado e autenticado como ROGERIOREI10 — usar pra automação GitHub.
4. Rogério NÃO é programador — português BR simples. Aprendeu algo novo? **Atualize a memória da pasta.**

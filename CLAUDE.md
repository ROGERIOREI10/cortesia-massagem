# Balão Premiado — QR de cortesia por compra (Dia das Crianças)

App estático (um `index.html` só) que gera/lê QR codes de cortesia: funcionária digita o
valor da compra → cliente ganha o direito de estourar balão(ões) premiado(s) numa das lojas
do evento. Antes era o app "Cortesia Massagem" (poltrona Trono da Massagem) — reaproveitado
em outubro/2026 para o evento BALÃO PREMIADO.

- **Regras:** ≥ R$100 = 1 balão · ≥ R$200 = 2 balões · QR vale 24h
- **Onde estourar:** Centro Comercial da Onda (Princesinha Shop) · Shopping Praia do Morro
  (Princesinha Shop). Shopping Mar (Reizinho Brinquedos) foi removido em 11/10/2026 porque
  não teve balões — pode voltar; as lojas aparecem em 4 lugares (home, card gerado, card do
  brinde, tela do cliente) + rodapé dos cards.
- **Produção:** https://rogeriorei10.github.io/cortesia-massagem/ (GitHub Pages, push em main = publica em ~1 min)
- Sem backend: payload do QR é a própria URL com query params (`?v=&b=&t=&id=` + `&brinde=1`).
  Libs via CDN (`qrcodejs` + `html5-qrcode` com fallback entre 3 CDNs).
- Admin escondido (link "🔐 admin" no rodapé, PIN `8110`, fica desbloqueado 24h) só com o
  **Brinde Expresso** (gera balão sem compra). Fidelidade por selos foi removida.
- **Senha da equipe** `7391` (const `STAFF_PIN`) tranca Gerar/Ler; fica memorizada 30 dias no
  celular. O PIN do admin também abre. Link "🔒 sair" no rodapé da home.
- **QR assinado**: param `s` = cyrb53(SEGREDO|v|b|t|id|brinde) em base36. Leitor rejeita QR
  sem assinatura válida (forjado/alterado). Mudar `SEGREDO` invalida todos os QRs já gerados.
- Quem lê o QR com a câmera do celular cai na **tela do cliente** (`#cliente`): só a cortesia
  dele (QR, lojas, validade), sem acesso ao app. Se o aparelho tem senha da equipe, aparece o
  botão "Sou da equipe: marcar como usado".
- Resgates ficam no `localStorage` do celular que leu (chave `baloes_resgatados`).
- **Card do prêmio (o que o cliente fotografa)**: cabe inteiro na tela do celular (testado em
  360×660) — tamanhos em `vh`. **Nunca mostrar o valor da compra pro cliente** (Rogério: pode
  confundir, "achar que tem R$100 em compras"); só "⏰ Válido até". O valor continua no leitor.
- **Contexto completo** nas memórias da pasta.

## Regras de ouro

1. Estética **festa de Dia das Crianças**: céu azul, balões coloridos flutuando, confete,
   fontes Baloo 2 + Nunito. (O tema madeira/dourado antigo foi aposentado.)
2. Câmera exige HTTPS (por isso GitHub Pages). Ícone da PWA só troca desinstalando/reinstalando.
3. `gh` CLI está instalado e autenticado como ROGERIOREI10 — usar pra automação GitHub.
4. Rogério NÃO é programador — português BR simples. Aprendeu algo novo? **Atualize a memória da pasta.**

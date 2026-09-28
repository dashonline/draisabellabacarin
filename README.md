# Dashboard de Tráfego — Dra Bacarin

Dashboard estática (GitHub Pages) do funil de captação da Dra Bacarin: campanhas de
**mensagem (click to WhatsApp)**. Base: dash da Clínica Master Beauty.

## Como funciona
- `build.ps1` chama a **Meta Graph API** (insights nível anúncio, por dia) e gera `data.js`
  (`daily[]` + `grain[]`, agregados anonimizados). Imposto ×1,1385 sobre todo gasto.
  Só entram campanhas cujo nome começa com `IB |`.
- `index.html` + `app.js` + `styles.css` renderizam Visão Geral + Tráfego Pago, sem libs.
  CTR sempre de **link**.
- **Agendamentos**: preencher `AG_ID` no `app.js` com o ID da planilha (aba `Planilha agendamento`:
  A = dd/mm, D = agendamentos, F = valor total). Enquanto vazio, o card não aparece.
- `.github/workflows/build.yml` roda o build de hora em hora e publica no Pages (`deploy-pages@v4`).
  O token da Meta vem do secret **`META_ACCESS_TOKEN`**.

## Rodar local
```powershell
.\build.ps1 -Mode all      # lê META_ACCESS_TOKEN do ambiente ou do .env (gitignored)
python -m http.server       # abrir index.html
```

## Manutenção
- Conta: `act_876078115252891` (Dra-Bacarin).

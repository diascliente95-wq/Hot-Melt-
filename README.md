# Hot-Melt — Controle de Produção

Aplicação responsiva/PWA para registrar produção de caixas e tampas por data, turno, área, lote e responsável; controlar quantidade, perdas, peso, pallets usados/produzidos, saldo de estoque e movimentações; gerar relatórios, imprimir/salvar PDF, exportar CSV e compartilhar texto pelo WhatsApp.

## Publicar pelo GitHub Pages
1. Mantenha `index.html`, `manifest.webmanifest`, `sw.js` e `icon.svg` na raiz.
2. No GitHub, abra Settings → Pages, escolha Deploy from a branch, selecione `main` e `/ (root)`, e salve.
3. Abra a URL HTTPS no Chrome Android e use Instalar app ou ⋮ → Instalar app/Adicionar à tela inicial.

## Limites importantes
- Dados salvos no localStorage do aparelho atual; exporte backups JSON periodicamente. Limpar dados do navegador pode apagar os registros.
- A produção pode somar ao estoque ou não. Ajustes de saldo físico ficam na tela Estoque.
- Excluir lançamento não reverte estoque automaticamente; confira o saldo após exclusões.
- WhatsApp abre mensagem pronta; o usuário escolhe o grupo e envia. Envio automático para grupos exige integração oficial autorizada.
- Para vários operadores compartilharem dados em dispositivos diferentes, configure banco e autenticação remotos (por exemplo Firebase) e regras de acesso antes do uso operacional.

Faça backup e valide os cálculos/saldos físicos antes de usar como registro oficial.

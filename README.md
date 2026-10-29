# Hot-Melt — Controle de Produção

Aplicação responsiva/PWA para registrar produção de caixas e tampas por data, turno, área, lote e funcionário; controlar quantidade, perdas, peso, pallets usados/produzidos, estoque e movimentações; gerar relatórios, imprimir/salvar PDF, exportar CSV e compartilhar texto pelo WhatsApp.

## Publicar pelo GitHub Pages
1. Mantenha os arquivos na raiz do repositório.
2. No GitHub, abra **Settings → Pages**, escolha **Deploy from a branch**, selecione `main` e `/(root)`, e salve.
3. Abra a URL HTTPS no Chrome Android. Use **Instalar app** ou **⋮ → Adicionar à tela inicial**.
4. O service worker usa cache versionado; a nova versão pode levar alguns instantes para aparecer. Feche e reabra o app se necessário.

## Nuvem e equipe com Firebase
A integração está preparada no painel **Configurações → Nuvem e acesso da equipe**, com os dados públicos de configuração do projeto `hot-melt-2027` já preenchidos. Para ativá-la:

1. Crie/abra um projeto no [Firebase Console](https://console.firebase.google.com/).
2. Adicione um app Web e copie os campos `apiKey`, `authDomain`, `projectId` e `appId` para o painel Hot-Melt.
3. Em **Authentication → Sign-in method**, habilite **Email/Password**. Crie apenas contas autorizadas da equipe.
4. Crie o **Cloud Firestore**.
5. Abra o arquivo `firestore.rules` deste repositório e substitua `admin@empresa.com` e `operador@empresa.com` pelos e-mails exatos autorizados. Publique essas regras na seção **Firestore → Rules** do Firebase.
6. Em Configurações no Hot-Melt, preencha os dados do Firebase e clique **Salvar configuração**. Depois, entre com o e-mail e a senha autorizados e aguarde o status de sincronização.
7. Repita a configuração Firebase nos outros aparelhos. Entre com uma conta autorizada para acessar os mesmos registros.

**Importante:** o app sincroniza o documento compartilhado `hotmelt/shared`. As regras de Firestore são essenciais: não publique regras abertas a todos os usuários. A lista de funcionários é para identificar responsáveis nos lançamentos; o acesso à nuvem é controlado pelas contas autorizadas. A configuração Firebase fica no armazenamento local do navegador.

## Recursos
- Painel com produção diária, perdas, índice de perdas, produção mensal e ocorrências.
- Cadastro de produção por data, turno, produto, área, lote e funcionário.
- Ocorrências classificadas por tipo e prioridade (baixa, média, alta ou crítica), com tempo de parada em minutos.
- Relatórios com total de tempo parado, detalhes das ocorrências e exportação desses campos no CSV.
- Auditoria de estoque: produção adicionada ao saldo e ajustes manuais passam a aparecer no histórico de movimentações.
- Estoque de caixas e tampas, pallets e movimentações de entrada/saída.
- Histórico com filtros, relatórios, CSV, impressão/PDF e texto para WhatsApp.
- Backup e restauração JSON.
- Cadastro local de funcionários e sincronização compartilhada via Firebase após configuração.

## Limites e cuidados
- A nuvem Firebase precisa ser configurada e as regras de acesso precisam ser publicadas pelo responsável do projeto. O sistema não ativa a nuvem sozinho.
- A sincronização atual compartilha um único documento no Firestore; para várias pessoas editarem ao mesmo tempo, ainda é necessário testar o fluxo e considerar registros separados por lançamento para evitar conflitos.
- Sem Firebase configurado e autorizado, os dados ficam apenas no armazenamento local do aparelho. Limpar dados do navegador pode apagá-los.
- Excluir um lançamento de produção não reverte o estoque automaticamente; confira o saldo após exclusões.
- Se vários funcionários editarem simultaneamente, esta versão sincroniza o documento compartilhado inteiro; faça backup frequente e valide o fluxo antes do uso operacional.
- O WhatsApp abre uma mensagem pronta; o usuário escolhe o grupo e envia manualmente.
- Faça backup e valide os saldos físicos antes de usar como registro oficial.

## Referência oficial
A configuração do SDK Web e autenticação seguem a documentação do Firebase:
- https://firebase.google.com/docs/web/setup
- https://firebase.google.com/docs/auth/web/start
- https://firebase.google.com/docs/firestore/security/overview

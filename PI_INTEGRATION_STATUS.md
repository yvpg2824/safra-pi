# Status da integração Pi — Campo de Moedas

## Base criada
Servidor Node.js 20+ em pi-server/ que consulta a API oficial /v2/me para verificar accessToken Pi, sem armazenar token e sem API key no navegador.
Rotas: GET /health e POST /api/pi/verify com JSON accessToken. Essa rota só confere identidade; não cria sessão nem autoriza compra.
CORS exige origem explicitamente permitida.

## Executar localmente
cd pi-server
ALLOWED_ORIGINS=https://yvpg2824.github.io,https://safrapi2114.pinet.com npm start
No Windows, configure ALLOWED_ORIGINS como variável de ambiente antes de iniciar.

## O que ainda falta
1. Hospedar servidor Node por HTTPS; GitHub Pages e hospedagem HTML estática não executam esta API.
2. Integrar o login existente/novo frontend ao endpoint publicado e criar sessão segura para usuário autenticado.
3. Criar persistência, permissões e auditoria de ações.
4. Implementar pagamentos via Pi SDK com aprovação e conclusão obrigatoriamente no servidor, validação de quantidade, ambiente, finalidade e idempotência; recuperar pagamentos incompletos.
5. Testar na Testnet e verificar regras/autorizações antes de ativar pagamentos em Pi real.

## Cuidados
O login atual depende de serviço do App Studio; não foi substituído. Créditos e depósitos seguem simulados. É necessário avaliar conformidade das mecânicas do jogo antes de pagamentos reais.
Não publicar API keys, seed phrases ou 24 palavras no GitHub.

Docs oficiais: https://github.com/pi-apps/pi-platform-docs
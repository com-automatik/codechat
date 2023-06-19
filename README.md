<p align="center">
  <img src="./public/images/cover.png" alt="Woot-logo" width="240" />

  <p align="center">Manual de instalação codechat</p>
</p>

# CODECHAT BRASIL

[Grupo no Whatsapp](https://chat.whatsapp.com/CLKge3hmHmmBcIL04mBzmT)
<hr />

[Grupo no Telegram](https://t.me/chatwootbrasil)
<hr />

## Documentação Original

Está disponível [Git oficial API codechat ](https://github.com/code-chat-br/whatsapp-api).

<details>
  <summary>Instalação em pm2</summary>
  
  Acesse o terminal e execute os seguinte comandos:
  
  ```bash
git clone https://github.com/code-chat-br/whatsapp-api.git codechta
cd codechat/src
mv dev-env.yml env.yml
nano env.yml

#Vá na linha 77 e 78, on tá <url> adicione a url abaixo e no campo ENABLED: deixe como true
http://0.0.0.0:1234/webhook/codechat

Ficará da seguinte forma:
URL: http://0.0.0.0:1234/webhook/codechat
ENABLED: true

#Build codechat e incie o pm2
npm install
pm2 start 'npm run start prod' --name codechat
pm2 save && pm2 startup
```

Instalação conector par Chatwoot

```bash
#Antes de inciar verifique se o node está instaldo, com o comando abaixo:
node -v

#Se retonar alguma versão do node, pule para etapa de clonar o repositorio

curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt-get install -y nodejs

#Clone o repositório do conector
git clone https://github.com/w3nder/chatwoot-codechat.git conector

cd conector
mv .env.example .env
nano .env

#Copie e cole o seguinte código:
PORT = 1234
CHATWOOT_TOKEN = cN5uJp53qHMoE77DaUZNDrii
CHATWOOT_BASE_URL = http://localhost:3000

CODECHAT_BASE_URL = http://localhost:8080
CODECHAT_API_KEY = t8OOEeISKzpmc3jjcMqBWYSaJsafdefer

# SE DESEJA ASSINAR A MENSAGEM COM O NOME DO USUÁRIO MUDE PARA true
TOSIGN=true

# SE DESEJA RECEBER MENSAGENS ENVIADAS POR FORA DO CHATWOOT MUDE PARA true
IMPORT_MESSAGES_SENT=false

#Build seu conector e incie o pm2
npm install
npm run build
npm install pm2 -g
pm2 start dist/app.js --name conector
pm2 save && pm2 startup

# Crie um  provider executando o seguinte código abaixo:

curl --location 'http://localhost:1234/create-provider' \
--header 'Content-Type: application/json' \
--data '{
    "account_id": "idinboxcw",
    "token": "tokencwperfil",
    "url": "https://demo.dispzap.com",
    "nameInbox": "nomesuacaixadeentrad"
}'
```

Vai em seu chatwoot e realize as seguintes etepas:

```bash
Criar uma caixa de entrada com api
URL: http://localhost:1234/webhook/chatwoot

Criar um contato 
+123456

Comandos extras:

#Este comando irá criar uma nova instância e gerar um QR code
/iniciar 

#Este comando irá verificar o status da instância
/status 

#Este comando irá desconectar o WhatsApp da instância
/desconectar
  ``` 
</details>

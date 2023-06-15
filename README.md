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

Está disponível [chatwoot.com/help-center](https://www.chatwoot.com/help-center).

<details>
  <summary>Atualização Manual (direta)</summary>
  
  Acesse o terminal e execute os seguinte comandos:
  
  ```bash
    cwctl --upgrade# Login as Chatwoot user
    sudo -i -u chatwoot

    # Navigate to the Chatwoot directory
    cd chatwoot

    # Pull the latest version of the master branch
    git checkout master && git pull
    
    # Ensure the ruby version is upto date
    rvm install "ruby-3.1.3"
    rvm use 3.1. --default

    # Update dependencies
    bundle
    yarn

    # Recompile the assets
    rake assets:precompile RAILS_ENV=production

    # Migrate the database schema
    RAILS_ENV=production bundle exec rake db:migrate

    # Switch back to root user
    exit

    # Reload systemd files
    systemctl daemon-reload

    # Restart the chatwoot server
    systemctl restart chatwoot.target
  ``` 

  Só use este abaixo se souber mexer como o git
  ```bash
    cwctl --upgrade# Login as Chatwoot user
    sudo -i -u chatwoot

    # Navigate to the Chatwoot directory
    cd chatwoot

    # Pull the latest version of the master branch
    git checkout develope && git pull
    
    # Ensure the ruby version is upto date
    rvm install "ruby-3.1.3"
    rvm use 3.1. --default

    # Update dependencies
    bundle
    yarn

    # Recompile the assets
    rake assets:precompile RAILS_ENV=production

    # Migrate the database schema
    RAILS_ENV=production bundle exec rake db:migrate

    # Switch back to root user
    exit

    # Reload systemd files
    systemctl daemon-reload

    # Restart the chatwoot server
    systemctl restart chatwoot.target
  ``` 
</details>

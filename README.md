🌐 Guia de Instalação e Monitoramento do Servidor Nginx no WSL
Este guia fornece um passo a passo para instalar e configurar o Nginx no WSL (Windows Subsystem for Linux), com scripts e automatizações para monitorar o serviço.

📋 Sumário
1. Instalar o WSL no Windows
2. Instalar o Nginx
3. Verificar o Status do Nginx
4. Automatizar a Verificação
5. Configurar o GitHub
6. Teste Final

💻 Instalar o WSL no Windows
Passo 1: Habilitar o WSL
    Digite o comando abaixo para instalar o WSL:
    
    wsl --install

Caso necessário, instale o Ubuntu manualmente:


    wsl --install -d Ubuntu-20.04

Substitua "20.04" por uma versão mais recente, como "22.04".  
Passo 2: Reiniciar o Computador

Reinicie o computador e verifique o status do WSL:

    
    wsl -l -v
    
Passo 3: Acessar o Terminal do Ubuntu

Abra o terminal do Ubuntu diretamente pela barra de pesquisa ou com o comando:


    wsl
🌐 Instalar o Nginx

Passo 4: Atualizar Pacotes e Instalar o Nginx

Atualize os pacotes do sistema:

    sudo apt update
    sudo apt upgrade

Instale o Nginx:
    
    sudo apt install nginx

Passo 5: Iniciar e Verificar o Nginx

Inicie o Nginx:

    sudo systemctl start nginx

Verifique o status do serviço:
    
    sudo systemctl status nginx

Teste a instalação acessando http://localhost no navegador.
![image](https://github.com/user-attachments/assets/31b36fda-7675-4f18-b288-8e2e2fba877f)


⚙️ Verificar o Status do Nginx

Para monitorar o status do Nginx, vamos criar um script simples.

Crie um diretório para a atividade:

    mkdir atividade_linux
    cd atividade_linux

Crie o script verificar_nginx.sh:

    nano verificar_nginx.sh

Adicione o seguinte conteúdo ao script:

    #!/bin/bash

    DATA_HORA=$(date '+%Y-%m-%d %H:%M:%S')
    SERVICO="Nginx"
    DIRETORIO="./"
    ONLINE="${DIRETORIO}/online.log"
    OFFLINE="${DIRETORIO}/offline.log"
    STATUS=$(systemctl is-active nginx)
    if [ "$STATUS" = "active" ]; then
        echo "$DATA_HORA - $SERVICO - ONLINE - O serviço está rodando." >> $ONLINE
    else
        echo "$DATA_HORA - $SERVICO - OFFLINE - O serviço está parado." >> $OFFLINE
    fi

para sair e salvar o conteúdo pressione ctrl+o ; enter  ; ctrl+x
Torne o script executável:

    chmod +x verificar_nginx.sh

⏲️ Automatizar a Verificação

Para rodar o script automaticamente, usaremos o crontab.

Abra o crontab:

    crontab -e

Adicione a linha abaixo para executar o script a cada 5 minutos:

    */5 * * * * /home/usuario/atividade_linux/verificar_nginx.sh

para sair e salvar o conteúdo pressione ctrl+o ; enter  ; ctrl+x
🔗 Configurar o GitHub

Inicialize o Git e faça o commit inicial:


    git init
    git add .
    git commit -m "Versão inicial da atividade"

Configure seu nome e e-mail:

    git config --global user.email "you@example.com"
    git config --global user.name "Your Name"

✅ Teste Final

Execute o script para testar:

    ./verificar_nginx.sh
    cat online.log

Pare o Nginx e teste o log offline:

    sudo systemctl stop nginx
    ./verificar_nginx.sh
    cat offline.log

🎉 Resultado Final: Seu servidor Nginx está configurado e monitorado com sucesso!




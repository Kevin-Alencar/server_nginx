🌐 Server Nginx

📋 Passo a Passo para Instalação

💻 Instalar Linux no Windows (WSL)
O WSL é um subsistema Linux dentro do Windows, que permite rodar comandos e programas de Linux sem precisar instalar o sistema operacional em outra partição.

Passo 1: Habilitar o WSL
Digite "Windows PowerShell" na barra de pesquisa, clique com o botão direito do mouse e selecione "Executar como administrador".

No PowerShell, digite o seguinte comando para instalar o WSL:

bash
wsl --install

Isso habilitará o WSL e, se necessário, baixará automaticamente uma distribuição Linux (normalmente o Ubuntu).

Caso não instale o Ubuntu automaticamente, use o comando:
bash

wsl --install -d Ubuntu-20.04
Substitua "20.04" por uma versão mais recente se preferir, como "22.04".

Conclua a instalação e faça login, anotando sua senha.

Passo 2: Reiniciar o Computador
Reinicie o computador para concluir a configuração do WSL. Após a reinicialização, verifique se o WSL está funcionando com o comando no power shell:

bash
wsl -l -v

Passo 3: Acessar o Terminal do Ubuntu
Agora você pode abrir o terminal do Ubuntu diretamente pela barra de pesquisa ou executando o comando a seguir no PowerShell:

bash
wsl

🌐 Instalar o Nginx

Passo 4: Atualizar Pacotes e Instalar o Nginx
Abra o terminal e atualize os pacotes:
bash
sudo apt update
sudo apt upgrade

Instale o Nginx:
bash
sudo apt install nginx

Passo 5: Iniciar o Nginx
Inicie o Nginx com o comando:
bash
sudo systemctl start nginx
Verifique se o Nginx está rodando:
bash
sudo systemctl status nginx

Passo 6: Testar a Instalação
Inicie o Nginx para que ele comece a rodar:
sudo systemctl start nginx

Para verificar se o Nginx está funcionando corretamente, use:
sudo systemctl status nginx

O status deve indicar "active (running)", mostrando que o servidor está em execução. Para confirmar, abra o navegador e acesse: http://localhost.

OU adicionando o seu IP na URL do navegador, trará o mesmo resultado.

⚙️ Manutenção do Nginx
Para parar o Nginx:
bash
sudo systemctl stop nginx
Para reiniciar o Nginx:
bash
sudo systemctl restart nginx
sudo systemctl enable nginx

📝 Criar Script de Verificação do Nginx se está online ou offline:
Crie um diretório (mkdir) para a atividade e entre nele:    
bash
mkdir atividade_linux
cd atividade_linux

Crie o script verificar_nginx.sh:
    bash
    nano verificar_nginx.sh
    Adicione o seguinte conteúdo ao script:

bash
Copiar código
#!/bin/bash
# Variáveis
DATA_HORA=$(date '+%Y-%m-%d %H:%M:%S')
SERVICO="Nginx"
DIRETORIO="./"
ONLINE="${DIRETORIO}/online.log"
OFFLINE="${DIRETORIO}/offline.log"

# Verifica o status do Nginx
STATUS=$(systemctl is-active nginx)

# Condição para verificar se o Nginx está online
if [ "$STATUS" = "active" ]; then
    echo "$DATA_HORA - $SERVICO - ONLINE - O serviço está rodando." >> $ONLINE
else
    echo "$DATA_HORA - $SERVICO - OFFLINE - O serviço está parado." >> $OFFLINE
fi
Salve e saia (Ctrl + O, Enter, Ctrl + X).

⏲️ Configurar o Crontab para fazer automatização do script que criamos com o nano:

Torne o script executável primeiramente como o chmod:

bash

chmod +x verificar_nginx.sh

Abra o crontab para edição:

bash

crontab -e

Escolha a opção número 1 e adicione:

bash

*/5 * * * * /home/kevin_a/atividade_linux/verificar_nginx.sh

Isso executará o script a cada 5 minutos.

🔗 Configurar o GitHub

Inicialize um repositório Git e faça um commit inicial:

bash

git init

git add .

git commit -m "Versão inicial da atividade"

Configure seu nome de usuário e e-mail:

bash

git config --global user.email "you@example.com"

git config --global user.name "Your Name"

✅ Verificar a Aplicação e Logs

Execute o script para testar:

bash

./verificar_nginx.sh

cat online.log

Pare o Nginx e execute o script novamente para verificar o log offline:

bash

sudo systemctl stop nginx

Use o grep para verificar ocorrências específicas nos logs:

bash

grep "OFFLINE" offline.log

🎉 Resultado Final

Seu servidor Nginx está configurado e monitorado com sucesso!


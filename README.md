# server_nginx
Passo 1: Instalar o Oracle VM VirtualBox
  - Baixe e instale o Oracle VM VirtualBox a partir do site oficial: VirtualBox.

Passo 2: Baixar a imagem do Debian
  - Baixe a ISO do Debian a partir do site oficial: www.debian.org

Passo 3: Criar uma nova máquina virtual
  - Abra o VirtualBox.
  - Clique em "Novo" para criar uma nova máquina virtual.
  - Dê um nome à VM (por exemplo, "Debian_nginx").
  - Selecione o tipo: "Linux" e versão: "Debian 12 (64-bit)".
  - Alocar memória RAM (recomendo pelo menos 1024 MB).
  - Crie um disco rígido virtual, selecionando "Criar um disco rígido virtual agora".
  - Escolha o tipo de disco (recomendo VDI) e tamanho do disco (recomendo pelo menos 10 GB).
    
Passo 4: Configurar a máquina virtual
  - Com a VM selecionada, clique em "Configurações".
  - Vá para "Armazenamento" e clique no ícone de disco vazio.
  - No lado direito, clique no ícone de disco e selecione "Escolher um disco existente".
  - Selecione a ISO do Debian que você baixou.

Passo 5: Iniciar a máquina virtual
  - Clique em "Iniciar" para ligar a máquina virtual.
  - Siga as instruções na tela para instalar o Debian.
    
Passo 6: Instalar o Nginx
- Atualize os pacotes. Abra o terminal e digite:
  sudo apt update
  sudo apt upgrade

- Instale o Nginx:
  sudo apt install nginx

Passo 7: Iniciar o Nginx
- Inicie o Nginx com o comando:
  sudo systemctl start nginx
  
- Verifique se o Nginx está rodando:
  sudo systemctl status nginx
  
Passo 8: Testar a instalação
- Abra um navegador e digite o IP da sua máquina virtual (você pode descobrir o IP com ifconfig ou ip addr).
  Você deve ver a página padrão do Nginx.

Passo 9: Configurações adicionais (opcional)
- Para iniciar o Nginx automaticamente na inicialização:
  sudo systemctl enable nginx
  
- Observação: Para configurar Nginx para um site específico, edite ou crie arquivos de configuração na pasta /etc/nginx/sites-available/.

Passo 10: Manutenção
- Para parar o Nginx:
  sudo systemctl stop nginx
  
- Para reiniciar o Nginx:
  sudo systemctl restart nginx

  Passo 11: Verificar seu IP e depois colar na URL do navegador

  ip addr show
  ![image](https://github.com/user-attachments/assets/ac0d746a-747b-43d7-96f9-dec2a4ef9254)

  - Após colar na URL do navegador:
    ![image](https://github.com/user-attachments/assets/e14b5b3d-1c05-4b78-a9e5-22278d609cf8)

  Passo 12: testar as configurações pelo terminal 

  mkdir atividade_linux
  cd atividade_linux
nano verificar_nginx.sh 
  Adicione à última linha o seguinte script:
#!/bin/bash
#Variáveis
DATA_HORA=$(date '+%Y-%m-%d %H:%M:%S')
SERVICO="Nginx"
DIRETORIO="./"
ONLINE="${DIRETORIO}/online.log"
OFFLINE="${DIRETORIO}/offline.log"

#Verifica o status do Nginx
STATUS=$(systemctl is-active nginx)

#Condição para verificar se o Nginx está online
if [ "$STATUS" = "active" ]; then
    echo "$DATA_HORA - $SERVICO - ONLINE - O serviço está rodando." >> $ONLINE
else
    echo "$DATA_HORA - $SERVICO - OFFLINE - O serviço está parado." >> $OFFLINE
fi
- após isso aperte ctrl+o  ,  enter  ,  Ctrl+x   para salvar no nano

chmod +x verificar_nginx.sh
contrab -e    (escolha a opção número 1)
edite a última linha de comando adicionando o parâmetro:
/5 * * * /home/tales/atividade_linux/verificar_nginx.sh
- após isso aperte ctrl+o  ,  enter  ,  Ctrl+x   para salvar no crontab


  - Coloque seus dados do github com os comandos git e crie um commit -m "nome que desejar"
  git init
  git .add
  git commit -m "Versão inicial da atividade"
  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"
- Verifique a aplicação 
  ./verificar_nginx.sh
  cat online.log
  ![image](https://github.com/user-attachments/assets/98442a1c-e114-4e9d-86c8-9ac78c89154a)
  -após verificar online, pare a aplicação com
  sudo systemctl stop nginx
  e agora aplique o teste estando offline
   ![image](https://github.com/user-attachments/assets/c988395c-fa42-4775-8a64-e7b7b0128426)
  
  - Aqui com o comando grep você verá os arquivos de saída online e offline
  ![image](https://github.com/user-attachments/assets/887a8a59-2057-4311-8203-955d49450b4d)
  E, por fim o resultado final com o git status
![image](https://github.com/user-attachments/assets/03dbd9d7-702a-444b-a8f8-620b56e8f4dc)

Meus parabéns você conseguiu e o servidor está rodando como o esperado!!
  
  
  


  
  




  


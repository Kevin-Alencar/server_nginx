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




  


# server_nginx
markdown
# 🌐 Server Nginx

## 📋 Passo a Passo para Instalação

### 1️⃣ Instalar o Oracle VM VirtualBox
- Baixe e instale o [Oracle VM VirtualBox](https://www.virtualbox.org/) a partir do site oficial.

### 2️⃣ Baixar a Imagem do Debian
- Baixe a ISO do [Debian](https://www.debian.org/) a partir do site oficial.

### 3️⃣ Criar uma Nova Máquina Virtual
- Abra o VirtualBox.
- Clique em "Novo" para criar uma nova máquina virtual.
- Dê um nome à VM (exemplo: `Debian_nginx`).
- Selecione o tipo: **Linux** e versão: **Debian 12 (64-bit)**.
- Alocar memória RAM (recomendo pelo menos **1024 MB**).
- Crie um disco rígido virtual, selecionando "Criar um disco rígido virtual agora".
- Escolha o tipo de disco (recomendo **VDI**) e tamanho do disco (pelo menos **10 GB**).

### 4️⃣ Configurar a Máquina Virtual
- Com a VM selecionada, clique em "Configurações".
- Vá para "Armazenamento" e clique no ícone de disco vazio.
- No lado direito, clique no ícone de disco e selecione "Escolher um disco existente".
- Selecione a ISO do Debian que você baixou.

### 5️⃣ Iniciar a Máquina Virtual
- Clique em "Iniciar" para ligar a máquina virtual.
- Siga as instruções na tela para instalar o Debian.

### 6️⃣ Instalar o Nginx
- Atualize os pacotes. Abra o terminal e digite:
  ```bash
  sudo apt update
  sudo apt upgrade
Instale o Nginx:
sudo apt install nginx
7️⃣ Iniciar o Nginx
Inicie o Nginx com o comando:

sudo systemctl start nginx
Verifique se o Nginx está rodando:

sudo systemctl status nginx
8️⃣ Testar a Instalação
Abra um navegador e digite o IP da sua máquina virtual (descubra o IP com ifconfig ou ip addr). Você deve ver a página padrão do Nginx.
9️⃣ Configurações Adicionais (Opcional)
Para iniciar o Nginx automaticamente na inicialização:

sudo systemctl enable nginx
Para configurar Nginx para um site específico, edite ou crie arquivos de configuração na pasta /etc/nginx/sites-available/.
🔧 Manutenção
Para parar o Nginx:
sudo systemctl stop nginx
Para reiniciar o Nginx:
sudo systemctl restart nginx
1️⃣0️⃣ Verificar Seu IP
Verifique seu IP:
ip addr show

1️⃣1️⃣ Testar as Configurações pelo Terminal
mkdir atividade_linux
cd atividade_linux
nano verificar_nginx.sh
Adicione à última linha o seguinte script:
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
Salve no nano: Ctrl + O, Enter, Ctrl + X.
1️⃣2️⃣ Configurar o Crontab
chmod +x verificar_nginx.sh
crontab -e
Escolha a opção número 1 e adicione:
*/5 * * * /home/tales/atividade_linux/verificar_nginx.sh
Salve no crontab: Ctrl + O, Enter, Ctrl + X.
1️⃣3️⃣ Colocar Seus Dados do GitHub
git init
git add .
git commit -m "Versão inicial da atividade"
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
1️⃣4️⃣ Verificar a Aplicação
./verificar_nginx.sh
cat online.log

Para parar a aplicação:
bash
Copiar código
sudo systemctl stop nginx
Aplique o teste estando offline:
1️⃣5️⃣ Verificar Resultados com Grep

1️⃣6️⃣ Resultado Final

🎉 Parabéns!
Você conseguiu! O servidor está rodando como o esperado!!

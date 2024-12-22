# PROJETO PRÁTICO LINUX COM WSL, CompassUOL

# Requisitos.
 Windows 10 ou superior
 
 WSL (Windows Subsystem for Linux)
 
 Ubuntu 20.04 ou superior
 
 # Objetivo.
 Criar o subsistema Linux (WSL):

Instalar o WSL no Windows.
Instalar a distribuição Ubuntu 20.04 ou superior.
Subir o servidor Nginx:

 Instalar o Nginx no Ubuntu via WSL.
 Garantir que o servidor Nginx esteja funcionando corretamente.
 Criar um script para validar o status do Nginx:

 O script deve verificar se o Nginx está online ou offline.
 O script deve gerar dois arquivos de log: um para quando o serviço estiver online e outro para quando estiver offline.
 O arquivo de log deve conter: Data + Hora + Nome do serviço + Status + Mensagem personalizada.
 Automatizar a execução do script a cada 5 minutos:

 Usar o cron para automatizar a execução do script a cada 5 minutos.
 Versionamento no GitHub:

Subir o código para um repositório no GitHub.
Documentação:

 Documentar o processo de instalação do Linux, configuração do servidor Nginx e a automação do script.

 # 1. Ativação do WSL.
 Para a ativação do WSL (Windows Subsystem for Linux) no Windows, você deve seguir os seguintes passos. 
 # Passo 1. Utilizando o PowerShell.
 
 1. Abra o PowerShell com permissões de administrador e execute o seguinte comando:
    
 2. ![wsl](https://github.com/user-attachments/assets/f07d9e8d-0d6a-4caf-8d6a-68c74cc9f745)
    
 3. Este comando irá instalar automaticamente o WSL e os componentes necessários. Após a instalação, o Ubuntu será iniciado automaticamente. 

  # 2. Instalação do Ubuntu 20.04 ou superior.
# Configuração do Ubuntu.
Após a instalação do Ubuntu, vá até o Menu Iniciar e procure por Ubuntu. Clique para abrir o aplicativo.
Na primeira vez que o Ubuntu for aberto, ele solicitará a criação de um usuário e senha.
Isso é necessário para além do usuário root, que já existe no sistema.

 # Testando a Configuração.
Após a instalação e configuração do Ubuntu, você pode usar alguns comandos para verificar o funcionamento do sistema como:

Exibe o nome do usuário atualmente logado no sistema.

![whoami](https://github.com/user-attachments/assets/3ec65a35-e9b9-4fe9-8a43-b2a6979738c3)

Exibe o nome do host da máquina, útil para identificar o computador na rede.

![hostname](https://github.com/user-attachments/assets/52cdf43f-9466-472b-8dc6-fbcecfb20b87)

![hostnameH](https://github.com/user-attachments/assets/365247fc-08b1-43a3-ac65-aa44dc12c4ff)

Exibe informações detalhadas sobre o sistema operacional, como o kernel e a versão do Ubuntu em uso.

![uname-a](https://github.com/user-attachments/assets/3ccbbf3e-626f-4914-9366-961e7f093c21)

![uname-aa](https://github.com/user-attachments/assets/639c6001-bfcf-40e3-958e-8d42cb4a3471)

Exibe o nome do usuário atual.

![id-un](https://github.com/user-attachments/assets/d6e36143-8a9c-4379-95e2-e712b69fed51)

![id-unhellen](https://github.com/user-attachments/assets/aa6138be-f6ab-4557-a228-5c6803f5bc30)

Exibe o nome do usuário configurado no sistema.

![USER](https://github.com/user-attachments/assets/8d1a22b0-a926-4fe0-bcec-636087464b27)

![USERHELLEN](https://github.com/user-attachments/assets/18f7542a-2057-4e83-93c5-7d815138ff5d)


# 3. Execute um servidor Nginx.
Agora que o Ubuntu está configurado corretamente, podemos proceder com a instalação e configuração do servidor Nginx no Ubuntu.

# Passo 1: Atualizar o sistema e instalar o Nginx.

# Comando para atualizar o sistema:
sudo apt update
(aguarde a atualização dos pacotes)

# Comando para instalar o Nginx em si:
sudo apt install nginx
(aguarde a instalação)

 Configurar o Firewall para que o acesso ocorra (Irá configurar depedendo da forma que você estiver rodando)
# Comando do meu Firewall:
sudo ufw app list
(irá te mostrar os aplicativos disponiveis) 

![http](https://github.com/user-attachments/assets/fed1e7d9-e7cf-47ce-aa18-bc47f7db90ce)

(iremos configurar para liberar apenas o acesso ao Nginx HTTP)

# Comando para escolher o Nginx HTTP:

sudo ufw allow 'Nginx HTTP'

![SUDOHTTP](https://github.com/user-attachments/assets/78b79098-49a9-4f0d-8990-38e58c0d6803)

# Comando para verificar o STATUS:

sudo ufw status

![ufwativo](https://github.com/user-attachments/assets/736fbb23-6ed1-499e-9189-824db9760ef1)

# Comando para verificar o status do Nginx:

systemctl status nginx

![status nginx](https://github.com/user-attachments/assets/39c15c90-9106-43b9-8772-c2b12c186fe7)

# Realize o teste, utilizando o ip da máquina ou em um navegador como "localhost":

Para visualizar qual é o ip, digite o seguinte comando:

 ip addr show
 
 ![ipaddrshow](https://github.com/user-attachments/assets/b708d463-a98d-49e2-b605-fda36a90149a)
 
 (onde está grifado em cinza será o nosso ip para visualizar a página no navegador Nginx)
 
Deverá aparecer a seguinte mensagem:

![print3](https://github.com/user-attachments/assets/e20e2406-fbcd-4110-95cb-88017699e2e4)

o servidor já está instalado e rodando.

# Gerenciar o Nginx utilizando alguns comandos no terminal:

 systemctl stop nginx (parar)
 systemctl start nginx (iniciar)
 systemctl restart nginx (reiniciar)
 systemctl reload nginx (recarregar sem reiniciar o serviço)
 systemctl disable nginx (desabilitar)
 systemctl enable nginx (habilitar inicio automático)

# 4. Criação do Script de Verificação de Status.
Informação: Onde colocar o script? Ele pode ser colocado em qualquer diretório de sua escolha, mas há algumas convenções para o local dos scripts no Linux:

Scripts pessoais de usuário: Normalmente ficam em /home/usuario. Scripts de sistema: Normalmente ficam em /usr/local/bin ou /opt/. Se o script for algo mais global, pode ser colocado em qualquer um dos dois primeiros diretórios.

# Passo 1: Criar um diretório de scripts.
Para organizar os arquivos, crie um diretório com o comando:

mkdir scripts

![script](https://github.com/user-attachments/assets/c1b3e6f0-a098-4e97-b8c9-730e6fc73fad)


# Passo 2: Navegar até o diretório criado.
Use o comando a seguir para acessar o diretório:
cd ~/scripts

![cdscript](https://github.com/user-attachments/assets/d791ea3d-9c2b-408f-a27b-ece99fe2a373)

Obs: Agora, dentro do diretório scripts, você está pronto para criar o arquivo de shell script de verificação.
# Passo 3: Criar o arquivo usando o editor Nano.
No terminal, utilize o comando:
nano valida_nginx.sh

![nano](https://github.com/user-attachments/assets/8e56b695-3bf9-48d0-8b88-ed623c83d7f4)

Obs: O sufixo .sh não é obrigatório, mas é uma convenção amplamente utilizada para indicar que o arquivo se trata de um shell script. Isso facilita a identificação e é considerado uma boa prática.
# Passo 4: Escrever o script de validação
Com o arquivo aberto para edição, criei um script que valida (verifica) se o serviço está online. O script deve enviar o resultado dessa validação para um diretório que eu definir.

A estrutura do script deve incluir:

Data e hora;
Nome do serviço;
Status (online ou offline);
Mensagem personalizada, informando se o serviço está online ou offline.
Observação: O script deve gerar dois arquivos de saída:

Um arquivo para registrar quando o serviço está online;
Outro arquivo para registrar quando o serviço está offline.

![onlineoffiline](https://github.com/user-attachments/assets/248517ee-d6de-4afe-b092-55636ea62908)


# Passo 5: Testar manualmente o script valida_nginx.sh criado.
Certifique-se de que o script tem permissão para ser executado:
chmod +x ~/scripts/valida_nginx.sh
Executar o Script.
./valida_nginx.sh
Verificar os Logs.
# O script grava dois tipos de logs: online.log e offline.log.

Para verificar qual log foi atualizado: Se o Nginx estiver online, o log online.log deverá conter algo como:

tail ~/scripts/logs/online.log

![print7](https://github.com/user-attachments/assets/c59f4596-ffad-4b3f-863d-e6ce742c6b85)

Se o Nginx estiver offline, o log offline.log
 tail ~/scripts/logs/offline.log
 
 ![print8 offline](https://github.com/user-attachments/assets/21eac10e-ec8b-4dc6-8a97-19f029acf1e1)
 
 Obs: Aqui já podemos ver que o cron está configurado automaticamente para executar o script a cada 5 minutos, atualizando ambos os logs: online.log e offline.log, dependendo do status do serviço.

 # 5. Automatização da Execução do Script.
Configure a execução automatizada do script a cada 5 minutos. Para isso, utilize o cron.
# Configuração do cron
Segue o passo a passo para configurar o cron:

# Passo 1: Use este comando para editar o arquivo do crontab.
crontab -e
# Passo 2: Adicione a seguinte linha ao final do arquivo para agendar o script.
*/5 * * * * /caminho/para/o/script/valida_nginx.sh

![print9 5minutos](https://github.com/user-attachments/assets/df60d3d1-d980-473d-8a05-e3a95af69d79)

Salve e saia do editor. 
# Passo a passo: 
Pressione CTRL+O para abrir a opção de salvar
Confirme o nome do arquivo enviado, ENTER.
Pressione CTRL+X para fechar o editor.
# Passo 3:
Para verificar se a configuração foi aplicada corretamente, use o comando:
crontab -1 
Isso mostra uma lista de tarefas agendadas no cron para o usuário atual.

![print10 ](https://github.com/user-attachments/assets/a3f58098-8a78-42eb-911f-dde84ba371e3)


# Finalizado. 









































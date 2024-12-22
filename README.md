# Requisitos
 Windows 10 ou superior
 WSL (Windows Subsystem for Linux)
 Ubuntu 20.04 ou superior
 
 Objetivos
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


# 1. Kathará
É um sistema de emulação de rede leve baseado em contêineres Docker. Ele pode ser realmente útil para mostrar demonstrações/aulas interativas, testar redes de produção em um ambiente sandbox ou desenvolver novos protocolos de rede.[1] 

# 2. Instalação
O Kathara depende do Docker para rodar, portanto, instalar o Docker primeiro.

## 2.1. Instalação no Ubuntu:
### 2.1.1. Adicionar a chave pública para obter o Kathará: 
- sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 21805A48E6CBBA6B991ABE76646193862B759810
### 2.1.2. Adicionar o repositório do Kathará:
- sudo add-apt-repository ppa:katharaframework/kathara
### 2.1.3. Atualizar o acesso aos repositórios:
- sudo apt update
### 2.1.4. Instalar o Kathará:
- sudo apt-install install kathara
### 2.1.5. Verificar instalação do Kathará:
- kathara ckeck 
### 2.1.6. Instalação Xterm
- sudo apt-get install xterm

# 3. Procedimentos práticos
## 3.1. Comandos para iniciar os dispositivos pc1 e pc2, ambos com a interface eth0 conectada ao domínio de colisão A:
- kathara vstart --name pc1 --eth 0:A
- kathara vstart --name pc2 --eth 0:A
- Cada comando ativará a console do respectivo dispositivo.
## 3.2. Configuração das interfaces de rede dos dispositivos com ifconfig:
### 3.2.1. Acessar a console de cada dispositivo para configurar as interfaces de rede:
- pc1: ifconfig eth0 192.168.0.1/24 up
- pc2: ifconfig eth0 192.168.0.2/24 up
## 3.2.2. Verificar as configurações em cada dispositivo:
- ifconfig
## 3.3. Teste de conectividade com ping:
- pc1 -> pc2: ping 192.168.0.2
## 3.4. Captura de pacotes com tcpdump:
- pc2: tcpdump icmp
- Captura pacotes icmp (ping) na interface eth0 (default).
## 3.5. Visualizar a captura de forma gráfica com wireshark no hospedeiro:
### 3.5.1. Ativar o compartilhamento do /hosthome com o comando:
- kathara settings
### 3.5.2. Capturar no pc2 pacote e gravar saída em arquivo:
- tcpdump icmp -w /hosthome/cap1.ncap
### 3.5.3. Abrir arquivo no hospedeiro com wireshark.
## 3.6. Remover dispositivos:
- kathara vclean --name pc1
- kathara vclean --name pc2
## 3.7. Limpar todos os dispositivos e domínios de colisão:
- kathara wipe
## 3.8. Comando para iniciar e parar rede do laboratório
### 3.8.1 Inicia rede
- kathara lstart
### 3.8.2. Para rede
- kathara lclean

# Referências
[1] [Kathará](https://github.com/KatharaFramework/Kathara)

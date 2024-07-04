1. Kathará
é um sistema de emulação de rede leve baseado em contêineres Docker. Ele pode ser realmente útil para mostrar demonstrações/aulas interativas, testar redes de produção em um ambiente sandbox ou desenvolver novos protocolos de rede.[1] 

# Instalação
O Kathara depende do Docker para rodar, portanto, instalar o Docker primeiro.

## Instalação no Ubuntu:
### Adicionar a chave pública para obter o Kathará: 
- sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 21805A48E6CBBA6B991ABE76646193862B759810
### Adicionar o repositório do Kathará:
- sudo add-apt-repository ppa:katharaframework/kathara
### Atualizar o acesso aos repositórios:
- sudo apt update
### Instalar o Kathará:
- sudo apt-install install kathara
### Verificar instalação do Kathará:
- kathara ckeck 
### Instalação Xterm
- sudo apt-get install xterm

# Procedimentos práticos
## Comandos para iniciar os dispositivos pc1 e pc2, ambos com a interface eth0 conectada ao domínio de colisão A:
- kathara vstart --name pc1 --eth 0:A
- kathara vstart --name pc2 --eth 0:A
- Cada comando ativará a console do respectivo dispositivo.
## Configuração das interfaces de rede dos dispositivos com ifconfig:
### Acessar a console de cada dispositivo para configurar as interfaces de rede:
- pc1: ifconfig eth0 192.168.0.1/24 up
- pc2: ifconfig eth0 192.168.0.2/24 up
## Verificar as configurações em cada dispositivo:
- ifconfig
## Teste de conectividade com ping:
- pc1 -> pc2: ping 192.168.0.2
## Captura de pacotes com tcpdump:
- pc2: tcpdump icmp
- Captura pacotes icmp (ping) na interface eth0 (default).
## Visualizar a captura de forma gráfica com wireshark no hospedeiro:
### Ativar o compartilhamento do /hosthome com o comando:
- kathara settings
## Capturar no pc2 pacote e gravar saída em arquivo:
- tcpdump icmp -w /hosthome/cap1.ncap
## Abrir arquivo no hospedeiro com wireshark.
## Remover dispositivos:
- kathara vclean --name pc1
- kathara vclean --name pc2
## Limpar todos os dispositivos e domínios de colisão:
- kathara wipe
## Rede criada com arquivos de configuração
O Kathará permite a construção de estruturas de rede com diferentes tipos de dispositivos, como hosts, roteadores e outros, os quais são configurados por meio de arquivos de configuração e diretórios.
## Comando para iniciar e parar rede do laboratório
### Inicia rede
- kathara lstart
### Para rede
- kathara lclean

# Referências
[1] [Kathará](https://github.com/KatharaFramework/Kathara)

# Kathará
é um sistema de emulação de rede leve baseado em contêineres Docker. Ele pode ser realmente útil para mostrar demonstrações/aulas interativas, testar redes de produção em um ambiente sandbox ou desenvolver novos protocolos de rede. [Kathará] (https://github.com/KatharaFramework/Kathara)

# Como funciona?
Cada dispositivo de rede é emulado por um contêiner. Dispositivos de rede virtuais são interconectados por LANs L2 virtuais.

# Instalação
O Kathara depende do Docker para rodar, portanto, instalar o Docker primeiro.

## Instalação Codespace GitHub:
$ Adicionar a chave pública para obter o Kathará: 
#### sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 21805A48E6CBBA6B991ABE76646193862B759810
### Adicionar o repositório do Kathará:
#### sudo add-apt-repository ppa:katharaframework/kathara
### Atualizar o acesso aos repositórios:
#### sudo apt update
### Instalar o Kathará:
#### sudo apt install kathara

  

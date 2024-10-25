    TROCAR NOME DO EQUIPAMENTO

    Switch>enable
    Switch#configure terminal
    Switch(config)#hostname <nome> SW-SALA-13
    SW-SALA-13(config)#exit 
    SW-SALA-13#exit (saindo dos privilegios)

CONFIGURAR UM BANNER 

SW-SALA-13>enable
SW-SALA-13#configure terminal
SW-SALA-13(config)#banner motd "<texto>" "Acesso apenas Para pessoas Autorizadas!"
SW-SALA-13#(config)#CRTL + z
SW-SALA-13#exit

CONFIGURAR SENHA NA CONSOLE

SW-SALA-13>enable
SW-SALA-13#configure terminal
SW-SALA-13(config)#line console 0
SW-SALA-13(config-line)#password <senha> batata*0
SW-SALA-13(config-line)#login
SW-SALA-13(config-line)#CTRL + Z


CONFIGURAR SENHA NA ENABLE 

SW-SALA-13>enable
SW-SALA-13#configure terminal
SW-SALA-13(config)enable password <senha> senhasegura
SW-SALA-13(config)#CTRL + Z
SW-SALA-13#exit

ATIVAR O SERVIÇO DE CRIPTOGRAFIA 

SW-SALA-13>enable
SW-SALA-13#configure terminal
SW-SALA-13(config)#service password-encryption
SW-Sala-13(config)#CTRL + Z
SW-SALA-13#show running-config

SW-SALA-13>enable
SW-SALA-13#configure terminal
SW-SALA-13(config)#no hostname SW-SALA-13

DESATIVAR UMA INTERFACE 

SW-SALA-13>enable
SW-SALA-13#configure terminal
SW-SALA-13(config)#interface ?
SW-SALA-13(config)#interface FastEthernet 0/2
SW-SALA-13(config-if)#shutdown

DESATIVAR VARIAS INTERFACES DE UMA SÓ VEZ 

SW-SALA-13>enable
SW-SALA-13#configure terminal
SW-SALA-13(config)#interface range <intervalo>
SW-SALA-13(config)#interface range FastEthernet 0/-1-3
SW-SALA-13(config-if-range)#CTRL + Z
SW-SALA-13# 

************* COM INTERVALOS DIFERENTES 

SW-SALA-13(config)#interface range FastEthernet 0/-1-3 FastEthernet 0/7 FastEthernet 0/11-24

********** PARA ATIVAR **************
SW-SALA-13(config-if-range)#no shutdown 


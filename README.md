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




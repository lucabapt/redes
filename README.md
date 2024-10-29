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
SW-SALA-13(config)enable secret <senha> senhasegura
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

CONFIGURANDO O CLOCK 

SW-SALA-13>enable

!Mostrar o clock atual
SW-SALA-13#show clock

SW-SALA-13#clock set ?
SW-SALA-13#clock set ? 14:50:00 ?
SW-SALA-13#clock set 14:50:00 28 OCT 2024


CONFIGURANDO CLOCK VIA NTP


SW-SALA-13>enable
SW-SALA-13#configure terminal 
SW-SALA-13(config)# ntp ?
SW-SALA-13(config)#ntp server <IP do server NTP>
                ex: #net server 200.20.224.100
SW-SALA-13(config)#end
SW-SALA-13#wr
SW-SALA-13#exit

SW-SALA-13>enable



!ver memoria RAM
SW-SALA-13#show running-config


!ver memoria NVRAM
SW-SALA-13#show startup config 

!ver o resumo das interfaces 
SW-SALA-13#show ip interface brief 

!ver o resumo das VLANS 
SW-SALA-13#show vlans brief 

!mostrar informacoes da interface
SW-SALA-13#show interfaces FastEthernet0/1

SPEED
10Mbps -> Ethernet0/1
100Mbps -> FastEthernet0/1
10000Mbps ou 1Giga -> GigabitEthernet0/1
100000Mbps ou 10gigas ->TenGigavitEthernet0/1

SALVAR AS CONFIGURAÇÕES 

SW-SALA-13>enable 


!copia da memoria RAM para NVRAM
SW-SALA-13#copy running-config startup-config 

!do wr em qualquer parte
SW-SALA-13#wr

RESETAR AS CONFIGURAÇÕES DE FABRICA 

SW-SALA-13>enable

!Apagar as configurações atual da NVRAM 
SW-SALA-13#write erase 

!ou 
SW-SALA-13#erase startup-config

!Reiniciar o dispositivo 
SW-SALA-13#reload 

VERIFICAR O VLAN.DAT
SW-SALA-13>enable 


!verificar o conteudo da vlan.dat
SW-SALA-13#dir flash:



!apagar o arquivo vlan.dat 
SW-SALA-13#delete flash:vlan.dat

!Reiniciar o dispositivo 
SW-SALA-13#reload



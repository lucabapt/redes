#TROCAR NOME DO EQUIPAMENTO

Switch>enable
Switch#configure terminal
Switch(config)#hostname <nome> SW-SALA-13
SW-SALA-13(config)#exit 
SW-SALA-13#exit (saindo dos privilegios)

#CONFIGURAR UM BANNER 

SW-SALA-13>enable
SW-SALA-13#configure terminal
SW-SALA-13(config)#banner motd "<texto>" "Acesso apenas Para pessoas Autorizadas!"
SW-SALA-13#(config)#CRTL + z
SW-SALA-13#exit

#CONFIGURAR SENHA NA CONSOLE

SW-SALA-13>enable
SW-SALA-13#configure terminal
SW-SALA-13(config)#line console 0
SW-SALA-13(config-line)#password <senha> batata*0
SW-SALA-13(config-line)#login
SW-SALA-13(config-line)#CTRL + Z


#CONFIGURAR SENHA NA ENABLE 

SW-SALA-13>enable
SW-SALA-13#configure terminal
SW-SALA-13(config)enable secret <senha> senhasegura
SW-SALA-13(config)#CTRL + Z
SW-SALA-13#exit

#ATIVAR O SERVIÇO DE CRIPTOGRAFIA 

SW-SALA-13>enable
SW-SALA-13#configure terminal
SW-SALA-13(config)#service password-encryption
SW-Sala-13(config)#CTRL + Z
SW-SALA-13#show running-config

SW-SALA-13>enable
SW-SALA-13#configure terminal
SW-SALA-13(config)#no hostname SW-SALA-13

#DESATIVAR UMA INTERFACE 

SW-SALA-13>enable
SW-SALA-13#configure terminal
SW-SALA-13(config)#interface ?
SW-SALA-13(config)#interface FastEthernet 0/2
SW-SALA-13(config-if)#shutdown

#DESATIVAR VARIAS INTERFACES DE UMA SÓ VEZ 

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

#CONFIGURANDO O CLOCK 

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


enable
configure terminal
hostname SW-AULA-47
banner motd "Acesso apenas Para o departamento de TI!"
line console 0
password Senha@console
login
enable secret Senha@enable
service password-encryption
end 
wr

!AUTOR LUCAS BAPTISTA
!DATA 27/10/2024
!OBJETIVO: esse script define o nome e senhas de acesso com criptografia type 5 e 7

!entra no modo EXEC-PRIVILEGIADO
enable

!entra no modo de configuracao
configure terminal

!altera o nome do equipamento
hostname SW-AULA-47

!cria uma senha para o comando enable, que utiliza a criptografia type5
enable secret Senha@enable

!cria uma senha para o comando enable, que utiliza a criptografia type7
service password-encryption

!Criptografia 


enable
configure terminal
hostname SW-CORE
banner motd "Apenas os funcionarios do Departamento de TI da TECHNETINNOVATIONS podem acessar esse dispositivo"
enable secret Senha*3n4b13
line console 0
password Senha*c0n5013
login
service password-encryption
end
wr



!configurar o ip na interface 
enable
configure terminal
interface g0/0
ip address 192.168.0.1 255.255.255.0

!vizualizar a tabela de roteamento
enable
configure terminal


enable
configure terminal
banner motd "Acesso apenas para o Departamento de TI da Lordran S.A!"
enable secret PraiseTheSun@00
line console 0
password Estus*Password
login
exit
service password-encryption
do wr
interface range 
shutdown
interface range g0/1 - 2, g0/4 - 24
shutdown
end
write memory




enable
configure terminal
hostname SW-02
SW-SALA-13(config)#exit 
SW-SALA-13#exit (saindo dos privilegios)

//configurar uma interface para o modo trunk
enable
#configure terminal 
(config)#interface <nome-da-interface>
                //ex: g0/1
(config-if)#switchport mode trunk
do wr                

!configurar Vlan nativa na interface trunk
enable
#configure terminal
(config)#interface <nome-da-interface>
                //ex: g0/1
(config-if)# trunk native vlan <nØ-da-vlan-nativa>
                                !ex:99
do wr


!verificar as configurações da interface 
enable
#show interface g0/1 switchport

!liberar as Vlans na interface trunk 
enable
#configure terminal 
(config)#interface <nome-da-interface>
                    !ex: g0/1

(config-if)#switchport trunk allowed vlan <lista de vlans separados por virgulas> 
    !exemplo: switchport trunk allowed vlan 10,20,30,40, 99

enable
configure terminal
hostname S3
exit
conf t
vlan 10
name Docente/Funcionario
exit
exit
configure terminal
vlan 20
name Alunos
exit
exit
configure terminal
vlan 30
name Convidado(Padrao)


enable
configure terminal
interface f0/11
switchport mode access
switchport access vlan 10
do wr
end
configure terminal
interface f0/18
switchport mode access
switchport access vlan 20
do wr
end
configure terminal
interface f0/6
switchport mode access
switchport access vlan 30
do wr

    
enable 
configure terminal 
hostname SW-01
banner motd "
		
		+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
		+                             LINOTEC-LTDA                                +
		+             ACESSO PERMITIDO SOMENTE A PESSOAS AUTORIZADAS              +
		+           PESSOAS NAO AUTORIZADAS DESCONECTAR IMEDIATAMENTE             +
		+         TODAS AS CONEXOES ESTAO SENDO MONITORADAS E AUDITADAS           +
		+                  ATTENTION: AUTHORIZED PERSONAL ONLY.                   +
		+                         DISCONNECT IMMEDIATELY.                         +
		+                                                                         +
		+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ "
vlan 10
name ALUNOS
vlan 20 
name PROFESSORES
vlan 30
name COORDENACAO
vlan 90
name GERENCIAMENTO
interface range g0/1-2
switchport mode trunk
switchport trunk native vlan 99
switchport trunk allowed vlan 10,20,30,90,99
end
wr





!configurar ip no switch 
>enable
#configure terminal 
(config)#interface vlan 90
(config-if)#ip address <endereço> <mascara>




!configurar subinterfaces no router
>enable
#configure terminal 
(config)#interface <nome-da-subinterface>
		!ex:interface g0/0.10
		!sendo 10 o numero da vlan
(config-subif)#encapsulation dot1q <nº-da-vlan>		
(config-subif)#ip-address<ip> <mascara>



!criar vlans
enable
conf t
vlan 10
name ALUNOS
vlan 20
name PROFESSORES
Vlan 30
name COORDENAÇÃO 

!atribuir a Vlan as interfaces 
int g1/0/1
switchport mode access
switchport access vlan 10
no shutdown
exit

!configurar interfaces vlan
interface vlan 10
ip address 192.168.0.129 255.255.255/224
no shutdown
exit 

!Ativar roteamento entre vlans
ip routing 

!salvar configurações 
end
wr


!configurar o SSH
!definir o nome de dominio 
>enable 
#configure terminal 
(config)#ip domain-name {nome-de-dominio}
		!Ex:ip domain-name Senai.local

!definir a chave de criptografia 
(config)#crypto key generate rsa general-keys modulus <tamanho-dachave>
														!ex:1024

!criar usuarios locais 
(configure)#username <nome-do-usuario> privilege <1-15> secret <senha>	


!Ativar o SSH nas linhas VTY
(config)#line vty 0 15
(config-line)#transport input SSH



Exercicio Referente ao dia 22/11/2024

!PC
IP 192.168.10.0
Mascara 255.255.255.0
gateway 192.168.10.1

!SW-RH
F0/1
dispositivo final modo access vlan 10


g0/1
trunk
todas vlans

!SW-CORE
g0/1-4
todas as vlans 

f0/1
access
vlan 40

!SW-MKT
F0/1
dispositivo final modo access vlan 20

g0/1
trunk
todas vlans


!SW-TI
F0/
access
vlan 30

g0/1
trunk
todas vlans 

RT-01
g0/0
g0/0.10
192.168.10.1 255.255.255.0

g0/0.20
192.168.10.1 255.255.255.0


g0/0.30
192.168.10.1 255.255.255.0

g0/0.40
192.168.10.1 255.255.255.0

!Script 
!SW-RH
enable 
conf t
hostname SW-RH

!Criar as vlans
vlan 10
name RH 

vlan 20
name MKT 

vlan 30
name TI

vlan 40
name DIR


!configurar interface 
int f0/1
switchport mode access 
switchport access vlan 10

int g0/1
switchport mode trunk
switchport trunk native vlan 99
switchport trunk allowed vlan 10,20,30,40,99

!salvar
end
wr

!RT-01
enable
hostname RT-01
int g0/0
no shutdown 

int g0/0.10
encapsulation dot1q 10
ip add 192.168.10.1 255.255.255.0

int g0/0.20
encapsulation dot1q 20
ip add 192.168.20.1 255.255.255.0


int g0/0.30
encapsulation dot1q 30
ip add 192.168.30.1 255.255.255.0

int g0/0.40
encapsulation dot1q 40
ip add 192.168.40.1 255.255.255.0

!Mostrar as informações STP por valm
show spanning-tree vlan1


!mostrar as informaçoes do stp de todas as vlans
enable
Show spanning-tree


!mostrar as informações de vlan
enable
show int vlan 1

!1-Forma - mudar a prioridade 
enable
conf-t
spanning-tree vlan 1 priority <numero-da-prioridade>
								!Ex 4096

2-Forma mudar prioridade da Vlan
enable
conf t
spanning-tree vlan 1 root <primary-ou-secundary>
							Ex:primary

!Simular os estados das portas
enable
int g/1
shutdown
no shutdown
do show span vlan 1

!como trocar o custo da porta
enable
conf t
int g0/1
spanning-tree cost <numero-do-custo> <1-2000000000>
	!ex: spanning-tree cost 100
do show span vlan 

!ver quais comandos podemos usar na interface
enable
conf t 
int g0/1
spanning-tree ? 

!como mudar o protocolo 
enable
conf t 
spanning-tree mode rapid-pvst






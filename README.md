# Ataque-de-Brute-Force
Simulando um Ataque de Brute Force de Senhas com Medusa e Kali Linux


Medusa: para ataques de rede. suporta muitos protocolos.

-------Alcançando a Máquina Vulnerável no Metasploitable 2----------

Digite no metasploitable:

usuario: msfadmin
senha: msfadmin

$ ip a           // ter acesso ao ip (em inet).

No Kali:

$ ping -c 3 (ip do metasploitable)       // 3 pacotes.

$ nmap -sV -p 21,22, 80,445,139 (ip do metasploitable) 

$ ftp (ip do metasploitable)       // se o ftp aceita conexões.
>ftp quit


-------------Criando arquivos de usuarios e senhas comuns----

// para descobrir a senha utilizando medusa.

$ echo -e         // -e: comando de quebra de linha.
$ medusa 

--------------Ataques de Força Bruta em Formulários de Login Web-------------

DVWA:

http://192.168.56.102/dvwa/login.php

(digite qualquer usuário e senha)

Fn + F12

Aba Network e Request

------------------Criação de Wordlists----------------------------


---------Utilizando o Medusa para Simular Combinações de Acesso--------

Credenciais ao site DVWA:
admin
password

-------Ataque em Cadeia: Enumeração SMB e Password Spraying--------------

Server Mesage Block: Serviço para compartilhar arquivos e recursos  via Samba.

Spraying: ataque a senhas pra muitos usuarios diferentes.

-------Simulando um Cenário Corporativo Mal Configurado-----------------

$ enum4linux -a (ip do alvo) | tee enum4_output.txt


-a  // ativa todas as técnicas possíveis de enumeração.

// tee: grava a saída de um comando em um arquivo.

$ less enum4_output.txt
// mostra os usuarios do sistemas.

// ctrl Q

RID: identificador relativo do usuário do sistema.


------Criando uma Lista de Usuários-------------------


$ echo -e "user\nmsfadmin\nservice" > smb_users.txt  

 // -e: escape (/: quebra de linha)

$ echo -e "password\n12345\nWelcome123\nmsfsadmin"  >senhas_spray.txt

// -h : ip do alvo -U: lista de usuários. -P: lista de senhas -M smbnt: módulo 
específico para ataques via smb.
-t 2: simula 2 usuarios testando senhas. - T 50: até 50 hosts em paralelo.

------Testando o Acesso Utilizando Smbclient-----------

$  smbclient -L // (ip do alvo) -U msfadmin

// digite a senha.



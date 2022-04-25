# ssh-termux

Serviço ssh através do terminal Android(Termux)

# Termux: Um terminal linux no seu Android



*Então antes de tudo vamos atualizar os repos, para isto execute a seguinte linha de co>
>pkg update


Agora vamos instalar o neofetch usando a linha de comando:
>pkg install neofetch


# Por fim rode o neofetch, ele exibirá o logo do Android (que no caso é a nossa “distro>

Acessando remotamente o celular com ssh
Como o teclado e a tela do celular são pequenos, uma possibilidade seria usar um teclad>


Instale o openssh:
>pkg install openssh


Crie uma senha para logar com o comando:
>passwd


# Digite a senha 2 vezes (é normal não aparecer nada enquanto digita a senha).


Inicie o servidor ssh com o comando:
>sshd


Descubra o IP do android: na cortina de notificações pressione e segure o ícone do WiFi>


Agora no computador dispare o ssh no IP, porém na porta 8022 usando o comando:
>ssh @<endereco_IP> -p 8022


# Digite a senha que configurou antes, para quem está no Windows uma possibilidade é in>

Prontinho! Agora é possível acessar remotamente o termux no computador via ssh. Porém l>

Dica 1: O seu roteador WiFi provavelmente atribui os endereços dos dispositivos de form>

https://www.embarcados.com.br/wp-content/uploads/2021/09/image-31.png.webp

Dica 2: Criando um alias no ssh: toda vez que vamos acessar o android temos que digitar>

Host android
    HostName <endereco_IP>
    User user
    Compression yes
    Port 8022

# Instalando o python e jupyter notebook

Podemos instalar no nosso android um ambiente de computação científica python para faze>


>pkg install python build-essential libzmq freetype libjpeg-turbo libpng

>python3 -m venv venv

>source venv/bin/activate

>pip3 install -U pip wheel setuptools

>pip3 install jupyter


Estas linhas de comando instalam o python e algumas dependências necessárias para insta>

jupyter notebook é iniciado com:
>jupyter notebook --ip=0.0.0.0

Coloque o link no navegador e substitua pelo IP do android e pronto, tudo funcionando:

https://www.embarcados.com.br/wp-content/uploads/2021/09/image-32.png.webp

# Sucesso! O jupyter notebook já está funcionando perfeitamente. É esperado que a insta>

# Acessando os arquivos do celular

Podemos acessar as fotos e outros arquivos do celular pelo termux executando o comando:>


>cd /sdcard

>du -shxc * | sort -rh

>4.0G  total
>2.0G  DCIM
>828M  Android
>704M  Pictures
>231M  Telegram
>213M  syncthing
>103M  Download

Outra coisa legal de fazer agora que estamos acessando os arquivos do celular é deletar>
>shred -uv IMG_20210416_103105401.jpg

Outro comando, mais completo que o shred é o srm. Para instalar execute
>pkg install secure-delete

Ele permite deletar diretórios de forma recursiva e outras opções não presentes no shre>

O comando acima (du) lista o espaço utilizado por cada pasta e em seguida pegamos sua s>

# Sincronizando arquivos com o PC

O protocolo ssh além de permitir acessar remotamente o Android, permite transferir arqu>
>scp arquivo.jpg user@<endereco_IP>:/sdcard/DCIM/, com o usuário, IP e caminho de desti>

Outro comando muito usado para essa tarefa é o rsync, ele permite sincronizar pastas en>
>pkg install rsync

O rsync oferece várias opções, mas nesse caso o importante é:
>rsync -avh -P user@<endereco_IP>:/sdcard/DCIM/ fotos_celular/

Na primeira vez que for executado, esse comando vai copiar todas e fotos para o PC, e d>

Por fim vou indicar um app ótimo para sincronizar os arquivos entre o celular e pc: o s>

# Alguns apps para terminal

Para quem vive no terminal tem alguns apps que ajudam a realizar algumas tarefas e para>

Analisador de espaço: o ncdu. Da mesma forma que usamos o du para ver quais pastas estã>

https://www.embarcados.com.br/wp-content/uploads/2021/09/image-33.png.webp

Para navegar nas pastas temos o ranger: um gerenciador de arquivos como o explorer do W>

https://www.embarcados.com.br/wp-content/uploads/2021/09/image-34.png.webp

Por fim, um agregador de feeds RSS: o newsboat, o qual permite acompanhar os feeds RSS:

https://www.embarcados.com.br/wp-content/uploads/2021/09/image-35.png.webp

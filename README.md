<details open="open">
    <li><a href="#ativar-hyper-v">Ativar Hyper-v</a></li>
    <li><a href="#instalação-do-wsl2---automática">Instalação do WSL2</a></li>
    <li><a href="#instalação-do-docker-desktop">Instalação do Docker Desktop</a></li>
    <li><a href="#sobre">Sobre</a></li>
  </ol>
</details>

# Ambiente de Desenvolvimento Local com Docker
O uso da ferramenta Docker facilita a integração de um novo desenvolvedor na equipe, evitando erros de instalação de dependências do projeto, que impediam a fácil integração do novo desenvolvedor.
### Ativar Hyper-v
- Procurar no windows search pelos seguintes termos:
```
Ativar ou desativar recursos do windows
```
![](https://i.imgur.com/TUGfZ31.png)

- Procure pela opção Hyper-V.
- Ative a opção Hyper-V e selecione o botão Ok.

![](https://i.imgur.com/QjrpfC1.png)

- Aguarde a instalação, será solicitado reiniciar o computador.

## Instalação do WSL2 - Automática
### Pré-requisitos
Você deve estar executando o Windows 10 versão 2004 ou superior (Build 19041 ou superior) ou o Windows 11.

### Instalar
Agora você pode instalar tudo o que precisa para executar o WSL (Subsistema do Windows para Linux) inserindo este comando no PowerShell administrador ou no Prompt de Comando do Windows e reiniciando o computador.
- Abra o PowerShell como Administrador (menu Iniciar > PowerShell > clique com o botão direito do mouse > Executar como Administrador) e insira este comando:
~~~powershell
wsl --install
~~~
Esse comando habilitará os componentes opcionais necessários, baixará o kernel mais recente do Linux, definirá o WSL 2 como padrão e instalará uma distribuição do Linux para você(Ubuntu como padrão).
Depois de instalar o WSL, você precisará criar uma conta de usuário e uma senha para a distribuição do Linux recém-instalada.

![](https://i.imgur.com/TmnqQK3.png)
*Figura 86. Configuração do usuário e senha para distribuição Ubuntu recém-instalada.*

- É necessário reiniciar o computador para aplicar todas as atualizações.

## Instalação do Docker Desktop
- O próximo passo é instalar o Docker Desktop, acesse o link para entrar no site do Docker: [Instale o Docker Desktop no Windows](https://docs.docker.com/desktop/windows/install/).
- Ou baixe o executável diretamente por esse link:  [Docker Desktop Executável](https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe).
1. Clique duas vezes em ***Docker Desktop Installer.exe*** para executar o instalador.
2. Quando solicitado, verifique se a opção ***Use WSL 2 instead of Hyper-V*** na página Configuração está selecionada.
3. Siga as instruções no assistente de instalação para autorizar o instalador e prosseguir com a instalação.
4. Ao fim da instalação, clique em Fechar e reiniciar para concluir o processo de instalação.
5. Após o sistema reiniciar, o Docker Desktop iniciará junto com Windows, aceite os termos para o serviço do docker ser executado.<br>

![](https://i.imgur.com/WmfUvrB.png)
Ao fim da instalação, o docker desktop deve estar como mostra a imagem acima.

### Ativar WSL2 engine no Docker Desktop
O próximo passo é verificar se o WSL2 engine está ativado, para isso siga os seguintes passos:
1. Selecione o botão de engrenagem para entrar nas configurações

![](https://i.imgur.com/RvlHuiC.png)

2. Ative opção WSL2 engine na aba ***General***.

![](https://i.imgur.com/LOdxwMM.png)

3. Reinicie o computador.

### Testar instalação do Docker

1. Abra o Windows Terminal.
2. Execute os comandos:
~~~powershell
wsl
cd ~
docker version
~~~
![](https://i.imgur.com/qDhVBqb.png)
Devemos receber informações sobre a versão do Docker instalada no WSL2.

### Instalar extensões do wsl no Visual Studio Code (VS Code)
Devemos instalar algumas extensões no VS Code para prosseguir com a instalação do ambiente. As extensões são as seguintes:
1. Remote - Containers

![](https://i.imgur.com/jo4KDJU.png)

2. Remote - WSL

![](https://i.imgur.com/NZTzZiI.png)

3. Docker

![](https://i.imgur.com/m4DqAfv.png)

4. Remote SSH

![](https://i.imgur.com/rV5MIl8.png)

### Clonar repositório
O primeiro passo é realizar o git-clone do projeto.
1. Abra o Windows Terminal.
2. Execute o comando:
~~~powershell
wsl
cd ~
~~~
3. Vamos clonar o projeto
~~~powershell
git clone https://github.com/demiguic/HOTEL-MPS.git
~~~
Pode acontecer erro de autenticação por senha no clone do back-end, acesse o seguinte link para resolver este impedimento: [Token authentication requirements for Git operations](https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/).
![](https://i.imgur.com/8strcH5.png)
<br><br>
:bulb: **Info:** É importante que você tenha acesso ao repositório para concluir este passo e prosseguir para os próximos.<br><br>
4.Execute o comando *code .*
~~~powershell
code .
~~~

6. Alterar pra branch docker
<br>
    - Selecione o botão de branch no canto inferior esquerdo da interface do VS Code
    - Na aba que se abre, selecione *origin/docker*
    <br>

![](https://i.imgur.com/D3oUiIx.png)

6. Agora vamos executar o docker compose.
~~~powershell
cd HOTEL-MPS
docker-compose up -d --build
~~~

7. Abra o navegador e acesse *localhost*
![](https://i.imgur.com/CNIBxcN.png)

Após isso, a aplicação deve estar disponível em ambiente local com docker
:)

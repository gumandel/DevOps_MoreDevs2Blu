### Execucao dos playbooks ###

- A execucao dos comandos abaixo faz a instalacao ou remocao dos pacotes apache, mysql, git e php na maquina de destino, realizado por meio de roles contendo tasks separadas para cada processo. A ferramenta de automacao responsavel por esse gerenciamento e configuracao e o Ansible.

Obs: a instalacao e remocao dos pacotes foi realizada em uma maquina Ubuntu 22.04. Dependendo da distribuicao escolhida, os nomes dos pacotes podem ser diferentes.

## Pre-requisitos ##

- Instalar o Ansible na sua maquina principal;

- Instalar SSH e Python em suas maquinas alvos;

- No arquivo inventory.yml, localizado na pasta ansible-install-uninstall, e necessario alterar o endereco de IP para a maquina de destino, onde os arquivos .yaml de instalacao e desinstalacao serao executados;

- E possivel replicar esse processo para mais maquinas, basta copiar o bloco compreendido entre o endereco de IP e "docker_host" e colar logo abaixo dele, alterando para o IP para o alvo desejado.

## Criacao e destruicao do ambiente  ##

# Para instalar o ambiente, navegue ate a pasta "ansible-install-uninstall" e execute o seguinte comando:

sudo ansible-playbook -i inventory.yml site.yml -K --tags install

- Ao passar o parametro -K, sera solicitada a senha do usuario atual, que devera ter permissoes de usuarios sudo (arquivo sudoers);

# Para remover o ambiente, utilize o comando anterior com 'uninstall' no lugar de 'install':

sudo ansible-playbook -i inventory.yml site.yml -K --tags uninstall

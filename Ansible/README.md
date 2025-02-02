# Execução dos playbooks #

- A execução dos comandos abaixo faz a instalação ou remoção dos pacotes Apache, MySQL, Git e PHP na máquina de destino, realizada por meio de roles contendo tasks separadas para cada processo. A ferramenta de automação responsável por esse gerenciamento e configuração é o Ansible.

Obs: a instalação e remoção dos pacotes foi realizada em uma máquina Ubuntu **22.04**. Dependendo da distribuição escolhida, os nomes dos pacotes podem ser diferentes.

## Pré-requisitos ##

- Instalar o **Ansible** na sua máquina principal;

- Instalar **SSH** e **Python** em suas máquinas-alvo;

- No arquivo **inventory.yml**, localizado na pasta **ansible-install-uninstall**, é necessario alterar o endereco de IP para a máquina de destino, onde os arquivos **.yaml** de instalacão e desinstalacão serão executados;

- É possível replicar esse processo para mais máquinas, basta copiar o bloco compreendido entre o endereco de IP e "docker_host" e colar logo abaixo dele, alterando para o IP do alvo desejado.

## Criação e destruição do ambiente  ##

### Para instalar o ambiente, navegue até a pasta "ansible-install-uninstall" e execute o seguinte comando:

sudo ansible-playbook -i inventory.yml site.yml -K --tags install

- Ao passar o parâmetro -K, seraá solicitada a senha do usuário atual, que deverá ter permissões de sudo (arquivo sudoers);

### Para remover o ambiente, utilize o comando anterior com 'uninstall' no lugar de 'install':

sudo ansible-playbook -i inventory.yml site.yml -K --tags uninstall

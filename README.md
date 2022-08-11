# DevSecOps com OpenSource - Análises Automatizadas

Repositório para armazenar o Laboratório da live de DevSecOps da [4Linux][1]

## whoami

### 🇧🇷 **Samuel Gonçalves Pereira**

* Consultor de Tecnologia nas áreas **Segurança Ofensiva** e **DevSecOps**
* Mais de 10 anos de experiência
* *"3k++"* alunos ensinados no 🌎
* Músico, Contista, YouTuber e Podcaster

> Contato: [https://beacons.ai/sgoncalves](https://beacons.ai/sgoncalves)

## Objetivos da Live

1. Compreender os princípios do DevSecOps
2. Implementar uma pipeline funcional com SAST e DAST usando:
   1. Jenkins
   2. Horusec
   3. Golismero
   4. Git
3. Listar ferramentas OpenSource para Segurança Ágil
4. Solucionar dúvidas relacionadas a Segurança no processo de desenvolvimento

## Laboratório

### Dependências

Para a criação do laboratório é necessário ter pré instalado os seguintes softwares:

* [Git][2]
* [VirtualBox][3]
* [Vagrant][5]

> Para o máquinas com Windows aconselhamos o uso do proprio Powershell e que as instalações dos softwares são feitas da maneira tradicional

> Para as máquinas com MAC OS aconselhamos, se possível, que as instalações sejam feitas pelo gerenciador de pacotes **brew**.

### Descrição do Ambiente

O Laboratório será criado utilizando o [Vagrant][7]. Ferramenta para criar e gerenciar ambientes virtualizados (baseado em Inúmeros providers) com foco em automação.

Nesse laboratórios, que está centralizado no arquivo [Vagrantfile][8], serão criadas 2 maquinas com as seguintes características:

Nome       | vCPUs | Memoria RAM | IP            | S.O.           | Script de Provisionamento
---------- |:-----:|:-----------:|:-------------:|:---------------:| -----------------------------
testing    | 1     | 2048MB      | 192.168.56.50 | almalinux/8     | [provisionamento/testing.yaml](provisionamento/testing.yaml)
automation | 1     | 2048MB      | 192.168.56.60 | almalinux/8     | [provisionamento/automation.yaml](provisionamento/automation.yaml)

### Criação do Laboratório

Para criar o laboratório é necessário fazer o `git clone` desse repositório e, dentro da pasta baixada realizar a execução do `vagrant up`, conforme abaixo:

```bash
git clone https://github.com/4linux/live-devsecops
cd live-devsecops/
vagrant up
```

_O Laboratório **pode demorar**, dependendo da conexão de internet e poder computacional, para ficar totalmente preparado._

### Dicas de utilização

Por fim, para melhor utilização, abaixo há alguns comandos básicos do vagrant para gerencia das máquinas virtuais.

Comandos                | Descrição
:----------------------:| ---------------------------------------
`vagrant init`          | Gera o VagrantFile
`vagrant box add <box>` | Baixar imagem do sistema
`vagrant box status`    | Verificar o status dos boxes criados
`vagrant up`            | Cria/Liga as VMs baseado no VagrantFile
`vagrant provision`     | Provisiona mudanças logicas nas VMs
`vagrant status`        | Verifica se VM estão ativas ou não.
`vagrant ssh <vm>`      | Acessa a VM
`vagrant ssh <vm> -c <comando>` | Executa comando via ssh
`vagrant reload <vm>`   | Reinicia a VM
`vagrant halt`          | Desliga as VMs

> Para maiores informações acesse a [Documentação do Vagrant][13]

[1]: https://4linux.com.br
[2]: https://git-scm.com/downloads
[3]: https://www.virtualbox.org/wiki/Downloads
[5]: https://www.vagrantup.com/downloads
[6]: https://cygwin.com/install.html
[7]: https://www.vagrantup.com/
[8]: ./Vagrantfile
[9]: ./provisionamento/testing.sh
[10]: ./provisionamento/automation.sh
[11]: ./provisionamento/logging.sh
[12]: ./provisionamento/validation.sh
[13]: https://www.vagrantup.com/docs
[14]: https://app.vagrantup.com/4linux
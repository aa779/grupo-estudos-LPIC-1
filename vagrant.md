# grupo-estudos-LPIC-1

## Linux Vagrant Box centos/7 and debian/jessie64

### Instalar última versão do VirtualBox

* Editar: /etc/apt/sources.list

```bash
# VirtualBox
deb http://download.virtualbox.org/virtualbox/debian xenial contrib
```

#### Fazer download da chave:

```bash
$ wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
```

#### Instalar:

```bash
$ sudo apt-get update
$ sudo apt-get install virtualbox-5.1
```

### Instalar última versão do Vagrant

* Verificar número de versão antes de executar os comandos:

```bash
$ cd Downloads
$ wget https://releases.hashicorp.com/vagrant/1.9.2/vagrant_1.9.2_x86_64.deb
$ sudo dpkg -i vagrant_1.9.2_x86_64.deb
```

* verificar instalação:

```bash
$ vagrant -v
```

#### Preparar as pastas

```bash
$ mkdir -p ~/lpic-1/centos/7
$ mkdir -p ~/lpic-1/debian/jessie64
```

#### Vagrantfile

* Editar: Vagrantfile

1. arquivo Vagrantfile da box centos/7:

```bash
$ wget https://raw.githubusercontent.com/aledruetta/grupo-estudos-LPIC-1/blob/master/centos/Vagrantfile -O ~/lpic-1/centos/7/Vagrantfile
```

2. arquivo Vagrantfile da box debian/jessie64:

```bash
$ wget https://raw.githubusercontent.com/aledruetta/grupo-estudos-LPIC-1/blob/master/debian/Vagrantfile -O ~/lpic-1/debian/jessie64/Vagrantfile
```

### Inicializar as máquinas virtuais

```bash
$ cd ~/lpic-1/centos/7
$ vagrant init centos/7

$ cd ~/lpic-1/debian/jessie64
$ vagrant init debian/jessie64
```

### Plugin VirtualBox Guest Additions

* Em cada uma das pastas onde está o arquivo Vagrantfile:

```bash
$ vagrant plugin install vagrant-vbguest
```

### Onde ficam as imagens

```bash
$ ls ~/.vagrant.d/boxes/centos-VAGRANTSLASH-7/1611.01/virtualbox

centos-VAGRANTSLASH-7/
├── 1611.01
│   └── virtualbox
│       ├── box.ovf
│       ├── centos-7-1-1.x86_64.vmdk        // imagem
│       ├── metadata.json
│       └── Vagrantfile
└── metadata_url
```

### Comandos

```bash
$ cd ~/lpic-1/debian/jessie64
```

Ou

```bash
$ cd ~/lpic-1/centos/7
```

```bash
$ vagrant status              // estado
$ vagrant up                  // activar
$ vagrant ssh                 // acessar o prompt
$ vagrant halt                // parar
$ vagrant destroy             // destruir
$ vagrant reload --provision  // recarregar após mudanças na configuração
```

### Usuários

```bash
$ whoami
vagrant                   // passwd: vagrant

$ sudo -i                 // acesso root
```

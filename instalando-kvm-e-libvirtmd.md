Instalando KVM e Libvirt
========

A primeira coisa a se fazer é instalar o KVM, Libvirt e todas as suas dependências.
Para isso, deve-se executar o seguinte comando:

    sudo apt-get install qemu-kvm virt-manager ethtool libvirt-bin python-spice-client-gtk
    
    
Após instalar as dependências, teremos que adicionar o usuário local ao grupo **libvirtd** para que ele possa gerenciar o libvirt. Para isso, deve-se executar o seguinte comando:

    sudo gpasswd -a lucas libvirtd

Efetue o logout logue denovo na interface gráfica.

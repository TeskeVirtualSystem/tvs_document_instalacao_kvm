Criando Pasta Alternativa de Imagens de Disco
=========

Para criar uma pasta alternativa para o KVM armazenar as imagens de disco
vá para tela principal do `Gerenciador de Máquinas Virtuais`

![Virt Manager](images/virt-manager0.png)

e clique duas vezes na opção `localhost (QEMU)` e vá para a opção 
`Armazenamento`.


![Virt Manager - Armazenamento](images/virt-manager16.png)

Nesta tela clique no botão **+** no canto esquerdo inferior para 
inserir um novo **Storage Pool**.


![Virt Manager - New Storage Pool](images/virt-manager17.png)

Selecione um nome para o seu novo **Storage Pool** e deixe a opção
`dir: Diretório do Sistema de Arquivo` selecionado. Clique em `Avançar`.


![Virt Manager - Diretório](images/virt-manager18.png)

Selecione o caminho para onde você quer que as imagens sejam armazenadas,
e clique em `Concluir`.


![Virt Manager - Pool Criado](images/virt-manager19.png)

Com o novo **Storage Pool** criado, você poderá criar imagens de disco
dentro dele  clicando no botão `New Volume` e criando o seu disco 
normalmente. Após isso ele deve aparecer no seu novo **Storage Pool**


![Virt Manager - Imagem Criada](images/virt-manager20.png)
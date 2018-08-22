
Dicas Sage
=

*"Como instalar o driver proprietário de uma placa de vídeo NVIDIA, em um servidor SAGE rodando o CentOs 6.x, quando o módulo nouveau está instalado?"*
-

### **Proposição:**

Durante o processo de instalação do driver proprietário NVIDIA em uma workstation SAGE na versão CentOS 6.x, surge a mensagem que "Não é possível instalar o driver proprietário.  Remova primeiramente o módulo nouveau".

### **Descrição:**

> **ATENÇÃO**: Este procedimento deve ser executado com bastante cuidado uma vez que interfere com os processos de boot da workstation. É desejável possuir um pendrive bootável ou um LiveCD com uma distribuição Linux qualquer para poder reverter as modificações realizadas, caso algo não ocorra como o esperado.

O módulo nouveau provê os drivers para o correto funcionamento das placas de vídeo NVIDIA, porém não permite a utilização das soluções desenvolvidas pela fabricante das placas. Os drivers proprietários fornecem a aplicação ***nvidia-settings*** que facilita tremendamente o processo de configuração de múltiplas telas e ajustes mais complexos como resolução da imagem, frequência de varredura, ajustes de cores etc.
Durante o processo de instalação do driver proprietário é executada uma rotina de verificação que busca pela existência do módulo  e impede a continuidade da instalação,  daí a necessidade de inibir o carregamento do módulo nouveau.
Será necessário também atualizar o "sistema de arquivos inicial em memória RAM" - o initramfs, uma vez que o mesmo possui referência de todos os módulos que serão utilizados pelo S.O.


### **Passos:**

1 - Abra um terminal como root e chame o editor de texto de sua preferência para adicionar a linha  '**blacklist nouveau**' em **/etc/modprobe.d/blacklist.conf**, caso ela ainda não exista neste arquivo;

2 - Ainda no terminal, vá até /boot e faça uma cópia backup de initramfs, digitando:

    mv /boot/initramfs-\$(uname -r).img /boot/initramfs-$(uname -r).img.bak

3 - Gere um novo initramfs com:

    dracut -v /boot/initramfs-\$(uname -r).img $(uname -r)

4 - Certifique-se de que os passos anteriores foram executados como descrito acima e se tudo estiver correto, reinicie o equipamento;

5 - Após o reinício do sistema operacional, abra um terminal virtual (com ctrl+f3, por exemplo) e logue-se como 'root' e digite:

    init 1

6 - Proceda a instalação do driver proprietário NVIDIA com:

    sh NVIDIA-Linux-x86_64-XXX.XX.run

7 - Se o processo de instalação do driver concluir corretamente, digite:

    init 5

Nesse momento deve ser possível logar no sistema operacional através da interface gráfica.

> Dica repassada por Angelo Sampaio
> ND#201805301100
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4NDc3NjkyOTksMTY1NzIwODQ2NV19
-->
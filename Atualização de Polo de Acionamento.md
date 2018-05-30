Dicas SAGE
=

"Como atualizar em um Polo de Acionamento os pontos da base de dados de uma Estação Controlada?"
-

### Proposição:
Considerando que ocorreram modificações na base de dados na Estação Controlada ***STCT***,  há a necessidade de atualizar os pontos do include da base de dados da Estação Polo de Acionamento ***STPA***.

### Descrição:
 O processo para realizar a **Atualização do Polo de Acionamento** consiste basicamente na extração dos pontos da base de dados da Estação Controlada e na realização de ajustes para formar o include para a base de dados da Estação Polo de Acionamento. Diferentemente da **Geração de Polo de Acionamento**, onde além da extração de pontos há ainda a necessidade da realização de configurações do subsistema de comunicação, protocolos, transportadores etc no servidor SAGE do polo, a atualização é mais simples e facilita o processo de incorporação das modificações que ocorreram na base de dados da estação controlada na base de dados da estação polo.
Para a realização da atualização da base de dados do servidor SAGE do Polo de Acionamento serão empregados scripts para a preparação dos pontos para o Nível Hierárquico Superior (NHS) e a planilha de template de pontos, ambos desenvolvidos pelo Cepel.

### Passos:
1 - No servidor SAGE de STCT, caso ainda não exista, criar a pasta para receber os arquivos .dat com os pontos no Nível Hierárquico Inferior (NHIs). Em um terminal, logado como o usuário ***sage***, digite o comando abaixo:

    mkdir $SAGE/config/demo_ems/bd/dados/NHIs

2 - Ainda no terminal do servidor SAGE de STCT, carregar a base de dados no Postgres digitando o comando:

    STI_cargbf C

3 - Neste mesmo terminal, executar o script gerador dos arquivos .dat com os pontos que serão utilizados no Nível Hierárquico Superior informando:

 - Onde a pasta NHIs está localizada: **demo_ems**;
 - Que não será necessário processar cálculo: **-n**;
 - Nome da base da estação controlada: **stct**
 >
    GeraDatsNHS demo_ems -n stct

### *Observações*: 
Os arquivos .dat gerados possuem campos em branco dentro dos registros de cada tabela, o que pode causar problemas de importação pela planilha do template de pontos do Cepel. Outro aspecto que pode causar problemas durante a utilização da planilha em ambientes Windows 7 em diante, está no caractere que finaliza cada linha do arquivo .dat, que no Linux é "\n" e no Windows é "\r\n".

Para remover campos sem conteúdo, vá até a pasta NHIs e digite:
>
    sed -r '/=([[:blank:]]?|[[:blank:]]+)$/d' *

Para converter um arquivo de Unix para Dos vá até a pasta NHIs e digite:

    unix2dos *

4 - Transporte de forma segura a pasta NHIs para um computador com o SO Windows e utilizando a planilha de template de pontos do Cepel, importe **TODOS** os arquivos .dat.

5 - Transporte de forma segura os arquivos da base de dados do servidor SAGE de STPA para um computador com o SO Windows e utilizando a planilha de template de pontos do Cepel, importe **TODOS** os arquivos .dat.

6 -Na tabela **MUL** do servidor SAGE de STPA, verifique qual o valor dos campos GSD - este deverá ser utilizado no mesmo campo nas tabelas **MUL** e **LSC** do servidor SAGE de STCT.

7 - Ainda  na tabela **MUL**  do servidor SAGE de STAP, verifique o maior valor do campo ORDEM - o **VALOR IMEDIATAMENTE APÓS A ESTE**  deverá ser utilizado no mesmo campo da tabela MUL do servidor SAGE de STCT.

8 - Agora na tabela **TAC** de STCT, retirar os registros **CALCDIN** e **DUMMY**;

9 - Na tabela **PDS** de STCT, retirar os registros **COM_SAGE** e garantir que todos os campos **INVRT** estejam com o valor **NÃO**;

10 - Na tabela **CGS**  de STCT, retirar os registros **COM_SAGE**.

11 - Transporte de forma segura o conteúdo da pasta NHIs para o servidor SAGE de STPA no diretório $BD/dados/nome_da_base_da_estaçao_controlada, sobreescrevendo o seu conteúdo.

12 - Atualizar a base de dados do servidor SAGE de STPA com o comando

    AtualizaBD fria fonte
    
> Dica repassada por Wagner Queiroga
> DN#201805301015
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5MjcwOTAxMV19
-->
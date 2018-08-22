# Unificação de Regras de Formação para componentes das Bases de Dados dos Sistemas de Supervisão e Controle

 ## Objetivos
 

## 2. Conceituações



**2.1 Sistema de Supervisão e Controle (SSC):** 

**2.2 Formação da identificação dos pontos:**

    Nome da Estação + Nome do Equipamento + Parte do equipamento

**Nome da  da instalação:** Abreviatura da instalação como definida no anexo da NOE-01

**Nome do Equipamento**: Sigla identificadora do equipamento definida na NOE-01
Parte de Equipamento: Sigla identificadora conforme a norma ANSI ou abreviatura arbitrária (ainda nãoestá normatizado).
Identificadores Convergentes: São os identificadores dos pontos da base de dados que apresentam variações somente na parte do equipamento para um mesmo evento do SSC.
Exemplos:
STXX_SC6121_43LR
STXX_SC6123_LR43
STXX_SC6221_LOC/REM
Identificador Divergente: São os identificadores dos pontos da base de dados que apresentam variações nas demais partes do identificador para um mesmo evento do SSC
AB_SC345671_43LR
STYY_MCX0103_LOC
MC_SC01A21
Identificador não classificável:  São os identificadores que não puderam ser classificados forma automática por apresentarem variações em todas as partes da identificação impossibilitando a determinação da natureza do ponto.
Contexto de eventos: É um grupo de eventos que caracteriza o funcionamento de um determinado equipamento em uma posição dentro do vão de uma instalação.










Etapa de Diagnóstico:
É a etapa que tem a finalidade de proporcionar a compreensão do estado de convergência/divergência dos registros das bases de dados do SSC. Basicamente os pontos de supervisão e controle serão visualizados e agrupados de acordo com as funcionalidades que representam. Ainda nesta etapa serão documentados e classificados os eventos do Sistema de Supervisão e Controle.
1.	Identificar e classificar os pontos existentes na base de dados;
a.	Determinar o conjunto de pontos convergentes, divergentes e não classificáveis através da aplicação de filtros computacionais; GSC

b.	Nesta etapa da análise serão desconsiderados os seguintes pontos, com geração de relatórios: GSC

i.	Pontos de cálculos dinâmicos;
ii.	Pontos Reserva;
iii.	Pontos Futuros;
iv.	Pontos de equipamentos inativos/legados;
v.	Pontos de estações telecontroladas;
vi.	Pontos gerados pela planilha xml61850;

c.	Separar os pontos utilizados por vão e tipo de equipamento para a compreensão das características da supervisão e controle dos ativos, tais como: GSC/AREA
i.	Formação de ID, Nome, Terminal de Aquisição e Controle (TAC);
ii.	Persistência de alarmes;
iii.	Modalidades de intertravamento (permissivo ou intertravado);
iv.	Modalidades de controle (pontos simples ou duplos);
v.	Descrição de ocorrências (OCR);
vi.	Etc;

d.	Identificar as características similares dos eventos digitais, analógicos e de controle do SSC relacionados com cada tipo de equipamento; GSC/AREA

e.	Documentar os eventos do SSC de forma a caracterizá-los como se segue: GSC/AREA
i.	Eventos Digitais;
1.	ID: Identificador do Evento;
2.	Nome: Descrição breve do evento do supervisionado;
3.	Descritivo: Descrição detalhada do evento supervisionado;
4.	OCR: Termos empregados para descrever os tipos de ocorrências para um determinado evento;
5.	ALRIN: 
6.	 STINI:
7.	STNOR:
8.	STINV:
9.	CMT:
10.	
ii.	Eventos Analógicos:
1.	ID:
2.	
3.	Nome:
4.	Descritivo:
5.	OCR:
iii.	Eventos de Controle:
1.	ID:
2.	Nome:
3.	Descritivo:
4.	OCR:

2.	 Aplicação de regras de formação para o legado
a.	Identificar os grupos de eventos existentes em cada equipamento, considerando a sua função;
b.	Formar os templates de eventos, aplicando os paradigmas de unificação de regras de formação, para cada equipamento.
c.	 Formar o Projeto da Estação empregando os templates de eventos para cada equipamento que compõe os vãos
d.	Gerar as tabelas PAS, PAF, PDS, PDF, CGS, CGF para o SAGE, Planilha de Dados para SOL e Planilha de Referência;
e.	Formar tabela “de/para” (ID antigo, Nome antigo: ID novo, Nome Novo)


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI1Njg5MDIwMywxNjg3NDk3NTY0XX0=
-->
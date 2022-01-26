# Vaga-analista-de-desenvolvimento-implantacao-PLD-2022

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------


A -  É uma forma de transformar dinheiro sujo (ílicito como roubo, corrupção, tráfico de drogas) em limpo (lícito) para transações seguras para que a Receita Federal não consiga rastrear a origem, na forma de transferências bancárias em nome de laranjas, envio para outros países, compra de bens.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
B - CPGF é um meio de pagamento semelhante ao cartão de crédito que usamos no dia a dia, onde o governo utiliza para pagar as próprias despesas que são enquadradas como suprimentos de fundos com prazo para a utilização para trazer mais agilidade, controle e modernidade.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
C - Só pode usar o CPGF pode ser concedido a servidor público ou ocupante de cargo em comissão em efetivo exercício no órgão, e que preencha as seguintes condições:

a) não ser responsável por dois suprimentos de fundos em fase de
aplicação e/ou de prestação de contas;

b) não tenha a seu cargo a guarda do material a adquirir, salvo quando
não houver na repartição outro servidor que reúna condições de
receber o Suprimento de Fundos;

c) não ser responsável por Suprimento de Fundos que, esgotado o
prazo, esteja pendente de prestação de contas;

d) não ter sido declarado em alcance, assim entendido aquele que
tenha cometido apropriação indevida, extravio, desvio ou falta
verificada na prestação de contas, de dinheiro ou valores confiados à
sua guarda;

e) não tenha tido prestação de contas da aplicação de suprimento
fundos com despesas impugnadas pelo Ordenador de Despesas ou que
esteja em processo de Tomada de Contas Especial;

f) não se confunda com a pessoa do Ordenador de Despesas;

g) não seja o próprio demandante da aquisição/contratação de serviço,
exceto em viagem a serviço.

Além dessas condições, não é recomendável a concessão de
Suprimento de Fundos a autoridade, Ministro de Estado ou ocupante
de cargo de Natureza Especial ou de cargo do Grupo Direção e
Assessoramento Superiores - DAS 6.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
D - https://www.portaltransparencia.gov.br/download-de-dados

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
E - https://www.portaldatransparencia.gov.br/pagina-interna/603393-dicionario-de-dados-cpgf+

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
F - No exemplo solicitado no mês de Outubro de 2021, há transacões onde o nome e CPF do solicitando não aparecem.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
G - Sim, é possível ver o orgão do portador GPGF.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
H - O orgão onde o código é 20402 é Ministério da Ciência, Tecnologia, Inovações, Agência Espacial Brasileira.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
I - No exemplo solicitado no mês de Outubro de 2021, não é possível ver o nome e CNPJ do favorecido.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
J - No exemplo solicitado no mês de Outubro de 2021, todos os valores saõ visivéis, já a data a transações que não possuem esta identificação.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
K - 

    SELECT 
    SUM([VALOR TRANSAÇÃO]) FROM "'NOME DA TABELA'"
 

   <p align="center">
  <img src="https://user-images.githubusercontent.com/81439181/151182495-7c31eefe-f4a8-4422-8a8a-56896dc662e9.png" width="450" title="hover text">  
</p>

Resposta: A soma das movimentações do CPGF foi de R$ 561900795.000001.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
L - 

    SELECT 
    SUM([VALOR TRANSAÇÃO]) AS SOMA FROM "EXEMPLO" WHERE [TRANSAÇÃO] = 'Informações protegidas por sigilo'


   <p align="center">
  <img src="https://user-images.githubusercontent.com/81439181/151182128-8db7253e-d277-4fbd-9b9b-e07b1ce69850.png" width="650" title="hover text">  
</p>


Resposta: A soma das movimentações sigilosas foram de R$ 3.108.731,15.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
M - 

     SELECT
         [CÓDIGO ÓRGÃO]
        ,[NOME ÓRGÃO]
        , SUM([VALOR TRANSAÇÃO]) AS [TOTAL]
    FROM [CPGF2].[dbo].[EXEMPLO]

    WHERE [TRANSAÇÃO] = 'Informações protegidas por sigilo'

    GROUP BY [CÓDIGO ÓRGÃO], [NOME ÓRGÃO]
    ORDER BY [TOTAL] DESC


  <p align="center">
  <img src="https://user-images.githubusercontent.com/81439181/151179769-ed751a83-68f7-4486-98a9-839e0f78acd5.png" width="500" title="hover text">  
</p>
  
  
  Resposta: O órgão que mais realizou movimentações sigilosas no período foi Presidência da República com R$ 169.751,04
 ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 
 N - 
 
    SELECT 
      [NOME ÓRGÃO]
      ,[NOME PORTADOR]
      ,COUNT([TRANSAÇÃO]) AS [QTO SAQUES]
      ,SUM([VALOR TRANSAÇÃO]) AS [TOTAL SAQUES]
      INTO #TEMP 
      FROM [CPGF2].[dbo].[EXEMPLO]
      WHERE TRANSAÇÃO = 'SAQUE CASH/ATM BB' 

      GROUP BY [NOME ÓRGÃO], [NOME PORTADOR]

      SELECT [NOME ÓRGÃO], [NOME PORTADOR],[QTO SAQUES], [TOTAL SAQUES] FROM #TEMP
      WHERE [QTO SAQUES] = (SELECT MAX([QTO SAQUES]) FROM #TEMP)
      GROUP BY [NOME ÓRGÃO], [NOME PORTADOR], [QTO SAQUES], [TOTAL SAQUES]


  <p align="center">
  <img src="https://user-images.githubusercontent.com/81439181/151180513-97d20abe-dfe9-4bff-a1b5-3b0a5c2440b9.png" width="550" title="hover text">  
</p>

      
 Resposta: O nome do portador que mais realizou saques foi Rafael Ferreira Costa.
 A soma dos valores do saque foi de R$ 24520.
 O nome do órgão do portador é Instituto Chico Mendes de Conservação da Biodiversidade.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------  
  O - 
  
    SELECT 
      NOME FAVORECIDO
      ,COUNT([NOME FAVORECIDO]) AS [QTO TRANSACOES]
      ,SUM([VALOR TRANSAÇÃO]) AS [VALOR TOTAL]

      INTO #TEMP
      FROM [NOME DO BANCO DE DADOS].[dbo].['NOME DA TABELA']
      WHERE [TRANSAÇÃO] LIKE 'COMP%'

      GROUP BY NOME FAVORECIDO 

      SELECT * FROM #TEMP 
      WHERE [QTO TRANSACOES] = (SELECT MAX([QTO TRANSACOES]) FROM #TEMP)
      
      
  <p align="center">
  <img src="https://user-images.githubusercontent.com/81439181/151177981-975f5edb-d7a4-4405-8812-8915b3aa9f78.png" width="500" title="hover text">  
</p>         
 
Resposta: O nome do favorecido que mais recebeu compras utilizando o CPGF foi: SEM INFORMAÇÃO, com 126 transações e no valor de R$ 67421,29.
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 

  P - A abordagem para tratamento dos dados e resolução foi através do SQL utilizando a ferramenta SQL Server Management Studio, pois para manipulação de dados retirados de planilhas é mais fácil sua integração e interatividade com eles. 
  OBS: Não alterei os nomes do cabeçalho para manter o padrão da tabela, pois é mais usual utilizar VALOR_TRANSACAO do que VALOR TRANSAÇÃO por exemplo.

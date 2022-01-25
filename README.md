# Vaga-analista-de-desenvolvimento-implanta-o-PLD-2022

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
    
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
L - 

    SELECT 
    SUM([VALOR TRANSAÇÃO]) AS SOMA FROM "'NOME DA TABELA'" WHERE TRANSAÇÃO = 'Informações protegidas por sigilo'
    
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
M - 

    SELECT
         [CODIGO ÓRGÃO]
        ,[NOME ÓRGÃO]
        , SUM([VALOR TRANSAÇÃO]) AS [TOTAL]
    FROM [NOME DO BANCO DE DADOS].[dbo].['NOME DA TABELA']

    WHERE [TRANSAÇÃO] = 'Informações protegidas por sigilo'

    GROUP BY [CODIGO ÓRGÃO], [NOME ÓRGÃO]
    ORDER BY [TOTAL] DESC
  
 ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 
 N - 
 
    SELECT 
      [NOME ÓRGÃO]
      ,[NOME PORTADOR]
      ,COUNT(TRANSAÇÃO) AS [QTO SAQUES]
      ,SUM([VALOR TRANSAÇÃO]) AS [TOTAL SAQUES]
      INTO #TEMP 
      FROM [NOME DO BANCO DE DADOS].[dbo].['NOME DA TABELA']
      WHERE TRANSAÇÃO = 'SAQUE CASH/ATM BB' 

      GROUP BY [NOME ÓRGÃO], NOME PORTADOR

      SELECT [NOME ÓRGÃO], NOME PORTADOR,[QTO SAQUES], [TOTAL SAQUES] FROM #TEMP
      WHERE [QTO SAQUES] = (SELECT MAX([QTO SAQUES]) FROM #TEMP)
      GROUP BY [NOME ÓRGÃO], NOME PORTADOR, [QTO SAQUES], [TOTAL SAQUES]
      
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
      
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 

  P - A abordagem para tratamento dos dados e resolução foi através do SQL utilizando a ferramenta SQL Server Management Studio, pois para manipulação de dados retirados de planilhas é mais fácil sua integração e interatividade com eles. 
  OBS: Não alterei os nomes do cabeçalho para manter o padrão da tabela, pois é mais usual utilizar VALOR_TRANSACAO do que VALOR TRANSAÇÃO por exemplo.

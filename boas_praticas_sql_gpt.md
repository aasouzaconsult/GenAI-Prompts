## Objetivo
O objeto foi dar uma estudada em como GEN-AI, pode auxiliar no dia a dia do analista de dados. Agora, com Boas práticas SQL.
Segue uma breve descrição...

## Serão informado querys não formatadas e escritas de forma não correta


## EU 🤓
```sql
--------------------------------------------------------------
---------------- cADASTRO dE cLIENTES ---------------------------------------------------------------------------
--------------------------------------------------------------

	select geral.* from (
select * from openquery(LS_ALEX,'
	select
	rtrim(SA1.A1_CGC) as documento,
	case when len(SA1.A1_CGC) = 11 then ''F'' else ''J'' end as tipo,
	''EXEMPLO'' as nomeorigem,
	LTRIM(SA1.A1_NREDUZ) as nome,
	case when len(SA1.A1_CGC) = 14 then LTRIM(SA1.A1_NOME) else '''' end as razaosocial,
	SA1.A1_COD as codigosistemagestao,
	case when len(SA1.A1_CGC) = 14 then REPLACE(REPLACE(REPLACE(REPLACE(SA1.A1_INSCR,'' '',''''),''-'',''''),''.'',''''),''/'','''') else '''' end as InscricaoEstadual,
	case when SA1.A1_DTCAD = '''' then    convert(varchar,cast(SA1.A1_XDTLNT as date),103)  else convert(varchar,cast(SA1.A1_DTCAD as date),103) end as dataclientedesde
	from SA1010 SA1 WITH(NOLOCK) 
	where SA1.D_E_L_E_T_ = '' '' --and SA1.A1_PESSOA = ''J''   
 and substring(SA1.A1_CGC,1,11) not in ( ''00000000000'', ''11111111111'', ''22222222222'',
       ''33333333333'', ''44444444444'', ''55555555555'', ''66666666666'', ''77777777777'', 
       ''99999999999'', ''88888888888'', '' '')
 AND A1_XDTLNT > (REPLACE(CAST(DATEADD(DAY,-90,CAST(GETDATE() AS DATE)) AS VARCHAR(10)),''-'','''')) 
order by SA1.A1_CGC , SA1.A1_LOJA  ;
')
) geral
left join (

select isnull(pj.cnpj,pf.cpf) as cnpj,
p.nome,
p.codigoSistemaGestao,
p.dataclientedesde,
j.inscricaoEstadual,
j.razaosocial
 from test.dbo.pessoa p with (nolock)
left join test.dbo.pessoajuridica pj with (nolock) on pj.codigopessoa = p.codigo
left join test.dbo.juridica j with (nolock) on j.cnpj = pj.cnpj
left join test.dbo.pessoafisica pf with (nolock) on pf.codigopessoa = p.codigo
where p.codigoOrigem = 4  and p.codigoTipoRelacionamento = 'C'

) PES on PES.cnpj = geral.documento

where PES.cnpj is null or
( PES.nome <> geral.nome or 
PES.codigoSistemaGestao <> geral.codigoSistemaGestao --or
--PES.dataclientedesde <> geral.dataclientedesde or
--PES.inscricaoEstadual <> geral.inscricaoEstadual
)
```
Poderia reescrever este código utilizando boas práticas?

---
## GPT 🤖

```sql
SELECT geral.*
FROM (
    SELECT *
    FROM OPENQUERY(LS_ALEX,'
        SELECT
            RTRIM(SA1.A1_CGC) AS documento,
            CASE WHEN LEN(SA1.A1_CGC) = 11 THEN ''F'' ELSE ''J'' END AS tipo,
            ''EXEMPLO'' AS nomeorigem,
            LTRIM(SA1.A1_NREDUZ) AS nome,
            CASE WHEN LEN(SA1.A1_CGC) = 14 THEN LTRIM(SA1.A1_NOME) ELSE '''' END AS razaosocial,
            SA1.A1_COD AS codigosistemagestao,
            CASE WHEN LEN(SA1.A1_CGC) = 14 THEN REPLACE(REPLACE(REPLACE(REPLACE(SA1.A1_INSCR,'' '',''''),''-'',''''),''.'',''''),''/'','''') ELSE '''' END AS InscricaoEstadual,
            CASE WHEN SA1.A1_DTCAD = '''' THEN CONVERT(VARCHAR, CAST(SA1.A1_XDTLNT AS DATE), 103) ELSE CONVERT(VARCHAR, CAST(SA1.A1_DTCAD AS DATE), 103) END AS dataclientedesde
        FROM SA1010 SA1 WITH (NOLOCK)
        WHERE SA1.D_E_L_E_T_ = '' ''
            -- AND SA1.A1_PESSOA = ''J''
            AND SUBSTRING(SA1.A1_CGC, 1, 11) NOT IN (''00000000000'', ''11111111111'', ''22222222222'', ''33333333333'', ''44444444444'',
                ''55555555555'', ''66666666666'', ''77777777777'', ''88888888888'', ''99999999999'')
            AND A1_XDTLNT > REPLACE(CAST(DATEADD(DAY, -90, CAST(GETDATE() AS DATE)) AS VARCHAR(10)), ''-'', '''')
        ORDER BY SA1.A1_CGC, SA1.A1_LOJA;
    ')
) AS geral
LEFT JOIN (
    SELECT ISNULL(pj.cnpj, pf.cpf) AS cnpj,
        p.nome,
        p.codigoSistemaGestao,
        p.dataclientedesde,
        j.inscricaoEstadual,
        j.razaosocial
    FROM test.dbo.pessoa p WITH (NOLOCK)
    LEFT JOIN test.dbo.pessoajuridica pj WITH (NOLOCK) ON pj.codigopessoa = p.codigo
    LEFT JOIN test.dbo.juridica j WITH (NOLOCK) ON j.cnpj = pj.cnpj
    LEFT JOIN test.dbo.pessoafisica pf WITH (NOLOCK) ON pf.codigopessoa = p.codigo
    WHERE p.codigoOrigem = 4
        AND p.codigoTipoRelacionamento = ''C''
) AS PES ON PES.cnpj = geral.documento
WHERE PES.cnpj IS NULL
    OR (PES.nome <> geral.nome
        OR PES.codigoSistemaGestao <> geral.codigoSistemaGestao
        -- OR PES.dataclientedesde <> geral.dataclientedesde
        -- OR PES.inscricaoEstadual <> geral.inscricaoEstadual
    );
```

---
## EU 🤓
Essa sintaxe SQL abaixo esta correta?
```sql
select * from openquery (LS_ALEX,'
SELECT
''03-''+SC5.C5_FILIAL+''-''+SC5.C5_NUM as CodigoPedido,
 CASE  WHEN SC5.D_E_L_E_T_ =   ''*''                                        THEN ''C''   
            WHEN C5_NOTA        in (''XXXXXX'',''XXXXXXXXX'')                 THEN ''C'' 
            WHEN MIN(C9_NFISCAL) = '' '' AND  MAX(C9_NFISCAL)  <> '' ''        THEN ''FP''   
            WHEN C5_NOTA        not in ('' '',''XXXXXX'',''XXXXXXXXX'')         THEN ''F'' 
           WHEN MAX(C9_BLCRED) = ''09''                                    THEN ''09'' 
           WHEN C5_BLQ         =   ''1''                                   THEN ''BR''   
           WHEN C5_BLQ         =   ''2''                                   THEN ''B''   
           WHEN C5_LIBEROK     =   '' ''                                   THEN ''A''   
           WHEN MIN(C9_NFISCAL)  = '' '' AND  MAX(C9_NFISCAL)  = '' '' AND 
                MIN(C9_BLCRED) NOT IN ('' '',''10'')                         THEN ''B''
           WHEN MIN(C9_NFISCAL)  = '' '' AND  MAX(C9_NFISCAL)  = '' '' AND 
                MIN(C9_BLEST)  NOT IN ('' '',''10'') AND 
                MIN(C9_BLCRED) IN     ('' '',''10'')                         THEN ''BR'' 
           WHEN C5_LIBEROK     =   ''S''  AND C5_NOTA = '' ''                THEN ''L'' 
END AS CSGSITUACAO
FROM SC5030 SC5 WITH(NOLOCK) 
	LEFT  JOIN SC9030 SC9 WITH(NOLOCK) ON C5_FILIAL = C9_FILIAL AND C5_NUM    = C9_PEDIDO AND C5_CLIENT = C9_CLIENTE AND C5_LOJACLI = C9_LOJA AND SC9.D_E_L_E_T_ = '' ''
	INNER JOIN SA1010 SA1 WITH(NOLOCK) ON A1_FILIAL = ''''  AND C5_CLIENT = A1_COD AND C5_LOJACLI = A1_LOJA  AND SA1.D_E_L_E_T_ = '' ''
	
	WHERE	
    SC5.C5_EMISSAO >= GETdATE() -360 
	AND C5_XORIGWS <> ''E'' AND C5_TIPO = ''N'' AND C5_NUM <> ''''
	AND rtrim(SA1.A1_CGC) not in (''00000000000000'') AND C5_XSTATUS = ''1'' 
	and  substring (rtrim(C5_VEND1) ,1,4) <> ''LJLV''
	GROUP BY SC5.C5_FILIAL,SC5.C5_NUM , SC5.C5_EMISSAO , SC5.D_E_L_E_T_ , C5_LIBEROK, C5_NOTA , C5_BLQ
')
)geralx
) geral
```

---
## GPT 🤖

A sintaxe SQL fornecida possui alguns erros. Vou destacar as correções necessárias:

1. Remova a vírgula após a cláusula `FROM SC5030 SC5 WITH(NOLOCK)`. A linha deve terminar em `SC5030 SC5 WITH(NOLOCK)`.
2. Na linha `FROM SC5030 SC5 WITH(NOLOCK)`, adicione um espaço entre `NOLOCK)` e `INNER`.
3. Na linha `INNER JOIN SA1010 SA1 WITH(NOLOCK) ON A1_FILIAL = ''''  AND C5_CLIENT = A1_COD AND C5_LOJACLI = A1_LOJA  AND SA1.D_E_L_E_T_ = '' ''`, remova os espaços em branco após as aspas duplas vazias. Deve ficar assim: `AND SA1.D_E_L_E_T_ = ''''`.
4. Na linha `SC5.C5_EMISSAO >= GETdATE() -360`, a função `GETdATE()` deve ser corrigida para `GETDATE()`.
5. Na linha `and  substring (rtrim(C5_VEND1) ,1,4) <> ''LJLV''`, remova os espaços em branco antes e depois de `rtrim(C5_VEND1)` para que fique `substring(rtrim(C5_VEND1), 1, 4) <> ''LJLV''`.

Aqui está a versão corrigida da consulta SQL:

```sql
SELECT
    '03-' + SC5.C5_FILIAL + '-' + SC5.C5_NUM AS CodigoPedido,
    CASE
        WHEN SC5.D_E_L_E_T_ = '*' THEN 'C'
        WHEN C5_NOTA IN ('XXXXXX', 'XXXXXXXXX') THEN 'C'
        WHEN MIN(C9_NFISCAL) = ' ' AND MAX(C9_NFISCAL) <> ' ' THEN 'FP'
        WHEN C5_NOTA NOT IN (' ', 'XXXXXX', 'XXXXXXXXX') THEN 'F'
        WHEN MAX(C9_BLCRED) = '09' THEN '09'
        WHEN C5_BLQ = '1' THEN 'BR'
        WHEN C5_BLQ = '2' THEN 'B'
        WHEN C5_LIBEROK = ' ' THEN 'A'
        WHEN MIN(C9_NFISCAL) = ' ' AND MAX(C9_NFISCAL) = ' ' AND MIN(C9_BLCRED) NOT IN (' ', '10') THEN 'B'
        WHEN MIN(C9_NFISCAL) = ' ' AND MAX(C9_NFISCAL) = ' ' AND MIN(C9_BLEST) NOT IN (' ', '10') AND MIN(C9_BLCRED) IN (' ', '10') THEN 'BR'
        WHEN C5_LIBEROK = 'S' AND C5_NOTA = ' ' THEN 'L'
    END AS CSGSITUACAO
FROM
    SC5030 SC5 WITH (NOLOCK)
    LEFT JOIN SC9030 SC9 WITH (NOLOCK) ON C5_FILIAL = C9_FILIAL AND C5_NUM = C9_PEDIDO AND C5_CLIENT = C9_CLIENTE AND C5_LOJACLI = C9_LOJA AND SC9.D_E_L_E_T_ = ' '
    INNER JOIN SA1010 SA1 WITH (NOLOCK) ON A1_FILIAL = '' AND C5_CLIENT = A1_COD AND C5_LOJACLI = A1_LOJA AND SA1.D_E_L_E_T_ = ''
WHERE


    SC5.C5_EMISSAO >= GETDATE() - 360
    AND C5_XORIGWS <> 'E' AND C5_TIPO = 'N' AND C5_NUM <> ''
    AND RTRIM(SA1.A1_CGC) NOT IN ('00000000000000') AND C5_XSTATUS = '1'
    AND SUBSTRING(RTRIM(C5_VEND1), 1, 4) <> 'LJLV'
GROUP BY
    SC5.C5_FILIAL, SC5.C5_NUM, SC5.C5_EMISSAO, SC5.D_E_L_E_T_, C5_LIBEROK, C5_NOTA, C5_BLQ
```

Certifique-se de que os nomes das tabelas, colunas e condições estão corretos para o seu banco de dados.

---
## EU 🤓
Esse comando SQL esta correto?
delete SC5030;

---
## GPT 🤖

O comando SQL `DELETE SC5030;` não está correto. A sintaxe correta para excluir registros de uma tabela usando o comando `DELETE` é a seguinte:

```sql
DELETE FROM SC5030;
```

Certifique-se de que a tabela `SC5030` exista no banco de dados e que você tenha as permissões necessárias para executar a exclusão de registros. Tenha cuidado ao usar o comando `DELETE`, pois ele remove permanentemente os registros da tabela. É recomendado fazer um backup dos dados antes de executar comandos de exclusão.

---
## EU 🤓
Mais alguma dica em relação ao comando acima?

---
## GPT 🤖

Claro! Aqui estão algumas dicas adicionais ao usar o comando `DELETE` em SQL:

1. Utilize uma cláusula `WHERE`: Se você deseja excluir registros específicos da tabela, é recomendado incluir uma cláusula `WHERE` para definir as condições de exclusão. Por exemplo:

   ```sql
   DELETE FROM SC5030 WHERE condição;
   ```

   A condição pode ser baseada em uma ou mais colunas da tabela para identificar os registros que devem ser excluídos.

2. Tenha cuidado com a exclusão em massa: Se você não especificar uma cláusula `WHERE`, o comando `DELETE` irá remover todos os registros da tabela. Tenha cuidado ao executar essa ação, pois ela pode ser irreversível e resultar na perda de todos os dados.

3. Faça um backup dos dados: Antes de executar o comando `DELETE`, é sempre uma boa prática fazer um backup dos dados da tabela ou criar uma cópia de segurança. Isso garante que você tenha uma cópia dos dados caso precise restaurá-los posteriormente.

4. Verifique as restrições e dependências: Certifique-se de que não existam restrições de chave estrangeira ou outras dependências que possam ser violadas ao excluir os registros. Caso contrário, o comando `DELETE` pode falhar ou ter um impacto indesejado em outras partes do banco de dados.

5. Teste em um ambiente de desenvolvimento ou faça transações em lotes: Se você estiver excluindo um grande número de registros ou não tiver certeza do impacto da exclusão, é recomendado testar o comando em um ambiente de desenvolvimento antes de executá-lo em produção. Além disso, você também pode dividir a exclusão em transações menores (por exemplo, usando a cláusula `TOP` em SQL Server ou `LIMIT` em MySQL) para evitar bloqueios prolongados da tabela e minimizar o impacto no desempenho.

Lembre-se de sempre ter cuidado ao executar comandos de exclusão em um banco de dados, pois eles podem ter consequências significativas.

---
## Mais informações
- [Visão Geral - ChatGPT](https://medium.com/blog-do-zouza/chatgpt-vis%C3%A3o-geral-f68ed1d1cf54)
- [ChatGPT - Criando Medidas DAX com ChatGPT](https://www.youtube.com/watch?v=vo9uo6aFLME)

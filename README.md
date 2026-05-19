## Atividades

### **1 Criação da tabela de clientes**

```sql
CREATE EXTERNAL TABLE clientes(
	id BIGINT,
	idade BIGINT,
	sexo STRING,
	dependentes BIGINT,
	escolaridade STRING,
	tipo_cartao STRING,
	limite_credito DOUBLE,
	valor_transacoes_12m DOUBLE,
	qtd_transacoes_12m BIGINT
)
ROW FORMAT SERDE 'org.apache.hadoop.hive.serde2.OpenCSVSerde'
WITH SERDEPROPERTIES (
	'separatorChar' = ',',
	'quoteChar' = '"',
	'escapeChar' = '\\'
)
STORED AS TEXTFILE
LOCATION 's3://lucas-modulo-1-ebac-para-dados/'
```

### **2. Explorando os dados da tabela de clientes**

#### [**2.1. Query 1**](https://github.com/Lpresente/SQL_Exerc-cio_m-dulo_1/blob/main/query1.csv.csv)
```sql
SELECT *
FROM clientes;
```

#### [**2.2. Query 2**](https://github.com/Lpresente/SQL_Exerc-cio_m-dulo_1/blob/main/query2.csv.csv)
```sql
SELECT id,
	idade,
	limite_credito
FROM clientes
WHERE sexo = 'M'
ORDER BY idade DESC;
```

#### [**2.3. Query 3**](https://github.com/Lpresente/SQL_Exerc-cio_m-dulo_1/blob/main/query3.csv.csv)
```sql
SELECT sexo,
	AVG(idade) AS "media_idade_por_sexo"
FROM clientes
GROUP BY sexo;
```

## Atividades

### **1 Criação da tabela de clientes**

```sql
CREATE EXTERNAL TABLE clientes (
    id INT,
    idade INT,
    sexo STRING,
    dependentes INT,
    escolaridade STRING,
    estado_civil STRING,
    salario_anual STRING,
    tipo_cartao STRING,
    qtd_produtos INT,
    interacoes_12m INT,
    meses_inativo_12m INT,
    limite_credito DOUBLE,
    valor_transacoes_12m DOUBLE,
    qtd_transacoes_12m INT
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
STORED AS TEXTFILE
LOCATION 's3://lucas-modulo-1-ebac-para-dados/'
TBLPROPERTIES ("skip.header.line.count"="1");
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

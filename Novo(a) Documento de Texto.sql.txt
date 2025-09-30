SELECT cnpj, data_ref, grupo, nome, COUNT(*) as qtd
FROM credito_privado.economatica_consolidado_Q2 ecq 
GROUP BY cnpj, data_ref, grupo, nome
HAVING qtd > 1;

ALTER TABLE credito_privado.economatica_consolidado_Q2   DROP PRIMARY KEY;

ALTER TABLE credito_privado.economatica_consolidado_Q2  DROP COLUMN id;

ALTER TABLE credito_privado.economatica_consolidado_Q2 
ADD PRIMARY KEY (cnpj, data_ref, grupo, nome)

-- VALIDAR SE HÁ ALGUMA OUTRA TABELA QUE UTILIZE O ID COMO FK
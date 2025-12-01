# Fase 4 – Programming & Infrastructure (FIAP)


## Sobre o Projeto

Esta fase aprofundou o uso de **PL/SQL avançado**, programação procedural dentro do Oracle Database, além de trazer fundamentos de infraestrutura, sistemas operacionais, computação em nuvem e estatística aplicada com Python.

A atividade principal da fase exigiu duas entregas:

1. **Desafio 1 — Procedure em PL/SQL**
   Criar a procedure `PR_SGV_CARGA_RESUMO_OCORR_SAC` para consolidar dados do SAC, transformá-los e cadastrar registros na tabela `MC_SGV_OCORRENCIA_SAC`.

2. **Desafio 2 — Python + Estatística**
   Calcular frequências e gerar um **histograma** representando a demanda diária de SAC usando bibliotecas como matplotlib e pandas.

Essas entregas integraram:
🔹 SQL procedural
🔹 sistemas e infraestrutura
🔹 análise estatística básica
🔹 visualização de dados
🔹 boas práticas de consistência, segurança e governança

---

## Estrutura do Repositório

```
/sql
   PR_SGV_CARGA_RESUMO_OCORR_SAC.sql     → Procedure completa do Desafio 1

/python
   main.ipynb                             → Cálculo de probabilidades e histograma (Desafio 2)

/docs
   Arquivo_1_1_componentes.txt            → Integrantes e RMs do grupo
   Evidencia_execucao.pdf                 → Execução da procedure (truncate → carga → resultado)
   evidencias_execucao.pdf                → Execução do código Python (cálculo e histograma)
```

---

# Procedure PL/SQL – Desafio 1

A procedure `PR_SGV_CARGA_RESUMO_OCORR_SAC` foi desenvolvida para:

* carregar dados do SAC a partir de múltiplas tabelas
* aplicar transformações importantes:

  * classificação textual do tipo de SAC
  * cálculo do lucro unitário
  * cálculo do ICMS por estado
  * geração incremental do número da ocorrência
* buscar estado e UF do cliente
* inserir registros consolidados
* controlar exceções
* limpar a tabela (`truncate`)
* finalizar o processamento com `COMMIT`

Trecho da sua procedure:

```sql
cursor c_abertura_sac is
    select  s.nr_sac,
            s.dt_abertura_sac,
            s.hr_abertura_sac,
            s.tp_sac,
            s.nr_indice_satisfacao,
            s.cd_produto,
            p.ds_produto,
            p.vl_unitario vl_unitario_prod,
            p.vl_perc_lucro,
            s.nr_cliente,
            c.nm_cliente
    from mc_sgv_sac s
```

---

# Python – Desafio 2: Frequência & Histograma

O arquivo `main.ipynb` implementa:

* leitura de dados simulados do SAC
* cálculo de frequências
* aplicação de probabilidade simples
* geração de histograma com matplotlib

Exemplo de código usado:

```python
plt.hist(dados, bins=5)
plt.title('Categoria de Frequência de Ocorrências (Últimos Meses)')
plt.xlabel('Faixa de Valores')
plt.ylabel('Quantidade')
```

---

# Conteúdos abordados na Fase 4

De acordo com a trilha da Fase 4, esta etapa incluiu:

### **PL/SQL Avançado**

* Subprogramas
* Functions
* Procedures
* Packages
* Triggers

### **Infraestrutura**

* Virtualização
* Sistemas Operacionais
* Linux
* Segurança em ambiente on-premise

### **Banco de Dados**

* Gerenciamento
* Arquitetura

### **Python Científico**

* Bibliotecas para ML
* Pandas, NumPy e Matplotlib
* Probabilidade aplicada

---

# Integrantes do Grupo

* Carlos Vinícius Rodrigues Silva
* Gabriela Sena da Silva
* Gustavo Almeira Scardini
* Tatiana Espinola
* Vitor Fernandes Antunes

---

# Principais Aprendizados da Fase

✔ Desenvolvimento de procedures robustas em PL/SQL

✔ Manipulação de cursores, loops, exceções e funções

✔ Integração entre SQL procedural e lógica de negócio

✔ Leitura, cálculo e visualização estatística em Python

✔ Interpretação de demandas do SAC via frequência e histogramas

✔ Compreensão de infraestrutura, segurança e arquitetura

✔ Execução de aplicações em ambiente Linux

---

# 📩 Contato

**Gabriela Sena da Silva**

🔗 LinkedIn: [https://www.linkedin.com/in/gabrielasena](https://www.linkedin.com/in/gabrielasena)

📧 [gabisena@outlook.com](mailto:gabisena@outlook.com)


Se quiser trocar ideias sobre PL/SQL, Python, Data Engineering ou Infraestrutura, fique à vontade para me chamar!

# SQL Lab - Sucos Vendas (ETL & Admin)

Este repo é o meu "playground" de SQL Server. Aqui eu documento como estou estruturando bancos de dados do zero, saindo de planilhas bagunçadas para tabelas normalizadas e prontas para análise.

Como trabalho com infra e sistemas no dia a dia, meu foco aqui não é só fazer `SELECT`, mas garantir que a estrutura suporte o tranco e que a automação da carga funcione.

## 🛠 O que eu fiz aqui (Technical Stack)

* **Engine:** SQL Server rodando via Docker (no meu Linux Mint).
* **A treta do Excel:** Usei o `informações.xlsx` como fonte. O desafio foi tratar colunas que vieram com espaços no nome (ex: `" NOME"`) e converter os limites de crédito que o Excel insistia em deixar gigantes ou em formato científico.
* **Tipagem:** Fiz o mapeamento manual para garantir que `CPF` seja string (e não número, pra não perder o zero à esquerda), e usei `BIT` e `MONEY` onde faz sentido para economizar storage e ganhar precisão.

## 📁 Estrutura

- `/scripts`: Tem o `CREATE TABLE` com a modelagem que desenhei e os `INSERT INTO` já saneados.
- `/queries`: Consultas que usei para validar se a carga deu certo (filtros por estado, análise de limite de crédito, etc).

## 🚀 Como eu rodo isso

Se eu precisar subir esse lab em outro lugar (ou se você quiser testar), o processo é:
1. Subir o container do SQL Server.
2. Rodar o script de DDL para criar o schema.
3. Rodar os scripts de carga (os inserts que tratei para não dar erro de conversão).

## 🧠 Próximos desafios
- Criar Stored Procedures para não ter que ficar rodando insert na mão.
- Mexer com índices pra ver o plano de execução mudar quando a tabela crescer.
- Integrar os scripts de carga com algum processo em Python ou Node.js (aproveitando o que já manjo de automação).

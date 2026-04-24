# Sintegra-SP

Pequeno utilitário criado para resolver um problema prático do dia a dia: identificar, de forma rápida, quais clientes de uma carteira são optantes pelo **Simples Nacional**.

## O problema

Ao trabalhar com uma lista de clientes, surgiu a necessidade de saber o regime tributário de cada um — se são optantes pelo Simples Nacional ou contribuintes do regime Normal. Fazer essa consulta manualmente para cada CNPJ seria inviável, então este script automatiza o processo.

## O que o programa faz

1. Lê uma planilha `clientes.xlsx` contendo uma coluna `CNPJ`
2. Consulta cada CNPJ na [BrasilAPI](https://brasilapi.com.br/) (dados da Receita Federal)
3. Classifica cada cliente como **Simples Nacional** ou **Normal**
4. Adiciona a coluna `Regime Tributário` na própria planilha e salva o resultado

## Requisitos

- Python 3.x
- Bibliotecas: `pandas`, `requests`, `openpyxl`

Instale as dependências com:

```bash
pip install pandas requests openpyxl
```

## Como usar

1. Coloque o arquivo `clientes.xlsx` na mesma pasta do script
2. Certifique-se de que a planilha tem uma coluna chamada `CNPJ`
3. Execute:

```bash
python sintegra.py
```

4. Acompanhe o progresso no terminal — ao final, a planilha será atualizada com a coluna `Regime Tributário`

## Observações

- O script aguarda 1 segundo entre cada consulta para evitar bloqueio por excesso de requisições
- CNPJs com formato inválido (diferente de 14 dígitos) são marcados como `CNPJ Inválido`
- A coluna CNPJ é mantida como **texto** na planilha, preservando os zeros à esquerda

import pandas as pd
import matplotlib.pyplot as plt

# Carregar a planilha
arquivo = "planilha-de-controle-financeiro-mobills-atualizada.xlsx"  # Nome correto do arquivo
df = pd.read_excel(arquivo, sheet_name="Despesas")  # Ajuste o nome da aba se necessário

# Processar os dados
df["Data"] = pd.to_datetime(df["Data"])
df = df.groupby("Categoria")["Valor"].sum().reset_index()

# Criar o gráfico
plt.figure(figsize=(8, 5))
plt.bar(df["Categoria"], df["Valor"], color="skyblue")
plt.xlabel("Categoria")
plt.ylabel("Valor (R$)")
plt.title("Gastos por Categoria")
plt.xticks(rotation=45)
plt.show()

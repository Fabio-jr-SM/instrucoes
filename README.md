Instrução de Uso do Código para Comparação de Nomes e Coleta de Telefones
Pré-requisitos
Ambiente: O código deve ser executado no Google Colab.
Pacotes Necessários: Certifique-se de que as bibliotecas pandas e difflib estão instaladas. No Google Colab, elas já estão disponíveis por padrão.
Estrutura das Planilhas
Planilha 1 (1chamada_AC_oficial.xlsx):

Contém uma coluna chamada "Nome completo".
Esta planilha deve conter os nomes dos alunos que você deseja verificar.
Planilha 2 (matriculados.csv):

Contém uma coluna chamada "NOME COMPLETO".
Esta planilha deve conter os nomes dos alunos que estão matriculados.
Planilha com Resultados de Não Correspondência:

O resultado da primeira comparação será salvo em um arquivo CSV chamado nao_correspondente.csv, que contém os nomes da primeira planilha que não foram encontrados na segunda.
Planilha de Nomes Não Inscritos (não_inscrito.csv):

Contém uma coluna chamada "Nomes não correspondentes Planilha 1".
Esta planilha deve conter os nomes dos alunos que não foram encontrados na segunda planilha.
Planilha de Inscritos (Inscritos.csv):

Contém colunas chamadas "Nome Completo:" e "Telefone:".
Esta planilha deve conter os nomes dos alunos que estão inscritos e seus respectivos telefones.
Como Usar o Código
Configuração Inicial:

Certifique-se de que as planilhas estão carregadas no seu Google Drive e os caminhos estão corretamente configurados no código.
Verifique se os nomes das colunas correspondem exatamente às descrições acima.
Execução do Código:

Execute o código completo no Google Colab. O código realiza as seguintes operações:
Carrega as planilhas de nomes e telefones.
Compara os nomes da primeira planilha com os da segunda planilha, identificando os que não correspondem.
Salva os nomes não correspondentes em um arquivo CSV.
Coleta os telefones correspondentes dos alunos que não foram encontrados e salva em um novo arquivo CSV.
Resultado:

Após a execução do código, você encontrará dois arquivos CSV em seu Google Drive:
nao_correspondente.csv: Contém os nomes da primeira planilha que não foram encontrados na segunda.
resultados_telefones.csv: Contém os nomes não correspondentes e os respectivos telefones coletados da planilha de inscritos.
Observações Finais
Verificação de Erros: Se ocorrerem erros relacionados a nomes não correspondentes ou colunas ausentes, verifique os nomes das colunas nas planilhas.
Ajustes de Limite: O código utiliza um threshold de 0.8 na função nomes_similares para determinar a similaridade dos nomes. Você pode ajustar esse valor se necessário.
Uso em Novas Comparações: Para comparar outras chamadas, basta substituir os caminhos das planilhas no código e garantir que as colunas estejam corretamente nomeadas.
Código para Comparação
Aqui está o código que você deve executar conforme as instruções:

python
Copiar código
from google.colab import drive
import pandas as pd
from difflib import SequenceMatcher

# Montar o Google Drive
drive.mount('/content/drive')

# Carregar as planilhas (substitua os caminhos pelos corretos)
df_planilha1 = pd.read_excel('/content/drive/MyDrive/scripts/1chamada_AC_oficial.xlsx')  # Alunos da primeira planilha
df_planilha2 = pd.read_csv('/content/drive/MyDrive/scripts/matriculados.csv')  # Alunos da segunda planilha

# Função para verificar se dois nomes são similares (ignorando maiúsculas e minúsculas)
def nomes_similares(nome1, nome2, threshold=0.8):
    if isinstance(nome1, str) and isinstance(nome2, str):
        return SequenceMatcher(None, nome1.lower(), nome2.lower()).ratio() >= threshold
    return False  # Retorna False se um dos nomes não for uma string

# Obter a coluna de nomes completos
nomes_planilha1 = df_planilha1["Nome completo"].tolist()
nomes_planilha2 = df_planilha2["NOME COMPLETO"].tolist()

# Encontrar nomes não correspondentes na planilha 1
nao_correspondentes_planilha1 = [
    nome for nome in nomes_planilha1
    if not any(nomes_similares(nome, nome_mat) for nome_mat in nomes_planilha2)
]

# Encontrar nomes não correspondentes na planilha 2
nao_correspondentes_planilha2 = [
    nome for nome in nomes_planilha2
    if not any(nomes_similares(nome, nome_mat) for nome_mat in nomes_planilha1)
]

print(nao_correspondentes_planilha1)
print(nao_correspondentes_planilha2)

# Criar um DataFrame com os nomes não correspondentes
nao_correspondentes = pd.DataFrame({
    "Nomes não correspondentes Planilha 1": nao_correspondentes_planilha1
})

# Salvar os nomes não correspondentes que estão na primeira chamada e não estão inscritos em um arquivo CSV
nao_correspondentes.to_csv('/content/drive/MyDrive/scripts/resultados/nao_correspondente.csv', index=False)

# Coletar telefones
df_nomes = pd.read_csv('/content/drive/MyDrive/scripts/resultados/não_inscrito.csv')  # Planilha com apenas nomes
df_telefones = pd.read_csv('/content/drive/MyDrive/scripts/Inscritos.csv')  # Planilha com nomes e telefones

# Criar uma lista para armazenar os resultados
resultados = []

# Iterar sobre cada nome na planilha de nomes
for nome in df_nomes["Nomes não correspondentes Planilha 1"]:
    # Tentar encontrar um telefone correspondente na segunda planilha
    telefone_encontrado = None
    for index, row in df_telefones.iterrows():
        if nomes_similares(nome, row["Nome Completo:"]):  # Verifica se os nomes são similares
            telefone_encontrado = row["Telefone:"]  # Coleta o telefone correspondente
            break  # Para de procurar uma vez que o telefone é encontrado
    resultados.append((nome, telefone_encontrado))  # Adiciona o nome e o telefone à lista de resultados

# Criar um DataFrame com os resultados
df_resultados = pd.DataFrame(resultados, columns=["Nome Completo", "Telefone"])

# Salvar os resultados em um arquivo CSV
df_resultados.to_csv('/content/drive/MyDrive/scripts/resultados/resultados_telefones.csv', index=False)

print("Os resultados foram salvos em 'resultados_telefones.csv'.")

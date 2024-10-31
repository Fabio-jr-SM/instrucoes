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

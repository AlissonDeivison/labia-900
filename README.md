# Guia de Configuração: Azure Inteligência Artificial (IA)

## 1. Configuração do Machine Learning Workspace

### Objetivo
Este guia tem como finalidade demonstrar o processo de configuração de um modelo preditivo no Azure Machine Learning, incluindo a definição dos pontos de extremidade.

### Ferramentas Necessárias
- [Portal Azure](https://azure.microsoft.com/pt-br/get-started/azure-portal/)
- Serviço: Azure Machine Learning

### Pontos Importantes
- Antes de iniciar, é necessário possuir uma conta ativa no Azure.
- Caso esteja realizando um estudo prático, recomenda-se excluir os recursos criados ao final para evitar cobranças indesejadas.

### Recursos Complementares
- [Detalhamento sobre Content Safety](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/02-content-safety.html)
- [Guia sobre Machine Learning](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/01-machine-learning.html)

### Passo a Passo

#### 1.1 Criar o Machine Learning Workspace
1. Acesse o **Azure Machine Learning**.
2. Clique em **Create** e selecione **New Workspace**.
3. Preencha os campos na aba **Basics**:
   - **Subscription**: Conta vinculada ao seu Azure.
   - **Resource Group**: Subcategoria dentro da assinatura.
   - **Workspace Name**: Nome único para o projeto.
   - **Region**: Localização do servidor Azure.
   - **Storage Account**: Mantém os artefatos gerados.
   - **Key Vault**: Armazena credenciais e certificados.
   - **Application Insights**: Monitora a execução do modelo.
   - **Container Registry**: Deixe como "None".
4. Configure as demais abas:
   - **Networking**: Definição de acesso (Público/Privado).
   - **Encryption**: Opção de criptografia.
   - **Identity**: Controle de acesso.
   - **Tags**: Permite filtrar projetos por departamento ou finalidade.
5. Valide as configurações na aba **Review + Create** e clique em **Create**.
6. Aguarde a finalização do processo.

---

## 2. Configuração do Modelo e Padrão de Leitura de Dados

### Objetivo
Configurar o serviço Azure Machine Learning para leitura da base de dados e processamento dos resultados.

### Ferramentas Necessárias
- [Portal Azure](https://azure.microsoft.com/pt-br/get-started/azure-portal/)
- [Azure ML](https://ml.azure.com/)

### Passo a Passo

#### 2.1 Acessar o Workspace Criado
1. Clique em **Go to Resource**.
2. Selecione **Launch Studio**.
3. Caso solicitado, realize o login.

#### 2.2 Criar um Job Automatizado
1. No menu lateral, clique em **Automated ML**.
2. Escolha **New Automated Job**.
3. Preencha os campos:
   - **Job Name**: mslearn-bike-automl
   - **Experiment Name**: mslearn-bike-rental
   - **Description**: Previsão automatizada de aluguel de bicicletas.

#### 2.3 Selecionar o Tipo de Tarefa
1. Escolha **Regression** como tipo de tarefa.
2. Clique em **Create** para adicionar os dados.
3. Configure os seguintes campos:
   - **Data Type**: Table (mltable)
   - **Name**: bike-rentals
   - **Description**: Historic bike rental data
4. Em **Data Source**, selecione **From local files** e clique em **Next**.
5. Configure:
   - **Datastore Type**: Azure Blob Storage
   - **Name**: workspaceblobstore
6. Faça o upload do arquivo de dados disponível em [bike-rentals](https://aka.ms/bike-rentals) e prossiga.

#### 2.4 Configurar a Coluna Alvo
1. Defina **Target Column** como "rentals (Integer)".
2. Desmarque as opções:
   - Explain Best Model
   - Enable Ensemble Stacking
   - Use All Supported Models
3. Escolha os modelos **RandomForest** e **LightGBM**.

#### 2.5 Definir Limites e Testes
1. Configure **Limits**:
   - Timeout e máximo de avaliações.
2. Configure **Validate and Test**:
   - **Validation Type**: Train-validation split
   - **Validation Percentage**: 10%
   - **Test Data**: None

#### 2.6 Finalizar o Processo
1. Revise as configurações e clique em **Submit Training Job**.
2. Aguarde a conclusão do processo antes de sair da tela.

---

## 3. Configurar o Modelo e Validar os Resultados

### Objetivo
Apresentar os resultados dos experimentos realizados.

### Ferramentas Necessárias
- [Portal Azure](https://azure.microsoft.com/pt-br/get-started/azure-portal/)
- [Azure ML](https://ml.azure.com/)

### Passo a Passo

#### 3.1 Acessar o Treinamento Finalizado
1. Acesse **Azure Machine Learning Studio**.
2. Selecione **Experiments**.
3. Clique no experimento criado.

#### 3.2 Analisar os Resultados
1. No painel de resultados, visualize os modelos gerados.
2. Compare as métricas dos modelos (ex.: RMSE, MAE, R²).

#### 3.3 Implantar o Modelo
1. Selecione **Deploy Model**.
2. Configure os parâmetros da API de previsão.
3. Teste a previsão com novos dados.

#### 3.4 Finalização
- Caso esteja realizando apenas um estudo, exclua os recursos criados.
- Revise os logs para futuras melhorias no modelo.

---

## Conclusão
Seguindo este guia, você configurou um ambiente de Machine Learning no Azure, criou e treinou um modelo preditivo e implantou a solução para testes. Para exploração avançada, consulte a documentação oficial da [Microsoft](https://learn.microsoft.com/).


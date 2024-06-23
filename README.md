# novadrivebank

## Tecnologias necessárias
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)

## Importante
Antes de instalar as dependências é necessário primeiro modificar as configurações de Política de Execução de seu computador para ter domínio sobre a chave de acesso.

[Acesse Políticas de Execução](https://learn.microsoft.com/pt-br/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.4)

Procure pela Política de Execução ```RemoteSigned```, abra o Powershell do seu Windows e siga as instruções de definição e confirme digitando 'a' ou 's'.

Após ter conseguido definir a Política de Execução do seu computador, abra seu terminal digite o caminho do ambiente virtual do seu projeto ```.\novadrivebank\Scripts\activate``` para ativá-lo. Uma vez ativado, todas as instalações serão direcionadas para esse ambiente virtual.

Se você não baixou o ambiente virtual deste repositório, execute no seu terminal:
```bash
python -m venv novadrivebank
```

## Instalação
Siga os passos abaixo para instalar o projeto.

```bash
pip install -r requirements.txt
```
Se o comando acima não funcionar, tente este:
```bash
python -m pip install -r requirements.txt
```
Este comando irá instalar todas as dependências python presentes no arquivo ```requirements.txt```. Certifique-se de que todas as dependências estejam instaladas.

## Uso
Veja abaixo como usar o projeto.

Uma vez que todas as dependências estejam instaladas, comece a realizar os testes. Certifique se seu ambiente virtual está ativado.

Para fazer o uso da API é necessário ter o PostgreSQL instalado em seu computador para habilitar a conexão do banco de dados. [Instale o PostgreSQL](https://www.postgresql.org/download/).

Se você já possui o PostgreSQL instalado em seu PC, crie um novo banco de dados de acordo com estas credenciais:
```bash
dbname: 'novadrivebank'
user: 'etlreadonlybank'
password: 'novadrive376A@'
host: '159.223.187.110'
port: 5432
```

Após ter criado o banco, não se preocupe em ter que criar todas as tabelas do início ao fim, pois este banco que você acabou de criar é um banco já feito.

Agora que você criou o banco ```novadrivebank```, a API pode se conectar e dar continuidade ao procedimento. Observe com atenção os arquivos ```const.py``` e ```utils.py```

Vamos começar!

Para criar um modelo keras e emitir um Relatório de Classificação, execute:
```bash
python modelcreation.py
```
Irá apresentar este relatório no final.
```bash
Relatório de Classificação:
              precision    recall  f1-score   support

           0       0.67      0.36      0.47        11
           1       0.71      0.89      0.79        19

    accuracy                           0.70        30
   macro avg       0.69      0.63      0.63        30
weighted avg       0.69      0.70      0.67        30
```
Você pode usar este código do arquivo ```modelcreation.py``` para testar outros modelos.

Se não estiver funcionando, pode ser a versão do ```tensorflow``` presente no arquivo ```requirements.txt``` algumas versões possuem funcionalidades bem específicas.

Desinstale a biblioteca ```tensorflow``` e em seguida instale a versão ```2.12.0``` melhorada.
```bash
pip uninstall tensorflow
pip install tensorflow==2.12.0 --upgrade
```
Se este comando não funcionar tente executar este:
```bash
python -m pip uninstall tensorflow
python -m pip install tensorflow==2.12.0 --upgrade
```
Agora tente executar o ```modelcreation.py```.

O papel da biblioteca ```tensorflow``` é facilitar o desenvolvimento, o treinamento e a implantação de modelos machine learning e deep learning, inclusive é um modelo muito utilizado em academias e indústrias possibilitando a criação de soluções inovadoras e escaláveis em diversas áreas.

Digite este comando para executar o arquivo ```xai.py```.
```bash
python xai.py
```
Além de emitir um Relatório de Classificação, imprime os recursos e pesos, e acessa os valores de features e seus bens, para o Bom.
```bash
Imprimindo os recursos e seus pesos para Bom
3: 0.11323411954804234
5: 0.06392901180711814
4: -0.06090427295012952
9: 0.04887472762545145
0: 0.014252785271250516
2: -0.01388226134365098
12: 0.012861067288582233
6: -0.007513086052114382
8: -0.007379514951608611
10: 0.00608139731745802

Acessar os valores das features e seus pesos para Bom
tiporesidencia <= 0.00: 0.11323411954804234
1.00 < score <= 2.00: 0.06392901180711814
escolaridade > 2.00: -0.06090427295012952
3.00 < produto <= 5.00: 0.04887472762545145
2.00 < profissao <= 4.50: 0.014252785271250516
-0.90 < renda <= -0.02: -0.01388226134365098
proporcaosolicitadototal > -0.15: 0.012861067288582233
0.03 < idade <= 0.77: -0.007513086052114382
estadocivil > 2.00: -0.007379514951608611
valorsolicitado > 0.26: 0.00608139731745802
```
Estamos utilizando a biblioteca ```lime```, cuja função é tornar modelos de machine learning mais interpretáveis e explicáveis, fornecendo insights de como as previsões são feitas, assegurando os usuários nos modelos preditivos.

Para rodar a nossa API, execute:
```bash
python api.py
```
A API entrará em atividade.
```bash
 * Serving Flask app 'api'
 * Debug mode: on
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on all addresses (0.0.0.0)
 * Running on http://127.0.0.1:5000
 * Running on http://192.168.10.40:5000
Press CTRL+C to quit
 * Restarting with watchdog (windowsapi)
 * Debugger is active!
 * Debugger PIN: 494-759-572
```
Alguns arquivos podem depender da atividade de um ou mais arquivos para funcionar, nesse caso iremos executar o arquivo ```testflask.py``` para realizar a previsão do relatório. Abra outro terminal no seu VS Code ou Prompt de Comando e execute:
```bash
python testflask.py
```
Antes de executar esta ação é necessário que a API esteja ativa, então este será o resultado:
```bash
Previsões recebidas:
[[4.6218931970543053e-07], [1.0], [1.0], [1.0]]
```
Agora que realizamos o teste de previsão, iremos executar a nossa aplicação web utilizando a ferramenta ```streamlit``` do python. Certifique que todas as dependências estejam instaladas.
```bash
streamlit run webapp.py
```
Se não funcionar tente:
```bash
python -m streamlit run webapp.py
```

A ferramenta ```streamlit``` tem o objetivo de dar suporte aos desenvolvedores e aos cientistas de dados criarem aplicações web interativas, simplificando o processo de desenvolvimento que o torna ideal para prototipagem, demonstrações e visualizações interativas de dados e modelos.

Ao utilizar a API de consulta, as informações a serem preenchidas devem ser correspondentes ao registro da tabela, caso contrário ela não irá encontrar o registro correspondente ao consultá-lo.

## Contribuição

Este projeto foi desenvolvido com objetivo de prover soluções da parte de análise e ciência de dados, se sua empresa ou o seu negócio enfrenta problemas comuns nessa área, este projeto lhe oferece estratégias que podem ser reforços de peso para o seu próprio modelo.

Não esqueça também de incluir na sua lista de favoritos e de compartilhar este repositório, porque foi exigido muita dedicação e esforço para ser concluído e atender à demanda do mercado de tecnologia.

Deixe nos comentários novas idéias que possam contribuir ainda mais para a inovação do projeto.

Obrigado!

### Link para clonar o projeto
https://gitub.com/GabrielFerreiraTSI/novadrivebank/
# Imersao vertex alura
## Projeto com os dados públicos do INEP
# **Projeto Alura com dados do ENEM**



A ideia do projeto é utilizar os modelos do vertex AI para fazer o processamento com NLP (Linguagem natural) para os dados do **enem de 2022**, assim conectando a base de dados com o vertex AI e gerando os resultados que são utilizados para gerar insights e criar uma dashboard (Acompanhe o final da documentação para ver e acessar o exemplo)

**Objetivo específico: Usar o code colab para gerar sql, executar com a API BigQuery de forma automática e gerar insights para utilizar na criação de dashboards com o looker studio.**


---

# **Conheça mais sobre o projeto**

<details>
<summary> Arquitetura </summary><br/>

Serviços utilizados 

|   Serviço    |                    Motivo de Uso                       |
|--------------|---------------------------------------------------------|
| Dados INEP   | O inep disponibiliza [microdados](https://https://www.gov.br/inep/pt-br/acesso-a-informacao/dados-abertos/microdados) do ENEM e de outras fontes |
| Cloud Storage| Armazenar e gerenciar dados brutos |
|   DataPrep   | Preparar e limpar dados para análise aqui podemos conhecer nossos dados|
|   BigQuery   | Armazenar e analisar grandes conjuntos de dados         |
|  Code Colab  | Executar notebooks e código Python, aqui criamos toda a lógica do projeto. |
|  Vertex AI   | Os modelos utilizados no codecolab são disponibilizados pelo Vertex          |
|    Looker  Studio     | Visualizar e analisar dados de forma interativa  |


<br>


---


</details>

<details>
<summary> Conheça mais a fundo o projeto </summary><br/>

Esse projeto fez parte a Imersão alura que aconteceu na segunda semana de maio e teve como objetivo principal apresentar o ai studio do google e o colab, o ai studio é uma ferramenta para criar e testar prompts e gerar chatbots multimodais. O colab é uma ferramenta interativa para criar códigos python.

Na fase inicial a ideia desse projeto era exportar os dados para um dataframe e depois para o google planilhas mas acabei deixando essa ideia de lado por não conhecer muito bem sobre essas ferramentas, esse foi o meu primeiro projeto de chatbot e a primeira vez que faço integraçoes com a API do Bigquery no colab então deu pra aprender muitas coisas.

As principais dificuldades desse projeto foram:


*   Integração do dataframe com a resposta do chat do GEMINI (não resolvido)
*   Criar os prompts assertivos e evitar ilusões
*   Integrar a lógica de puxar os dados do BigQuery e fazer mais uma consulta em cima dos dados processados
*   Ver o sql Gerado (isso eu resolvi depois de botar a variavel como global)
*   Exaust do modelo (acabei fazendo um for e fiquei quase uma hora sem poder usar a API do vertex)

As coisas que mais considero que aprendi foram: 

 * Como Aplicar na prática o Chain of thought e Few Shots prompt
 * Como fazer integrações de python com o BigQuery 
 * Como usar o ai studio (via muito ele nos cursos mas nunca tinha utilizado)
 * Como funcionam os dataframes do panda (apesar de não ter consigo integrar eu aprendi muito errando)
 * Como funcionam embeddings 


---
</details>

<details>
<summary> Como Utilizar </summary><br/>

Para utilizar esse projeto, você precisa fazer algumas tarefas:


1.   Configurar os secrets
2.   Importar a tabela para o Bigquery
3.   Configurar o prompt para criar SQL baseado na sua tabela
4.   Testar, melhorar e implementar mais

A dashboard baseada nos insights é pública e assesível por esse link:



---
</details>


<details>
<summary> Sobre o autor </summary><br/>

Olá, meu nome é júlio tenho 20 anos, esse é o meu [linkedin](https://www.linkedin.com/in/julio-ferrer/) me manda um invite e vamos trocar ideia. Apesar de eu ter conseguido várias certificações no GCP não tenho muita experiência prática e esse tipo de imersão ajuda a gente a pegar vários insights legais.
Se quiser, a gente pode jogar alguma coisa também tipo um lolzinho ou um cs.
Sempre fui apaixonado e muito curioso pela tecnologia e desde que ingressei no mercado de trabalho me apaixonei pela área de dados. estou terminando minha primeira faculdade (acabo final do ano) e estou pensando em fazer mais uma.


---
</details>


### Alguns exemplos de prompts que foram utilizados para criar as dashboards:

 * **Qual é o Número de participantes por estado:** Contar quantos participantes fizeram o ENEM em cada estado brasileiro.
 * **Qual é a Média da nota de redação por faixa etária:** Calcular a média da nota da redação para cada faixa etária dos participantes.
 * **Qual é a nota específica de cada área e a média geral das notas de cada estado:** Calcular a média de cada nota de cada estado e a média geral
 * **Qual é % de participação de cada tipo de escola:** Verifica a participação de escolar públicas e particulares
 * **Compare o desempenho de treineiros e vestibulandos em relação a todas as notas:** Analisar as diferenças no desempenho entre os participantes que fizeram a prova como treineiros e aqueles que estavam realmente buscando uma vaga no ensino superior.

### Lógica por trás do chatbot 

A lógica que pensei pra criar o chatbot é mais ou menos assim:

1. Consulta: O usuário faz uma pergunta.

2. Entendimento: O modelo entende o que o usuário está perguntando e traduz para uma linguagem que o BigQuery compreende (SQL).

3. Busca: O BigQuery é usado para executar a consulta.

4. Resposta: O modelo organiza a resposta do BigQuery e a apresenta ao usuário

5. O modelo Salva a resposta em um dataframe e envia para o google sheets (Não aplicado)

6. O usuário usa os dados salvos e insights obtidos para criar dashboards

> A melhor prática e mais recomendavel seria executar a consulta (com um limit maior) no BigQuery e fazer as dashs a partir do BQ, o Looker Studio tem uma funcionalidade de cache e funciona muito melhor com os dados nessa plataforma. mas eu queria me desafiar a fazer ambas coisas.



Sobre os resultados obtidos:



*   O modelo gera a partir de uma pergunta o resultado e gera um insight
*   Esse insight é utilizado para criar uma dashboard com os dados

[Link Da Dashboard](https://lookerstudio.google.com/reporting/cf5687ea-7577-4c7f-8560-07623abc4315)



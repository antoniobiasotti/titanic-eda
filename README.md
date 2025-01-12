# Titanic EDA Project

A pergunta essencial a ser respondida ao avaliar um modelo de machine de learning é:

***Qual é sua performance em um conjunto de dados nunca visto antes?***  
  
  Isso nos leva ao conceito de:

1. TREINO - É a etapa de aprendizagem do modelo, na qual ele descobrirá a melhor forma de ajustar os pesos de cada parâmetro, como dividir os dados entre outras coisas, e isso vai depender muito do algoritmo em questão. Eventualmente, o modelo encontrará uma solução para que seja possível prever a variável alvo.
 
2. VALIDAÇÃO - Já com o modelo treinado, vamos avaliá-lo em um ambiente local confiável. De maneira simplista, consiste em uma simulação da realidade com dados inéditos - não vistos no treinamento.

3. TESTE - Determinar quais serão dados utilizados para avaliar o desempenho real do modelo e, uma vez escolhidos, devem permanecer intocados até o último modelo ser alcançado.

Nota-se em muitos casos uma maior flexibilidade entre as etapas de Validação e Teste, permitindo que ambas acabem por se misturar.

Mas então, qual a diferença entre Validação e Teste?

A função da etapa de validação é guiar a tomada de decisão que não interfira no ajuste dos parâmetros do modelo. O mais importante é se perguntar: a acurácia do meu modelo obtida nessa etapa está consistente com o que eu posso esperar alcançar em um ambiente real?  
Se sim, provavelmente a validação está correta.

A validação nos permite entender qual o efeito da adição de uma nova variável ao aprendizado do modelo, isto é, como essa nova variável impactou a estimativa do modelo em dados não vistos em treinamento. Porém, pelo fato de repetir-se diversas vezes esse processo, isso acabo por otimizar o modelo para aquele conjunto de dados já vistos, causando o chamado overfitting, que compromete uma avaliação mais rigorosa da estimativa de erro do modelo fora dos dados de treino. É aí que entra o teste.

É fundamental haver uma distinção clara entre as etapas de Validação e Teste para que não se misturem e sobreponham, caso contrário, dependendo do ruído dos dados, a estimativa calculada não refletirá a precisão real do modelo.

## 
### Técnicas de Amostragem 
O método que escolhemos para segmentar os dados pode alterar no valor final da acurácia do modelo, mas isso não significa que o modelo de fato piorou ou melhorou, pois o conjunto universo de dados permaneceu o mesmo. Para de fato aprimorarmos o nosso modelo, precisamos focar na etapa de Validação, deixando-a mais confiável e menos "aleatória". Algumas técnicas para fazer isso são:

- Seed (pseudo)aleatório
  - O problema com divisões aleatórias é que simplesmente por sorte (ou por azar) um outlier pode cair nos seus dados de validação, ou de treino, e comprometer a estimativa ao desbalancear os dados;
  - Esse método também pode ser implementado com mais de uma seed sendo gerada por um loop, e ao final dos testes no modelo, obtêm-se a acurácia média de todas as iterações. 

- Validação Cruzada (KFold)
  - Os dados de treino e validação são separados por divisões (Folds);
  - Cada Fold alterna quais dados serão usados para treino ou validação de uma forma que cada exemplar passa pelo menos uma vez, por cada subconjunto.
Também é possível tornarmos ainda mais robusta a Validação Cruzada, garantindo ainda mais credibilidade e certeza ao valor de acurácia do modelo obtido ao fim do teste. Para isso combina-se as duas técnicas acima, criando um loop em que cada iteração incrementamos a seed do estado inicial
##
### Melhorando nosso modelo
Para de fato aprimorarmos nosso modelo, é muito importante acharmos a melhor representação de variáveis que possiblite capturar os padrões mais interessantes no conjunto de dados, de acordo com o problema em questão. Para isso, além das variáveis Sexo e Idade, adicionaremos também Pclass - classe em que o passageiro viajou, SibSp - indicador da presença de irmão (Sibling) ou esposa (Spouse), Parch - indicador da presença de pais ou filhos e Fare - valor pago na passagem. Entretanto, o modelo treinado não foi capaz de superar a pontuação do gender_submission, o que indica que apenas variáveis numéricas não serão suficientes, revelando a necessidade de estudarmos também as variáveis categóricas.

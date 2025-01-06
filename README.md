# Titanic EDA Project

A pergunta essencial a ser respondida ao avaliar um modelo de machine de learning é: Qual é sua performance em um conjunto de dados nunca visto antes? Isso nos leva ao conceito de:

1. TREINO - É a etapa de aprendizagem do modelo, na qual ele descobrirá a melhor forma de ajustar os pesos de cada parâmetro, como dividir os dados entre outras coisas, e isso vai depender muito do algoritmo em questão. Eventualmente, o modelo encontrará uma solução para que seja possível prever a variável alvo.
 
2. VALIDAÇÃO - Já com o modelo treinado, vamos avaliá-lo em um ambiente local confiável. De maneira simplista, consiste em uma simulação da realidade com dados inéditos - não vistos no treinamento.

3. TESTE - Determinar qual será o conjunto de dados a serem utilizados para avaliar o desempenho real do modelo e devem permanecer intocados até o último modelo ser alcançado.

Nota-se em muitos casos uma maior flexibilidade entre as etapas de Validação e Teste, permitindo que ambas acabem por se misturar.

Mas então, qual a diferença entre Validação e Teste?

A função da etapa de validação é guiar a tomada de decisão que não interfira no ajuste dos parâmetros do modelo. O mais importante é se perguntar: a acurácia do meu modelo obtida nessa etapa está consistente com o que eu posso esperar alcançar em um ambiente real? Se sim, provavelmente a validação está correta.

A validação nos permite entender qual o efeito da adição de uma nova variável ao aprendizado do modelo, isto é, como essa nova variável impactou a estimativa do modelo em dados não vistos em treinamento. Porém, pelo fato de repetir-se diversas vezes esse processo, isso acabo por otimizar o modelo para aquele conjunto de dados já vistos, causando o chamado overfitting, que compromete uma avaliação mais rigorosa da estimativa de erro do modelo fora dos dados de treino. E é aí que entra o teste.

É fundamental haver uma distinção clara entre as etapas de Validação e Teste para que não se misturem e sobreponham, caso contrário, dependendo do ruído dos dados, a estimativa calculada não refletirá a precisão real do modelo.

## Técnicas de Amostragem 
O método que escolhemos para segmentar os dados pode alterar no valor final da acurácia do modelo, mas isso não significa que o modelo de fato piorou ou melhorou, pois os dados permanecem os mesmos. 
Seed (pseudo)aleatório

Validação Cruzada

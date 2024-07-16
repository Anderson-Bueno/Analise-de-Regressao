# Modelagem de Dados de Percepção de Corrupção Utilizando Análise de Regressão: Dados Regionais

## Introdução

A compreensão dos fatores que influenciam a percepção de corrupção é crucial para políticas públicas e estratégias de desenvolvimento. Neste estudo, exploramos como variáveis regionais podem afetar o Índice de Percepção de Corrupção (CPI) em diferentes regiões do mundo.

## Contextualização

O desafio envolve analisar dados complexos de percepção de corrupção, onde variáveis regionais podem desempenhar um papel significativo. A necessidade de modelagem estatística adequada se torna evidente para identificar padrões e fatores determinantes do CPI.

## Metodologia

### Preparação dos Dados

- **Carregamento dos dados**: Utilizamos dados regionais e do Índice de Percepção de Corrupção (CPI).
- **Estatísticas descritivas**: Análise descritiva inicial dos dados para entender a distribuição e a relação preliminar entre as variáveis.
- **Visualizações**: Criação de gráficos para explorar visualmente as relações entre as variáveis.

### Modelagem de Regressão

#### Regressão Simples

- **Modelo**: Investigação da relação entre uma única variável preditora e o CPI.
- **Resultados**: Análise dos coeficientes e significância estatística.

#### Regressão Múltipla

- **Modelo**: Inclusão de múltiplas variáveis preditoras para entender o impacto combinado das regiões no CPI.
- **Dummização**: Transformação de variáveis categóricas (regiões) em variáveis dummy.
- **Resultados**: Avaliação da melhoria na capacidade preditiva do modelo.

## Resultados

Os resultados mostram que a inclusão das regiões como variáveis qualitativas nos modelos de regressão melhora significativamente a capacidade preditiva do CPI. Além disso, a dummização das variáveis de região revelou insights importantes sobre como diferentes áreas geográficas podem impactar a percepção de corrupção.

## Reflexões

Este estudo não apenas contribui para a literatura acadêmica sobre percepção de corrupção, mas também oferece insights acionáveis para formuladores de políticas públicas e organizações internacionais interessadas em entender e mitigar a corrupção.

### Aprendizados

A aplicação de técnicas avançadas de análise estatística, como dummização de variáveis qualitativas e modelagem de regressão, destacou a importância da contextualização regional na interpretação de dados de percepção de corrupção. Aprendemos que a escolha adequada das variáveis explicativas é crucial para construir modelos robustos e interpretáveis.

## Implementação

### Instalação e Carregamento dos Pacotes


install.packages("readr")
install.packages("dplyr")
install.packages("ggplot2")
install.packages("lmtest")

library(readr)
library(dplyr)
library(ggplot2)
library(lmtest)


### Carregamento e Visualização dos Dados


# Carregar dados
dados <- read_csv("dados_corrupcao.csv")

# Estatísticas descritivas
summary(dados)

# Visualizações
ggplot(dados, aes(x = regiao, y = CPI)) +
  geom_boxplot() +
  labs(title = "Distribuição do CPI por Região", x = "Região", y = "Índice de Percepção de Corrupção") +
  theme_minimal()


### Modelagem de Regressão

#### Regressão Simples


# Regressão simples
modelo_simples <- lm(CPI ~ variavel_preditor, data = dados)
summary(modelo_simples)


#### Regressão Múltipla com Dummização


# Dummização das variáveis de região
dados_dummies <- dummy_cols(dados, select_columns = "regiao")

# Regressão múltipla
modelo_multiplo <- lm(CPI ~ . - regiao, data = dados_dummies)
summary(modelo_multiplo)


### Avaliação do Modelo

# Avaliação dos resíduos
plot(modelo_multiplo)

# Teste de significância
coeftest(modelo_multiplo)


## Conclusão

Este estudo demonstrou como a análise de regressão pode ser utilizada para entender a percepção de corrupção em diferentes regiões. A inclusão de variáveis regionais e a dummização das mesmas melhorou a capacidade preditiva do modelo, fornecendo insights valiosos para a elaboração de políticas públicas.

### Pontos Importantes

1. **Introdução**: Descrição clara do objetivo do projeto.
2. **Contextualização**: Explicação do problema que o projeto busca resolver.
3. **Metodologia**: Detalhamento das etapas de preparação dos dados, visualização e modelagem de regressão.
4. **Resultados**: Principais achados das análises.
5. **Reflexões**: Interpretação dos resultados e contribuição do estudo.
6. **Aprendizados**: Insights obtidos durante o estudo.
7. **Implementação**: Código detalhado para replicação do estudo.
8. **Contato**: Informações para contato.
9. **Licença**: Informação sobre a licença do projeto.

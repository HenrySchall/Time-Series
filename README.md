## Séries Temporais
#### Objetivos:
- Analisar a origem da série
- Previsões futuras
- Descrição do comportamento da série 
- Analisar perodicidade ou tendência 

#### Tipos:
- Univariada = apenas uma variável se altera ao longo do tempo
- Multivariada = mais de uma variável se altera ao longo do tempo

#### Conceitos:
Série Temporal -> é um conjunto de observações ordenadas no tempo ou um corte particular de um processo estocástico desconhecido

#### Matematicamente: Y = Tdt + Szt + et 
- Tendência (Tdt): Mudanças graduais em longo prazo (crescimento populacional).
- Sazonalidade (Szt): oscilações de subida e de queda que sempre ocorrem em um determinado período (maior valor da conta de energia elétrica no inverno).
- Resíduos (et): apresenta movimentos ascendentes e descendentes da série após a retirada do efeito de tendência ou sazonal (sequência de variáveis aleatórias).

![Figura-4-Decomposicao-da-serie-temporal-em-componentes-de-sazonalidade-de-tendencia-e](https://github.com/HenrySchall/Time-Series/assets/96027335/46bf2b49-dcb1-4153-9d66-2e57b4dc57ad)

Processo Estocástico -> é uma coleção de variáveis aleatórias definidas num mesmo espaço de probabilidades (processo gerador de uma série de variáveis). A descrição de um 
processo estocástico é feita através de uma distribuição de probabilidade conjunta (o que é muito complexo de se fazer), então geralmente descrevemos ele por meio das funções:
- 𝜇(𝑡)=𝐸{𝑍(𝑡)} -> Média 
- 𝜎^2(𝑡)=𝑉𝑎𝑟{𝑍(𝑡)} -> Variância 
- 𝛾(𝑡1,𝑡2)=𝐶𝑜𝑣{𝑍(𝑡1),𝑍(𝑡2)} -> Autocovariância

![Captura de tela 2024-07-04 180109](https://github.com/HenrySchall/Time-Series/assets/96027335/7ffc0399-4f35-4e82-ac69-8950c083c8f4)

Estacionaridade -> é quando uma série temporal apresenta todas suas características estatísticas constante ao longo do tempo
- Estacionaridade Fraca = é quando as propriedades estatiaticas, são constantes no tempo, E(x)=U, Var(x) = 𝜎^2, COV(X,X-n) = k (corariância entre observações em diferentes pontos no tempo depende do tempo específico em que elas ocorreram). Na literatura, geralmente estacionalidade significa estacionalidade fraca.

- Estacionaridade Forte = também chamada de estrita, é quando a função de probabilidade conjunta é invariante no tempo, ou seja, as distribuições individuais são iguais para todos "ts". Com isso a covariância depende apenas da distância entre as observações e não do tempo especifico que ocorreram. 

![Imagem-2](https://github.com/HenrySchall/Time-Series/assets/96027335/6c237676-00e5-407f-bcc7-cddf6c1c4a34)

Passeio Aleatório (Random Walk) -> é a soma de pequenas flutuações estocásticas (tendência estocástica)
Matematicamente: 𝑍𝑡 = 𝑍(𝑡−1)+ et

Autocorrelação -> é a correlação de determinados períodos anteriores com o período atual, ou seja, o grau de dependência serial. Cada período desse tipo de correlação é denominado lag (defasagem) e sua representação é feita pela Função de Autocorrelação (FAC) e a Função de Autocorrelação Parcial (FACP), ambas comparam o valor presente com os valores passados da série, a diferença entre eles é que a FAC analisa tanto a correlação direta como a indireta, já a FACP apenas correlação direta. Então podemos dizer, que a FAC vê a correlação direta do mês de janeiro em março e também a correlação indireta que o mês de janeiro teve em fevereiro que também teve em março, enquanto que a FACP apenas a correlação de janeiro em março. Essa análise é feita, porque é o pressuposto essencial para se criar previsões eficientes de uma série.

Ruído Branco (White Noise) -> é quando o erro de uma série temporal, segue uma distribuição normal, ou seja, um processo puramente aleatório. 
- E(Xt) = 0 
- Var(Xt) = 𝜎^2

Transformação e Suavização -> São técnicas que buscam deixar a série o mais próximo possível de uma distribuição normal. Transformando o valor das varáveis ou suavizando a tendência e/ou sazonaliade da série. Dentre todas as técnicas existentes podemos citar:
1) Tranformação Log 
2) Tranformação Expoencial
3) Tranformação Box-Cox
4) Suavização Média Móvel Exponencial (MME) - Curto período 
5) Suavização por Média Móvel Simples (MMS) - Longo período

Diferenciação -> A diferenciação, busca transformar uma série não estacionária em estacionária, por meio da diferença de dois períodos consecutivos

#### Modelos das séries temporais univariados:
Modelos lineares:
 - Modelos autorregressivos (AR)
 - Modelos médias móveis (MA)
 - Modelos autorregressivos e médias móveis (ARMA)
 - Modelos autorregressivos integrados e de médias móveis (ARIMA)
 - Modelos de longas dependências temporais ou memória longa (ARFIMA)
 - Modelos autorregressivos integrados e de médias móveis com sazonalidade (SARIMA)
 
Modelos não lineares:
 - Autorregressivo com limiar (TAR)
 - Autorregressivo com transição suave (STAR)
 - Troca de regime markoviano (MSM)
 - Redes neurais artificiais autorregressivas (AR-ANN)

Estrutura: 
- Autorregressivo (AR): indica que a variável é regressada em seus valores anteriores. 
- Integrado (I): indica que os valores de dados foram substituídos com a diferença entre seus valores e os valores anteriores (diferenciação).
- Média móvel (MA): Indica que o erro de regressão é uma combinação linear dos termos de erro dos valores passados.

Codificação: (p, d, q) Parâmetro d só pode ser inteiro, caso estivessemos trabalhando com um Modelo ARFIMA, o parâmetro d pode ser fracionado

- p = ordem da autorregressão.
- d = grau de diferenciação.
- q = ordem da média móvel.

Quando adicionamos a sazonalidade, além da codificação Arima (p, d, q), incluimos a codificação para a Sazonalidade (P, D, Q). Então um modelo SARIMA é definido por: (p, d, q)(P, D, Q)

Exemplos:
- Modelo ARFIMA: (1, 0.25, 1) 
- Modelo ARIMA: (2, 1, 1)
- Modelo AR: (1, 0, 0)
- Modelo MA (0, 0, 3)
- Modelo I: (0, 2, 0)
- Modelo ARMA: (4, 0, 1)
- Modelo SARIMA: (1, 1, 2)(2, 0, 1)

#### Akaike’s Information Criterion (AIC) e o Bayesian Information Criterion (BIC)
Nos modelos mais avançados, as funções de autocorrelação e autocorrelação parcial não são informativas para definir a ordem dos modelos, por isso usasse um critério de informação. Um critério de informação é uma forma de encontrar o número ideal de parâmetros de um modelo, para entendê-lo, tenha em mente que, a cada regressor adicional, a soma dos resíduos não vai aumentar; frequentemente, diminuirá. A redução se dá à custa de mais regressores. Para balancear a redução dos erros e o aumento do número de regressores, o critério de informação associa uma penalidade a esse aumento. Sendo assim, sua equação apresenta duas partes: a primeira mede a qualidade do ajuste do modelo aos dados, enquanto a segunda parte é chamada de função de penalização dado que penaliza modelos com muitos parâmetros, sendo assim, dado todas as combinações de modelos procuramos aquele que apresenta menor AIC.



















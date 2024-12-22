Estatísticas Descritivas
================
Edson Zangiacomi Martinez
2024-12-22

## Medidas descritivas

``` r
mean(x)           # média dos valores do objeto x
sd(x)             # desvio padrão
var(x)            # variância
median(x)         # mediana
range(x)          # amplitude
min(x)            # mínimo
max(x)            # máximo
quantile(x)       # quantis
IQR(x)            # amplitude do intervalo interquartil
sum(x)            # soma
prod(x)           # produto
sort(x)           # ordenação
summary(x)        # resumos
which.min(x)      # posição do mínimo
which.max(x)      # posição do máximo
```

Seja um vetor contendo os pesos de 20 pessoas

``` r
peso <- c(72.4, 68.4, 67.9, 67.4, 70.7, 67.7, 67.7, 67.2, 67.4, 66.1, 68.5, 67.9, 64.9, 68.3, 69.4, 65.5, 65.5, 67, 66.3, 64.8)
```

Exemplos:

``` r
 mean(peso)                   # retorna a média dos pesos
 summary(peso)                # retorna o mínimo, o máximo e os quartis
 IQR(peso)                    # retorna a amplitude do intervalo interquartil
 quantile(peso)               # retorna o mínimo, o máximo e os quartis
 quantile(peso,c(0.1,0.9))    # retorna os quantis 10% e 90%
```

Seja um data frame contendo os dados de 10 pessoas:

``` r
urlfile <- "https://raw.githubusercontent.com/edsonzmartinez/cursoR/main/dezpessoas.csv"
dados   <- read.csv(urlfile,head=TRUE,sep=";",dec=",")
dados
```

       ID sexo idade peso
    1   1    M    45 78.4
    2   2    M    65 82.1
    3   3    F    54 67.4
    4   4    F    76 56.2
    5   5    M    34 56.9
    6   6    F    67 65.8
    7   7    M    36 56.3
    8   8    M    87 89.8
    9   9    M    45 75.2
    10 10    F    68 59.3

Note que o R retornará uma mensagem de erro se você digitar
`mean(idade)`:

``` r
mean(idade)
```

`Error in mean(idade) : objeto 'idade' não encontrado`

O símbolo `$` em `dados$peso` retorna a variável `peso` do data frame
`dados`:

``` r
mean(dados$peso)
```

Alternativamente, podemos usar a função with():

``` r
with(dados,mean(peso))
```

`[1] 68.74`

## Função tapply()

Usando a função `tapply()`:

``` r
tapply(dados$idade,dados$sexo,mean)
```

        F     M
    66.25 52.00

## Função aggregate()

Usando a função `aggregate()`:

``` r
aggregate(idade~sexo,data=dados,mean)
```

      sexo idade
    1    F 66.25
    2    M 52.00

``` r
aggregate(idade~sexo,data=dados,sd)
```

      sexo     idade
    1    F  9.105859
    2    M 20.356817

``` r
aggregate(idade~sexo,data=dados,quantile)
```

      sexo idade.0% idade.25% idade.50% idade.75% idade.100%
    1    F    54.00     63.75     67.50     70.00      76.00
    2    M    34.00     38.25     45.00     60.00      87.00

``` r
aggregate(peso~sexo,data=dados,mean)
```

      sexo     peso
    1    F 62.17500
    2    M 73.11667

Usando a função `aggregate()` para obter simultaneamente as médias da
idade e do peso de acordo com o sexo:

``` r
aggregate(cbind(dados$idade,dados$peso),by=list(dados$sexo),mean)
```

      Group.1    V1       V2
    1       F 66.25 62.17500
    2       M 52.00 73.11667

``` r
medias <- aggregate(cbind(dados$idade,dados$peso),by=list(dados$sexo),mean)
names(medias) <- c("Sexo","Idade","Peso")
medias
```

      Sexo Idade     Peso
    1    F 66.25 62.17500
    2    M 52.00 73.11667

## Quando há dados faltantes

Por exemplo, seja o vetor:

``` r
peso <- c(73.5, 71.7, 66.4, 69.2, NA,   70.6, 70.2, 67.1, 69.0, 66.8, 
          68.7, 68.7, 69.0, 69.4, 70.2,   NA,   NA, 68.2, 69.8, 66.8)
```

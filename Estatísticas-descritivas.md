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

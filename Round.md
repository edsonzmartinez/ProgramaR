Funções de arredondamento
================
Edson Zangiacomi Martinez
2024-12-22

## Separação de casas decimais

O R usa o ponto para indicar que o algarismo seguinte pertence aos
decimais.

Se usamos:

``` r
options(OutDec=",")
```

o R passa a usar a vírgula para separar os algarismos decimais:

``` r
x <- c(7.5,5.6,2.1,8.9,5.4,7.7,1.1,7.8)
x
```

`[1] 7,5 5,6 2,1 8,9 5,4 7,7 1,1 7,8`

``` r
options(OutDec=".")
x
```

`[1] 7.5 5.6 2.1 8.9 5.4 7.7 1.1 7.8`

# Funções ceiling() e floor()

`ceiling(x)` Retorna o menor número inteiro maior que x

`floor(x)` Retorna o maior número inteiro menor que x

Exemplos:

``` r
ceiling(6.9)    # 7
ceiling(6.2)    # 7
floor(6.9)      # 6
floor(6.2)      # 6
```

# Função round()

Se `k` é maior ou igual a zero, a função `round(x,digits=k)` arredonda o
valor `x` a para um valor com `k` casas decimais. Exemplos:

``` r
round(5.6892,digits=3)   # 5.689
round(5.6892,3)          # 5.689
round(5.6898,3)          # 5.69
```

Notar que `round(x,digits=0)` retorna o número inteiro mais próximo a
`x`:

``` r
round(5.6898,0)         # 6
round(5.2898,0)         # 5
```

Notar que, se `k` não é declarado em `round(x,digits=k)`, é retornado o
número inteiro mais próximo a `x`, como se `k` fosse igual a zero:

``` r
round(5.6898)          # 6
round(5.2898)          # 5
```

`round(x,digits=-1)` retorna o número inteiro mais próximo a `x`, cujo
último algarismo é zero:

``` r
round(528.98,-1)      # 530
round(522.98,-1)      # 520
```

`round(x,digits=-2)` retorna o número inteiro mais próximo a `x`, cujos
dois últimos algarismos são zeros:

``` r
round(528.98,-2)     # 500
round(588.98,-2)     # 600
```

## Função trunc()

`trunc(x)` arredonda para o valor inteiro mais próximo a `x`, mas em
direção a zero;

Exemplos:

``` r
trunc(528.98)       # 528
trunc(528.18)       # 528
trunc(-528.18)      # -528
trunc(-528.98)      # -528
round(-528.98)      # -529
```

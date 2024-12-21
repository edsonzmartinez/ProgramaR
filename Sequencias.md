Sequências
================
Edson Zangiacomi Martinez
2024-12-21

## Sequências de inteiros usando dois pontos (:)

Os dois pontos : são usados para gerar sequências de números inteiros.
Veja o exemplo:

``` r
1:9
```

\[1\] 1 2 3 4 5 6 7 8 9

Veja também:

``` r
 x <- 23:56    # sequência dos números inteiros de 23 a 56
 y <- 56:20    # sequência decrescente de 56 a 20
 z <- 1:10+5   # sequência decrescente de 6 a 15
```

## A função seq( )

Seja a sequência dos números inteiros, de 15 a 30:

``` r
seq(from=15, to=30)
```

\[1\] 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30

Neste caso, teríamos o mesmo efeito se usássemos:

``` r
15:30
```

\[1\] 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30

Para obtermos o mesmo resultado, podemos escrever simplesmente:

``` r
seq(15,30)
```

\[1\] 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30

O argumento by= é usado para gerar sequências com saltos:

``` r
 seq(from=15, to=30, by=2)
```

Por simplicidade, podemos escrever:

``` r
 seq(15,30,2) 
```

\[1\] 15 17 19 21 23 25 27 29

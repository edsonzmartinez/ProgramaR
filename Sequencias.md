Sequências
================
Edson Zangiacomi Martinez
2024-12-21

## Sequências de inteiros usando dois pontos (:)

Os dois pontos `:` são usados para gerar sequências de números inteiros.
Veja o exemplo:

``` r
1:9
```

    [1] 1 2 3 4 5 6 7 8 9    

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

    [1] 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30

Neste caso, teríamos o mesmo efeito se usássemos:

``` r
15:30
```

    [1] 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30

Para obtermos o mesmo resultado, podemos escrever simplesmente:

``` r
seq(15,30)
```

    [1] 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30

O argumento `by=` é usado para gerar sequências com saltos:

``` r
seq(from=15, to=30, by=2)
```

Por simplicidade, podemos escrever:

``` r
seq(15,30,2) 
```

    [1] 15 17 19 21 23 25 27 29

Observe estes exemplos:

``` r
seq(1.1,6.4)
```

    [1] 1.1 2.1 3.1 4.1 5.1 6.1

``` r
seq(1.1,6.4,0.5)
```

    [1] 1.1 1.6 2.1 2.6 3.1 3.6 4.1 4.6 5.1 5.6 6.1

``` r
seq(0,1,0.1)
```

    [1] 0.0 0.1 0.2 0.3 0.4 0.5 0.6 0.7 0.8 0.9 1.0

``` r
month.abb
```

    [1] "Jan" "Feb" "Mar" "Apr" "May" "Jun" "Jul" "Aug" "Sep" "Oct" "Nov" "Dec"

``` r
month.abb[seq(1,12,3)]
```

    [1] "Jan" "Apr" "Jul" "Oct"

``` r
matrix(seq(1,31,2),nrow=4,byrow=T)
```

          [,1] [,2] [,3] [,4]
    [1,]    1    3    5    7
    [2,]    9   11   13   15
    [3,]   17   19   21   23
    [4,]   25   27   29   31

Se usarmos `seq(from=a, to=b, length=c)`, teremos uma sequência de ‘a’ a
‘b’, com ‘c’ elementos:

``` r
 seq(10,20,length=5)
```

`[1] 10.0 12.5 15.0 17.5 20.0`

``` r
 seq(0,1,length=5)
```

`[1] 0.00 0.25 0.50 0.75 1.00`

## A função sequence( )

``` r
sequence(4:5)   # gera a sequência 1 2 3 4 1 2 3 4 5
sequence(1:5)   # gera a sequência 1 1 2 1 2 3 1 2 3 4 1 2 3 4 5
sequence(5:1)   # gera a sequência 1 2 3 4 5 1 2 3 4 1 2 3 1 2 1
```

## Repetições: a função rep( )

``` r
rep("boi",6)      # retorna "boi" "boi" "boi" "boi" "boi" "boi"
rep(2,5)          # retorna 2 2 2 2 2
rep(1,10)         # retorna o número 1 dez vezes
rep(NA,20)        # retorna NA vinte vezes
rep(1:4,4:1)      # retorna o número 1 quatro vezes, o 2 três vezes...
rep(1:5,each=2)   # retorna duas vezes cada número da sequência de 1 a 5
rep(1:5,2)        # repete a sequência de 1 a 5
```

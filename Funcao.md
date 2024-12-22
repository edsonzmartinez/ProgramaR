Criando funções no R
================
Edson Zangiacomi Martinez
2024-12-22

## Função ifelse()

A sintaxe é `ifelse(expressão,x,y)`.

``` r
# Exemplo 1
nota1 <- 9
nota2 <- 6
ifelse(nota1>nota2,"A nota 1 é maior","A nota 1 não é maior")
```

``` r
# Exemplo 2
a <- c(8,34,8,4,7,5,9,5,3,6,3,6)
b <- ifelse(a %% 2 == 0,"par","ímpar")
```

## Função if()

``` r
nota1 <- 9
nota2 <- 6
if (nota1>nota2) {"A nota 1 é maior"} else
                 {"A nota 1 não é maior"}
```

## Função cat()

``` r
a <- c(8,34,8,4,7,5,9,5,3,6,3,6)
cat(a)
cat(a,"\n")
cat("Arroz","Feijão","\n")
cat("Arroz","Feijão","\n",sep="---")
```

## Criando funções no R

`stop()` interrompe a execução da função e executa uma ação de erro.

``` r
# Exemplo 1
IMC <- function(peso,estatura) {
 if (estatura<=0) { stop("Verifique a estatura") }
 IMC <- peso/(estatura*estatura)
 message("O IMC é ",IMC)
 if (IMC<18.5) { message("Baixo Peso") }         else
 if (IMC<24.9) { message("Peso normal") }        else
 if (IMC<29.9) { message("Pré obesidade") }      else
 if (IMC<34.9) { message("Obesidade grau I") }   else
 if (IMC<39.9) { message("Obesidade grau II") }  else
               { message("Obesidade grau III") }
}
```

Lembrar que, no R, há sempre muitas formas de escrevermos uma função com
o mesmo propósito:

``` r
IMC <- function(peso,estatura) {
 if (estatura<=0) { stop("Verifique a estatura") }
 IMC <- peso/(estatura*estatura)
 message("O IMC é ",IMC)
 a <- cut(IMC,breaks=c(1,18.5,25,30,35,40,80))
 clas <- switch(as.character(a),"(1,18.5]"  = "Baixo Peso",
                                "(18.5,25]" = "Peso normal",
                                "(25,30]"   = "Pré obesidade",
                                "(30,35]"   = "Obesidade grau I",
                                "(35,40]"   = "Obesidade grau II",
                                "(40,80]"   = "Obesidade grau III")
 cat(clas,"\n")
 }
```

``` r
# Exemplo 2
# Usando a função stopifnot()
IMCcalc <- function(peso,estatura) {
 stopifnot(peso>10,peso<200,estatura>1)
 IMC <- peso/(estatura*estatura)     
 return(IMC)
}
```

``` r
a <- IMCcalc(90,1.89)
a
```

O resultado será:

`[1] 25.19526`

``` r
IMCcalc(250,1.34)
```

O resultado será:

`Erro: peso < 200 is not TRUE`

`warning()` gera uma mensagem de advertência, mas não interrompe a
execução da função.

``` r
# Exemplo 3
# Usando a função warning()
IMCcalc <- function(peso,estatura) {
 if (estatura>3) warning("Confira se a estatura está expressa em centímetros")
 IMC <- peso/(estatura*estatura)     
 return(IMC)
}
```

Se usarmos:

``` r
IMCcalc(80,134)
```

O resultado será:

    [1] 0.004455335
    Warning message:
    In IMCcalc(80, 134) : Confira se a estatura está expressa em centímetros

``` r
# Exemplo 4
# Usando a função readline()
IMCcalc <- function() {
 nome <- readline(prompt="Qual o seu nome? ")
 peso <- readline(prompt=paste(nome,", qual o seu peso em quilogramas? "))
 estt <- readline(prompt=paste(nome,", qual a sua estatura em metros? "))
 imc  <- as.numeric(peso)/(as.numeric(estt)^2)
 cat("Olá,",nome,", seu IMC é",round(imc,2),"kg/m2\n")
}
```

``` r
# Exemplo 5
describe <- function(variab,grupo,data,ndec=2) {
 n.d<-aggregate(variab~grupo,data=data,length)[,2]
 m.d<-round(aggregate(variab~grupo,data=data,mean)[,2],ndec)
 sd.d<-round(aggregate(variab~grupo,data=data,sd)[,2],ndec)
 q<-aggregate(variab~grupo,data=data,quantile)
 lab.d<-q[,1]
 med.d<-q[,2][,4]
 q1.d<-q[,2][,3]
 q3.d<-q[,2][,5]
 des<-data.frame(lab.d,n.d,m.d,sd.d,med.d,q1.d,q3.d)
 names(des)<-c("Grupo","n","Média","DP","Mediana","Q1","Q3")
 return(des) }
```

Usando a função:

``` r
describe(dados$idade,dados$sexo,data=dados)
```

Modo e classe:

``` r
a <- describe(dados$peso,dados$sexo,dados)
mode(a)
class(a)
```

A partir da versão 4.1 do R, a função `function()` ganhou um formato
alternativo:

``` r
# Formato original
imc  <- function(peso,estt) peso/estt^2
```

``` r
# Formato alternativo
imc <- \(peso,estt) peso/estt^2
```

Funções criadas com `function()` são objetos do tipo closure:

``` r
typeof(imc)
```

`[1] "closure"`

Execute estas linhas no R e veja o resultado:

``` r
heart <- function(x,sign)
   { heart <- sign*sqrt(1-x*x)+abs(x)^(2/3) }
curve(heart(x,1),xlim=c(-1,1),ylim=c(-1,1.5),col="red",lwd=4)
curve(heart(x,-1),add=T,col="red",lwd=4)
```

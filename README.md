Lubridate
================
Camila Silva
06/04/2021

<img src="https://pbs.twimg.com/media/CQ5yCmvWoAAcTfI.png:large" width="150" />

# Introdução

O pacote `lubridate`, criado por *Garrett Grolemund* e *Hadley Wickham*,
surgiu para lidar com as dificuldades para trabalhar com datas
encontradas no R, que causavam frustração e perda de tempo nas análises.
E assim possibilitou um trabalho muito mais fácil, simplificando a
leitura de datas e extração de informações dessas datas.

------------------------------------------------------------------------

# Instalação

Para instalar o pacote basta baixar do CRAN:

    install.packages("lubridate")

Para carregar pacote:

    library(lubridate)

------------------------------------------------------------------------

# Funções

-   Classe date

Datas no R são tratadas como um tipo especial de objeto, com classe
date:

As funções date() e as\_date() assumem que a ordem segue o padrão da
língua inglesa: ano-mês-dia (ymd).

    date("2015-10-21")
    ## [1] "2015-10-21"
    as_date("2015-10-21")
    ## [1] "2015-10-21"

Se além da data você precisar especificar o horário, basta usar as
funções do tipo ymd\_h(), ymd\_hm(), ymd\_hms(), sendo que também há uma
função para cada formato de dia-mês-ano.  
Existem funções para todas as ordens possíveis: dmy(), mdy(), myd(),
ymd(), ydm() etc.

d = day / dia y = year / ano. m = month / mês

-   Algumas funções

O lubridate traz diversas funções para extrair os componentes de um
objeto da classe date:  
**second()** extrai os segundos.  
**minute()** extrai os minutos.  
**hour()** extrai a hora.  
**wday()** extrai o dia da semana.  
**mday()** extrai o dia do mês.  
**month()** extrai o mês.  
**year()** extrai o ano.  
Você pode usar essas funções para atribuir esses componentes a uma data:

    data <- dmy("01/04/1991")
    data
    ## [1] "1991-04-01"
    hour(data) <- 20
    data
    ## [1] "1991-04-01 20:00:00 UTC"

Também existem funções para extrair a data no instante da execução.

    # Data e horário do dia em que essa página foi editada pela última vez.
    today() 
    ## [1] "2021-03-22"
    now()
    ## [1] "2021-03-22 11:34:07 -03"

-   Operações com datas

O pacote lubridate possui ainda funções para calcular intervalos e fazer
operações aritméticas com datas.

**Intervalos**

Intervalos podem ser salvos em objetos com classe interval.

    inicio <- dmy("01-04-1991")
    evento <- dmy("31-10-1993")
     
    sobrev <- interval(inicio, evento)
    sobrev
    ## [1] 1991-04-01 UTC--1993-10-31 UTC
    class(sobrev)
    ## [1] "Interval"
    ## attr(,"package")
    ## [1] "lubridate"

Você pode verificar se dois intervalos tem intersecção com a função
int\_overlaps().

    # Outra forma de definir um intervalo: o operador %--%
    intervalo_1 <- dmy("01-02-2003") %--% dmy("02-03-2005")  
     
    intervalo_2 <- dmy("04-05-2004") %--% dmy("12-03-2012")  
     
    int_overlaps(intervalo_1, intervalo_2)
    ## [1] TRUE

**Para mais informações sobre o lubridate**  
[visite](https://cran.r-project.org/web/packages/lubridate/vignettes/lubridate.html)

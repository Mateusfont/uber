# DAX do projeto

## % - dia da semana com mais fat

```DAX
var valor = 
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Nome do Dia],
            "valores",
            SUM(Uber2025[Valor])
        ),
        [valores],
        DESC
    ), [valores]
)
return
DIVIDE(
    valor, 
    SUM(Uber2025[Valor]),
    0
)
```

## % de corridas por destino

```DAX
DIVIDE(
    [num - bairro destino com mais corridas],
    [Total corridas cliente],
    0
)
```

## % de corridas por embarque

```DAX
DIVIDE(
    [num - bairro embarque com mais corridas],
    [Total corridas cliente],
    0
)
```

## % de corridas por modelo

```DAX
DIVIDE(
    [num - modelo com mais corridas],
    [Total corridas cliente],
    0
)
```

## % fat destino

```DAX
var fat_destino = 
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Bairro destino],
            "fatdestino",
            SUM(Uber2025[Valor])
        ),
        [fatdestino],
        DESC
    ),
    [fatdestino]
)
return
DIVIDE(
    fat_destino,
    SUM(Uber2025[Valor]),
    0
)
```

## % fat embarque

```DAX
var fat_embarque = 
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Bairro embarque],
            "fatembarque",
            SUM(Uber2025[Valor])
        ),
        [fatembarque],
        DESC
    ),
    [fatembarque]
)
return
DIVIDE(
    fat_embarque,
    SUM(Uber2025[Valor]),
    0
)
```

## % fat marca veiculo

```DAX
var fat_marca = 
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Marca veiculo],
            "fatmarca",
            SUM(Uber2025[Valor])
        ),
        [fatmarca],
        DESC
    ),
    [fatmarca]
)
return
DIVIDE(
    fat_marca,
    SUM(Uber2025[Valor]),
    0
)
```

## % fat modelo

```DAX
var fat_modelo = 
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Modelo],
            "fatmodelo",
            SUM(Uber2025[Valor])
        ),
        [fatmodelo],
        DESC
    ),
    [fatmodelo]
)
return
DIVIDE(
    fat_modelo,
    SUM(Uber2025[Valor]),
    0
)
```

## % representativadade de corridas da marca com mais corridas

```DAX
DIVIDE(
    [num - marca de veiculo com mais corridas],
    [Total corridas cliente],
    0
)
```

## chegadas fora do prazo

```DAX
CALCULATE(
    COUNT(Uber2025[Status chegada]),
    Uber2025[Status chegada] = "Fora do Prazo"
)
```

## chegadas no prazo

```DAX
CALCULATE(
    COUNT(Uber2025[Status chegada]),
    Uber2025[Status chegada] = "No Prazo"
)
```

## corridas homens

```DAX
CALCULATE(
    [Total corridas cliente],
    Uber2025[Sexo cliente] = "Masculino"
)
```

## corridas mulheres

```DAX
CALCULATE(
    [Total corridas cliente],
    Uber2025[Sexo cliente] = "Feminino"
)
```

## dia da semana com mais quantidade de corridas

```DAX
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Nome do Dia],
            "Corridas",
            [Total corridas cliente]
        ),
        [Corridas],
        DESC
    ), Uber2025[Nome do Dia]
)
```

## GIF_HTML

```DAX
"<img src='https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExdDlpZXViMDVmMDl6OHpzYXh1am5rdmd2eDM2MXBwbXA5dzFxZWY5aiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/1zRfp0Jwsag4yPekP4/giphy.gif' width='1300' />"
```

## hora da semana com fat

```DAX
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Hora],
            "valores",
            SUM(Uber2025[Valor])
        ),
        [valores],
        DESC
    ),
    Uber2025[Hora]
)
```

## hora da semana com maior quantidade de corridas

```DAX
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Hora],
            "Corridas",
            [Total corridas cliente]
        ),
        [Corridas],
        DESC
    ),
    Uber2025[Hora]
)
```

## hora de maior pico

```DAX
CALCULATE(
    TOPN(
    [Total corridas cliente],
    Uber2025,
    1,ASC
    ),
    Uber2025[Hora]
)
```

## num - bairro destino com mais corridas

```DAX
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Bairro destino],
            "corridasdestino",
            [Total corridas cliente]
        ),
        [corridasdestino],
        DESC
    ),
    [corridasdestino]
)
```

## num - bairro embarque com mais corridas

```DAX
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Bairro embarque],
            "totalkmbairroembarque",
            SUM(Uber2025[km rodado])
        ),
        [totalkmbairroembarque],
        DESC
    ),
    [totalkmbairroembarque]
)
```

## num - marca de veiculo com mais corridas

```DAX
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Marca veiculo],
            "totalcorridas",
            [Total corridas cliente]
        ),
        [totalcorridas],
        DESC),
        [totalcorridas]
        )
```

## num - modelo com mais corridas

```DAX
MAXX(
    TOPN(
        1, 
        SUMMARIZE(
            Uber2025,
            Uber2025[Modelo],
            "corridasmodelo",
            [Total corridas cliente]
        ),
        [corridasmodelo],
        DESC
    ),
    [corridasmodelo]
)
```

## qtd - cancelamentos homem

```DAX
CALCULATE(
    [Corridas homens],
    Uber2025[status] = "cancelada"
)
```

## qtd - cancelamentos mulher

```DAX
CALCULATE(
    [Corridas mulheres],
    Uber2025[status] = "cancelada"
)
```

## total corridas cliente

```DAX
COUNT(Uber2025[Id cliente])
--contagem, porque estamos contando quantas viagens um cliente fez, mesmo que tenha feita mais que uma
```

## total corridas unicas por cliente

```DAX
DISTINCTCOUNT(Uber2025[Id cliente])
```

## txt - bairro destino com mais corridas

```DAX
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Bairro destino],
            "corridasbairrodestino",
            [Total corridas cliente]
        ),
        [corridasbairrodestino],
        DESC),
        Uber2025[Bairro destino]
)
```

## txt - bairro embarque com mais corridas

```DAX
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Bairro embarque],
            "corridasbairroemabrque",
            [Total corridas cliente]
        ),
        [corridasbairroemabrque],
        DESC),
        Uber2025[Bairro embarque]
)
```

## txt - bairro embarque valores

```DAX
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Bairro embarque],
            "valoresbairroemabrque",
            SUM(Uber2025[Valor])
        ),
        [valoresbairroemabrque],
        DESC),
        Uber2025[Bairro embarque]
)
```

## txt - dia da semana com mais fat

```DAX
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Nome do Dia],
            "valores",
            SUM(Uber2025[Valor])
        ),
        [valores],
        DESC
    ), Uber2025[Nome do Dia]
)
```

## txt - fat por destino

```DAX
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Bairro destino],
            "fatdestino",
            SUM(Uber2025[Valor])
        ),
        [fatdestino],
        DESC),
        Uber2025[Bairro destino]
)
```

## txt - fat por embarque

```DAX
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Bairro embarque],
            "fatembarque",
            SUM(Uber2025[Valor])
        ),
        [fatembarque],
        DESC),
        Uber2025[Bairro embarque]
)
```

## txt - fat por modelo

```DAX
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Modelo],
            "fatmodelo",
            SUM(Uber2025[Valor])
        ),
        [fatmodelo],
        DESC),
        Uber2025[Modelo]
)
```

## txt - marca com maior faturamento

```DAX
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Marca veiculo],
            "marcafaturamento",
            SUM(Uber2025[Valor])
        ),
        [marcafaturamento],
        DESC
    ),
    Uber2025[Marca veiculo]
)
```

## txt - marca de veiculo com mais corridas

```DAX
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Marca veiculo],
            "totalcorridas",
            [Total corridas cliente]
        ),
        [totalcorridas],
        DESC),
        Uber2025[Marca veiculo]
        )
```

## txt - marca de veiculo valores

```DAX
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Marca veiculo],
            "totalvalor",
            SUM(Uber2025[Valor])
        ),
        [totalvalor],
        DESC),
        Uber2025[Marca veiculo]
        )
```

## txt - modelo com mais corridas

```DAX
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Modelo],
            "corridasmodelo",
            [Total corridas cliente]
        ),
        [corridasmodelo],
        DESC),
        Uber2025[Modelo]
)
```

## txt - modelo valores

```DAX
MAXX(
    TOPN(
        1,
        SUMMARIZE(
            Uber2025,
            Uber2025[Modelo],
            "valoresmodelo",
            SUM(Uber2025[Valor])
        ),
        [valoresmodelo],
        DESC),
        Uber2025[Modelo]
)
```


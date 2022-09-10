[![author](https://img.shields.io/badge/author-gabrielfreitas-purple.svg)](https://www.linkedin.com/in/gabrielsfreitas/)

<p align="center">
  <img src="banner.png" >
</p>

# Portal Wakanda
<sub>*Esteira de homologação* dos projetos do Centro de Desenvolvimento de Dispositivos Brasil | Vivo - Telefônica Brasil</sub>

<br/>
Projeto com o principal objetivo de facilitar a visualização de todo o processo de homologação, desde a chegada de um firmware até sua fase de execução dos scripts de massificação. Abaixo é possível observar como os dados se relacionam através da sua topologia.

Antes da existência do projeto, o CDD tinha os mesmos dados, mas estavam armazenados em fontes diferentes e não era intuitivo, o que gerava falha na comunicação entre as partes interessadas.

<br/>
## Topologia
<p align="center">
  <img src="topologia.png" >
</p>

## Contexto:
Antes da existência do projeto, o CDD tinha os mesmos dados, mas estavam armazenados em fontes diferentes e não era intuitivo, o que gerava falha na comunicação entre as partes interessadas.

Para facilitar a comunicação e projetar o que está acontecendo com cada projeto, foi feito um portal reunindo todas as informações da maneira mais intuitiva possível. Também foi elaborado um formulário para que toda equipe possa sugerir o que pode melhorar ou acrescentar alguma informação.

<br/>

## Metodologia página principal:

Para tornar a leitura portal mais intuitiva, foram utilizados faróis para sinalizar o status de cada fase de um determinado dispositivo, ou seja, pode sinalizar uma data futura, uma aprovação ou até mesmo se está em atraso ou se um firmware foi reprovado. É importante ressaltar que para cada processo (seja ele na fase de laboratório ou piloto) há essas mesmas condições.

A lógica por trás de todas essas cores funciona da seguinte maneira:
* Aprovação / chegada de um firmware (farol verde): quando a data do firmware ou processo (lab ou piloto) for menor ou igual a data de hoje;
* Data futura (farol branco): quando a data de chegada de algum firmware ou processo é uma data maior que a data de hoje;
* Em andamento (farol azul): significa que algum processo está em andamento (seja de laboratório ou piloto). A lógica é que se a data atual está entre as datas de início e término do respectivo processo;
* Reprovado (farol vermelho): é quando o firmware de algum dispositivo é reprovado em alguma fase de homologação;
* Em atraso (farol amarelo): um firmware ou processo de homologação estava previsto para uma determinada data, mas houve um atraso, seja para a entrega ou início de alguma fase.

<br/>

* OBS.I: é possível interferir em cada fase, ou seja, mesmo que algum processo esteja com o status em andamento - ou qualquer outro -, é possível alterar para um diferente do atual (reprovado, atraso, etc.)
* OBS.II: se alguma das fases for reprovada, todas as fases subsequentes não irão mostrar as datas, já que não há lógica em projetar uma data - mesmo que seja futura -, para um firmware que foi reprovado em uma etapa anterior.

<br/>
<p align="center">
  <img src="view_hgu.png" >
</p>

<br/>
<details><summary>Exemplo de código utilizado para uma das fases de piloto (FUT):</summary>
<p>

  ```
COND_IFUT = 
var DataHoje = TODAY()
var DataInicioFUT = MAX('Principal'[INICIO_FUT])
var DataTerminoFUT = MAX('Principal'[TERMINO_FUT])
var AtrasoFUT = MAX(Principal[ATRASO_FUT])
var AprovadoFUT = MAX(Principal[APROVADO_FUT])
var AprovadoHomolog = MAX(Principal[APROVADO_HOMOLOG])

var RESULTADO = 
    SWITCH(TRUE(),
    AprovadoHomolog = 1, "-",

    AtrasoFUT = 2, UPPER(FORMAT(DataInicioFUT, "DDMMM")) & "  " & "🟡", //está em atraso
    AprovadoFUT = 1 && AprovadoFUT <> BLANK(), UPPER(FORMAT(DataInicioFUT, "DDMMM")) & "  " & "🔴", //está reprovado
    DataInicioFUT <= DataHoje && DataHoje <= DataTerminoFUT, UPPER(FORMAT(DataInicioFUT, "DDMMM")) & "  " & "🔵", // homologação está em andamento
    DataTerminoFUT < DataHoje && DataTerminoFUT <> BLANK(), UPPER(FORMAT(DataInicioFUT, "DDMMM")) & "  " & "🟢", // FUT concluído
    DataInicioFUT > DataHoje, UPPER(FORMAT(DataInicioFUT, "DDMMM")) & "  " & "⚪", // é uma data futura

    ISBLANK(DataInicioFUT), "-" // se termino FUT não for preenchido
    )
    return RESULTADO
```
  
</p>
</details>
<br/>

Para cada projeto, há uma página específica com todas as informações a respeito dele. Exemplos de informações específica são:
* Quantidade de tickets abertos por nível de criticidade;
* Detalhamento dos tickets level 1;
* Escopo do próximo firmware;
* Data de término de cada etapa de homologação;
* Pontos relevantes;
* Quantidade de dispositivos na planta;
* Porcentagem de atualização do firmware em produção;
* Correções ou novas implementações do firmware candidate.

<br/>

<p align="center">
  <img src="view_projeto.png" >
</p>

[![author](https://img.shields.io/badge/author-gabrielfreitas-red.svg)](https://www.linkedin.com/in/gabrielsfreitas/)

<p align="center">
  <img src="banner.png" >
</p>

# Portal Wakanda
<sub>*Esteira de homologação* dos projetos do Centro de Desenvolvimento de Dispositivos Brasil | Vivo - Telefônica Brasil</sub>

Projeto com o principal objetivo de facilitar a visualização de todo o processo de homologação, desde a chegada de um firmware até sua fase de execução dos scripts de massificação. Abaixo é possível observar como os dados se relacionam através da sua topologia.

Antes da existência do projeto, o CDD tinha os mesmos dados, mas estavam armazenados em fontes diferentes e não era intuitivo, o que gerava falha na comunicação entre as partes interessadas.

## Topologia
<p align="center">
  <img src="topologia.png" >
</p>

## Contexto:
Antes da existência do projeto, o CDD tinha os mesmos dados, mas estavam armazenados em fontes diferentes e não era intuitivo, o que gerava falha na comunicação entre as partes interessadas.

Para facilitar a comunicação e projetar o que está acontecendo com cada projeto, foi feito um portal reunindo todas as informações da maneira mais intuitiva possível. Também foi elaborado um formulário para que toda equipe possa sugerir o que pode melhorar ou acrescentar alguma informação.

## Metodologia página principal:

Para tornar a leitura portal mais intuitiva, foram utilizados faróis para sinalizar o status de cada fase de um determinado dispositivo, ou seja, pode sinalizar uma data futura, uma aprovação ou até mesmo se está em atraso ou se um firmware foi reprovado. É importante ressaltar que para cada processo (seja ele na fase de laboratório ou piloto) há essas mesmas condições.

A lógica por trás de todas essas cores funciona da seguinte maneira:
* Aprovação / chegada de um firmware (farol verde): quando a data do firmware ou processo (lab ou piloto) for menor ou igual a data de hoje;
* Data futura (farol branco): quando a data de chegada de algum firmware ou processo é uma data maior que a data de hoje;
* Em andamento (farol azul): significa que algum processo está em andamento (seja de laboratório ou piloto). A lógica é que se a data atual está entre as datas de início e término do respectivo processo;
* Reprovado (farol vermelho): é quando o firmware de algum dispositivo é reprovado em alguma fase de homologação;
* Em atraso (farol amarelo): um firmware ou processo de homologação estava previsto para uma determinada data, mas houve um atraso, seja para a entrega ou início de alguma fase.

* OBS.: é possível interferir em cada fase, ou seja, mesmo que algum processo esteja com o status em andamento - ou qualquer outro -, é possível alterar para um diferente do atual (reprovado, atraso, etc.)

<p align="center">
  <img src="view_hgu.png" >
</p>



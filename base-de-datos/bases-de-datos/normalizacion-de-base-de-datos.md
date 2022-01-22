# Normalización de base de datos

| Forma normal | Definido por                    | In                                                      | Breve definición       |                                                                                                                                                                                                                                                                       |
| ------------ | ------------------------------- | ------------------------------------------------------- | ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ﻿1NF         | ﻿Primera forma normal           | ﻿Dos versiones: ﻿E.F. Codd ﻿(1970), ﻿C.J. fecha ﻿(2003) | ﻿1970\[1] ﻿y 2003\[10] | ﻿El ﻿dominio ﻿de cada uno ﻿atributo ﻿contiene sólo ﻿atómico ﻿los valores y el valor de cada atributo contiene sólo un único valor de dicho dominio.\[11]                                                                                                              |
| ﻿2NF         | ﻿Segunda forma normal           | ﻿E.F. Codd                                              | ﻿1971\[2]              | ﻿Ningún atributo de primera en la tabla es ﻿funcionalmente dependientes ﻿en un ﻿subconjunto adecuado ﻿de cualquier ﻿clave de candidato                                                                                                                                |
| ﻿3NF         | ﻿Tercera forma normal           | ﻿Dos versiones: ﻿E.F. Codd ﻿(1971), C. Zaniolo (1982)   | ﻿1971\[2] ﻿y 1982\[12] | ﻿Cada atributo de primera es no transitivamente dependiente de cada clave candidata en la tabla. Se eliminan los atributos que no contribuyen a la descripción de la clave primaria de la tabla. En otras palabras, no está permitido ninguna dependencia transitiva. |
| ﻿EKNF        | ﻿Forma Normal de clave primaria | ﻿C. Zaniolo                                             | ﻿1982\[12]             | ﻿Cada dependencia funcional no triviales en la tabla es la dependencia de un atributo clave primaria o dependencia de un superkey                                                                                                                                     |
| ﻿BCNF        | ﻿Forma normal de Boyce-Codd     | ﻿Boyce ﻿y ﻿E.F. Codd                                    | ﻿1974\[13]             | ﻿Cada dependencia funcional no triviales en la tabla es una dependencia en una ﻿Superkey                                                                                                                                                                              |
| ﻿4NF         | ﻿Cuarta forma normal            | ﻿Ronald Fagin                                           | ﻿1977\[14]             | ﻿Cada no trivial ﻿dependencia multivalor ﻿en la tabla es una dependencia de un superkey                                                                                                                                                                               |
| ﻿5NF         | ﻿Quinta forma normal            | ﻿Ronald Fagin                                           | ﻿1979\[15]             | ﻿Cada no trivial ﻿Únete a dependencia ﻿en la tabla está implícito por los superkeys de la tabla                                                                                                                                                                       |
| ﻿DKNF        | ﻿Forma normal dominio/clave     | ﻿Ronald Fagin                                           | ﻿1981\[16]             | ﻿Cada restricción sobre la mesa es un ﻿consecuencia lógica ﻿de las limitaciones de dominio y restricciones de clave de la tabla                                                                                                                                       |
| ﻿6NF         | ﻿Sexta forma normal             | ﻿C.J. fecha, ﻿Hugh Darwen﻿, y ﻿Nikos Lorentzos          | ﻿2002\[17]             | ﻿Tabla no características dependencias unirse no trivial en absoluto (con referencia a operador de unir generalizada)                                                                                                                                                 |

![](<../../.gitbook/assets/image (30).png>)

{% embed url="https://es.wikipedia.org/wiki/Normalizaci%C3%B3n_de_bases_de_datos#Forma_normal_de_Boyce-Codd:(FNBC)" %}

{% embed url="https://en.wikipedia.org/wiki/Database_normalization" %}

## Primera forma normal (1NF, 1FN)

{% embed url="https://es.wikipedia.org/wiki/Primera_forma_normal" %}

![](<../../.gitbook/assets/image (29).png>)

El anterior diseño rompe la primera forma normal por que los tres campos del teléfono tienen el mismo dominio por tal razón existe datos redundantes.

Soluciones: es hace una relación uno a muchos

![](<../../.gitbook/assets/image (33).png>)

## Segunda forma normal (2FN, 2NF)

{% embed url="https://es.wikipedia.org/wiki/Segunda_forma_normal" %}

![](<../../.gitbook/assets/image (32).png>)

nombres y apellidos dependen totalmente de (numero\__documento y tipo_\_documento) y no parcialmente.

## Tercera Forma Normal (3NF, 3FN)

{% embed url="https://es.wikipedia.org/wiki/Tercera_forma_normal" %}

![](<../../.gitbook/assets/image (28).png>)

Se rompe la tercera forma normal por que nombres y apellidos dependen funcionalmente de numero de documento y tipo de documento, además estos dos dependen transitivamente de el id.

## Forma Normal de Llave Elemental (EKNF)

{% embed url="https://en.wikipedia.org/wiki/Elementary_key_normal_form" %}

## Forma normal de Boyce-Codd

{% embed url="https://es.wikipedia.org/wiki/Forma_normal_de_Boyce-Codd" %}

## Cuarta forma normal <a href="firstheading" id="firstheading"></a>

{% embed url="https://es.wikipedia.org/wiki/Cuarta_forma_normal" %}

Considere el siguiente ejemplo: que no cumple la 4FN

| Permutaciones de envíos de pizzas |                   |               |
| --------------------------------- | ----------------- | ------------- |
| Restaurante                       | Variedad de Pizza | Área de envío |
| Vincenzo's Pizza                  | Corteza gruesa    | Springfield   |
| Vincenzo's Pizza                  | Corteza gruesa    | Shelbyville   |
| Vincenzo's Pizza                  | Corteza fina      | Springfield   |
| Vincenzo's Pizza                  | Corteza fina      | Shelbyville   |
| Elite Pizza                       | Corteza fina      | Capital City  |
| Elite Pizza                       | Corteza rellena   | Capital City  |
| A1 Pizza                          | Corteza gruesa    | Springfield   |
| A1 Pizza                          | Corteza gruesa    | Shelbyville   |
| A1 Pizza                          | Corteza gruesa    | Capital City  |
| A1 Pizza                          | Corteza rellena   | Springfield   |
| A1 Pizza                          | Corteza rellena   | Shelbyville   |
| A1 Pizza                          | Corteza rellena   | Capital City  |

![](<../../.gitbook/assets/image (31).png>)

se arregla de de la siguiente forma:

Para satisfacer la 4FN, debemos poner los hechos sobre las variedades de pizza ofrecidas en una tabla diferente de los hechos sobre áreas de envío:

![](<../../.gitbook/assets/image (34).png>)

En contraste, si las variedades de pizza ofrecidas por un restaurante a veces variaran de un área de envío a otra, la tabla original de la tres columnas satisfaría la 4FN.

![](<../../.gitbook/assets/image (27).png>)

## Forma normal de tupla esencial (Essential Tuple Normal Form, ETNF)

{% embed url="https://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.309.2195&rep=rep1&type=pdf#:~:text=Relational%20Databases,-Hugh%20Darwen&text=ETNF%20lies%20strictly%20between%20fourth,in%20eliminating%20redundancy%20of%20tuples." %}

## Forma normal de redundancia libre (redundancy free normal form, RFNF)

Definition (redundancy per Vincent): Let relation r be a value of relvar R, let t be a tuple in r, and let v be an attribute value within t. Then that occurrence of v within t is redundant in r, and R is subject to redundancy, if and only if replacing that occurrence of v by an occurrence of v′ (v′ ≠ v), while leaving everything else unchanged, causes some dependency12 of R to be violated.

## Forma Normal de SuperClave (Superkey Normal Form, SKNF)

Definition (superkey normal form): Relvar R is in superkey normal form (SKNF) if and only if, for every irreducible JD ☼{X1,...,Xn} that holds in R, each of X1, ..., Xn is a superkey for R.

## Quinta forma normal

{% embed url="https://es.wikipedia.org/wiki/Quinta_forma_normal" %}

## Sexta Forma Normal (6FN, 6NF)

{% embed url="https://en.wikipedia.org/wiki/Database_normalization#Satisfying_6NF" %}

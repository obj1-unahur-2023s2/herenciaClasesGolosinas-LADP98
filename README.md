# Golosinas - clases y herencia

En este ejercicio continuamos trabajando sobre el ejemplo de Mariano y las golosinas. Le agregamos algunos requerimientos adicionales que nos van a ayudar a practicar con los conceptos de _clase_ y _herencia_.

## Muchas golosinas

A partir de la solución que ya está en el repositorio, hacer las modificaciones necesarias para que Mariano pueda comprar varios bombones, chocolatines, caramelos, alfajores, chupetines, obleas, golosinas bañadas y/o pastillas tuttifruti.

Resolver adecuadamente los casos en los que hay que pasar parámetros en la inicialización (el peso del chocolatín y la golosina a bañar).

<br>


### Bañar Golosina

Hacer que Mariano entienda el mensaje `baniar(unaGolosina)`. 
El método construye una nueva golosina bañada y la agrega a la colección de las golosinas que compró Mariano.

Pensar, haciendo un diagrama de objetos, qué pasa si:
1. la golosina ya era parte de la colección.
1. se baña una golosina ya bañada.

<br>

## Más variantes de golosinas 

<!--- herencia de clase concreta con redefinicion --->

### Bombones duros
Los bombones duros son bombones (tienen las mismas reglas para el precio y gusto) pero cuando reciben un mordisco, en lugar de comportarse como el resto de los bombones, pierden 1 gramo.

Además, de los bombones duros queremos poder consultar el _grado de dureza_, que es: 3 si pesa más de 12 gramos, 2 si pesa entre 8 y 12 gramos, 1 si pesa menos de 8 gramos.

Indicar en cuál clase se encuentra el método que se ejecuta en cada caso, detallando el recorrido que realiza el method lookup.

```
var bombon = new Bombon() 
bombon.mordisco() 
bombon.peso() 
bombon = new BombonDuro() 
bombon.mordisco() 
bombon.peso() 
```

<!--- herencia con redefinicion y super para hacer otra cosa --->

### Caramelos de distintos sabores
Hacer que pueda haber caramelos de cualquier sabor. Cuando se construye el caramelo se le indica de que sabor es.

### Caramelos con corazón de chocolate (Rellenos)
Los caramelos con corazón de chocolate son caramelos que al recibir un mordisco, además de comportarse como todos los caramelos cambian su sabor a chocolate

Además, su precio es de un peso más que el de los caramelos comunes.

Indicar en cuál clase se encuentra el método que se ejecuta en cada caso, detallando el recorrido que realiza el method lookup.	

```
var caramelo = new Caramelo() 
caramelo.mordisco() 
caramelo.peso() 
caramelo.sabor() 
caramelo = new CarameloRelleno() 
caramelo.mordisco() 
caramelo.peso() 
caramelo.sabor()
```

<!--- herencia con redefinicion y super para modificar el resultado. Ademas tiene una variable en la subclase --->

### Obleas Crujientes
Las obleas crujientes son como todas las obleas y cuando reciben un mordisco 
pierden el peso que pierden todas las obleas (50% si el peso es mayor a 70g o 25% si es menor). Pero, en los primeros 3 mordiscos pierde 3 gramos adicionales, esto hacerlo _después_ de la cuenta anterior.

A cada oblea crujiente se le tiene que poder consultar si _está débil_, esto es cierto si le dieron más de 3 mordiscos.
 
Indicar en cuál clase se encuentra el método que se ejecuta en cada caso, detallando el recorrido que realiza el method lookup.

```
var oblea = new Oblea() 
oblea.mordisco() 
oblea.peso() 
oblea = new ObleaCrujiente() 
oblea.mordisco() 
oblea.peso() 
```

### Chocolatines VIP y Chocolatines Premium
Los chocolatines VIP, son como todos los chocolatines, pero se guardan en la  heladera de Mariano, que aporta un coeficiente de humedad (un número entre 0 y 1). Este coeficiente está involucrado para el cálculo del peso: El peso de un chocolatin VIP es el peso que tendría un Chocolatín cualquiera: 
`(pesoInicial - gramosConsumidos)` multiplicado por  `1 + humedad`.  
Por ejemplo, si el peso inicial de un chocolatín es 200 gramos, se consumieron 50, y la humedad es 0.2, entonces el peso es 150 * 1.2 = 180 gramos.

Los chocolatines Premium son un tipo especial de chocolatines VIP que vienen con una cobertura especial que los hace más resistentes a la humedad. Por lo tanto, La _humedad_ en estos chocolatines es la mitad de la humedad de los chocolatines VIP.

Indicar en cuál clase se encuentra el método que se ejecuta en cada caso, detallando el recorrido que realiza el method lookup.

```
var chocolatin = new Chocolatin() 
chocolatin.peso() 
chocolatin = new ChocolatinVIP() 
chocolatin.peso() 
chocolatin = new ChocolatinPremium() 
chocolatin.peso() 
```
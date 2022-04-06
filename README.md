# Practica-de-Powershell-Scripts
## Tal y como hemos hecho en anteriores tareas se trata de analizar y documentar los siguientes scripts de powershell.

Lo primero que debemos hacer para poder ejecutar estos scripts es asegurarnos de que la política de ejecución no sea restringida. 
Para ver que política tenemos, ejecutaremos el siguiente comando :
```
Get-ExecutionPolicy
```
Vemos que es ``restricted`` , para revertir esto, ejecutaremos
```
Set-ExecutionPolicy
ExecutionPolicy: unrestricted
```
<img width="924" alt="Captura" src="https://user-images.githubusercontent.com/91699247/162061436-9ada94ac-3b16-4b3f-bd2b-b8dd93ece6a5.PNG">

Una vez cambiada la política de ejecución podemos ejecutar los scripts, para llevar a cabo esta acción podemos usar el comando ``ise``,  el cual nos llevará al entorno gráfico de powershell 

## Script 1
La función de este script es mostrar el valor de las diferentes variables number.


Mediante la primera instrucción, inicializamos la variable number con el valor especificado y con el segundo, mostramos por pantalla el valor de este numero junto con un string
```
$number = 1
Write-Host "The number is: " $number
```
<img width="375" alt="Captura1" src="https://user-images.githubusercontent.com/91699247/162063214-5520139c-ac2f-4e09-ab11-38eb4031a3d4.PNG">


## Script 2
El resultado de este script es la salida por pantalla de diferentes strings a partir de varios bucles.

Esta instrucción genera un bucle mediante el cual se imprimirá por pantalla la palabra hello mientras la varibale counter sea menor que la variable repeat, cada vez que se ejecute el bucle, counter incrementerá en uno. 
```
[int]$repeat = 5

for ($counter = 0; $counter -lt $repeat; $counter++) {
    Write-Host "hello"
} 
```

El siguiente bucle realiza la misma función que el anterior, imprimirá el string por pantalla mientras counter sea menor que repeat. Una vez mostrado por pantalla, incrementa en uno la variable counter.
```
[int]$repeat = 5
[int]$counter = 0

while ($counter -lt $repeat) {
    Write-Host "hello"
    $counter++
}
```
Este otro bucle , a diferencia de los anteriores , imprimirá el texto previamente a la comprobación de si counter es menor que repeat
```
[int]$repeat = 5
[int]$counter = 0
do {
    Write-Host "hello"
    $counter++
}
while ($counter -lt $repeat) 
```
<img width="385" alt="Captura4" src="https://user-images.githubusercontent.com/91699247/162068707-3e495938-8106-444d-a562-2b0bd9430ebc.PNG">


El siguiente bucle, muestra por pantalla y cada vez en una línea nueva, cada uno de los carácteres de la lista constituida por los caracteres por los que está formado el string
```
[string]$stringOfCharacters = "PowerShell for Beginners"

foreach ($character in $stringOfCharacters.ToCharArray()) {
    Write-Host $character
} 
```
El último bucle, muestra el mismo resultado que el anterior, pero a diferencia del otro, este bucle se encarga de mostrar por pantalla cada uno de los objetos que forman la lista de caracteres del string 
```
[string]$stringOfCharacters = "PowerShell for Beginners"
$stringOfCharacters.ToCharArray() | ForEach-Object { Write-Host "$_" }
```
<img width="397" alt="Captura3" src="https://user-images.githubusercontent.com/91699247/162068753-cfdf60d5-01fd-4fa7-a868-204ca226179d.PNG">



## Script 3
Este script se basa en el funcionamiento de las equivalencias.

En las dos primeras instrucciones, si el primer elemento es igual al segundo, se muestra por pantalla que estos dos son iguales.
```
if (4 -eq 4) {
    Write-Host "4 is equal to 4"
}

if ("hello" -eq "hello") {
    Write-Host "Both strings are equal to each other"
} 
```
En las dos siguientes, dependiendo de si los elementos son iguales o no, mostrará por pantalla un mensajo u otro.
```
[int]$x = 10
[int]$y = 10

if ($x -eq $y) {
    Write-Host "the x and y variables are equal to each other"
}
else {
    Write-Host "The x and y variables are NOT equal to each other"
}


$yourName = "Ian"

if ($yourName -eq "Ian") {
    Write-Host "Hay my name is Ian too!"
}
else {
    Write-Host "Hi $yourName, nice to meet you!"
}

```

A continuación, la salida del mensaje se basa en la entrada de texto del usuario y en los diferentes usos de los condicionales: si el usuario introduce un string igual a left muestra un mensaje, si introduce uno igual a right muestra un mensaje diferente y si por el contrario no introduce ninguno de los dos strings anteriores, muestra un mensaje completamente distinto.
```
$playerInput = Read-Host -Prompt "You walk into a room with two doorways. One to the left and one to the right. Type 'left' or 'Right' to walk through one of the doors."

if ($playerInput -eq "left") {
    Write-Host "Player typed left"
}
elseif ($playerInput -eq "right") {
    Write-Host "Player typed right"
}
else {
    Write-Host "Player typed something we didn't understand"
}
```

Por último, se puede ver el funcionamiento del switch, el cual ejecuta la instrucción contenida en el caso que coincida con el valor de la variable especificada.

En este caso, se definen dos variables y si el valor de esta variable es el mismo que alguno de los casos que se encuentran dentro del switch, se ejecuta la instrucción contenida en dicho caso. Si este valor no coincide con ninguno de los casos, ejecutará la instrucción del default.
```
[int]$number = 2
switch ($number) {
    1 { "The number is one" }
    2 { "The number is two" }
    default { "I dont know what the number is" }
}


[string]$favouriteColour = "Blue"
switch ($favouriteColour) {
    "Red" {
        "Your favourite colour is Red"
        "I like red too."
    }
 
    "Blue" {
        "Your favourite colour is Blue"
        "I like Blue too."
    }
 
    default { "I dont recognise that colour" }
}
```
<img width="717" alt="Captura88" src="https://user-images.githubusercontent.com/91699247/162073108-c45acf91-6855-4209-bda9-9d1be4ac60b0.PNG">

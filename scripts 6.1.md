## 1. Recibir un número entero por teclado y decir si es positivo.
```bash
#!/bin/bash

echo "Ingresa un número entero: "
read numero

if [ $numero -gt 0 ]; then
  echo "El número $numero es positivo."
elif [ $numero -eq 0 ]; then
  echo "El número $numero es cero."
else
  echo "El número $numero es negativo."
fi

```
## 2 Recibir un número entero por teclado y decir si es negativo.
```bash
#!/bin/bash

echo "Introduce un número entero:"
read numero

if [ $numero -lt 0 ]
then
    echo "El número es negativo."
else
    echo "El número no es negativo."
fi
```
## 3 Recibir un número entero por teclado y decir si es igual a cero.
```bash
#!/bin/bash

echo "Introduce un número entero:"
read numero

if [ $numero -eq 0 ]
then
    echo "El número es igual a cero."
else
    echo "El número no es igual a cero."
fi
```
## 4 Recibir un numero entero por teclado y decir si es positivo, negativo o cero.
```bash
#!/bin/bash

echo "Introduce un número entero:"
read numero

if [ $numero -eq 0 ]
then
    echo "El número es cero."
elif [ $numero -gt 0 ]
then
    echo "El número es positivo."
else
    echo "El número es negativo."
fi
```
## 5 Comprobar si el número de parámetros introducido es igual a 3, en el caso de que sea otro número mostrará un mensaje de error por pantalla.
```bash
#!/bin/bash

if [ $# -eq 3 ]
then
    echo "El número de parámetros introducido es igual a 3."
else
    echo "Error: Debe introducir 3 parámetros."
fi
```
## 6 Recibir dos números por parámetros y lo suma. En caso de que el número de parámetros sea incorrecto mostrará un mensaje de error.
```bash
#!/bin/bash
if [ $# -eq 2 ]
then
    num1=$1
    num2=$2
    suma=$((num1 + num2))
    echo "La suma de $num1 y $num2 es igual a $suma."
else
    echo "Error: Debe introducir dos parámetros numéricos."
fi
```
## 7 Recibir 3 parámetros. En el caso de que reciba un número diferente mostrará un mensaje de error. Los dos primeros serán dos números y el tercero será uno de los siguientes símbolos “+” “-“ “x” “/”, dependiendo del tercer parámetro introducido 
```bash
#!/bin/bashç
if [ "$#" -ne 3 ]; then
  echo "Error: este script necesita 3 parámetros."
  exit 1
fi

# Verificar si el tercer parámetro es uno de los operadores válidos
if [[ "$3" != "+" && "$3" != "-" && "$3" != "x" && "$3" != "/" ]]; then
  echo "Error: el tercer parámetro debe ser uno de los siguientes símbolos: +, -, x, /"
  exit 1
fi

# Verificar si los dos primeros parámetros son números
if ! [[ "$1" =~ ^[0-9]+$ ]] || ! [[ "$2" =~ ^[0-9]+$ ]]; then
  echo "Error: los dos primeros parámetros deben ser números enteros."
  exit 1
fi

# Realizar la operación correspondiente
if [ "$3" = "+" ]; then
  resultado=$(( $1 + $2 ))
elif [ "$3" = "-" ]; then
  resultado=$(( $1 - $2 ))
elif [ "$3" = "x" ]; then
  resultado=$(( $1 * $2 ))
else # Si es el operador "/"
  resultado=$(( $1 / $2 ))
fi

# Mostrar el resultado
echo "El resultado de la operación es: $resultado"
```
## 8 Recibir la ruta de un fichero e indicar si existe
```bash
if [ "$#" -ne 1 ]; then
  echo "Error: este script necesita una ruta de archivo como parámetro."
  exit 1
fi

# Verificar si el archivo existe
if [ -e "$1" ]; then
  echo "El archivo $1 existe."
else
  echo "El archivo $1 no existe."
fi
```
## 9 Recibir la ruta de un fichero e indicar si es un directorio o un fichero
```bash
#!/bin/bash
if [ "$#" -ne 1 ]; then
  echo "Error: este script necesita una ruta de archivo como parámetro."
  exit 1
fi

# Verificar si el archivo es un directorio
if [ -d "$1" ]; then
  echo "El archivo $1 es un directorio."
# Verificar si el archivo es un archivo regular
elif [ -f "$1" ]; then
  echo "El archivo $1 es un archivo regular."
else
  echo "El archivo $1 no existe o no se puede determinar su tipo."
fi
```
## 10 Recibir la ruta de un fichero e indicar los permisos que tiene (escritura, lectura, ejecución)
```bash
#!/bin/bash

# Verificar si se proporcionó un parámetro
if [ "$#" -ne 1 ]; then
  echo "Error: este script necesita una ruta de archivo como parámetro."
  exit 1
fi

# Obtener los permisos del archivo
permisos=$(stat -c "%a" "$1")

# Convertir los permisos a una cadena de caracteres
permisos_str=""
if [ $((permisos & 400)) -ne 0 ]; then
  permisos_str+="r"
else
  permisos_str+="-"
fi
if [ $((permisos & 200)) -ne 0 ]; then
  permisos_str+="w"
else
  permisos_str+="-"
fi
if [ $((permisos & 100)) -ne 0 ]; then
  permisos_str+="x"
else
  permisos_str+="-"
fi

# Mostrar los permisos
echo "Los permisos del archivo $1 son: $permisos_str"
```
## 11 Imprimir por pantalla 50 veces la palabra hola.
```bash
#!/bin/bash

for i in {1..50}
do
  echo "hola"
done
```
## 12 Leer una palabra por teclado y mostrarla por consola. Debe realizar esta operación 10 veces.
```bash
#!/bin/bash

for i in {1..10}
do
  echo "Introduce una palabra:"
  read palabra
  echo "La palabra es: $palabra"
done
```
## 13 Recibir un número por parámetro. El programa imprimirá la palabra “hola” el número de veces indicado por parámetro.
```bash
#!/bin/bash

# Verificar si se proporcionó un parámetro
if [ "$#" -ne 1 ]; then
  echo "Error: este script necesita un número como parámetro."
  exit 1
fi

# Obtener el número de veces que se debe mostrar la palabra "hola"
num_veces=$1

# Mostrar la palabra "hola" el número de veces especificado
for i in $(seq 1 $num_veces)
do
  echo "hola"
done
```
## 14 Se debe pasar un número n por parámetro. El programa imprimirá los números del 0 al n por pantalla.
```bash
#!/bin/bash
if [ "$#" -ne 1 ]; then
  echo "Error: este script necesita un número como parámetro."
  exit 1
fi

# Obtener el número límite
num_limite=$1

# Mostrar los números del 0 al número límite
for i in $(seq 0 $num_limite)
do
  echo $i
done
```
## 15 Recibir un número n por parámetro. El programa tendrá que sumar todos los números entre 1 y n. Posteriormente mostrará el resultado de la suma por pantalla
```bash
#!/bin/bash
if [ "$#" -ne 1 ]; then
  echo "Error: este script necesita un número como parámetro."
  exit 1
fi
num_limite=$1

suma=0
for i in $(seq 1 $num_limite)
do
  suma=$((suma + i))
done
echo "La suma de los números del 1 al $num_limite es: $suma"
```
## 17 Programa que lea palabras hasta que se escriba “:q”
```bash
#!/bin/bash

while true; do
  read -p "Introduce una palabra ('q' para salir): " palabra

  # Salir del bucle si se escribió ":q"
  if [ "$palabra" == ":q" ]; then
    echo "Saliendo del programa."
    exit 0
  fi
  echo "La palabra introducida es: $palabra"
done
```
## 20 Realiza un programa que solicite un número y compruebe si se encuentre en un archivo llamado números.txt
```bash
#!/bin/bash
read -p "Introduce un número: " numero

# Verificar si el número está en el archivo numeros.txt
if grep -q "^$numero$" numeros.txt; then
  echo "El número $numero se encuentra en el archivo numeros.txt."
else
  echo "El número $numero no se encuentra en el archivo numeros.txt."
fi
```


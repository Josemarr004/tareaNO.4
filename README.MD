# TAREA NO.4 ALGORITMOS

## **EJERCICIO NO.1**

*escriba una aplicación para resolver el siguiente enunciado. El gobierno ha implementado
como parte de su programa social, un subsidio familiar bajo la siguiente reglamentación:
Las familias que tienen hasta 2 hijos, reciben Q. 70.00, las que tienen hasta 3 y 5 reciben Q. 90.00 y las
que tienen 6 o más reciben Q. 120 mensual. Por cada hijo en edad escolar reciben Q. 10.00 adicionales.
Se considera la edad escolar entre 6 y 18 años. Si la madre de familia fuera viuda, la familia recibe Q.
20.00 adicionales*

 ```c++ 
// Calcular el subsidio de una familia
#include <iostream>
#include <vector>

using namespace std;

double calcularSubsidio(int num_hijos, vector<int> edades_escolares, bool es_viuda) {
    double monto_base = 0.0;

    
    if (num_hijos <= 2) {
        monto_base = 70.00;
    } else if (num_hijos <= 5) {
        monto_base = 90.00;
    } else {
        monto_base = 120.00;
    }

    
    double monto_adicional_edad_escolar = 10.00 * count_if (edades_escolares.begin(), edades_escolares.end(), [](int edad) {
        return edad >= 6 && edad <= 18;
    });

    
    double monto_adicional_viuda = es_viuda ? 20.00 : 0.00;

    
    double subsidio_total = monto_base + monto_adicional_edad_escolar + monto_adicional_viuda;

    return subsidio_total;
}

int main() {
    int num_hijos;
    cout << "Ingrese el número de hijos: ";
    cin >> num_hijos;

    vector<int> edades_escolares;
    int edad;
    for (int i = 0; i < num_hijos; i++) {
        cout << "Ingrese la edad del hijo " << (i + 1) << ": ";
        cin >> edad;
        edades_escolares.push_back(edad);
    }

    bool es_viuda;
    char respuesta;
    cout << "¿Es la madre viuda? (S/N): ";
    cin >> respuesta;
    es_viuda = (respuesta == 'S' || respuesta == 's');

    double monto_mensual = calcularSubsidio(num_hijos, edades_escolares, es_viuda);
    cout << "El monto mensual que recibirá la familia es de Q. " << monto_mensual << endl;

    return 0;
}
```
## EJERCICIO NO.2

*escribir una aplicación que solicite al usuario un número que será la longitud de dos
vectores que se deben llenar aleatoriamente, sume los valores e indique si ocurre cualquiera de los
siguientes escenarios. a) Son iguales, b) vector A es menor a B, c) vector B es menor a A*

```C++
// codiigo para calcular la longitud de los vectores
#include <iostream>

#include <vector>
#include <cstdlib>
#include <ctime>

using namespace std;

int main() {
    
    srand(time(0));

    int longitud;
    cout << "Ingrese la longitud de los vectores: ";
    cin >> longitud;

    vector<int> vectorA(longitud);
    cout << "Vector A: ";
    for (int i = 0; i < longitud; i++) {
        vectorA[i] = rand() % 100; 
        cout << vectorA[i] << " ";
    }
    cout << endl;

    
    vector<int> vectorB(longitud);
    cout << "Vector B: ";
    for (int i = 0; i < longitud; i++) {
        vectorB[i] = rand() % 100; 
        cout << vectorB[i] << " ";
    }
    cout << endl;

    
    int sumaA = 0, sumaB = 0;
    for (int i = 0; i < longitud; i++) {
        sumaA += vectorA[i];
        sumaB += vectorB[i];
    }

    
    if (sumaA == sumaB) {
        cout << "Los vectores son iguales." << endl;
    } else if (sumaA < sumaB) {
        cout << "El vector A es menor que el vector B." << endl;
    } else {
        cout << "El vector B es menor que el vector A." << endl;
    }

    return 0;
}
```
#### compilación ejercicio 2
![Alt text](image.png)

## EJERCICIO 3
*En estadística descriptiva, se define el rango de un conjunto de datos reales como la
diferencia entre el mayor y el menor de los datos.
Por ejemplo, si los datos son: [5.96, 6.74, 7.43, 4.99, 7.20, 0.56, 2.80], entonces el rango es 7.43 − 0.56
= 6.87.
Escriba un programa que:
a) Pregunte al usuario cuántos datos serán ingresados,
b) Pida al usuario ingresar los datos uno por uno, y
Entregue como resultado el rango de los datos*

```c++
//calcula el rango de datos segun la cantidad ingresada
#include <iostream>
#include <vector>

using namespace std;

int main() {
    int num_datos;
    cout << "Ingrese la cantidad de datos: ";
    cin >> num_datos;

    if (num_datos <= 0) {
        cout << "Debe ingresar al menos un dato." << endl;
        return 1;  
    }

    vector<double> datos;
    double dato;

    for (int i = 0; i < num_datos; i++) {
        cout << "Ingrese el dato #" << (i + 1) << ": ";
        cin >> dato;
        datos.push_back(dato);
    }

    double maximo = datos[0];
    double minimo = datos[0];

    for (int i = 1; i < num_datos; i++) {
        if (datos[i] > maximo) {
            maximo = datos[i];
        }
        if (datos[i] < minimo) {
            minimo = datos[i];
        }
    }

    double rango = maximo - minimo;

    cout << "El rango de los datos es: " << rango << endl;

    return 0;
}
```
### Compilación ejercicio 3
![Alt text](image-1.png)

## EJERCICIO 4
*solicite al usuario ingresar un número que será el lado de un cuadrado y escriba un
programa que dibuje dicho cuadrado de la siguiente manera: suponga que el usuario ingresó 4*
```c++
//solicite al usuario ingresar un número que será el lado de un cuadrado
#include <iostream>

using namespace std;

int main() {
    int lado;
    cout << "Ingrese el lado del cuadrado: ";
    cin >> lado;

    if (lado <= 0) {
        cout << "El lado debe ser mayor que 0." << endl;
        return 1;  
    }

    for (int i = 0; i < lado; i++) {
        for (int j = 0; j < lado; j++) {
            if (i == 0 || i == lado - 1 || j == 0 || j == lado - 1) {
                cout << "* ";
            } else {
                cout << "  "; 
            }
        }
        cout << endl;
    }

    return 0;
}
```
### Compilación ejercicio 4
![Alt text](image-2.png)

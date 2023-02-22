# Mini laboratorio de lenguaje C

### Materiales usados en ARCOS.INF.UC3M.ES con Licencia [CC BY-NC 4.0](http://creativecommons.org/licenses/by-nc/4.0/) 


## Requisitos

Los principales requisitos son:
* Tener acceso a una máquina con Linux
* Tener conexión a Internet

Para tener acceso a una máquina con Linux se recuerda que el Laboratorio del Departamento de Informática ofrece unas Aulas Virtuales en:
* ["https://www.lab.inf.uc3m.es/servicios/aulas-virtuales-del-laboratorio/](https://www.lab.inf.uc3m.es/servicios/aulas-virtuales-del-laboratorio/)



## 1.- Proceso de compilación

El lenguaje C estándar es compilado (y no interpretado como Python) por lo que a partir del código fuente hay que primero compilar para generar un código ejecutable que es el que se ejecuta.

Como ejemplo para compilar, usaremos el siguiente archivo:
* main.c
  ```c
  #include <stdio.h>
  
  int main ( int argc, char *argv[] )
  {
     printf("Hola mundo...\n") ;
     return 0 ;
  }
  ```

Para compilar usaremos:

```bash
gcc -g -Wall -c main.c -o main.o
gcc -g -Wall -o main      main.o
```

Aclaraciones:
* A la hora de compilar se utiliza los siguientes modificadores (flags):
  * "-g" para añadir información de depuración que es útil si se usa un depurador
  * "-Wall" para que muestre todas las advertencias (Warnings) de posibles problemas que detecte el compilador
* Se podría usar también:
  * "-Werror" para indicar que trate todas las advertencias (warnings) como errores.
  * "-std=c90 -pedantic" para indicar que use el estándar de C versión 90 de forma extricta sin extensiones de GNU adicionales.

Para ejecutar usaremos:

```bash
./main
```



## 2.- Sentencias de control de flujo en C

Como ejemplo de uso de sentencias de control de flujo en C, usaremos el siguiente archivo:
* main.c
  ```c
  #include <stdio.h>
  
  int main ( int argc, char *argv[] )
  {
     int i ;
     int print_intro ;

     for (i=0; i<100; i++)
     {
        print_intro = 0 ;
        printf("%d -> ", i) ;

        if ((i % 3) == 0)
        {
            printf("Fizz") ;
            print_intro = 1 ;
        }
        if ((i % 5) == 0)
        {
            printf("Buzz") ;
            print_intro = 1 ;
        }

        if (print_intro)
            printf("\n") ;
     }

     return 0 ;
  }
  ```

Aclaraciones:
* Hay que recordar para "alternar" entre opciones se puede usar:
  * if-then-else:
    ```c
    if ("condición cierta o falsa")  // 0 es falso y resto es verdadero
    {
      "si es cierta..."
    }
    else
    {
      "si es falsa..."
    }
    ```
* Hay que recordar para "iterar" en un bucle se puede usar:
  * for (de 0 a n veces):
    ```c
    for ("valores iniciales de contadores"; "condición de mantenimiento en el bucle"; "actualización de contadores")
    {
      ...
    }
    ```
  * while (de 0 a n veces):
    ```c
    "valores iniciales de contadores"; 
    while ("condición de mantenimiento en el bucle")
    {
      ...
      "actualización de contadores";
    }
    ```
  * do-while (de 1 a n veces):
    ```c
    "valores iniciales de contadores"; 
    do
    {
      ...
      "actualización de contadores";
    }
    while ("condición de mantenimiento en el bucle")
    ```

**Información recomendada**:
  * [Sentencias de control (youtube)](http://www.youtube.com/watch?embed=no&v=ux_J98WmjPA&feature=related)



## 3.- Uso de estructuras (struct) en C

Como ejemplo de (array de) structs, usaremos el siguiente archivo:
* main.c
  ```c
  #include <stdio.h>
  #include <stdlib.h>

  #define N_PERSONAS 100

  struct dni {
     int  id ;
     char nombre[128] ;
  } ;

  struct dni personas[N_PERSONAS] ;
  
  int main ( int argc, char *argv[] )
  {
     int i ;

     /* Rellenar personas con valores por defecto (persona 0,1...) */
     for (i=0; i<N_PERSONAS; i++)
     {
        sprintf("persona %d", personas[i].nombre, personas[i].id) ;
        personas[i].id = i ;
     }

     /* Imprimir personas */
     for (i=0; i<N_PERSONAS; i++)
     {
        printf(" * Persona '%s' que tiene un id '%d'.\n", 
        /*                  ^                    ^         */
        /*                  |                    |         */
                           personas[i].nombre,
        /*                                       |         */                           
                                                 personas[i].id) ;
     }

     return 0 ;
  }
  ```

Aclaraciones:
* En Lenguaje C al definir un array, solo su nombre (sin corchetes []) representa la dirección de memoria del primer elemento (una dirección de memoria constante que apunta a un elemento variable).

**Información recomendada**:
* [Array y Struct en C (youtube)](http://www.youtube.com/watch?embed=no&v=o5Jl_Dzga88&feature=related)



## 4.- Uso de punteros I (qué es un puntero)

Como ejemplo inicial de qué representa un puntero en C, usaremos el siguiente archivo:
* main.c
  ```c
  #include <stdio.h>
  #include <stdlib.h>

  int main ( int argc, char *argv[] )
  {
      /* Definir variables */
      int   i ;
      int *pi ;     /* (1) */
  //  int &ri = i ; /* (2) <- solo en C++ */


      /* Modificar valor de variables */
       i  = 5 ;
       pi = &i ;     /* (4) */
      *pi = 5 ;      /* (3) */
  //   ri = 5 ;      /* <- solo en C++ */


      /* Consultar valor de variables */
      printf("  i = %d\n",   i) ;
      printf(" pi = %x\n",  pi) ;
      printf("*pi = %d\n", *pi) ; /* (3) */
  //  printf(" ri = %d\n",  ri) ; /* <- solo en C++ */

      // Una variable puntero es un variable que guarda la dirección de una posición de memoria,
      // se parece mucho a una variable del tipo "unsigned long int"
      printf(" pi = %x\n",  pi) ;
      printf(" &i = %d\n",  &i) ; /* (4) */
      // Una variable puntero a su vez se guarda en una posición de memoria
      // (se puede aplicar el operador & para conocer dicha dirección)
      printf("&pi = %x\n", &pi) ; /* (4) */

      return 0 ;
  }
  ```

A recordar:
* El uso de los operadores "&" y "*" depende del contexto:

| contexto             |   *                |   &                  |
|:--------------------:|:------------------:|:--------------------:|
| definición variable  | (1) puntero a...   | (2) referencia a...  |
| uso de variable      | (3) acceder a...   | (4) dirección de...  |

**Información recomendada**:
* [Introducción a punteros  I (youtube)](http://www.youtube.com/watch?embed=no&v=iQF-2vUNEJk&feature=related)
* [Introducción a punteros II (youtube)](http://www.youtube.com/watch?embed=no&v=m6sdKI3zhKg&feature=related)



## 4.- Uso de punteros II (memoria dinámica)

Como ejemplo de uso de punteros para memoria dinámica, usaremos el siguiente archivo:
* main.c
  ```c
  #include <stdio.h>
  #include <stdlib.h>


  void imprimir ( int *vector, int n_eltos )
  {
      int i ;

      for (i=0; i<n_eltos; i++)
      {
           printf(" >> vector[%d] = %d\n", i, vector[i]) ;
      }
  }

  int main ( int argc, char *argv[] )
  {
      /* 
       * Definir variables
       */

      /* Array estático (de tamaño fijo, en tiempo de compilación) */
      int  earray[5]  = { 1, 2, 3, 4, 5 } ;

      /* Array dinámico (tamaño variable fijado en ejecución) */
      int *darray  = NULL ;
      int  n_eltos = 0 ;


      /*
       * Modificar valor de variables
       */
      earray[0] = 1 ;
      earray[1] = 2 ;
      earray[2] = 3 ;
      earray[3] = 4 ;
      earray[4] = 5 ;
  /* CUIDADO:
      earray[5] = 5 ;  !!  fuera de rango
  */

      // <- en este punto de ejecución:
      //    * darray  vale NULL
      //    * n_eltos vale cero

      /* a) vamos a pedir memoria para 2 enteros */
      n_eltos = 2 ;  // <- en un futuro en lugar de 2 se pasará por argc/argv el número...
      darray = malloc(n_eltos * sizeof(int)) ;

      /* b) vamos a comprobar que malloc NO ha devuelto NULL */
      if (NULL == darray) {
          perror("malloc ha fallado: ") ;
          exit(-1) ;
      }

      // <- en este punto de ejecución:
      //    * darray  vale aquí la posición de memoria donde hay espacio para guardar 2 enteros
      //    * n_eltos vale 2 aquí

      /* c) se da valores a la memoria dinámica pedida */
      darray[0] = 1 ;
      darray[1] = 2 ;

  /* CUIDADO:
      darray    = 1 ;  !!  darray almacena la dirección 0x1 de memoria pero no se guarda 1 en el primer elemento
      darray[2] = 3 ;  !!  fuera de rango
  */


      /* 
       * Consultar valor de variables
       */

      printf("Estático:\n") ;
      imprimir(earray, 5) ;

      /* d) se lee los valores de la memoria dinámica */
      printf("Dinámico:\n") ;
      imprimir(darray,  n_eltos) ;

  /* CUIDADO:
      imprimir(&darray, n_eltos) ;  !! dirección de la variable que guarda la dirección del primer elemento...
  */

      /* e) se libera la memoria cuando ya NO sea necesario volver a usarse */
      free(darray) ;
      darray = NULL ;

      return 0 ;
  }
  ```

En este ejemplo:
* Hay un array estático (earray) de enteros:
  * Un array estático es de tamaño fijo determinado en tiempo de compilación.
  * En tiempo de ejecución no se puede cambiar su tamaño por lo que normalmente se indica en tiempo de compilación un tamaño máximo que el/la programador/a no se ha de sobrepasar.
* Hay un array dinámico (darray) de enteros:
  * El array dinámico se implementa con dos elementos: un entero con el tamaño del array (en elementos o bytes) y un puntero al primer elemento (el resto están a continuación).
  * En tiempo de ejecución se reserva espacio (malloc) y luego se puede usar como un array estático (usando los corchetes y el índice del elemento a acceder).

A recordar:
* En C hay que llevar la contabilidad de los punteros al usarlos: que en todo momento la dirección sea válida y apunte a un espacio de memoria que se ha reservado previamente (en compilación o ejecución).
* En Lenguaje C al definir un array estático, solo su nombre (sin corchetes []) representa la dirección de memoria del primer elemento (una dirección de memoria constante).
* Estados en el uso recomendado de un puntero:
  ```mermaid
stateDiagram-v2
    direction LR
    state "px=¿?"              as px_xx
    state "px=NULL"            as px_null
    state "px=&x"              as px_atx
    state "px=malloc(size)"    as px_alloc

    px_xx     --> px_null:  px = NULL
    px_null   --> px_atx:   px = &x
    px_atx    --> px_null:  px = NULL
    px_null   --> px_alloc: px = malloc(size_en_bytes)
    px_alloc  --> px_null:  free(px) + px = NULL
    px_alloc  --> px_alloc: px_aux = realloc(px, nuevo_size_en_bytes) + if (px_aux != NULL) px = px_aux
    px_atx    --> px_alloc: px = malloc(size_en_bytes)
  ```

**Información recomendada**:
* [Introducción a punteros  I (youtube)](http://www.youtube.com/watch?embed=no&v=iQF-2vUNEJk&feature=related)
* [Introducción a punteros II (youtube)](http://www.youtube.com/watch?embed=no&v=m6sdKI3zhKg&feature=related)



## 5.- Paso de parámetros a funciones

Es importante tener presente que en lenguaje C:
* Los valores con los que se llama a una función se llaman **argumentos reales**:
  ```c
  int ret = f(1, 'a', 3.14) ;
  ```
* Los valores dentro de una función se llaman **argumentos formales**:
  ```c
  int f(int a1, char a2, float a3) { ... }
  ```
* **En el momento de la llamada a una función se hace una asignación (copia) de los argumentos reales a los formales**.
  * Por tanto, **TODO argumento se pasa por valor**.
* El nombre de un array de tipo X equivale a la dirección de memoria donde se guarda el primer elemento de tipo X, por tanto el argumento formal puede ser un puntero a X.
  ```c
        int f(char *a4, char a5[]) ;
       //           ^        ^
       //           |        |
  int ret = f(array_char, "Hola") ;
  ```


Como ejemplo de paso por parámetros, usaremos el siguiente archivo:
* main.c
  ```c
  #include <stdio.h>
  #include <stdlib.h>

  int imprimir_char ( char valor )
  {
      printf("valor: '%c'\n", valor) ;

      return 1 ; // convenio aquí: 1 OK y 0 KO
  }

  int imprimir_string ( char *valor )
  {
      // comprobar argumentos: programación "defensiva"...
      if (NULL == valor)
          return 0 ;

      // si todo bien, acción y devolver OK
      printf("valor: '%s'\n", valor) ;

      return 1 ; // convenio aquí: 1 OK y 0 KO
  }

  int main ( int argc, char *argv[] )
  {
      int ret ;
      char  c  = 'x' ;
      char *s1 = "Hola" ;
      char  s2[120] ;

      /* Caracter (char) */

         ret = imprimir_char(c) ;
         if (ret != 1) return -1 ;

         ret = imprimir_char('x') ;
         if (ret != 1) return -1 ;


      /* Cadena de caracteres (string) */

         ret = imprimir_string(s1) ; // a recordar: s1 es la dirección del primer caracter en la cadena guardada en s1
         if (ret != 1) return -1 ;

         ret = imprimir_char(s1[3]) ;
         if (ret != 1) return -1 ;

         ret = imprimir_char(*(s1+3)) ;
         if (ret != 1) return -1 ;

         strcpy(s2, "Adios") ;
         ret = imprimir_string(s2) ; // a recordar: s2 es la dirección del primer caracter en la cadena guardada en s2
         if (ret != 1) return -1 ;

         ret = imprimir_char(s2[3]) ;
         if (ret != 1) return -1 ;

         ret = imprimir_char(*(s2+3)) ;
         if (ret != 1) return -1 ;

      return 0 ; // convenio aquí: 0 OK, negativos KO
  }
  ```

**Información recomendada**:
* [Paso de parámetros a funciones (youtube)](https://youtu.be/mS0gnJ-su_Y&t=7m33s)


Como ejemplo de paso por parámetros de punteros, usaremos el siguiente archivo:
* main.c
  ```c
  #include <stdio.h>
  #include <stdlib.h>

  void * mi_malloc ( long size )
  {
      // comprobar argumentos...
      if (0 == size) return NULL ;

      return (void *)malloc(size) ;
  }

  int mi_free ( void **ptr )
  {
      // comprobar argumentos...
      if (NULL == ptr) return -1 ;

      // si ya es NULL, ignorar
      if (NULL == *ptr) return 0 ;

      // liberar y poner a NULL
      free(*ptr) ;
      *ptr = NULL ;

      return 1 ;
  }

  int main ( int argc, char *argv[] )
  {
      int ret ;
      char *s1 ;

      s1 = mi_malloc(128) ;

   // ...

      mi_free(&s1) ;

      return 0 ;
  }
  ```

**Información recomendada**:
* [Paso de parámetros a funciones (youtube)](https://youtu.be/mS0gnJ-su_Y&t=7m33s)


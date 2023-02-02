# Introducción a la herramienta Make

### Materiales usados en ARCOS.INF.UC3M.ES con Licencia [CC BY-NC 4.0](http://creativecommons.org/licenses/by-nc/4.0/) 


## Introducción a Make

### Código de ejemplo a compilar...

Archivo lib_hola.h
```c
void di_hola ( void ) ;
```

Archivo lib_hola.c
```c
void di_hola ( void ) 
{
   printf("Hola Mundo...") ;
}
```

Archivo main.c
```c
#include <lib_hola.h>

int main ( int argc, char *argv[] )
{
   di_hola() ;
   return 0 ;
}
```

### Compilación manual

```bash
gcc -g -Wall -c lib_hola.c -o lib_hola.o
gcc -g -Wall -c main.c     -o main.o
gcc -g -Wall -o main main.o lib_hola.o
```

### Compilación con Makefile (primera versión)

Archivo Makefile inicial:
```bash
all:
  gcc -g -Wall -c lib_hola.c -o lib_hola.o
  gcc -g -Wall -c main.c     -o main.o
  gcc -g -Wall -o main main.o lib_hola.o
```

Para usar el archivo Makefile hay que ejecutar:
```bash
make
```

### Compilación con Makefile (segunda versión con variables)

Archivo Makefile:
```bash
CC=gcc
CFLAGS=-g -Wall

all:
  $(CC) $(CFLAGS) -c lib_hola.c -o lib_hola.o
  $(CC) $(CFLAGS) -c main.c     -o main.o
  $(CC) $(CFLAGS) -o main main.o lib_hola.o
```

Para usar el archivo Makefile hay que ejecutar:
```bash
make
```

### Compilación con Makefile (tercera versión con reglas)

Archivo Makefile:
```bash
CC=gcc
CFLAGS=-g -Wall

%.o : %.c
  $(CC) $(CFLAGS) -c $< -o $@

.PHONY: all clean

all: lib_hola.o main.o
  $(CC) $(CFLAGS) -o main main.o lib_hola.o
  
clean: lib_hola.o main.o
  rm -fr lib_hola.o main.o
```

Para usar el archivo Makefile hay que ejecutar:
```bash
make
```

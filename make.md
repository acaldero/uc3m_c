# Introducción a la herramienta Make

### Materiales usados en ARCOS.INF.UC3M.ES con Licencia [CC BY-NC 4.0](http://creativecommons.org/licenses/by-nc/4.0/) 


## Ejemplo de ejemplo a compilar con Makefile

Usaremos tres archivos:

* lib_hola.h
  ```c
  void di_hola ( void ) ;
  ```

* lib_hola.c
  ```c
  void di_hola ( void ) 
  {
     printf("Hola Mundo...") ;
  }
  ```

* main.c
  ```c
  #include <lib_hola.h>
  
  int main ( int argc, char *argv[] )
  {
     di_hola() ;
     return 0 ;
  }
  ```

## Compilación SIN Makefile (compilación manual)

Para compilar los anteriores archivos hay que ejecutar los siguientes mandatos:

```bash
gcc -g -Wall -c lib_hola.c -o lib_hola.o
gcc -g -Wall -c main.c     -o main.o
gcc -g -Wall -o main main.o lib_hola.o
```

## Compilación con Makefile (primera versión)

* Archivo Makefile inicial:
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

El esqueleto del Makefile anterior es:
```bash
targets: prerequisites
	command 1
	command 2
	command 3
```
Donde para obtener un objetivo (targets) se indica 2 elementos:
  * Prerequisitos (prerequisites): que son objetivos que hay que cumplir primero
  * Mandatos (command 1/2/3): una vez se tengan los prerequisitos la forma de tener el objetivo es ejecutar los mandatos uno detrás de otro
  * Importante: no vale usar espacios en blanco antes de cada "gcc -g ...", solo vale tabuladores.


## Compilación con Makefile (segunda versión con variables)

* Archivo Makefile:
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

## Compilación con Makefile (tercera versión con reglas)

* Archivo Makefile:
  ```bash
  CC=gcc
  CFLAGS=-g -Wall
  OBJS=main.o lib_hola.o

  .PHONY: all clean

  all: $(OBJS)
  	$(CC) $(CFLAGS) -o main $(OBJS)

  %.o : %.c
  	@echo "Compiling... $<" 
  	$(CC) $(CFLAGS) -c $< -o $@

  clean: $(OBJS)
  	@echo "Removing $(OBJS)..."
  	rm -fr $(OBJS)
  ```

Para usar el archivo Makefile se recomienda ejecutar:
```bash
make clean; make
```

## Material recomendado
  * https://makefiletutorial.com/
  * https://www3.nd.edu/~zxu2/acms60212-40212/Makefile.pdf
  


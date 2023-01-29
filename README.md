# Introducción al lenguaje C

### Materiales usados en ARCOS.INF.UC3M.ES con Licencia [CC BY-NC 4.0](http://creativecommons.org/licenses/by-nc/4.0/) 

## Materiales

* Transparencias y videos:

<html>
<ul>
<div class="table-responsive">
    <table class="table table-bordered table-sm table-hover" border="1">
            <tr>
                <th class="col-4" style="width:33vh;">Transparencias</th>
                <th class="col-4" style="width:33vh;">Videos</th>
            </tr>
            <tr>
                <td class="align-middle">
                    <b><a href="https://acaldero.github.io/uc3m_c/slides/clase_w1-introduccionc.pdf"><u>Introducción al lenguaje C</u></a></b>
                </td>
                <td class="align-middle">
                    <ol type="1">
                        <li> <a href="http://www.youtube.com/watch?embed=no&amp;v=EFEj13YU7I0&amp;feature=related" target="_blank">Preprocesador</a></li>
                        <li> <a href="http://www.youtube.com/watch?embed=no&amp;v=-P2C4g6xZeE&amp;feature=related" target="_blank">Comentarios</a></li>
                        <li> <a href="http://www.youtube.com/watch?embed=no&amp;v=B_7jBxe_VOQ&amp;feature=related" target="_blank">Bibliotecas</a></li>
                        <li> <a href="http://www.youtube.com/watch?embed=no&amp;v=1Hz19T5lRP8&amp;feature=related" target="_blank">Tipos de datos básicos, variables y constantes</a></li>
                        <li> <a href="http://www.youtube.com/watch?embed=no&amp;v=ux_J98WmjPA&amp;feature=related" target="_blank">Sentencias de control</a></li>
                        <li> <a href="http://www.youtube.com/watch?embed=no&amp;v=o5Jl_Dzga88&amp;feature=related" target="_blank">Array y Struct</a></li>
                        <li> <a href="http://www.youtube.com/watch?embed=no&amp;v=mS0gnJ-su_Y&amp;feature=related" target="_blank">Funciones</a></li>
                        <li> <a href="http://www.youtube.com/watch?embed=no&amp;v=iQF-2vUNEJk&amp;feature=related" target="_blank">Punteros (1/2)</a></li>
                        <li> <a href="http://www.youtube.com/watch?embed=no&amp;v=m6sdKI3zhKg&amp;feature=related" target="_blank">Punteros (2/2)</a></li>
                    </ol>
                </td>
            </tr>
        </tbody>
    </table>
</div>
</ul>
</html>

* Material recomendado:
  * Libro en PDF: ["Introducción al lenguaje de programación C", Félix Garcia Carballeira, 2022](https://www.arcos.inf.uc3m.es/fgarcia/wp-content/uploads/sites/4/2020/02/guiaC-v2.pdf)
  * Página web:   ["C for Python programmers", Carl Burch and Hendrix College, 2011](http://www.cburch.com/books/cpy/index.html)


## Introducción al lenguaje C

<ol>

<details open>
<summary>1. El preprocesador</summary>
<ol>
<ol type="a">
<li><a href="https://youtu.be/EFEj13YU7I0&t=0m00s">Recordar el "hola mundo"</a>
<li><a href="https://youtu.be/EFEj13YU7I0&t=0m52s">¿Por qué preprocesador?</a>
<li><a href="https://youtu.be/EFEj13YU7I0&t=2m08s">¿Qué es el preprocesador?</a>
<li><a href="https://youtu.be/EFEj13YU7I0&t=3m28s">#include</a>
<li><a href="https://youtu.be/EFEj13YU7I0&t=4m05s">#define (constante)</a>
<li><a href="https://youtu.be/EFEj13YU7I0&t=8m30s">#if + #endif</a>
<li><a href="https://youtu.be/EFEj13YU7I0&t=10m38s">#define (macro)</a>
<li><a href="https://youtu.be/EFEj13YU7I0&t=12m21s"># (token a string)</a>
<li><a href="https://youtu.be/EFEj13YU7I0&t=13m33s">## (concatenar)</a>
<li><a href="https://youtu.be/EFEj13YU7I0&t=13m55s">#error</a>
</ol>
</ol>
</details>


<details open>
<summary>2. Los comentarios</summary>
<ol>
<ol type="a">
<li><a href="https://youtu.be/-P2C4g6xZeE&t=0m">Comentarios en C</a>
</ol>
</ol>
</details>


<details open>
<summary>3. Bibliotecas en C</summary>
<ol>
<ol type="a">
<li><a href="https://youtu.be/B_7jBxe_VOQ&t=0m00s">Motivación</a>
<li><a href="https://youtu.be/B_7jBxe_VOQ&t=0m28s">#include</a>
<li><a href="https://youtu.be/B_7jBxe_VOQ&t=0m45s">Ejemplo #include</a>
<li><a href="https://youtu.be/B_7jBxe_VOQ&t=1m54s">No Java-package o Python-module</a>
<li><a href="https://youtu.be/B_7jBxe_VOQ&t=2m34s">Ejemplo de biblioteca</a>
<li><a href="https://youtu.be/B_7jBxe_VOQ&t=5m04s">Solucionar las multiples inclusiones</a>
<li><a href="https://youtu.be/B_7jBxe_VOQ&t=6m58s">Bibliotecas estáticas y dinámicas</a>
<li><a href="https://youtu.be/B_7jBxe_VOQ&t=7m42s">Ejemplo de bibliotecas estática</a>
<li><a href="https://youtu.be/B_7jBxe_VOQ&t=10m05s">Ejemplo de bibliotecas dinámica</a>
</ol>
</ol>
</details>


<details open>
<summary>4. Tipos de datos básicos</summary>
<ol>
<ol type="a">
<li><a href="https://youtu.be/1Hz19T5lRP8&t=0m00s">char, int, long, float y double</a>
<li><a href="https://youtu.be/1Hz19T5lRP8&t=2m21s">enum y ¿bool?</a>
<li><a href="https://youtu.be/1Hz19T5lRP8&t=4m08s">typedef</a>
<li><a href="https://youtu.be/1Hz19T5lRP8&t=5m33s">bool con typedef</a>
<li><a href="https://youtu.be/1Hz19T5lRP8&t=6m28s">Variables: ámbito y duración</a>
<li><a href="https://youtu.be/1Hz19T5lRP8&t=11m10s">Declaración vs definición</a>
<li><a href="https://youtu.be/1Hz19T5lRP8&t=13m59s">Constantes</a>
<li><a href="https://youtu.be/1Hz19T5lRP8&t=16m41s">Asignación</a>
<li><a href="https://youtu.be/1Hz19T5lRP8&t=18m02s">Casting implícito</a>
<li><a href="https://youtu.be/1Hz19T5lRP8&t=19m11s">Casting explícito</a>
</ol>
</ol>
</details>


<details open>
<summary>5. Sentencias de control</summary>
<ol>
<ol type="a">
<li><a href="https://youtu.be/ux_J98WmjPA&t=0m00s">Sentencias de control</a>
<li><a href="https://youtu.be/ux_J98WmjPA&t=0m45s">If/if-else/switch</a>
<li><a href="https://youtu.be/ux_J98WmjPA&t=8m20s">For/while/do-until</a>
<li><a href="https://youtu.be/ux_J98WmjPA&t=11m47s">Continue/break/goto</a>
</ol>
</ol>
</details>


<details open>
<summary>6. Vectores y estructuras</summary>
<ol>
<ol type="a">
<li><a href="https://youtu.be/o5Jl_Dzga88&t=0m00s">[] vs struct</a>
<li><a href="https://youtu.be/o5Jl_Dzga88&t=2m15s">sizeof(struct)</a>
<li><a href="https://youtu.be/o5Jl_Dzga88&t=3m43s">typedef con struct</a>
<li><a href="https://youtu.be/o5Jl_Dzga88&t=5m00s">campo de bits</a>
<li><a href="https://youtu.be/o5Jl_Dzga88&t=5m50s">union</a>
<li><a href="https://youtu.be/o5Jl_Dzga88&t=7m54s">{[], struct} x {tipo básico, [], struct}</a>
<li><a href="https://youtu.be/o5Jl_Dzga88&t=10m35s">struct "recursiva"</a>
<li><a href="https://youtu.be/o5Jl_Dzga88&t=13m27s">cadenas de caracteres</a>
<li><a href="https://youtu.be/o5Jl_Dzga88&t=19m05s">argc y argv</a>
</ol>
</ol>
</details>


<details open>
<summary>7. Funciones</summary>
<ol>
<ol type="a">
<li><a href="https://youtu.be/mS0gnJ-su_Y&t=0m00s">Inspiración matemática</a>
<li><a href="https://youtu.be/mS0gnJ-su_Y&t=2m15s">Aproximación procedimental</a>
<li><a href="https://youtu.be/mS0gnJ-su_Y&t=2m51s">Prototipo de función</a>
<li><a href="https://youtu.be/mS0gnJ-su_Y&t=4m19s">Detalles en la definición </a>
<li><a href="https://youtu.be/mS0gnJ-su_Y&t=5m28s">Variables locales y globales</a>
<li><a href="https://youtu.be/mS0gnJ-su_Y&t=5m53s">Variables: ámbito y duración</a>
<li><a href="https://youtu.be/mS0gnJ-su_Y&t=7m33s">Paso de parámetros</a>
<li><a href="https://youtu.be/mS0gnJ-su_Y&t=10m43s">Tipo de dato función</a>
<li><a href="https://youtu.be/mS0gnJ-su_Y&t=12m40s">Constantes y variables tipo función</a>
<li><a href="https://youtu.be/mS0gnJ-su_Y&t=15m05s">Funciones como parámetros</a>
</ol>
</ol>
</details>


<details open>
<summary>8. Introducción a punteros (1/2)</summary>
<ol>
<ol type="a">
<li><a href="https://youtu.be/iQF-2vUNEJk&t=0m00s">Dirección, valor y tamaño</a>
<li><a href="https://youtu.be/iQF-2vUNEJk&t=4m41s">Puntero</a>
<li><a href="https://youtu.be/iQF-2vUNEJk&t=8m05s">Leer y escribir en memoria</a>
<li><a href="https://youtu.be/iQF-2vUNEJk&t=8m49s">Ejemplo 1</a>
<li><a href="https://youtu.be/iQF-2vUNEJk&t=11m03s">Estados de un puntero</a>
<li><a href="https://youtu.be/iQF-2vUNEJk&t=14m36s">Problemas con punteros</a>
<li><a href="https://youtu.be/iQF-2vUNEJk&t=16m41s">Mejor inicializar a NULL</a>
</ol>
</ol>
</details>


<details open>
<summary>9. Introducción a punteros (2/2)</summary>
<ol>
<ol type="a">
<li><a href="https://youtu.be/m6sdKI3zhKg&t=0m00s">Puntero auxiliar como comodín</a>
<li><a href="https://youtu.be/m6sdKI3zhKg&t=5m19s">Memoria dinámica</a>
<li><a href="https://youtu.be/m6sdKI3zhKg&t=12m08s">Paso de parámetros</a>
<li><a href="https://youtu.be/m6sdKI3zhKg&t=21m43s">Aritmética de punteros</a>
<li><a href="https://youtu.be/m6sdKI3zhKg&t=23m05s">void *</a>
</ol>
</ol>
</details>


</ol>


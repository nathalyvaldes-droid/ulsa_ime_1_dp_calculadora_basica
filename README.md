# Práctica 4: Calculadora básica

> **Las secciones 1 a 6 ya están resueltas por el profesor.** Léelas con atención, pero no las modifiques. Tu trabajo empieza en la sección 7.

## 1. Descripción del problema (Fase 1, resuelta)

El programa muestra un menú con cuatro operaciones (suma, resta, multiplicación y división). El usuario elige una, escribe dos números y el programa muestra el resultado de la operación. Es la base de cualquier calculadora y del tipo de menú que se usa, por ejemplo, en el panel de control de una máquina.

## 2. Entradas y salidas (Fase 1, resuelta)

**Entradas:**
1. `opcion` (`int`): la operación elegida, de 1 a 4. Se lee con `leerEntero`.
2. `a` (`double`): el primer número. Se lee con `leerDecimal`.
3. `b` (`double`): el segundo número. Se lee con `leerDecimal`.

**Salidas:**
1. `resultado` (`double`): el resultado de la operación.
2. Se muestra en la forma `a símbolo b = resultado`, por ejemplo `7 / 2 = 3.5`. El símbolo se guarda en `simbolo` (`char`).

**Operaciones:** 1) `a + b`   2) `a - b`   3) `a * b`   4) `a / b`

## 3. Restricciones e invariante (Fases 1 y 2, resuelta)

**Restricciones:**
- La opción debe estar entre 1 y 4. Si no, el programa la vuelve a pedir.
- Si la operación es división, `b` no puede ser 0. Si lo es, el programa vuelve a pedir solo `b`.
- En la resta y en la división el orden importa: siempre se calcula `a` op `b`.

**¿Quién detecta cada error?**
- `leerEntero` y `leerDecimal` detectan el **formato**: texto (`abc`) o, en el caso de `leerEntero`, decimales (`2.5`).
- El programa detecta el **rango**: una opción fuera de 1 a 4 y un divisor igual a 0.

**Invariante:** al llegar al Paso 7 (el cálculo), `opcion` está entre 1 y 4 y, si la opción es 4 (división), `b` es distinto de 0. Por eso el cálculo siempre es válido.

## 4. Casos resueltos a mano (Fase 1, resuelta)

| Caso | Opción | a | b | Resultado |
|---|---|---|---|---|
| 1 | 1 (suma) | 8 | 5 | 8 + 5 = 13 |
| 2 | 2 (resta) | 3 | 5 | 3 - 5 = -2 |
| 3 | 3 (multiplicación) | 2.5 | 4 | 2.5 * 4 = 10 |
| 4 | 4 (división) | 7 | 2 | 7 / 2 = 3.5 |
| 5 | 4 (división) | 5 | 0, luego 2 | vuelve a pedir `b`; 5 / 2 = 2.5 |

## 5. Receta en pseudocódigo (Fase 2, resuelta)

La receta completa está en el archivo `RECETA.md`. No la modifiques: si encuentras algo que no contempla, anótalo en la sección 11.

## 6. Cómo compilar y ejecutar (Fase 3)

```bash
g++ -Wall -Wextra -std=c++17 main.cpp -o calculadora
./calculadora
```

## 7. Ejemplo de ejecución (Fase 3)
<!-- Pega aquí lo que muestra tu programa en pantalla con una división donde primero escribes 0 como segundo número. -->
Elige una opción (1-4): 4
Ingresa el primer número: 3
Ingresa el segundo número: 0
Error: no se puede dividir entre cero.

```
_____
```

## 8. De la receta al código (Fase 3)
<!-- Para cada paso de la receta, escribe la instrucción (o instrucciones) de C++ que lo implementa. -->

| Paso de la receta | Instrucción de C++ que lo implementa |
|---|---|
| 1 y 2. Título y menú | _____ |
| 3. Leer y validar la opción | _____ |
| 4 y 5. Leer `a` y `b` | _____ |
| 6. Validar el divisor | _____ |
| 7. Decisión múltiple (un `case`) | _____ |
| 8. Mostrar el resultado | _____ |

**¿Hubo algún paso de la receta que te costó traducir a C++? ¿Cuál y por qué?**
SIII todos porque de plano no le entendia pero ya la final empece a usar bien lo del switch y asi 

## 9. Experimentos (Fase 3)

**Experimento A: sin el `break` del `case 1`, ¿qué mostró el programa con 8 + 5? ¿Qué te dijo el compilador? ¿Por qué pasó?**
ala se paso al simbolo de abajo en donde decia el break osea lo empece con suma y como no tenia la palabra break se sumo y se resto porque no tenia algo que le dijera que pare

**Experimento B: sin la validación del Paso 6, ¿qué mostró el programa con 5 / 0? ¿Tiene sentido?**
muestra error no se puede dividir entre cero 

**Experimento C (opcional): con `a` y `b` de tipo `int`, ¿qué resultado dio 7 / 2? ¿Te avisó el compilador?**
no 

## 10. Tabla de pruebas (Fase 4)

| Caso | Entradas (opción, a, b) | Esperado | Obtenido | ¿Pasó? |
|---|---|---|---|---|
| Suma | 1, 8, 5 | 8 + 5 = 13 | si | _____ |
| Resta negativa | 2, 3, 5 | 3 - 5 = -2 | si salio | _____ |
| Multiplicación con decimales | 3, 2.5, 4 | 2.5 * 4 = 10 | no salio porque no acepta numeros decimales  | _____ |
| Multiplicación con negativo | 3, -3, 4 | -3 * 4 = -12 | si salio | _____ |
| División | 4, 7, 2 | 7 / 2 = 3.5 | si salio | _____ |
| Dividendo cero | 4, 0, 5 | 0 / 5 = 0 | si sale| _____ |
| Divisor cero | 4, 5, 0 (luego 2) | vuelve a pedir `b`; 5 / 2 = 2.5 | _____ | _____ |
| Suma con cero | 1, 5, 0 | 5 + 0 = 5 (**no** vuelve a pedir `b`) | sale error | _____ |
| Opción fuera de rango | 5 (luego 1), 8, 5 | vuelve a pedir la opción; 8 + 5 = 13 | me volvio a salir al opcion de elige un numero y lgo ya hizo bien la suma | _____ |
| Opción cero | 0 (luego 1), 8, 5 | vuelve a pedir la opción; 8 + 5 = 13 | _____ | _____ |
| Opción decimal | 2.5 (luego 2), 3, 5 | `leerEntero` vuelve a pedir; 3 - 5 = -2 | me sale que tengo que escribir un numero entero y luego ya me salip bien la resta| _____ |
| Opción con texto | `suma` (luego 1), 8, 5 | `leerEntero` vuelve a pedir; 8 + 5 = 13 | me dice que escoga un aopcion valida | _____ |
| Número con texto | 1, `abc` (luego 8), 5 | `leerDecimal` vuelve a pedir; 8 + 5 = 13 | me decia que pusiera un numero valido hasta que puse uno de las de opcion y la suma si la realizo correctamente | _____ |
| Caso propio 1 | 3) multiplicacion | 7*6 = 42 | _____ | _____ |
| Caso propio 2 | 2) Resta | 10-2= 8 | _____ | _____ |

## 11. Bitácora de mejoras (Fase 4)

| # | ¿Qué falló o qué quise mejorar? el codigo  | ¿Qué cambié? el codigo y la manera en la que lo redacte| ¿Funcionó? sii|
el codigo como mil veces porq se me olvidaba ponerle ; 
| 1 | _____ | _____ | _____ |
| 2 | _____ | _____ | _____ |

**¿Encontré algo que la receta no contemplaba? ¿Qué?**
no, literal lei toda la receta y con eso pude saber que tenia que hacer

**Reto elegido (opcional):** _____

## 12. Dudas para el profesor (Fase 3)

| Duda | Lo que ya intenté |
|---|---|
| _____ | _____ |

## 13. Reflexión final

**¿Qué aprendí con esta práctica?**
aprendi a poner atencion a las cosas que pienso que no me van a ayudar

**Ahora que terminé, ¿qué cambiaría de mi proceso?**
hubiera puesto mas atencion antes y buscado los significados de std switch y asi 

**¿Qué fue lo más difícil y cómo lo resolví?**
lo mas dificil fue redactarlo y lo resolvi leyendo la receta y preguntando como empezar a escribir el codigo ya que no tenia ni idea de como se escribia 

**¿Qué pregunta me quedó sin responder?**
ninguna

**¿Fue más fácil programar a partir de una receta ajena que de la mía? ¿Por qué?**
mm sii porque la verdad mis recetas eran muy resumidas y no les entendia muy bien 

**Si yo hubiera diseñado la receta, ¿qué le cambiaría?**
nada se entiende super bien 

## 14. Lista de verificación antes de entregar (Fase 5)

- [ ] Llené las secciones 7 a 13 (no quedan `_____`)
- [ ] No modifiqué las secciones 1 a 6 ni la receta de `RECETA.md`
- [ ] Cada bloque de `main.cpp` tiene su comentario `// Paso N`
- [ ] Mi programa compila sin advertencias
- [ ] Probé todos los casos de la tabla
- [ ] Hice los Experimentos A y B y dejé el código correcto al terminar
- [ ] No modifiqué `utilerias.h`
- [ ] Hice al menos 4 commits con mensajes claros
- [ ] Hice `git push` y verifiqué mi fork en GitHub
- [ ] Entregué el enlace de mi fork en Classroom
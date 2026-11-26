# Plantilla de examen con banco de problemas (xsim)

Plantilla en LaTeX para exámenes del curso **Fundamentación en Física** (302133,
Universidad de Antioquia), con banco de problemas y soluciones conmutables,
usando el paquete [xsim](https://ctan.org/pkg/xsim).

- **Overleaf:** <https://www.overleaf.com/project/6b0862db0a86c5748e890b7f> (sincronizado con este repositorio).
- **Sistema de calificación y banco de problemas:** repositorio `restrepo/calificador-examenes`
  (skills `banco-examenes` y `calificador-parcial`).

## Cómo se usa

Cada problema es un entorno `exercise` con su `solution` justo debajo:

```latex
\begin{exercise}[ID=caida, subtitle={Caída libre}, tags={examen}, points=50]
  Enunciado...
\end{exercise}
\begin{solution}
  Solución...
\end{solution}
```

| Quiero… | Cambio |
|---|---|
| Elegir qué problemas van en el examen | La etiqueta de cada problema (`tags={examen}` se imprime; `tags={banco}` queda guardado) y la línea `\xsimsetup{tags={examen}}` del bloque «Selección del examen» |
| Imprimir el solucionario | `\solucionestrue` (también muestra lo que va dentro de `\phantom`) |
| Ocultar «(50 puntos)» | `\mostrarpuntosfalse` |
| Empezar un problema en página nueva | `nuevapagina=true` en sus opciones |
| Dejar sin preguntar una parte de un problema | `\begin{comment}…\end{comment}` dentro del problema |
| Reutilizar un problema en otro examen | Copiar el par `exercise` + `solution` y cambiarle la etiqueta |

El bloque entre `% --- xsim:` y `% --- fin xsim ---` es el estándar del curso: no
lo modifique. Resuelve dos problemas conocidos de xsim: en español, babel activa
`<` y `>` (y rompe opciones de TikZ como `>=stealth`), y el paquete `comment` no
funciona dentro de un `exercise` (aquí `comment` se define con `environ`).

Compila con `pdflatex` (dos pasadas). En Overleaf funciona tal cual.

## Con Claude

En una sesión de Claude Code con el repositorio `calificador-examenes`, la skill
`banco-examenes` lista todos los problemas de los exámenes, arma el PDF del banco
con o sin soluciones y monta un examen, taller o quiz nuevo con los problemas que
se elijan, en este mismo formato. Ese archivo se pega como `main.tex` de un
proyecto de Overleaf hecho a partir de esta plantilla.

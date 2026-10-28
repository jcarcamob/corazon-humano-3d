# Corazón humano 3D

Visualización educativa e interactiva del corazón en three.js: ciclo cardíaco, arritmias e infartos por oclusión coronaria. Es una sola página estática (`index.html`), sin build ni backend.

> **Aviso:** material educativo y simplificado. No es una herramienta clínica ni de diagnóstico.

## Uso

Abre `index.html` en el navegador o sírvelo con cualquier servidor estático:

```bash
python3 -m http.server 8000
```

Requiere conexión a internet para cargar three.js r128 (cdnjs) y las fuentes (Google Fonts).

## Qué incluye

- **Anatomía procedural:** superficie única generada con un campo de distancia (SDF) y surface nets. Incluye ventrículos, aurículas, orejuelas, grandes vasos, surcos con grasa y árbol coronario trazado sobre los surcos.
- **Arritmias (9):** sinusal normal, taquicardia, bradicardia, fibrilación auricular, flutter 2:1, extrasístoles ventriculares, taquicardia ventricular, fibrilación ventricular y bloqueo AV completo. En TV y FV se puede desfibrilar.
- **Infartos (3):** oclusión de descendente anterior, circunfleja o coronaria derecha. La zona irrigada se vuelve isquémica y acinética, y el ECG cambia de derivación con supradesnivel del ST.
- **Monitor:** ECG, presión arterial, FC, FE y gasto cardíaco, calculados por un modelo de elastancia variable (no son valores fijos).
- **Vista de flujo:** partículas de sangre y válvulas animadas, cámara lenta, etiquetas y sonido.

## Estructura

Todo vive en `index.html`, en tres bloques de script:

| Módulo | Función |
|---|---|
| `HeartGeom` | Geometría (SDF, malla, territorios coronarios, coronarias). Corre también en Node. |
| `SimCore` | Simulación sin DOM: eventos eléctricos, hemodinámica y síntesis de ECG. |
| App | Render three.js, deformación en GPU (`onBeforeCompile`), interfaz y monitor. |

## Desplegar

Funciona sin cambios en GitHub Pages o Cloudflare Pages (subida directa del archivo). Para endurecerlo, agrega `integrity` y `crossorigin` (SRI) a la etiqueta de three.js, o sirve three.js desde el mismo proyecto.

## Créditos

La anatomía y el código de colores (arterias en rojo, venas en azul, válvulas en celeste) se inspiran en [Interactive-3D-Human-Heart-Visualization](https://github.com/simonreisinger/Interactive-3D-Human-Heart-Visualization). No se usan sus modelos: provienen de BodyParts3D (CC BY-SA 2.1 JP) y aquí la geometría se genera por código.

## Licencia

[MIT](LICENSE)

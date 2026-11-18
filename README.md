# Monitoreo de calidad de agua · ECA Categoría 3 (Perú)

Aplicación web 100 % estática (HTML + JavaScript, sin dependencias ni servidor) para registrar muestras de agua,
compararlas estadísticamente y generar un informe de monitoreo con interpretación según el
**D.S. N.º 004-2017-MINAM, Categoría 3 (D1 Riego de vegetales / D2 Bebida de animales)**.

## Qué hace
- **Registro por muestra:** código, grupo/punto, día, hora, UTM (zona, Este, Norte), reactivos (observación),
  SST, SSV, DBO₅, DQO, turbidez (NTU), pH, temperatura, alcalinidad, grasas y aceites.
- **Estadística descriptiva:** n, media, mediana, DE, CV %, mín., máx. (global y por grupo).
- **Estadística inferencial:** t de una muestra vs. ECA (H₁: media > límite), Welch (2 grupos) o ANOVA (≥3 grupos),
  Kruskal-Wallis (no paramétrico) y correlación de Pearson con valor p.
- **Informe:** encargado de monitoreo, códigos, día, hora, coordenadas UTM, reactivos, marco legal, resultados vs. ECA,
  interpretación, conclusiones y espacio de firmas. Se exporta a **PDF** (Imprimir → Guardar como PDF) o **Word (.doc)**.
- Los datos se guardan en el navegador (`localStorage`) y se pueden exportar/importar en JSON o CSV.

## Publicar en GitHub
1. Crea un repositorio nuevo (p. ej. `monitoreo-eca3`) y sube estos archivos.
2. En **Settings → Pages**, elige *Deploy from a branch* → `main` → `/ (root)`.
3. Tu app quedará en `https://TU_USUARIO.github.io/monitoreo-eca3/`.

## Límites ECA incluidos (editables en la pestaña Estadística)
| Parámetro | D1 Riego | D2 Bebida animales |
|---|---|---|
| Aceites y grasas | 5 mg/L | 10 mg/L |
| DBO₅ | 15 mg/L | 15 mg/L |
| DQO | 40 mg/L | 40 mg/L |
| pH | 6,5 – 8,5 | 6,5 – 8,4 |
| Temperatura | Δ 3 °C respecto a la T de referencia | Δ 3 °C |

SST, SSV, turbidez y alcalinidad **no tienen valor en la Categoría 3**: se reportan solo de forma descriptiva.
Verifica los límites con el texto oficial del D.S. 004-2017-MINAM antes de emitir un informe.

## Limitaciones
- Con n pequeño las pruebas tienen poca potencia; no se incluye prueba de normalidad (se ofrece Kruskal-Wallis como alternativa).
- Valores "menor al límite de detección" deben ingresarse como número (p. ej. el LD o LD/2, según tu criterio) y aclararse en el informe.

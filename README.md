# Etiquetador de prendas

Sistema que etiqueta automáticamente imágenes de ropa: identifica **el tipo de prenda** (KNN) y **sus colores dominantes** (K-Means). Con ambas etiquetas se pueden hacer búsquedas tipo `"red shirt"` o `"pink dress"` en una tienda online.

## Cómo funciona

1. **Forma → KNN.** Cada imagen se describe con *shape features* (descriptor de silueta) y se clasifica en una de las 8 categorías: Dresses, Shirts, Jeans, Shorts, Sandals, Flip Flops, Socks y Handbags.
2. **Color → K-Means.** Agrupa los píxeles RGB en unos pocos colores dominantes y los traduce a nombres (Red, Blue, Black, White...).
3. **Búsqueda.** Combina la etiqueta de forma y la de color para filtrar productos.

## Archivos

| Archivo | Qué hace |
|---|---|
| `KNN.py` | Algoritmo KNN, predice el tipo de prenda. |
| `Kmeans.py` | K-Means para detectar colores dominantes. |
| `shape_features.py` | Extrae la silueta (foreground_mask, garment_mask, skin_mask...). |
| `utils.py` | Funciones de apoyo (RGB → gris, color → probabilidades). |
| `utils_data.py` | Carga imágenes y etiquetas del dataset. |
| `app.py` | Aplicación web sencilla para usar el sistema. |
| `analysis.py` | Prueba parámetros y compara resultados. |

## Resultados

- **KNN:** K=1 con shape features → **91.09%** de accuracy (vs. 72.02% con píxeles en gris, +19.07 pp).
- **K-Means:** `find_bestK` elige el número de colores automáticamente (para cuando la mejora del WCD baja del 20%), con inicialización **kmeans++**.

## Uso

```bash
python app.py
```

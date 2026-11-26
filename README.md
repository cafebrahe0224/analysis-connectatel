# ConnectaTel: análisis del comportamiento de uso de clientes

Análisis exploratorio de uso de llamadas y mensajes de ConnectaTel (México y Colombia, datos hasta 2024): calidad de datos, perfil de uso por usuario, valores atípicos, segmentación y recomendaciones comerciales.

## Datasets

| Archivo | Contenido |
|---|---|
| `plans.csv` | Catálogo de planes: precio, minutos, mensajes y GB incluidos, costo por extra |
| `users_latam.csv` | 4,000 clientes: edad, ciudad, fecha de registro, plan, fecha de baja |
| `usage.csv` | 40,000 eventos de uso: llamadas (duración) y mensajes (longitud) |

Los archivos no se incluyen en el repositorio. Colócalos en `data/`.

## Etapas

1. Carga y exploración
2. Diagnóstico de calidad de datos (nulos, centinelas, fechas)
3. Limpieza
4. Perfil de uso por usuario
5. Distribuciones y valores atípicos (histogramas, boxplots, IQR)
6. Segmentación por uso y por edad
7. Conclusiones y recomendaciones

## Principales hallazgos

- El plan contratado no distingue el comportamiento: Básico y Premium tienen la misma mediana de uso.
- La edad tampoco explica el uso.
- Premium concentra cerca del 53% del ingreso mensual por suscripción con el 35% de los usuarios.
- Las diferencias de baja entre segmentos son pequeñas (entre 10.5% y 14.0%).

## Ejecución

```bash
pip install -r requirements.txt
jupyter notebook connectatel_analysis.ipynb
```

El notebook lee los datos de `data/` (o de `/datasets` si existe).

## Limitaciones

- Sin datos de facturación ni de consumo de GB.
- `reg_date` no es confiable (25% del uso es anterior al alta), por lo que no se analiza antigüedad.
- La edad de 55 usuarios es imputada con la mediana.

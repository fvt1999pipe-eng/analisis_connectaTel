# 📱 Análisis de clientes de ConnectaTel

Análisis exploratorio del comportamiento de uso de los clientes de **ConnectaTel**, una empresa de telecomunicaciones con operaciones en México y Colombia. El objetivo es entender cómo los clientes usan los servicios móviles (llamadas y mensajes), detectar comportamientos atípicos y segmentarlos para optimizar la oferta comercial.

---

## 🎯 Objetivo del proyecto

Construir una visión clara, confiable y accionable del uso real de los servicios, para responder las siguientes preguntas del negocio:

- ¿Qué segmentos de clientes usan más o menos las llamadas y los mensajes?
- ¿Qué usuarios presentan valores atípicos que puedan indicar comportamientos inusuales, fraude o errores de registro?
- ¿Cómo varía el uso según la edad y el tipo de plan contratado?
- ¿Qué patrones pueden ayudar a diseñar mejores planes y mejorar la satisfacción del cliente?

---

## 📂 Datasets utilizados

| Archivo | Filas | Descripción |
|---|---|---|
| `plans.csv` | 2 | Catálogo de planes (Básico y Premium): precio mensual, minutos, mensajes y GB incluidos, y costo por consumo extra. |
| `users_latam.csv` | 4.000 | Información de los clientes: edad, ciudad, fecha de registro, plan contratado y fecha de cancelación (churn). |
| `usage.csv` | 40.000 | Registros de uso durante 2024: tipo de evento (llamada o mensaje), fecha, duración de las llamadas y longitud de los mensajes. |

---

## 🔄 Etapas del análisis

1. **Carga y exploración**: estructura, tipos de datos y dimensiones de cada dataset.
2. **Identificación de problemas de calidad**: valores nulos, sentinels (`-999` en edad, `"?"` en ciudad) y fechas fuera de rango (años 2026).
3. **Limpieza de datos**: reemplazo de sentinels, conversión de fechas y validación de que los nulos de `duration` y `length` dependen del tipo de registro.
4. **Estadísticas descriptivas**: agregación del uso por usuario (mensajes, llamadas y minutos) y unión con la información de clientes.
5. **Visualización y outliers**: histogramas por plan, boxplots y cálculo de límites con el método IQR.
6. **Segmentación de clientes**: por nivel de uso (Bajo, Medio y Alto) y por edad (Joven, Adulto y Adulto Mayor).
7. **Insight

---

## 💡 Principales hallazgos

- El cliente típico consume poco: una mediana de **5 mensajes, 4 llamadas y 19,8 minutos**.
- Los clientes **Básico y Premium tienen el mismo patrón de consumo**, aunque el Premium cuesta más del doble.
- El uso real está **muy por debajo** de lo incluido en los planes (media de 23 minutos frente a 100 y 600 incluidos).
- Los outliers representan **clientes intensivos reales**, no errores ni fraude.
- **Recomendación principal**: rediseñar la oferta con un plan de entrada más económico y un Premium que se diferencie por valor y no por volumen.

---

## 🛠️ Herramientas

- Python 3
- pandas
- matplotlib
- seaborn
- Jupyter Notebook / Google Colab

---

## ▶️ Cómo ejecutar el notebook

### Opción 1: Google Colab (recomendada)

1. Abre [Google Colab](https://colab.research.google.com/).
2. Ve a **Archivo → Abrir cuaderno → GitHub**.
3. Pega la URL de este repositorio y selecciona el notebook del proyecto.
4. Sube los tres archivos CSV desde el panel lateral **Archivos** (ícono de carpeta).
5. Ejecuta todas las celdas con **Entorno de ejecución → Ejecutar todas**.

### Opción 2: Jupyter en local

```bash
git clone <URL-de-este-repositorio>
cd <nombre-del-repositorio>
pip install pandas matplotlib seaborn jupyter
jupyter notebook
```

---

## 🔁 Guía de reproducción

1. Descarga los tres datasets: `plans.csv`, `users_latam.csv` y `usage.csv`.
2. Colócalos en una carpeta accesible desde el notebook.
3. Ajusta las rutas de carga si es necesario. El notebook usa rutas del tipo `/datasets/archivo.csv`:

```python
   plans = pd.read_csv('/datasets/plans.csv')
   users = pd.read_csv('/datasets/users_latam.csv')
   usage = pd.read_csv('/datasets/usage.csv')
```

   - En **Colab**, si subiste los archivos al panel lateral, cambia la ruta a `'/content/plans.csv'` (y lo mismo para los otros dos).
   - En **local**, usa la ruta relativa, por ejemplo `'data/plans.csv'`.

4. Ejecuta las celdas **en orden**: cada paso depende de la limpieza y las transformaciones del anterior.
5. Los resultados (tablas, gráficos y segmentos) deben coincidir con los del notebook publicado.

---

## 👤 Autor

**Felipe**: análisis de datos del proyecto ConnectaTel.

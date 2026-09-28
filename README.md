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

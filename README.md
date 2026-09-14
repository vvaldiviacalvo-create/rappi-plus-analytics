# 🛵 RappiPlus: Análisis de Comportamiento, Margen y Experimento A/B

Este proyecto analiza el desempeño integral del servicio **RappiPlus** para identificar oportunidades de crecimiento y eficiencia operativa. A través de la integración de registros transaccionales, catálogo de productos, gasto publicitario y analítica de producto, se evalúan la rentabilidad unitaria, el comportamiento del usuario en el embudo y la efectividad del rediseño de pago.

### 🛠️ Herramientas

[![Python](https://img.shields.io/badge/PYTHON-3776AB?style=for-the-badge&logo=python&logoColor=white)]()
[![Pandas](https://img.shields.io/badge/PANDAS-150458?style=for-the-badge&logo=pandas&logoColor=white)]()
[![SciPy](https://img.shields.io/badge/SCIPY-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white)]()
[![Power BI](https://img.shields.io/badge/POWER_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)]()
[![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white)]()

---

### ❓ Preguntas Clave

1. ¿Existen inconsistencias o valores atípicos en los registros de ventas que distorsionen los KPIs financieros?
2. ¿Cuáles canales de adquisición y mercados generan mayor Margen Neto en relación con su CAC?
3. ¿En qué etapas del embudo se pierden usuarios y cómo se comporta la retención por semana?
4. ¿El rediseño de la interfaz de Checkout genera un impacto estadísticamente significativo en la conversión?

---

### 🛠️ Metodología

 * **Depuración**: Limpieza de +25k órdenes a 24,600 entradas válidas y Winsorización al p99 para outliers.
 * **Modelado Financiero**: Recálculo de Margen Bruto, Ganancia Neta y CAC por canal/país.
 * **Analítica de Retención**: Matrices de cohortes a 6 meses y embudos de conversión en SQL/Python.
 * **Pruebas A/B**: Validación estadística con prueba Chi-cuadrada en SciPy.
 * **Dashboarding Interactivo**: Diseño de un reporte en Power BI (Overview Ejecutivo y Desempeño) para el seguimiento de KPIs clave (Revenue, Profit, Gasto Marketing, Ticket Promedio) y análisis de concentración de ventas por producto.

---

### 💡 Conclusiones y Recomendaciones

#### **Conclusiones:**

 * La corrección de precios base y descuentos reales evitó sobreestimaciones en el revenue.
 * Se detectó alta fuga en canales de adquisición de pago respecto al tráfico orgánico.
 * No se encontró evidencia estadística de que el cambio en la UI mejore la conversión, por lo que no se justifica su despliegue sin antes iterar el diseño.

#### **Recomendaciones:**

 * Detener el despliegue de la nueva interfaz de pago. Se sugiere iterar la propuesta de diseño y reevaluar mediante un nuevo test antes de comprometer recursos de desarrollo.
 * Priorizar la inversión publicitaria en canales orgánicos y de búsqueda de alta intención, reduciendo el gasto en campañas pagadas de baja retención para controlar el CAC y proteger el Margen Neto.
 * Foco en productos de mayor margen y recurrencia (como electrónica y tecnología) mediante campañas de cross-selling dirigidas a frenar el churn a partir del segundo mes en la matriz de cohortes.
 * Implementar reglas de validación en la capa de captura transaccional para evitar inconsistencias en precios base y asegurar un seguimiento financiero preciso en los dashboards de Power BI.

---

### 📖 Diccionario de Datos

Cada registro representa una transacción u orden dentro de la plataforma:

* **`id_pedido`**: Identificador único de la transacción.
* **`fecha`**: Fecha de emisión del pedido.
* **`id_usuario`**: Identificador único del cliente.
* **`pais`**: Mercado donde se realizó la compra.
* **`categoria`**: Categoría del producto adquirido.
* **`precio_unitario`**: Precio base registrado.
* **`canal_adquisicion`**: Origen del tráfico (`organic`, `paid_search`, `social`).
* **`grupo_experimento`**: Asignación del test A/B (`Control` vs. `Treatment_UI`).

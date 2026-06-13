# 🛒 Análisis Correlacional de Factores de Comportamiento — NovaRetail+ 2024

## 🧩 Contexto del negocio
NovaRetail+ es una plataforma de comercio electrónico en Latinoamérica.
El equipo de Crecimiento y Retención busca identificar qué factores del comportamiento del cliente están más fuertemente asociados con el ingreso anual generado.

> ⚠️ Este análisis es estrictamente **correlacional** (exploratorio).  
> **Correlación ≠ causalidad.**

## 🎯 Preguntas de negocio
1. ¿Qué variables numéricas tienen mayor correlación con `ingreso_anual`?
2. ¿El estatus Premium o el abandono están asociados con mayores ingresos?
3. ¿El tipo de dispositivo o la región geográfica influyen en el ingreso?

## 🚀 Análisis Extendido — Iniciativa Propia
Adicional a los entregables del proyecto, se plantearon 4 preguntas de negocio propias para profundizar en los patrones detectados:

1. ¿El co-movimiento publicidad-visitas varía entre dispositivos?
2. ¿Y entre regiones geográficas?
3. ¿La tasa de abandono es homogénea entre regiones?
4. ¿Y entre tipos de dispositivo?

> Si el churn es ciego al valor económico, ¿será también ciego a la geografía y al canal de acceso?

## 🛠️ Herramientas y librerías
- **Python** — pandas · numpy · seaborn · matplotlib · scipy
- **Métodos estadísticos:** Pearson · Spearman · Punto Biserial · V de Cramér
- **Fuente:** novaretail_comportamiento_clientes_2024.csv (15,000 registros)

## 🔍 Pipeline de análisis
1. **Ingesta y EDA** — Carga, auditoría estructural y perfil estadístico
2. **Preparación** — Corrección de tipos y documentación de supuestos
3. **Visualización** — Heatmap de correlaciones y scatterplots bivariados
4. **Evidencia numérica** — Pearson, Spearman, Punto Biserial y V de Cramér
5. **Hallazgos** — 3 hallazgos principales con implicaciones de negocio
6. **Limitaciones** — Alcance del análisis y próximos pasos
7. **Análisis extendido** — 4 preguntas adicionales por iniciativa propia

## 💡 Hallazgos principales

**Hallazgo 1 — Redundancia del Volumen de Transacciones:**
`compras_mes` e `ingreso_anual` tienen correlación 0.967 — colinealidad confirmada. No incluir ambas en modelos predictivos.

**Hallazgo 2 — El Motor Publicitario y la Brecha de Conversión:**
`gasto_publicidad_dirigida` ↔ `visitas_mes` (Pearson 0.579) — la publicidad atrae tráfico pero no garantiza conversión (correlación publicidad-ingreso: solo 0.20).

**Hallazgo 3 — La Paradoja del Churn Ciego al Valor:**
Punto Biserial abandono-ingreso = -0.003 — el churn es completamente independiente del valor económico del cliente.

## 🔍 Hallazgos del Análisis Extendido

**Publicidad vs Visitas:** Correlación invariante al canal (~0.58) y a la geografía (~0.57-0.60) — el driver publicitario es estructural, no segmentado.

**Churn Triple Ciego:** El abandono es homogéneo entre regiones (14.43%-15.75%) y entre dispositivos (14.89%-15.60%) — confirma que el churn no responde a ninguna segmentación detectada. 
Se recomienda investigar disparadores cualitativos: UX, fricción en pagos, tiempos de soporte.

## 📁 Archivos del repositorio
- `novaretail_analisis_correlacional_2024.ipynb` — Pipeline completo
- `novaretail_analisis_correlacional_2024.csv` — Dataset exportado

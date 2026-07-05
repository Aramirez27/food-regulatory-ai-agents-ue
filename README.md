# 🤖 Food Regulatory AI Agents Ecosystem

Este ecosistema consiste en el diseño, arquitectura y despliegue de agentes inteligentes de IA multimodales capaces de realizar de forma automática auditorías de listas de ingredientes y etiquetas alimentarias bajo marcos legales internacionales.

La arquitectura está diseñada de forma modular por regiones independientes, facilitando la auditoría de alérgenos (Visión/OCR), la detección de aditivos regulados o prohibidos y el análisis predictivo de riesgos microbiológicos.

---

## 🗂️ Estructura de Carpetas del Proyecto

*   **[`/EU-Agent`](./EU-Agent):** Módulo especializado en la normativa de la Unión Europea.
*   **[`/FDA-Agent`](./FDA-Agent):** Módulo especializado en la normativa de la FDA (Estados Unidos).

---

## 🇪🇺 Fase 1: Unión Europea (Reglamento UE Nº 1169/2011)

El agente de esta sección evalúa alérgenos obligatorios, alertas de la EFSA (como la prohibición del Dióxido de Titanio E-171) y riesgos de estabilidad bajo el clima europeo.

👉 **[Ver lógica de Prompt de la UE](./EU-Agent/prompt_eu.txt)**

### 📊 Benchmarking de Modelos de Lenguaje (UE)
Sometido a una matriz crítica de prueba: *"Harina enriquecida, azúcar, grasa vegetal de palma, suero de leche en polvo, lecitina de soya, dióxido de titanio. Conservación: 35 °C por 60 días en envase abierto."*

*   **Precisión Regulatoria:** **GPT-4o** incurrió en omisiones graves de auditoría al no detectar la falta de destaque tipográfico en los alérgenos.
*   **Rigor Científico:** **Gemini Lite (Flash)** demostró un excelente desempeño técnico-jurídico y agilidad.
*   **Análisis Avanzado:** **Gemini Pro** se posicionó como el modelo óptimo, detectando con precisión reológica que a 35 °C la grasa de palma se funde y el suero de leche absorbe humedad (higroscópico), disparando la actividad de agua ($a_w$) y propiciando hongos toxigénicos.

---

## 🇺🇸 Fase 2: Estados Unidos (FDA - 21 CFR)

Agente optimizado para el cumplimiento de las directrices de la **FDA**, evaluando los 9 alérgenos mayores bajo las leyes **FALCPA** y **FASTER Act**, controlando aditivos por sus nombres comunes y sustancias **GRAS** (21 CFR Part 170-189).

👉 **[Ver lógica de Prompt de la FDA (USA)](./FDA-Agent/prompt_fda.txt)**

### 🧪 Matriz de Prueba Actual (En Desarrollo)
Actualmente preparando el set de datos e ingredientes críticos para realizar el benchmark del mercado americano.

---

## 🚀 Próximos Pasos (Roadmap)
1. **Fase 3 (LATAM):** Diseño del agente enfocado en normativas de Latinoamérica (Mercosur/Codex Alimentarius).
2. **Orquestación Multi-Agente:** Creación de un Agente Director que reciba un empaque global y delegue el análisis en paralelo a los expertos de la UE, FDA y LATAM.

### 📅 Cronología del Proyecto
* **Fase de Investigación y Concepto:** Finales de Junio 2026
* **Despliegue de Arquitectura (UE & FDA):** Julio 2026
* **Fase 3 (LATAM):** En desarrollo activo


# 🤖 Food Regulatory AI Agents Ecosystem

Este ecosistema consiste en el diseño, arquitectura y despliegue de agentes inteligentes de IA multimodales capaces de realizar de forma automática auditorías de listas de ingredientes y etiquetas alimentarias bajo marcos legales internacionales.

La arquitectura está diseñada de forma modular por regiones independientes, facilitando la auditoría de alérgenos (Visión/OCR), la detección de aditivos regulados o prohibidos y el análisis predictivo de riesgos microbiológicos.

---

## 🗂️ Estructura de Carpetas del Proyecto

*   **[`/EU-Agent`](./EU-Agent):** Módulo especializado en la normativa de la Unión Europea.
*   **[`/FDA-Agent`](./FDA-Agent):** Módulo especializado en la normativa de la FDA (Estados Unidos).

---

---

## 🇪🇺 Fase 1: Unión Europea (Reglamento UE Nº 1169/2011)

El agente de esta sección evalúa alérgenos obligatorios, alertas de la EFSA (como la prohibición del Dióxido de Titanio E-171) y riesgos de estabilidad bajo el clima europeo.

👉 **[Ver lógica de Prompt de la UE](./EU-Agent/prompt_eu.txt)**

### 📊 Benchmarking de Modelos de Lenguaje (UE)
Sometido a una matriz crítica de prueba: *"Harina enriquecida, azúcar, grasa vegetal de palma, suero de leche en polvo, lecitina de soya, dióxido de titanio. Conservación: 35 °C por 60 días en envase abierto."*

*   **Evolución del Modelo (GPT-4o / GPT-4o mini):** En las primeras fases de desarrollo, las versiones estándar de GPT incurrían en omisiones graves al no identificar que los alérgenos carecían de distinción tipográfica. Tras **blindar el System Prompt con reglas críticas de auditoría**, el modelo (evaluado en su versión GPT-4o mini) logró detectar con precisión quirúrgica el incumplimiento del Artículo 21 del Reglamento 1169/2011 por falta de formato destacado, además de rechazar de inmediato el aditivo prohibido E-171.
*   **Análisis Avanzado:** **Gemini Pro** se mantiene como el modelo óptimo en la parte científica del benchmark, detectando con precisión reológica que a 35 °C la grasa de palma se funde y el suero de leche absorbe humedad (higroscópico), disparando la actividad de agua ($a_w$) y propiciando hongos toxigénicos.

---

### 🧪 Reporte de Auditoría Optimizado (Resultados del Benchmark UE)

<details>
<summary><b>🤖 Desplegar Reporte de Auditoría - GPT-4o mini (Prompt Blindado)</b></summary>

*   **Texto extraído / Datos de la imagen:** Harina de trigo enriquecida, azúcar, grasa vegetal de palma, suero de leche en polvo, lecitina de soya (E-322), dióxido de titanio (E-171). Instrucciones de empaque: Una vez abierto, mantener a temperatura ambiente de 35ºC por 60 días.
*   **Cumplimiento de Reg. 1169/2011 (Alérgenos):**
    *   Alérgenos detectados: Wheat (harina de trigo), Milk (suero de leche en polvo), Soy (lecitina de soya).
    *   No se observa declaración explícita de alérgenos en un formato destacado (por ejemplo, en negrita o con un color de fondo diferente) como lo exige el Artículo 21 del Reglamento 1169/2011.
    *   La falta de un formato de declaración claro y destacado para los alérgenos representa un **INCUMPLIMIENTO REGULATORIO INMEDIATO**.
*   **Estatus de Aditivos de la EFSA (Alertas de Seguridad):**
    *   El dióxido de titanio (E-171) ha sido clasificado como no seguro para su uso como aditivo alimentario por la EFSA, y su uso está estrictamente prohibido en la UE bajo el Reglamento (UE) 2022/63.
    *   La presencia de E-171 en la lista de ingredientes representa un incumplimiento crítico de la normativa vigente.
*   **Riesgo Bromatológico y Microbiológico:**
    *   Las instrucciones de empaque indican mantener el producto a 35ºC por 60 días una vez abierto. Esta temperatura es alta y puede favorecer el crecimiento de microorganismos, especialmente si el producto es higroscópico.
    *   La falta de un empaque hermético puede aumentar el riesgo de absorción de humedad y, por lo tanto, de crecimiento microbiano, lo que podría comprometer la seguridad del producto.
*   **Veredicto Final:** **NO CONFORME CON LA NORMATIVA DE LA UE**.
    *   INCUMPLIMIENTO REGULATORIO por falta de declaración de alérgenos en formato destacado.
    *   Uso de dióxido de titanio (E-171) prohibido en la UE.
    *   Las condiciones de almacenamiento propuestas no son adecuadas para garantizar la estabilidad microbiológica y la calidad del producto.
</details>

---

## 🇺🇸 Fase 2: Estados Unidos (FDA - 21 CFR)

Agente optimizado para el cumplimiento de las directrices de la **FDA**, evaluando los 9 alérgenos mayores bajo las leyes **FALCPA** y **FASTER Act**, controlando aditivos por sus nombres comunes y sustancias **GRAS** (21 CFR Part 170-189).

👉 **[Ver lógica de Prompt de la FDA (USA)](./FDA-Agent/prompt_fda.txt)**

### 📊 Benchmarking de Modelos de Lenguaje (FDA)
Sometido a una matriz crítica de prueba: *"Enriched flour (wheat flour, niacin, reduced iron), sugar, vegetable shortening (partially hydrogenated soybean oil), semisweet chocolate chips (sugar, chocolate liquor, cocoa butter, soy lecithin), natural flavor, fd&c yellow no. 5, tahini (sesame paste). Storage: Store in a warm warehouse at 90 °F (32 °C) for up to 90 days in a highly permeable non-hermetic packaging."*

* **Precisión Regulatoria:** **GPT-4o** identificó las deficiencias del formato de alérgenos y el sésamo (FASTER Act). Sin embargo, en su primera versión incurrió en una omisión legal grave al clasificar el *aceite parcialmente hidrogenado (PHO)* como una simple falta de etiquetado de grasas trans, ignorando que la FDA prohibió su uso por completo al retirarle el estatus GRAS. El error se corrigió blindando las instrucciones del System Prompt.
* **Análisis Técnico y Científico:** **Gemini Pro** demostró un desempeño sobresaliente y un rigor científico impecable desde su primera interacción. No solo identificó la prohibición directa del PHO por la FDA, sino que aportó un análisis bromatológico avanzado: estimó con precisión la actividad de agua del producto ($a_w \approx 0.60 - 0.80$), predijo el desarrollo de mohos xerófilos y detalló el fenómeno reológico de la fusión de grasas (*fat bloom*) provocado por las condiciones térmicas críticas del empaque.

---

### 🧪 Reportes Completos de Auditoría (Resultados del Benchmark FDA)

<details>
<summary><b>🤖 Desplegar Reporte de Auditoría - GPT-4o</b></summary>

* **Texto extraído / Datos de la imagen:** Enriched flour (wheat flour, niacin, reduced iron), sugar, vegetable shortening (partially hydrogenated soybean oil), semisweet chocolate chips (sugar, chocolate liquor, cocoa butter, soy lecithin), natural flavor, FD&C Yellow No. 5, tahini (sesame paste). Storage: Store in a warm warehouse at 90 °F (32 °C) for up to 90 days in a highly permeable non-hermetic packaging.
* **Cumplimiento de FALCPA / FASTER Act (Alérgenos):**
  * Alérgenos detectados: Trigo (derivado de la harina enriquecida), Soya (derivada del aceite de soya y la lecitina de soya), Sésamo (derivado del tahini).
  * La declaración de alérgenos es implícita pero no está resaltada explícitamente ni se presenta en una declaración tipo "Contains:" (Contiene) o entre paréntesis claros. Según la sección 21 CFR 101.2(c), los alérgenos deben declararse claramente, ya sea en la lista de ingredientes (entre paréntesis) o en una declaración independiente de "Contains:". Esta etiqueta carece de una declaración explícita de alérgenos.
  * El sésamo está reconocido como el 9° alérgeno mayor bajo la ley FASTER Act y debe declararse por su nombre común de forma obligatoria; el uso exclusivo del término "tahini" es insuficiente.
* **Estatus de Aditivos Alimentarios y GRAS de la FDA:**
  * El colorante **FD&C Yellow No. 5 (Tartrazina)** es un aditivo cromático aprobado por la FDA que requiere certificación. Su presencia está declarada correctamente por su nombre específico.
  * *Fallo Crítico del Modelo:* El modelo identificó el *aceite de soya parcialmente hidrogenado* como un problema menor de etiquetado de grasas trans. Omitió que la FDA retiró formalmente el estatus **GRAS** (Generally Recognized as Safe) a los aceites parcialmente hidrogenados (PHOs), por lo que su uso en alimentos procesados está estrictamente prohibido, induciendo a un error legal grave (corregido posteriormente mediante prompt engineering).
* **Evaluación de Riesgo Microbiológico y Estabilidad:**
  * El almacenamiento a 90 °F (32 °C) en un empaque no hermético y altamente permeable durante 90 días incrementa drásticamente la absorción de humedad del ambiente. Esto eleva la actividad de agua ($a_w$), facilitando el desarrollo de mohos toxigénicos en productos de panadería.
  * Un empaque altamente permeable acelera la oxidación de las grasas (rancidez lipídica) debido a la exposición constante al oxígeno a altas temperaturas, además de provocar el endurecimiento prematuro del producto.
  * Se dictamina el uso mandatorio de empaques herméticos con barrera contra la humedad y el oxígeno, así como almacenamiento en ambientes controlados y frescos.
* **Veredicto Final:** RECHAZADO CON OBSERVACIONES (REJECTED WITH OBSERVATIONS).
  * Los alérgenos (especialmente el sésamo) deben declararse explícitamente según FALCPA/FASTER Act.
  * Las condiciones de empaque y almacenamiento son críticas y no garantizan la estabilidad microbiológica ni la vida útil del producto.
  * *Incumplimiento Crítico:* Reformulación obligatoria del producto para eliminar los aceites parcialmente hidrogenados (PHOs) por prohibición expresa de la FDA.
</details>

<details>
<summary><b>✨ Desplegar Reporte de Auditoría - Gemini Pro</b></summary>

* **Texto extraído / Datos de la imagen:** Enriched flour (wheat flour, niacin, reduced iron), sugar, vegetable shortening (partially hydrogenated soybean oil), semisweet chocolate chips (sugar, chocolate liquor, cocoa butter, soy lecithin), natural flavor, fd&c yellow no. 5, tahini (sesame paste). Storage: Store in a warm warehouse at 90 °F (32 °C) for up to 90 days in a highly permeable non-hermetic packaging.
* **Cumplimiento de FALCPA / FASTER Act (Alérgenos):**
  * Wheat (Trigo): Presente como harina de trigo (Alérgeno mayor bajo FALCPA).
  * Soy (Soya): Presente como lecitina de soya y aceite de soya parcialmente hidrogenado (Alérgeno mayor bajo FALCPA).
  * Sesame (Sésamo/Ajonjolí): Presente como tahini (pasta de sésamo). Bajo la ley FASTER Act, el sésamo es oficialmente el 9° alérgeno mayor y debe declararse de forma explícita.
  * Observación formativa: Aunque los alérgenos de origen son técnicamente identificables dentro de la lista, debe imprimirse una declaración formal e independiente tipo "Contains: Wheat, Soy, Sesame" directamente debajo de la lista para asegurar el cumplimiento total de la FDA.
* **Estatus de Aditivos Alimentarios y GRAS de la FDA:**
  * **FD&C Yellow No. 5:** Este aditivo cromático está sujeto a una estricta certificación de la FDA. Bajo la sección 21 CFR 74.705, debe declararse obligatoriamente por su nombre común ("FD&C Yellow No. 5" o "Yellow 5") debido a reacciones de tipo alérgico en individuos sensibles. La nomenclatura aquí cumple, pero el lote utilizado debe estar certificado por la FDA.
  * 🛑 **Aceite de Soya Parcialmente Hidrogenado (PHO) - INFRACCIÓN CRÍTICA:** La FDA retiró el estatus GRAS (Generally Recognized as Safe) a los aceites parcialmente hidrogenados debido a su contenido de grasas trans. Los fabricantes de alimentos tienen estrictamente prohibido añadir PHOs a los alimentos humanos.
* **Evaluación de Riesgo Microbiológico y Estabilidad:**
  * Condiciones de almacenamiento: Almacenar una galleta de textura blanda (que típicamente exhibe una actividad de agua intermedia, $a_w \approx 0.60 - 0.80$) a 90 °F (32 °C) durante 90 días en un empaque altamente permeable y no hermético representa un riesgo severo para la inocuidad.
  * Riesgo Microbiológico: El empaque permeable permite el intercambio de humedad con el ambiente. Las altas temperaturas (90 °F) combinadas con el ingreso de humedad aceleran el crecimiento de mohos xerófilos y levaduras osmófilas.
  * Estabilidad Química y Reológica: A 32 °C, la manteca de cacao de las chispas de chocolate y las grasas de la manteca vegetal superarán sus puntos de fusión. Esto provocará un "fat bloom" masivo (migración y recristalización de grasa), pérdida de la integridad estructural (colapso/fusión de las galletas) y una rápida rancidez oxidativa catalizada por el calor y la exposición al oxígeno.
* **Veredicto Final:** RECHAZADO CON OBSERVACIONES (REJECTED WITH OBSERVATIONS)
  * Este producto no puede ser aprobado para su comercialización debido a la inclusión de una sustancia expresamente prohibida (aceite parcialmente hidrogenado) y parámetros de almacenamiento inseguros que comprometen tanto la seguridad química como la microbiológica del alimento.
</details>

---

## 🚀 Próximos Pasos (Roadmap)
1. **Fase 3 (LATAM):** Diseño del agente enfocado en normativas de Latinoamérica (Mercosur/Codex Alimentarius).
2. **Orquestación Multi-Agente:** Creación de un Agente Director en Coze que reciba un empaque global y delegue el análisis en paralelo a los expertos de la UE, FDA y LATAM.

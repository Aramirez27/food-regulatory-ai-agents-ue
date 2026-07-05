# 🤖 Sistema de IA para Auditoría Bromatológica y Asuntos Regulatorios (Normativa Unión Europea)

Este proyecto consiste en el diseño y despliegue de un agente inteligente de IA (desarrollado en la plataforma Coze) capaz de realizar auditorías automáticas de listas de ingredientes y etiquetas alimentarias. El sistema cuenta con capacidades multimodales (visión artificial y OCR) para evaluar alérgenos directamente desde imágenes de empaques reales, detectar aditivos regulados o prohibidos y realizar un análisis predictivo de riesgos microbiológicos y físico-químicos basados en las instrucciones de conservación.

> 🚀 **Nota de desarrollo (Roadmap):** Esta es la **Fase 1** del proyecto enfocado en la Unión Europea. La arquitectura está diseñada para escalar hacia un sistema multi-agente orquestado por un Agente Director que delegará análisis a expertos de EE.UU. (FDA) y LATAM (Mercosur/Codex).

---

## 📝 Ingeniería de Prompts (Prompt Engineering)

A continuación se detalla la lógica de instrucciones (*System Prompt*) optimizada para este agente, dotándolo de capacidades de lectura de texto plano y procesamiento de imágenes sin pérdida de rigor científico:

```markdown
Actúa como un Auditor Senior de Calidad y Asuntos Regulatorios en Tecnologías de Alimentos. Tu objetivo es analizar listas de ingredientes de productos alimentarios que te proporcione el usuario (ya sea en formato de texto directo o mediante imágenes/fotografías de etiquetas y empaques reales) para identificar posibles alérgenos ocultos, evaluar riesgos físico-químicos y dictaminar sobre la coherencia de su conservación.

[PROCESAMIENTO DE IMÁGENES Y CAPACIDAD VISUAL]
Si el usuario proporciona una imagen o fotografía:
1. Extrae mediante visión artificial (OCR) el texto completo de la lista de ingredientes, aditivos y leyendas de conservación. No omitas ningún término por secundario que parezca.
2. Analiza el formato gráfico/visual: Verifica si los alérgenos identificados cumplen con el Artículo 21 del Reglamento (UE) Nº 1169/2011, el cual exige que se destaquen obligatoriamente mediante una composición tipográfica que los diferencie claramente del resto (ej. negrita, MAYÚSCULAS, color contrastante o subrayado). Si aparecen en texto plano sin resaltar, indícalo como un incumplimiento formal.

[MARCO REGULATORIO]
Debes regir tus dictámenes estrictamente bajo:
1. El Reglamento (UE) Nº 1169/2011 del Parlamento Europeo (sobre la información alimentaria facilitada al consumidor) para la declaración obligatoria de alérgenos.
2. Las normativas de la EFSA (European Food Safety Authority) y FDA para el uso de aditivos y dosis permitidas. 

[INSTRUCCIONES]
1. Identifica los alérgenos obligatorios presentes según el Reglamento UE 1169/2011. Si se procesó una imagen, evalúa si su presentación visual en la etiqueta cumple la normativa.
2. Alerta sobre aditivos (códigos E-) sospechosos o que requieren advertencias específicas en la etiqueta. 
3. Evalúa si la conservación declarada es apta para la composición descrita, estimando riesgos microbiológicos y físico-químicos potenciales según la legislación alimentaria europea. 

[ESTRUCTURA DE LA SALIDA]
### 📊 REPORTE DE AUDITORÍA BROMATOLÓGICA (NORMATIVA UE)
- **Texto / Datos Extraídos de la Imagen:** [Transcripción de ingredientes]
- **Cumplimiento del Reg. 1169/2011 (Alérgenos):** [Lista de alérgenos y formato visual]
- **Alertas de Aditivos (EFSA/FDA):** [Análisis de aditivos]
- **Evaluación Microbiológica y Estabilidad:** [Riesgo según conservación]
- **Veredicto Final:** [APROBADO o RECHAZADO CON OBSERVACIONES]



## 📊 Benchmarking de Modelos de Lenguaje (LLMs)

Para evaluar el rigor científico y la precisión legal del prompt, se sometió el sistema a una matriz crítica de prueba (*"Harina enriquecida, azúcar, grasa vegetal de palma, suero de leche en polvo, lecitina de soya, dióxido de titanio. Conservación: 35 °C por 60 días en envase abierto"*). 

A continuación, se presenta el análisis comparativo estructurado por criterios de auditoría (haz clic en cada sección para desplegar las respuestas reales de cada IA):

<details>
<summary><b>🔍 1. Cumplimiento del Reg. 1169/2011 (Alérgenos)</b></summary>

*   **🧠 GPT-4o:** *Se detectan los siguientes alérgenos obligatorios según el Reglamento UE 1169/2011: Trigo (gluten), Leche (suero de leche en polvo), Soja (lecitina de soya E-322).* 
    > ⚠️ **Fallo de Auditoría:** Validó el etiquetado como correcto, pasando por alto que la lista provista carecía del destaque tipográfico obligatorio.
*   **⚡ Gemini Lite (Flash):** *Trigo (Gluten): Presente en la "harina de trigo enriquecida". Leche y sus derivados (incluida la lactosa): Presente en el "suero de leche en polvo". Soja: Presente en la "lecitina de soya". Observación Normativa: Según el Artículo 21 del Reglamento (UE) Nº 1169/2011, todos los alérgenos deben destacarse... La lista proporcionada no cumple con este requisito de diferenciación visual.*
*   **👑 Gemini Pro:** *Gluten: Presente de forma directa en la harina de trigo enriquecida. Leche y sus derivados (incluida lactosa): Alérgeno oculto bajo la denominación de suero de leche en polvo. Soja y productos a base de soja: Presente en la lecitina de soya. Observación de Etiquetado: El Reglamento (UE) Nº 1169/2011 exige que estos tres ingredientes se destaquen obligatoriamente... La formulación actual no cumple.*
</details>

<details>
<summary><b>🚨 2. Alertas de Aditivos (EFSA/FDA)</b></summary>

*   **🧠 GPT-4o:** *Lecitina de soya (E-322): Aditivo emulsionante permitido... Dióxido de titanio (E-171): En la Unión Europea, su uso en alimentos está prohibido desde 2022 debido a preocupaciones sobre su seguridad (posible genotoxicidad). Por tanto, su presencia en el producto es no conforme y requiere retiro o reformulación inmediata.*
*   **⚡ Gemini Lite (Flash):** *Dióxido de titanio (E-171): 🚨 NO CONFORME. Su uso está estrictamente prohibido en la UE según el Reglamento (UE) 2022/63. La EFSA dictaminó que ya no puede considerarse seguro debido a que no se puede descartar su genotoxicidad... Aunque la FDA estadounidense lo permite en cantidades que no excedan el 1%...*
*   **👑 Gemini Pro:** *Dióxido de titanio (E-171): 🚨 ADITIVO NO CONFORME (CRÍTICO). Según el Reglamento (UE) 2022/63, el uso de dióxido de titanio está estrictamente prohibido... La EFSA determinó que no se puede descartar su genotoxicidad. Aunque la FDA permite su uso como colorante (máx. 1%), su presencia hace que el producto sea ilegal para el mercado europeo.*
</details>

<details>
<summary><b>🌡️ 3. Evaluación Microbiológica y Estabilidad</b></summary>

*   **🧠 GPT-4o:** *La conservación a temperatura ambiente de hasta 35ºC por 60 días puede ser adecuada para un producto seco... siempre que el envase sea hermético... Sin embargo, la presencia de suero de leche puede aumentar el riesgo... 35ºC es un poco elevado para mantener la estabilidad óptima, aunque es aceptable si el producto está bien envasado.*
    > ⚠️ **Fallo de Auditoría:** El prompt especificaba que el producto se encontraba en **envase abierto**, por lo que asumir hermeticidad es un error crítico de evaluación de riesgo.
*   **⚡ Gemini Lite (Flash):** *Estabilidad de la matriz: Los azúcares y el suero de leche son altamente higroscópicos. Riesgo Físico-Químico (Severo): A 35 °C, la grasa vegetal de palma está en su punto de fusión... provocará migración de grasas y rápida oxidación lipídica... Riesgo Microbiológico: El aw aumentará drásticamente, favoreciendo la proliferación de mohos toxigénicos (Aspergillus, Penicillium) y levaduras osmófilas...*
*   **👑 Gemini Pro:** *Riesgo Físico-Químico: La indicación de mantener el producto abierto a 35 °C por 60 días es técnicamente errónea. A esa temperatura, la grasa vegetal de palma experimentará una severa aceleración de la oxidación lipídica y separación de fases, ya que se encuentra cerca de su punto de fusión... Riesgo Microbiológico: ...crea un ambiente ideal para la proliferación rápida de mohos de almacenamiento (Aspergillus spp., Penicillium spp.) y levaduras osmófilas, representando un riesgo directo de deterioro y formación de micotoxinas.*
</details>

<details>
<summary><b>⚖️ 4. Veredicto Final y Exigencias</b></summary>

*   **🧠 GPT-4o:** *RECHAZADO CON OBSERVACIONES. La inclusión del dióxido de titanio (E-171) no cumple... se recomienda revisar las condiciones de conservación... La declaración de alérgenos es correcta y está acorde a la legislación.*
*   **⚡ Gemini Lite (Flash):** *RECHAZADO CON OBSERVACIONES. El producto es inviable... debido al colorante E-171... Adicionalmente, el etiquetado de alérgenos incumple el formato estipulado por el Reg. 1169/2011. Finalmente, el estudio de vida útil debe rediseñarse... Se exige reformulación y ajuste de la leyenda de conservación a "lugar fresco y seco" (típicamente ≤ 25 °C).*
*   **👑 Gemini Pro:** *RECHAZADO CON OBSERVACIONES. El producto es inelegible para comercialización en la UE principalmente por el aditivo prohibido E-171. Se requiere: 1. Eliminar o sustituir el E-171. 2. Modificar la tipografía de la etiqueta para resaltar trigo, soya y leche. 3. Corregir urgentemente las instrucciones a "Mantener en un lugar fresco y seco..." reduciendo el tiempo de vida útil una vez abierto según estudios de estabilidad adecuados.*
</details>

### 🎯 Conclusiones del Benchmarking

1. **Precisión Regulatoria:** **GPT-4o** incurrió en dos omisiones graves de auditoría al no detectar el envase abierto en el análisis térmico y validar un formato de alérgenos que viola el Reg. 1169/2011.
2. **Rigor Científico:** **Gemini Lite (Flash)** demostró un excelente desempeño técnico-jurídico y agilidad, siendo el único en citar artículos específicos (Art. 21).
3. **Análisis Avanzado:** **Gemini Pro** se posicionó como el modelo óptimo para producción gracias a su comprensión avanzada de la reología de alimentos (punto de fusión y separación de fases de las grasas), bioquímica (higroscopía) y toxicología alimentaria (riesgo de micotoxinas).

# 🌎 LATAM Regulatory Auditor Agent

Este módulo contiene la lógica, prompts y arquitectura de enrutamiento para la auditoría bromatológica automatizada en **América Latina**, cubriendo un espectro de **20 países** divididos en 4 macro-bloques regulatorios.

El agente cuenta con capacidades **multimodales (Visión + OCR)**, lo que le permite extraer ingredientes desde fotografías de empaques reales y evaluar el cumplimiento visual del etiquetado.

## 🗂️ Contenido de la Carpeta
* **[`prompt_latam.txt`](./prompt_latam.txt):** Contiene el System Prompt optimizado y blindado para modelos LLM (GPT-4o mini, Gemini Pro).
* **`architecture_latam.json`:** Matriz de mapeo de países y leyes asociadas para integraciones vía API.

## ⚙️ Funcionamiento del Enrutador Geográfico

El agente actúa como un "enrutador virtual". Cuando el usuario sube un texto o una imagen, el flujo sigue los siguientes pasos lógicos:

```text
[Entrada: Ingredientes + País] 
             │
             ▼
   ¿País especificado? 
     ├── NO ──> [Solicitar aclaración al usuario: "Indique el país de destino"]
     └── SÍ ──> [Identificar Macro-Bloque]
                    ├── México ───────────────> (NOM-051)
                    ├── MERCOSUR ─────────────> (Resoluciones GMC)
                    ├── Alianza del Pacífico ─> (Leyes de Sellos Frontales)
                    └── Centroamérica/Caribe ─> (RTCA / Codex)
```
📋 Criterios Críticos de Evaluación por Bloque
Octágonos de Advertencia y Sellos: Monitoreo y proyección de advertencias frontales en México, Chile, Colombia y Perú (los marcos más estrictos en azúcares, sodio y grasas).

Leyendas para Niños: Identificación de edulcorantes y cafeína para activación de alertas obligatorias (específico de la NOM-051 en México).

Destaque de Alérgenos: Verificación por visión artificial de que los alérgenos estén tipográficamente resaltados en los bloques donde la norma nacional lo exija.




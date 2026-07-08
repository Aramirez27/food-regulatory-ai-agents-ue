# 🌎 LATAM Regulatory Auditor Agent (Hierarchical Architecture)

Este módulo contiene la lógica, prompts y la arquitectura de enrutamiento para la auditoría bromatológica automatizada en **América Latina**, diseñada para cubrir un espectro de **20 países** mediante un sistema jerárquico en cascada liderado por un **Sub-Director Regional**.

El agente cuenta con capacidades **multimodales (Visión + OCR)**, lo que le permite extraer ingredientes desde fotografías de empaques reales, evaluar tablas nutricionales y verificar el cumplimiento visual del etiquetado frontal.

---

## 🗂️ Nueva Estructura del Módulo
*   📄 **`sub_director_latam.md`:** El agente orquestador regional (Cerebro de LATAM). Recibe la consulta, identifica el país y delega el análisis al sub-auditor correspondiente.
*   📁 **`paises/`:** Carpeta que alojará de forma independiente los prompts de los 20 países.
    *   📄 **`argentina_ley27642.md`:** 🚀 *¡Activo y en fase de pruebas!* Primer agente local implementado, configurado con un criterio pragmático de inspección y un **Semáforo de Riesgo Regulatorio**.
    *   *Próximamente:* Chile (Ley 20.606), México (NOM-051) y los 17 países restantes.

---

## ⚙️ Funcionamiento del Enrutador Geográfico (En Cascada)

Cuando el usuario ingresa un empaque al ecosistema global, el **Director Global** lo deriva a este módulo, donde el **Sub-Director de LATAM** ejecuta el siguiente flujo lógico:

```text
[Entrada: Datos + País de LATAM] 
             │
             ▼
     ¿País desarrollado? 
       ├── NO ──> [Aplicar Codex Alimentarius (FAO/OMS) como arbitraje preventivo]
       └── SÍ ──> [Activar Agente Local en /paises/]
                     ├── Argentina ────> (Ley 27.642 + Semáforo de Riesgo Pragmático) 🟢🟡🔴
                     ├── México ───────> (Próximamente - NOM-051)
                     ├── Chile ────────> (Próximamente - Ley 20.606)
                     └── Otros 17 ─────> (En desarrollo activo)
```

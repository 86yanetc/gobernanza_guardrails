# AegisForensic LLM Guardrails OWASP & Forensics <img src="./imagenes/framework-owasp-llm-forensics-logo.jpg" width="100" align="right">

**Framework de Cumplimiento Normativo, Mitigación OWASP & Auditoría Forense de LLMs**

<div align="right">
  <em>"Donde el cumplimiento regulatorio se encuentra con la eficiencia operativa: Un servidor de inspección en capas diseñado para que los modelos de lenguaje empresariales operen bajo un marco estricto, auditable, libre de fugas de privacidad y blindado contra alucinaciones factuales.."</em>
</div>

**Desarrollado por: Msc. Yanet Cesaire Velazquez**

👉 **[Probar Aplicación de Gobernanza & Guardrails](https://86yanetc.github.io/gobernanza_guardrails/)**

## 📖 Glosario de Términos de Alta Ingeniería

**NIST AI RMF 1.0 (National Institute of Standards and Technology - Artificial Intelligence Risk Management Framework)**: Marco de Gestión de Riesgos de Inteligencia Artificial.

**GDPR (General Data Protection Regulation):** Reglamento General de Protección de Datos de la Unión Europea (en español, RGPD). Entró en vigor en 2018 y es el estándar de oro mundial para la privacidad en internet.

**HIPAA (Health Insurance Portability and Accountability Act):** Ley de Portabilidad y Responsabilidad del Seguro Médico de los Estados Unidos (promulgada en 1996).

## 🏙️ Visión Arquitectónica

El Framework **AegisForensic** no es un simple validador de texto; es una infraestructura de **Gobernanza y Ciberseguridad de Grado Industrial** diseñada para interceptar, evaluar y mitigar los riesgos inherentes al despliegue de Modelos de Lenguaje de Gran Escala (LLMs) en la empresa. Actúa como una capa perimetral (Proxy de Seguridad) que se interpone entre las peticiones de los usuarios y los motores de inferencia. El sistema resuelve de raíz las cuatro grandes fricciones del Gobierno de IA: **Fugas de Información Confidencial (PII), Inyecciones de Prompt Maliciosas, Cumplimiento Regulatorio (Compliance) y Trazabilidad Forense.**

## 💡 Preguntas Clave de Gobernanza y Mitigación de Riesgos

**1. ¿Por qué implementar un pipeline secuencial en capas en lugar de un único modelo de seguridad masivo?**

Ningún modelo de Inteligencia Artificial es 100% infalible ante ataques adversarios (Jailbreaks). Basar la seguridad en una sola capa expone a la organización a un punto único de falla. El pipeline en capas aplica el principio de Defensa en Profundidad (Defense in Depth) recomendado por el NIST AI RMF 1.0. Al segmentar el control (Fase 0: Sintáctica, Fase 1: Probabilística, Fase 2: Temática, Fase 3: Factual) garantizamos que si una inyección burla la primera barrera, sea capturada de forma redundante por las capas subsecuentes, minimizando el riesgo residual de la operación.

**2. ¿Cómo equilibra el sistema las exigencias estrictas de privacidad con la usabilidad del negocio?**

Un enfoque de cumplimiento normativo tradicional (como un cortafuegos rígido) bloquearía cualquier prompt que contenga un correo o número telefónico para evitar multas de GDPR o HIPAA. Sin embargo, esto destruiría la utilidad del bot para flujos comerciales reales. AegisForensic LLM Guardrails resuelve esta fricción mediante la Sanitización de Doble Vía con Máscaras Amigables. El filtro local de la Fase 0 destruye el dato sensible real de forma local en la CPU en 0.07 ms (cumpliendo con la ley), pero inyecta tokens sintéticos conversacionales inofensivos (tarjeta-visa-del-cliente) que permiten que el negocio continúe y el LLM central procese la transacción de forma ordinaria.

**3. ¿Bajo qué criterio económico y operativo se justifican los Circuit Breakers tempranos?**

La gobernanza corporativa efectiva incluye la gestión del riesgo financiero (FinOps Governance). Evaluar un prompt malicioso a través de toda la infraestructura consume tiempo de procesamiento, degrada la experiencia del usuario por latencia y genera gastos masivos por tokens en la nube (Denial of Wallet). La implementación de cortocircuitos basados en umbrales matemáticos estrictos (threshold = 0.60) permite que el orquestador actúe como un filtro de excepción: ante la detección de un Jailbreak en la Fase 1, se aborta la ejecución en milisegundos, logrando un 95% de ahorro en costos operativos y protegiendo el presupuesto de la organización.

**4. ¿Por qué auditar de forma pos-generativa la salida del sistema si el contexto proviene de fuentes de datos corporativas (RAG)?**

Existe el riesgo crítico de la Sobreconfianza automatizada (Overreliance, OWASP LLM09), donde la junta directiva asume que el bot siempre dirá la verdad solo porque lee PDFs oficiales de la empresa. No obstante, los LLMs sufren de alucinaciones semánticas nativas debido a su naturaleza probabilística. La Fase 3 actúa como un Auditor Factual Independiente: no confía en la salida del modelo central; obliga a un evaluador neutro a aplicar razonamiento desglosado (Chain-of-Thought) para certificar la fidelidad factual antes de la entrega final. Esto mitiga el riesgo reputacional y legal de entregar información falsa o inventada a un cliente.

**5. ¿Cómo garantiza el servidor la trazabilidad de las decisiones automatizadas ante una auditoría regulatoria externa?**

Una política de gobernanza moderna exige transparencia técnica inmutable. Cada transacción procesada por AegisForensic LLM Guardrails genera una bitácora estructurada que asocia la estampa de tiempo (Timestamp), el veredicto del orquestador y los Commit SHAs exactos de los pesos binarios de Hugging Face utilizados en la moderación. Estos logs se clasifican automáticamente bajo las etiquetas oficiales de riesgo del Top 10 de OWASP. Esto expone una traza forense transparente y verificable que demuestra ante reguladores estatales o auditores externos que la Inteligencia Artificial de la compañía opera bajo control estricto y conforme a los estándares internacionales.

## ⚠️ Desafíos Reales de Gobernanza y Guardrails

**1. El Conflicto de Intereses entre Cumplimiento y Negocio (Gobernanza de Entrada)**

**El desafío real:** La directriz de gobernanza exige cumplir con leyes estrictas de privacidad (como GDPR). El camino fácil y "seguro" de un Oficial de Riesgos tradicional sería bloquear cualquier prompt que contenga un correo o un número para evitar multas legales. Pero si hacés eso, destruís el negocio porque el bot deja de ser útil para que los empleados atiendan clientes (ej: procesar un pago de Juan).

**Solución de guardrail:** Resolviste esta fricción implementando un Filtro de Sanitización de Doble Vía. Se logró que el sistema cumpla con la ley (borrando el dato real de forma local en la CPU en 0.07 ms) pero manteniendo la continuidad del negocio al permitir que la transacción avance usando tokens sintéticos inofensivos. Encontraste el punto de equilibrio exacto entre cumplimiento legal estricto y usabilidad operativa.

**2. El Desafío del Cortocircuito del Riesgo frente al Desperdicio Financiero (FinOps Governance)**

**El desafío real:** El marco NIST AI RMF y el estándar OWASP exigen auditar exhaustivamente cada prompt contra inyecciones y taxonomías complejas. Sin embargo, evaluar secuencialmente un ataque masivo a través de múltiples LLMs en la nube genera una latencia inaceptable para el usuario y destruye el presupuesto de la empresa en tokens innecesarios (Denial of Wallet).

**Solución de guardrail:** Se diseño una Estrategia de Mitigación en Cascada con Circuit Breakers Estadísticos. En lugar de evaluar todo al mismo tiempo, se calibró el orquestador para que actúe como un tribunal de apelaciones: si el clasificador rápido de la Capa 1 (Prompt Guard 2) detecta un Jailbreak que supera el umbral probabilístico de 0.60, se activa un cortocircuito inmediato. Se aborta el resto del pipeline en milisegundos, garantizando la seguridad del clúster mientras registrás un 95% de ahorro financiero. Se gobernó el riesgo de seguridad gobernando el riesgo financiero.

**3. La Paradoja de la Confianza y la Auditoría de Salida (Overreliance)**

**El desafío real:** El riesgo más complejo de gobernanza actual según OWASP (LLM09) es el "exceso de confianza" (Overreliance). Las empresas implementan sistemas RAG asumiendo que el bot siempre dirá la verdad porque tiene acceso a los PDFs corporativos, pero los modelos de lenguaje tienden a alucinar de forma nativa. ¿Cómo gobernar la veracidad de un sistema sin poner a un humano a leer cada respuesta en tiempo real?

**Solución de guardrail:** Se implemento un Auditor Factual Pos-Generativo Automatizado. Se diseñó un mecanismo de control de calidad que no confía en el modelo central. Forzás a una capa secundaria (Llama Instruct / Granite) a aplicar una técnica de razonamiento neutro (Chain-of-Thought) que contrasta de forma matemática la salida contra las premisas lógicas del documento de origen. Si la fidelidad cae por debajo del umbral de cumplimiento, el Circuit Breaker final veta la entrega. Garantizaste una traza de auditoría inmutable que certifica que el sistema es una fuente de verdad regulada




```mermaid
graph TD
    %% Estilos de Nodos Industriales
    classDef entrada fill:#f8f9fa,stroke:#3c4043,stroke-width:2px,color:#3c4043;
    classDef fase fill:#fff3e0,stroke:#ef6c00,stroke-width:2px,color:#e65100;
    classDef motor fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px,color:#1b5e20;
    classDef breaker fill:#ffebee,stroke:#c62828,stroke-width:2px,color:#b71c1c;

    %% Nivel de Entrada
    IN[✉️ Prompt Crudo del Empleado o Cliente]:::entrada
    
    subgraph Perimetro_Filtros [🛡️ Ecosistema Perimetral de Guardrails]
        
        %% FASE 0
        F0["⚙️ FASE 0: Filtro PII Local Sintáctico (CPU)"]:::fase
        F0_1["• Destrucción local de datos privados en 0.07 ms<br>• Suavizado semántico en minúsculas<br>• Cumplimiento Nativo GDPR / HIPAA"]
        
        %% FASE 1
        F1["🤖 FASE 1: Llama Prompt Guard 2 (22M)"]:::fase
        F1_1["• Filtro probabilístico de Jailbreaks / DAN<br>• OWASP LLM01: Mitigación de Prompt Injection"]
        B1["⚠️ CIRCUIT BREAKER 1:<br>Aborta la petición al superar umbral de riesgo (0.60)"]:::breaker
        
        %% FASE 2
        F2["🛡️ FASE 2: Llama Guard 3 8B (Input Moderation)"]:::fase
        F2_1["• Taxonomía temática de seguridad MLCommons (S1-S14)<br>• Parser robusto inmune a variaciones de formato"]
        B2["⚠️ CIRCUIT BREAKER 2:<br>Mitiga exploits de malware / ciberdelitos"]:::breaker
    end

    %% Capa Central de Procesamiento
    subgraph Engine_Cognitivo [🧠 Procesamiento Central]
        LLM_GEN[LLM Generativo Central]:::motor
        LLM_PROC[Procesamiento y Generación de Respuesta]:::motor
    end

    %% Capa Post-Inferencia (Salida)
    subgraph Validacion_Salida [🔍 Capa de Auditoría Forense]
        F3["👁️ FASE 3: Auditor RAG de Salida (Llama Instruct)"]:::fase
        F3_1["• Validación factual cruzada Chain-of-Thought<br>• Contraste lógico de la respuesta contra el PDF<br>• OWASP LLM09: Mitigación de Overreliance"]
        B3["⚠️ CIRCUIT BREAKER 3:<br>Veto inmediato de alucinaciones"]:::breaker
    end

    %% Entrega Final
    OUT[📜 Respuesta Conforme y Certificada]:::entrada

    %% Conectividad y Flujo del Pipeline Secuencial
    IN --> F0
    F0 --- F0_1
    F0 --> F1
    F1 --- F1_1
    F1 -->|Evaluación de Riesgo > 0.60| B1
    F1 -->|Filtro Exitoso| F2
    F2 --- F2_1
    F2 -->|Detección de Malware| B2
    F2 -->|Payload Seguro| LLM_GEN
    
    %% Flujo Central y Auditoría de Salida
    LLM_GEN --> LLM_PROC
    LLM_PROC --> F3
    F3 --- F3_1
    F3 -->|Detección de Alucinación| B3
    F3 -->|Validación Exitosa| OUT

    %% Enlaces de Cierre de los Circuit Breakers
    B1 & B2 & B3 -->|Interrupción del Proceso| OUT

    %% Clases
    class IN,OUT entrada;
    class F0,F1,F2,F3 fase;
    class LLM_GEN,LLM_PROC motor;
    class B1,B2,B3 breaker;
```


# 📘 DOCUMENTO TÉCNICO Y HOJA DE RUTA
## VCDs Automation - Sistema de Diagnóstico Inteligente para Audi A3 8L

**Versión del Documento:** 1.2 (Actualizado con Roadmap Extendido)  
**Fecha:** 19 de Abril, 2026  
**Vehículo:** Audi A3 8L (1.9 TDI PD) - WAUZZZ8L83A055890  
**Plataforma de Despliegue:** Portátil Windows 10 (Entorno Aislado)  
**Desarrollador:** Dnk29k

---

## 1. 🎯 ¿Qué es este proyecto?

Este sistema es un **Asistente Técnico Inteligente y Seguro** diseñado exclusivamente para tu Audi A3 8L. No es un simple lector de códigos OBD; es una herramienta de diagnóstico avanzada que combina:
- 🔌 **Hardware profesional VAG-COM (HEX-V2)** para comunicación directa con las centralitas.
- 🧠 **Inteligencia Artificial Local (Qwen 2.5)** para interpretar fallos en lenguaje técnico pero comprensible.
- 🛡️ **Protocolos de Seguridad Estrictos** que garantizan que ninguna acción se ejecute sin tu supervisión.

El objetivo es transformar un escaneo genérico en un **plan de mantenimiento preventivo y diagnóstico accionable**, ahorrando tiempo, dinero y evitando intervenciones innecesarias en taller.

---

## 2. 🛡️ Seguridad y Control (Principios Innegociables)

Dado que el sistema interactúa con la electrónica del vehículo, la seguridad es la prioridad absoluta:

| Principio | Implementación |
|-----------|----------------|
| 🔒 **Confirmación Humana Obligatoria** | Cualquier acción que modifique el coche (borrar DTCs, escribir codificaciones, resetear contadores) requiere tu autorización explícita `[S/N]`. |
| 💾 **Backup Automático Pre-Intervención** | Antes de tocar un módulo, se genera una copia de seguridad criptográfica de su configuración. Siempre hay vuelta atrás. |
| 🌐 **100% Offline y Privado** | Toda la IA y la base de conocimiento corren en tu portátil. **Ningún dato del VIN, kilometraje o fallos sale a internet.** |
| 📜 **Auditoría Inmutable** | Cada acción queda registrada en `logs/` con timestamp, hash SHA-256 y resultado. Transparencia total. |

---

## 3. ✅ Funcionalidades Actualmente Implementadas (Fases 0-5)

El sistema ya está probado y operativo en entorno de simulación. Estas son las capacidades listas para despliegue:

### 🧠 1. Diagnóstico Asistido por IA
- Interpreta códigos crudos (ej: `P1261`, `01367`) y explica **qué falla, por qué y qué probabilidades hay**.
- Prioriza causas por coste y dificultad (ej: *"Revisa cableado antes de cambiar inyector"*).
- Incluye advertencias de seguridad específicas para cada sistema.

### 📚 2. Base de Conocimiento Técnica Local
- Contiene valores de referencia verificados para el 1.9 TDI AXR (bloques de medida, tolerancias, TSBs VAG).
- El agente **solo sugiere datos técnicos reales**, eliminando alucinaciones o recomendaciones genéricas.

### 🎮 3. Menú Interactivo y Ejecución Guiada
- Te permite leer bloques de medida, guardar backups o salir con un solo comando.
- Cada opción muestra descripción técnica y herramientas necesarias antes de ejecutarse.

### 📦 4. Exportación de Tareas (`tasks.yaml`)
- Genera planes de diagnóstico estructurados que puedes guardar, imprimir o seguir paso a paso sin depender del portátil en el momento.

---

## 4. 🗺️ Hoja de Ruta: Próximas Fases de Desarrollo

Una vez conectado el sistema a tu portátil Windows 10 (Fase 6), se activarán módulos avanzados diseñados específicamente para un vehículo de **309.900 km**. Estas funcionalidades se desplegarán de forma escalonada para garantizar estabilidad:

### 🔌 FASE 6: Conector Real Windows (Inmediata)
- **Objetivo:** Puente entre el software y el adaptador HEX-V2 físico.
- **Qué aporta:** Comunicación directa con las centralitas del A3 8L. Lectura real de módulos, escritura segura y sincronización de tiempos VCDS.
- **Estado:** En desarrollo final. Requiere tu portátil Windows 10 para validación.

### 📄 FASE 7: Informes Profesionales y Control ITV
- **🖨️ Exportación a PDF Técnico:** Genera documentos listos para imprimir con: VIN, software de centralitas, lista de fallos con descripción, bloques congelados (Freeze Frame) y recomendaciones del agente. Ideal para llevar a un taller o documentar el estado pre-venta.
- **🔄 Monitor de Readiness (Preparación ITV):** Interpreta los bits `0 0 X X X` del escaneo. Te avisa si el motor está listo para emisiones o si necesitas hacer ciclos de conducción antes de pasar la inspección técnica. Evita suspensiones por "No Listo".

### 📊 FASE 8: Historial SQLite y Data Logger
- **📈 Registro de Evolución de Fallos:** Base de datos local que guarda cada escaneo en el tiempo. Podrás consultar: *"¿El P1261 es nuevo o lleva apareciendo 6 meses?"*, *"¿Se borró sin reparar?"*, *"¿Qué backups existen?"*.
- **📉 Data Logger (Grabadora de Datos en Vivo):** Graba bloques de medida cada 500ms durante periodos definidos. Detecta tendencias invisibles en lecturas puntuales: *"La presión de rail cae un 15% tras 40s en ralentí → posible fallo N75 o bomba secundaria"*.
- **⚖️ Comparador de Cilindros:** Lee el Bloque 018 (contribución de cilindros) y genera un análisis de desbalance. *"El cilindro 1 aporta -4.5 mg/stk vs -1.2 del resto. Desbalance >300%: confirma inyector N240 o compresión baja."*

### 🎛️ FASE 9: Asistente de Codificación y Voz
- **🔤 Traductor de Bytes a Humano:** VCDS muestra cadenas como `00001011`. El agente las traduce: *"Bit 3 activo = Aguja de combustible en reserva habilitada. ¿Quieres desactivarlo?"*.
- **📖 Recetas de Personalización:** Guías paso a paso para activar funciones ocultas (barrido de agujas, confirmación de cierre, etc.) con backup automático y confirmación por bit.
- **🗣️ Interfaz por Voz (Hands-Free):** Usa `whisper.cpp` (ligero, offline) para comandos como *"Agente, lee bloque 13"* o *"Guarda backup"*. El sistema responde en voz alta con los valores. Ideal cuando tienes las manos ocupadas bajo el capó.

---

## 5. 📋 Guía de Uso Operativo (Una vez instalado en tu portátil)

1.  **Preparación:** Conecta el HEX-V2 al puerto USB del portátil y al conector OBD del Audi (bajo el salpicadero, lado conductor).
2.  **Ejecución:** Abre la terminal y lanza el comando correspondiente:
    - `python run.py scan` → Escaneo rápido de fallos.
    - `python run.py diagnose P1261` → Diagnóstico profundo del inyector.
    - `python run.py diagnose P1261 --export-task` → Genera plan de acción en `tasks.yaml`.
3.  **Interacción:** Lee el diagnóstico en pantalla. Usa el menú interactivo para leer bloques, hacer backups o salir.
4.  **Seguridad:** Si decides borrar un fallo o modificar algo, el sistema te pedirá confirmación `[S/N]`. **Nunca actúa solo.**
5.  **Registro:** Todo queda guardado en `logs/` y `backups/`. Puedes revisar el historial cuando quieras.

---

## 6. 💡 ¿Por qué este enfoque es superior para tu A3 8L?

| Taller Genérico / OBD Genérico | VCDs Automation (Tu Sistema) |
|-------------------------------|------------------------------|
| Lee códigos, borra y listo. | Interpreta, prioriza y guía la reparación. |
| Sin historial ni trazabilidad. | Registro completo con timestamps y backups. |
| Riesgo de borrar sin readiness listo. | Monitor de preparación ITV integrado. |
| Depende de la experiencia del mecánico. | Base de conocimiento técnica verificada VAG. |
| Sin control sobre qué se modifica. | Confirmación humana obligatoria + auditoría. |

**Beneficio directo para ti:** 
Con 309.900 km, los fallos intermitentes (`P1261`, `01367`) son comunes. Este sistema te permite **diferenciar entre un fallo eléctrico barato y un desgaste mecánico costoso**, documentar el estado real del vehículo y tomar decisiones informadas sin prisas ni presiones externas.

---

## 7. 📅 Próximos Pasos y Entrega

1.  **Instalación en Portátil:** Configuración limpia de Python, Ollama, VCDS y dependencias en tu Windows 10.
2.  **Validación Fase 6:** Pruebas de conexión real con el HEX-V2 y lectura de módulos físicos.
3.  **Despliegue Escalonado:** Activación de Fases 7, 8 y 9 según confirmación de estabilidad.
4.  **Formación Rápida:** Sesión de 30 minutos para que domines los comandos básicos y el menú interactivo.

---

**Firma del Desarrollador:**  
Dnk29k 
*Arquitecto de Sistemas, Automatización VAG y Diagnóstico Inteligente*  
📧 [Tu Contacto] | 🔒 Código Auditado | 🚗 Especialización A3 8L / 1.9 TDI

---


<img width="2486" height="1362" alt="Captura de pantalla 2026-04-19 132330" src="https://github.com/user-attachments/assets/edadc793-ae77-4e13-ae38-3cfd7b01e2d6" />

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

<img width="2494" height="650" alt="Captura de pantalla 2026-04-19 132347" src="https://github.com/user-attachments/assets/f1fe6192-975d-45ee-95e4-6fb091aa208a" />


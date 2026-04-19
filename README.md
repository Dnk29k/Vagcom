# Vagcom
---

# 📘 PROYECTO: VCDs Automation - Asistente de Diagnóstico Inteligente

**Fecha:** 19 de Abril, 2026  
**Vehículo:** Audi A3 8L (1.9 TDI) - WAUZZZ8L83A055890  
**Operador:** [Tu Nombre]  
**Plataforma de Ejecución:** Portátil Windows 10 (Aislado y Seguro)

---

## 1. 🎯 ¿Qué es este proyecto?

Este no es un simple script de automatización. Es un **Sistema de Asistencia Técnica Inteligente** diseñado específicamente para tu Audi A3 8L.

A diferencia de usar VCDS manualmente, donde uno tiene que saber interpretar códigos crudos (como `P1261` o `01367`), este sistema:
1.  **Interpreta** los fallos usando Inteligencia Artificial Local (Qwen 2.5).
2.  **Explica** en lenguaje humano qué está fallando (ej: "El inyector del cilindro 1 está fuera de rango").
3.  **Guía** paso a paso en cómo verificar el fallo antes de gastar dinero en repuestos.
4.  **Controla** el hardware VAG-COM (HEX-V2) de forma segura.

---

## 2. 🛡️ Seguridad y Control (Lo más importante)

El sistema está diseñado bajo la premisa: **"El humano siempre tiene el mando"**.

*   🔒 **Bloqueo de Seguridad (Safety Lock):** Ninguna acción que pueda modificar el vehículo (como borrar fallos o escribir códigos) se ejecutará sin una **confirmación explícita** `[S/N]`.
*   👁️ **Transparencia Total:** Antes de actuar, el sistema te dice exactamente qué va a hacer.
*   💾 **Backups Automáticos:** Antes de cualquier intervención, se genera una copia de seguridad de la configuración original del módulo. Si algo sale mal, siempre hay vuelta atrás.
*   🧠 **Privacidad 100%:** Toda la "inteligencia" del sistema corre en el portátil, **offline**. Ningún dato del coche sale a internet.

---

## 3. ⚙️ Funcionalidades Clave

El sistema ya cuenta con las siguientes capacidades probadas:

### ✅ 1. Escaneo y Detección de Fallos
Lee automáticamente todos los módulos del coche y filtra solo los que tienen errores.
*   *Estado actual:* Detecta los 12 fallos conocidos de tu coche (Motor, Cierre Centralizado, Inmovilizador, etc.).

### 🧠 2. Diagnóstico Asistido por IA
Al seleccionar un fallo (ej: `P1261 - Inyector N240`), el sistema no solo te da el código, sino:
*   📖 **Descripción:** Qué significa el error.
*   🔍 **Causas Probables:** Ordenadas por probabilidad y coste (ej: "Cableado roto" vs "Inyector roto").
*   📊 **Pasos de Verificación:** Te dice qué bloques de medida leer en VCDS y qué valores buscar para confirmar la avería.
*   ⚠️ **Advertencias de Seguridad:** Avisos específicos (ej: "Cuidado con la presión de combustible").

### 📦 3. Generación de Tareas Ejecutables
Puede exportar un plan de diagnóstico a un archivo (`tasks.yaml`) que contiene todos los pasos recomendados para que puedas seguirlos con calma sin tener el portátil en la mano.

### 🎮 4. Menú Interactivo
El sistema te presenta opciones claras:
*   `[1]` Leer un bloque de medida específico.
*   `[2]` Guardar una copia de seguridad.
*   `[0]` Salir de forma segura.

---

## 4. 🗺️ Estado Actual y Siguientes Pasos

### 🟢 Lo que ya está hecho (Fases 0-5):
*   ✅ Lógica del sistema completa.
*   ✅ Inteligencia Artificial conectada y afinada para motores TDI.
*   ✅ Sistema de seguridad y backups operativo.
*   ✅ Base de conocimiento técnico del A3 8L cargada.

### 🟡 Lo que falta (Fase 6 - Puente de Conexión):
*   Estamos desarrollando el **Driver Real para Windows**.
*   Actualmente, el sistema se prueba en un entorno de simulación (Linux) para garantizar que la lógica es perfecta antes de tocar el coche real.
*   Una vez finalizado el Driver, se trasladará al portátil Windows 10 para la conexión física con el HEX-V2.

---

## 5. 📋 Guía de Uso (Cuando esté listo en tu portátil)

Una vez instalemos todo en tu portátil Windows 10, el flujo de trabajo será muy sencillo:

1.  **Conexión:** Conecta el adaptador HEX-V2 al puerto USB del portátil y al conector OBD del Audi.
2.  **Ejecución:** Abre la terminal y escribe el comando (ej: `python run.py diagnose P1261`).
3.  **Análisis:** Espera unos segundos mientras el "cerebro" del sistema analiza el fallo.
4.  **Lectura:** Verás una pantalla con el diagnóstico, las causas probables y los pasos a seguir.
5.  **Acción:**
    *   El sistema te preguntará: `¿Quieres que ejecute alguna verificación?`.
    *   Tú decides si quieres leer un bloque de medida, hacer un backup o salir.
    *   **Siempre** te pedirá confirmación antes de tocar nada.

---

## 6. 💡 ¿Por qué hacerlo así?

Hacer este desarrollo a medida tiene ventajas frente a usar un taller genérico o programas gratuitos:
1.  **Historial:** Tendrás un registro de cada diagnóstico realizado (fechas, fallos, soluciones).
2.  **Prevención:** Podrás detectar fallos intermitentes (como los del inyector N240) antes de que rompan algo mayor.
3.  **Ahorro:** Te ayuda a saber si el fallo es un simple cable roto (gratis) o una pieza cara, evitando que te engañen en un taller.
4.  **Tranquilidad:** Sabrás exactamente qué estado tiene el coche en todo momento.

---

**Firma del Desarrollador:**  
*Dnk29k*  
*Arquitecto de Sistemas y Automatización*

---

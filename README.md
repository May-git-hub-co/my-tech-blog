# My Tech Blog

## Incident 01

**Title:** Login Authentication Failure

This technical blog documents simulated software incidents, investigations, GitHub workflows, and lessons learned.

### Status

- ✅ Slack notification completed
- ✅ GitHub Issue created
- 🔄 Investigation in progress

## Investigation Summary

### Root Cause

During the investigation, it was identified that the authentication tokens were configured to expire after **15 seconds** instead of the expected **60 minutes**.

### Current Status

- ✅ Root cause identified
- 🔄 Configuration update in progress


## Resolution

The token expiration was updated from **15 seconds** to **60 minutes**.

### Validation

- ✅ Login successful with valid credentials.
- ✅ Tested on Android and iOS.
- ✅ Validated with new and existing users.

### Status

- ✅ Incident resolved
- ✅ QA validation completed
  

<br>
> Una vez restablecido el servicio, el equipo realizó un análisis retrospectivo para identificar oportunidades de mejora.
<br>
<br>

- # 📝 Post-Mortem y Lecciones Aprendidas

## 📌 Resumen del incidente

Una vez implementada la solución e integrada mediante **Pull Request** y **Merge**, el equipo realizó un análisis retrospectivo para documentar la causa del incidente, las acciones ejecutadas y las oportunidades de mejora. El objetivo fue fortalecer el proceso de desarrollo y prevenir que una situación similar vuelva a ocurrir.

<br>

## 🔍 Causa raíz

La investigación permitió identificar que el tiempo de expiración del **token JWT (TTL)** estaba configurado en **15 segundos**, cuando el valor esperado era de **60 minutos**.

Como consecuencia, el servicio rechazaba solicitudes con credenciales válidas devolviendo un **401 (Unauthorized)**, debido a que el backend interpretaba el token como expirado.

### 💡 Factores contribuyentes

* Configuración incorrecta del tiempo de expiración (TTL) del JWT.
* Ausencia de alertas para detectar expiraciones anómalas de tokens.
* Cobertura insuficiente de pruebas automatizadas para escenarios de autenticación.

<br>

## 📈 Impacto del incidente

| Indicador             | Resultado                            |
| --------------------- | ------------------------------------ |
| 👥 Usuarios afectados | Aproximadamente **2.350**            |
| ⏱️ Duración           | **30 minutos**                       |
| ⚙️ Servicio afectado  | **Inicio de sesión y autenticación** |
| 🚨 Severidad          | **Alta**                             |

<br>

## 🛠️ Acciones tomadas

### 🔎 Detección

* Revisión de los logs del servicio de autenticación.
* Análisis de las respuestas **401 (Unauthorized)** y validación del estado de los tokens JWT.
* Identificación de la configuración incorrecta del tiempo de expiración.

### ⚡ Mitigación

* Corrección de la configuración del tiempo de expiración (TTL) del JWT.
* Actualización de la configuración del servicio de autenticación.

### ✅ Verificación

* Validación funcional en **Android** e **iOS**.
* Pruebas con usuarios nuevos y existentes.
* Integración de la solución mediante **Pull Request** y **Merge**.

<br>

## 📚 Lecciones aprendidas

* Definir y documentar los parámetros críticos de autenticación y sus valores esperados.
* Incorporar pruebas automatizadas para escenarios de expiración de JWT y autenticación.
* Validar configuraciones sensibles antes de cada despliegue.
* Fortalecer el monitoreo de los servicios relacionados con autenticación.

<br>

## 🚀 Acciones preventivas

* Implementar alertas para detectar expiraciones anómalas de tokens.
* Agregar validaciones automáticas de configuración durante el proceso de despliegue.
* Revisar periódicamente los tiempos de expiración configurados para JWT.
* Actualizar la documentación técnica y la checklist de despliegue para los servicios de autenticación.

<br>

## 📋 Resumen ejecutivo

| Pregunta                                        | Respuesta                                                                                                                                                      |
| ----------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **¿Qué ocurrió?**                               | Los usuarios no podían iniciar sesión porque los tokens JWT expiraban antes del tiempo esperado.                                                               |
| **¿Por qué ocurrió?**                           | El tiempo de expiración (TTL) del JWT estaba configurado en **15 segundos** en lugar de **60 minutos**.                                                        |
| **¿Qué acciones se tomaron?**                   | Se investigó el incidente mediante revisión de logs, se corrigió la configuración, se validó con QA y la solución fue integrada mediante Pull Request y Merge. |
| **¿Qué acciones preventivas se implementarán?** | Implementar alertas, fortalecer las pruebas automatizadas y validar configuraciones críticas antes de cada despliegue.                                         |

<br>

## 📌 Estado final del incidente

| Estado           | Resultado      |
| ---------------- | -------------- |
| 🐞 Incidente     | ✅ Resuelto     |
| 🔍 Causa raíz    | ✅ Identificada |
| 🔧 Corrección    | ✅ Implementada |
| 🧪 Validación QA | ✅ Completada   |
| 🔄 Pull Request  | ✅ Fusionado    |
| 📝 Post-Mortem   | ✅ Documentado  |

---

## ✅ Conclusión

Este incidente permitió fortalecer las prácticas de documentación técnica, control de versiones y colaboración entre los equipos de **QA** y **Desarrollo**. La gestión mediante **GitHub Issues**, **Commits**, **Pull Requests**, **Merge** y **Post-Mortem** garantizó la trazabilidad del proceso desde la detección del problema hasta la implementación de acciones preventivas para reducir el riesgo de recurrencia.

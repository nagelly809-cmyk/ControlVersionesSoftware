# Control de Versiones y Gestión de Cambios
Repositorio diseñado para aplicar flujos de trabajo estructurados, separando los entornos de Desarrollo, Certificación y Producción, con pruebas de seguridad obligatorias.

---

## Estructura de ramas y entornos
| Rama                | Entorno          | Propósito                                                                 |
|---------------------|------------------|---------------------------------------------------------------------------|
| `main` 🟢           | Producción       | Versión final estable. Solo recibe cambios aprobados y validados.       |
| `certificacion` 🟡  | Certificación    | Espacio para pruebas funcionales, de rendimiento y escaneo de seguridad. |
| `desarrollo` 🔵     | Desarrollo       | Integración de nuevas funcionalidades y correcciones preliminares.       |
| `feature/*`         | —                | Ramas temporales para crear cada nueva característica.                   |
| `hotfix/*`          | —                | Ramas exclusivas para solucionar errores críticos en producción.         |
| `release/vX.Y.Z`    | —                | Etiquetas para identificar cada versión liberada oficialmente.           |

---

## Reglas de control y seguridad
1. No se permite fusionar cambios directamente en `main` ni en `certificacion` sin revisión.
2. Toda integración requiere **aprobación de al menos un revisor**.
3. Las pruebas de seguridad automáticas deben finalizar sin alertas antes de pasar a certificación.
4. Todo cambio debe registrarse con un mensaje claro que explique su propósito.

---

## Flujo de trabajo completo
1. Crear rama desde `desarrollo`: `feature/nombre-funcionalidad`
2. Desarrollar, probar localmente y subir los cambios
3. Abrir **Solicitud de Extracción** hacia `desarrollo` → revisión y aprobación
4. Fusionar en `certificacion` → se ejecutan automáticamente los escaneos de seguridad
5. Validar en entorno de certificación
6. Abrir solicitud hacia `main` → aprobación final
7. Crear etiqueta de versión y liberar a producción

---

**Herramientas utilizadas**: Git, GitHub, Code Scanning, Dependabot

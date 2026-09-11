# SUPERVISOR HANDOFF — TallerOS

## 1. Mandato

Asumes el puesto de **arquitecto principal / supervisor del proyecto TallerOS**.

Tu responsabilidad no es solamente escribir código. Debes mantener la coherencia completa del proyecto, decidir el orden de las fases, revisar lo que produzca Lovable, detectar errores de arquitectura y evitar que el proyecto quede acoplado a Lovable.

El usuario es el propietario del proyecto y toma las decisiones de producto. Tú eres el responsable de arquitectura, planificación técnica, revisión y dirección.

## 2. Objetivo del producto

TallerOS es un sistema web completo para la gestión de un taller mecánico.

Debe cubrir dos grandes áreas:

1. **Área pública:** sitio del taller, servicios, detalles de servicios, contacto, reservas, solicitud de presupuesto, promociones, preguntas frecuentes, contenido/SEO y portal del cliente.
2. **Área privada:** panel operativo del taller con clientes, vehículos, agenda, órdenes de trabajo, diagnósticos, presupuestos, aprobaciones, inventario, proveedores, técnicos, facturación, notificaciones, CRM, reportes, usuarios, roles y auditoría.

La intención a largo plazo es que pueda evolucionar a una plataforma para varios talleres, por eso las entidades futuras deben contemplar `workshop_id` sin construir ahora una complejidad innecesaria de multi-tenancy.

## 3. Restricción arquitectónica fundamental

**El proyecto no debe depender de Lovable para existir.**

Lovable es el ejecutor de desarrollo visual/código durante esta etapa. El código debe quedar en GitHub y el backend debe pertenecer a la infraestructura del propietario.

Arquitectura prevista:

- Frontend: React/TypeScript dentro del proyecto generado por Lovable.
- Git: GitHub como fuente principal del código.
- Backend: proyecto propio de Supabase.
- Base de datos: PostgreSQL de Supabase.
- Auth: Supabase Auth.
- Storage: Supabase Storage.
- Seguridad: RLS y autorización de backend.
- Lovable Cloud: NO usar como dependencia crítica.
- Secretos: nunca incrustarlos en el frontend ni en el repositorio.

## 4. Estado actual confirmado

FASE 00 fue ejecutada por Lovable y devolvió un informe indicando:

- arquitectura modular en `src/`;
- áreas pública y privada separadas;
- estructura `features/` para 13 módulos;
- `PublicLayout` y `AdminLayout`;
- configuración centralizada;
- cliente público de Supabase preparado;
- cliente administrativo server-only preparado;
- `.env.example` creado;
- `ARQUITECTURA.md` creado;
- tipos provisionales preparados;
- `/` y `/admin` responden correctamente;
- compilación de tipos sin errores;
- revisión realizada en escritorio y móvil;
- no hay `App.tsx` monolítico;
- no se añadieron datos ficticios.

## 5. FASE 00 no debe considerarse 100 % cerrada hasta verificar dos puntos

El informe de Lovable declaró como pendientes:

1. conexión real/sincronización del proyecto con GitHub;
2. conexión del proyecto Lovable con el proyecto Supabase propio.

No debes comenzar a diseñar el esquema de datos definitivo hasta verificar primero cuál de esas conexiones ya está hecha actualmente.

El usuario posteriormente indicó que **ya conectó GitHub y creó el proyecto TallerOS en Lovable**. Por tanto, no vuelvas a pedirle que cree el proyecto ni que conecte GitHub desde cero. Primero verifica el estado actual.

## 6. Principios de trabajo con el usuario

El usuario prefiere instrucciones extremadamente progresivas.

**No entregar grandes bloques de pasos de golpe cuando una sola acción sea suficiente.**

Forma recomendada:

- explicar brevemente qué estamos haciendo;
- dar UNA acción concreta;
- esperar el resultado;
- revisar;
- continuar.

No pedir confirmación para cada microdecisión técnica que puedas resolver tú mismo. Solo detenerse ante bloqueos reales o decisiones de producto que cambien sustancialmente el proyecto.

El usuario es principiante en programación. Las instrucciones deben ser claras, prácticas y copiables.

## 7. Cómo dirigir Lovable

Lovable debe recibir tareas cerradas por fase.

No permitir que Lovable:

- cambie la arquitectura sin autorización;
- cree un backend propietario de Lovable como dependencia crítica;
- invente datos persistentes para aparentar funcionalidades terminadas;
- concentre lógica en un archivo monolítico;
- coloque secretos en frontend;
- ignore RLS;
- implemente funcionalidades de fases futuras antes de tiempo;
- cambie decisiones arquitectónicas para solucionar un problema local sin explicar el impacto.

Cada tarea entregada a Lovable debe indicar: objetivo, alcance, archivos/áreas permitidas, restricciones, criterios de aceptación y verificación.

## 8. Flujo de supervisión

Para cada fase:

1. Diseñar la fase.
2. Dividirla en tareas pequeñas.
3. Entregar a Lovable instrucciones concretas.
4. Revisar el resultado reportado.
5. Verificar arquitectura y consistencia.
6. Corregir desviaciones.
7. Solo entonces declarar la fase completada.

## 9. Estados de órdenes de trabajo previstos

`RECIBIDA`
`DIAGNÓSTICO`
`PRESUPUESTO`
`APROBACIÓN`
`EN_REPARACIÓN`
`ESPERANDO_PIEZAS`
`PRUEBAS`
`LISTA`
`ENTREGADA`
`CERRADA`

## 10. Roles previstos

- `SUPERADMIN`
- `ADMIN`
- `RECEPCION`
- `TECNICO`
- `INVENTARIO`
- `CLIENTE`

Las etiquetas pueden cambiar posteriormente si existe una buena razón, pero el control de acceso siempre debe ser real y aplicar también en backend/RLS.

## 11. Orden conceptual de desarrollo

- FASE 00 — Constitución y base del proyecto.
- FASE 01 — Supabase, esquema base, RLS, autenticación, clientes y vehículos.
- FASE 02 — Agenda/citas.
- FASE 03 — Órdenes de trabajo.
- FASE 04 — Presupuestos y aprobación.
- FASE 05 — Inventario y proveedores.
- FASE 06 — Facturación/pagos.
- FASE 07 — Portal del cliente.
- FASE 08 — Notificaciones y CRM.
- FASE 09 — Reportes.
- FASE 10 — Seguridad, auditoría, QA y migración/despliegue independiente de Lovable.

El orden puede ajustarse si el análisis técnico demuestra una dependencia real, pero no debe saltarse la base de seguridad y datos.

## 12. Objetivo final de infraestructura

El producto debe poder salir de Lovable sin rehacer la aplicación.

El nuevo supervisor debe considerar desde ahora:

- build reproducible;
- variables de entorno estándar;
- base de datos y migraciones exportables;
- funciones backend portables cuando sea razonable;
- almacenamiento con estrategia de migración;
- documentación de despliegue fuera de Lovable;
- GitHub como fuente de código.

## 13. Primera obligación del nuevo supervisor

Antes de ordenar FASE 01, inspecciona el estado real de TallerOS en su repositorio principal y el estado de la integración con Supabase.

Después compara el estado real contra `PROJECT_STATE.md`.

No asumas que el informe de Lovable sigue siendo exactamente cierto: úsalo como evidencia histórica y vuelve a verificar lo que sea crítico.

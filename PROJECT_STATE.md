# PROJECT STATE — TallerOS

## Estado al momento de la transferencia

Fecha de referencia: 2026-09-11.

## Repositorios

### Repositorio de transferencia

`AaronGabrielD/cambio-de-supervisor-tallerOS`

Uso: exclusivamente transferencia de contexto al nuevo supervisor. No es el repositorio de desarrollo del producto.

### Repositorio principal

Existe un repositorio principal denominado **TallerOS**, creado previamente por el usuario para el proyecto y destinado a ser la fuente de verdad del código. El nuevo supervisor debe localizar/verificar el repositorio exacto conectado al proyecto Lovable antes de asumir cualquier referencia adicional.

## Estado de Lovable

El usuario ya:

- creó su proyecto en Lovable;
- conectó/autorizó GitHub;
- ejecutó FASE 00 mediante Lovable.

Lovable reportó la creación de la base modular del proyecto.

## Resultado reportado por FASE 00

### Estructura

- `src/app/`
- `src/components/ui/`
- `src/components/common/`
- `src/features/` con 13 módulos y subestructura `components/ hooks/ api/`
- `src/hooks/`
- `src/layouts/`
- `src/lib/`
- `src/routes/`
- `src/services/`
- `src/types/`
- `src/config/`

Áreas:

- pública: `/` con `PublicLayout`;
- privada: `/admin` con `AdminLayout`.

### Archivos importantes creados

- `src/config/env.ts`
- `src/config/app.ts`
- `src/config/navigation.ts`
- `src/types/index.ts`
- `src/types/common.ts`
- `src/types/auth.ts`
- `src/types/database.ts`
- `src/lib/supabase/client.ts`
- `src/lib/supabase/admin.server.ts`
- `src/lib/errors.ts`
- `src/lib/query-client.ts`
- `src/layouts/PublicLayout.tsx`
- `src/layouts/AdminLayout.tsx`
- `src/components/common/EmptyState.tsx`
- `src/components/common/ModuleRoadmap.tsx`
- `src/components/common/IntegrationStatus.tsx`
- `src/routes/admin.tsx`
- `src/features/auth/hooks/useSupabaseSession.ts`
- `.env.example`
- `ARQUITECTURA.md`
- README por cada módulo de `src/features/*`;
- documentación inicial de `src/services/` y `src/app/`.

### Archivos modificados reportados

- `src/styles.css`
- `src/routes/index.tsx`
- `src/routes/__root.tsx`
- `src/router.tsx`
- `package.json`

## Verificaciones reportadas

Lovable informó:

- compilación de tipos sin errores;
- revisión de estilo sin errores relevantes;
- únicamente avisos provenientes de archivos de plantilla;
- `/` responde;
- `/admin` responde;
- sin errores en consola;
- prueba visual en 1280 px y 390 px.

Estas verificaciones deben considerarse **reportadas por Lovable**, no una auditoría independiente definitiva.

## Supabase

La arquitectura fue preparada para Supabase mediante `@supabase/supabase-js`.

Variables previstas:

Frontend:

- `VITE_SUPABASE_URL`
- `VITE_SUPABASE_PUBLISHABLE_KEY`

Servidor:

- `SUPABASE_URL`
- `SUPABASE_SERVICE_ROLE_KEY`

El informe de FASE 00 declaró que el proyecto Supabase todavía no estaba conectado en ese momento. Posteriormente el usuario indicó que había realizado conexiones, por lo que el nuevo supervisor debe **verificar el estado actual antes de concluir que falta la conexión**.

## Dependencia añadida

La única dependencia declarada como nueva durante FASE 00 fue:

`@supabase/supabase-js`

## Decisiones que ya existen

- No usar Lovable Cloud como dependencia crítica.
- GitHub debe ser la fuente principal del código.
- Backend propio de Supabase.
- Credenciales únicamente mediante variables de entorno.
- Arquitectura modular.
- Entidades futuras preparadas para `workshop_id`.
- No fingir funcionalidades mediante datos ficticios.
- Sistema de diseño centralizado.
- Área pública y área administrativa separadas.

## Pendiente técnico inmediato

Antes de desarrollar funcionalidades de negocio:

1. localizar/confirmar el repositorio principal exacto de TallerOS;
2. verificar que Lovable está sincronizado con él;
3. verificar el proyecto Supabase real;
4. decidir y ejecutar el esquema base;
5. configurar seguridad/RLS;
6. generar tipos reales de la base de datos;
7. implementar autenticación real;
8. comenzar clientes y vehículos.

## No hacer todavía

No implementar todavía inventario, facturación, CRM avanzado, reportes complejos ni multi-tenancy avanzado.

La prioridad es construir una base de datos y seguridad correctas antes de aumentar la superficie funcional.

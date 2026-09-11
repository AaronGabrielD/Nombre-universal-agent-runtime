# ARCHITECTURE CONSTITUTION — TallerOS

Este documento define límites arquitectónicos que no deben romperse para resolver problemas de corto plazo.

## A. Portabilidad

TallerOS debe poder ejecutarse fuera de Lovable.

Lovable es una herramienta de desarrollo, no la plataforma propietaria del producto.

## B. Fuente de verdad

El código fuente vive en GitHub.

Los cambios sustanciales deben terminar versionados en Git.

## C. Backend

El backend principal previsto es Supabase bajo control del propietario.

No sustituirlo por Lovable Cloud salvo una decisión explícita del propietario después de evaluar el impacto de dependencia y migración.

## D. Seguridad

Nunca confiar en la interfaz para seguridad.

Las reglas de acceso deben existir también en backend y/o RLS según corresponda.

Nunca:

- poner `SUPABASE_SERVICE_ROLE_KEY` en código de navegador;
- incluir secretos en Git;
- usar datos ficticios para simular seguridad;
- exponer información de otro taller por errores de filtrado.

## E. Multi-taller preparado, no sobreconstruido

Las entidades de negocio deben contemplar la pertenencia a un taller mediante `workshop_id` cuando sea aplicable.

Esto no significa implementar un sistema SaaS multi-tenant completo desde FASE 01.

## F. Modularidad

Cada dominio debe poder evolucionar sin convertir `routes`, `App`, componentes globales o servicios genéricos en depósitos monolíticos de lógica.

Las funcionalidades de dominio deben vivir preferentemente dentro de `src/features/<dominio>/`.

## G. Datos reales

No crear registros falsos para esconder una funcionalidad pendiente.

Los estados vacíos deben ser honestos.

## H. Migraciones

El esquema de base de datos debe poder reconstruirse mediante migraciones/documentación versionada.

No depender de cambios manuales imposibles de reproducir.

## I. Autorización

Los roles iniciales previstos son:

- SUPERADMIN
- ADMIN
- RECEPCION
- TECNICO
- INVENTARIO
- CLIENTE

El nombre puede revisarse, pero la autorización debe estar centralizada y ser consistente.

## J. Fases

No saltar fases simplemente porque una interfaz pueda diseñarse rápidamente.

Primero:

- fundación;
- datos;
- seguridad;
- autenticación;
- dominios centrales.

Después funcionalidades secundarias.

## K. Lovable

Toda instrucción para Lovable debe limitar el alcance.

Lovable no debe reinterpretar la arquitectura ni introducir servicios propietarios sin autorización.

## L. Calidad

Una fase no está terminada porque compile solamente.

Debe verificarse como mínimo:

- tipos;
- build;
- rutas;
- errores de consola;
- comportamiento funcional relevante;
- seguridad de datos;
- compatibilidad móvil cuando corresponda;
- impacto sobre otros módulos.

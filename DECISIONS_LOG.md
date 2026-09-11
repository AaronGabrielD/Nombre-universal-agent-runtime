# DECISIONS LOG — TallerOS

## D-001 — Lovable no es la plataforma final

Lovable se utiliza como herramienta de construcción. El producto debe permanecer portable.

## D-002 — GitHub como fuente principal del código

El código debe mantenerse versionado en GitHub y poder recuperarse fuera de Lovable.

## D-003 — Supabase propio

La base de datos, autenticación y almacenamiento deben pertenecer al proyecto Supabase del propietario, no a Lovable Cloud.

## D-004 — Arquitectura modular

El frontend se divide por dominios y mantiene separadas las áreas pública y administrativa.

## D-005 — Preparación para varios talleres

Las entidades de negocio deben contemplar `workshop_id` cuando corresponda, aunque la primera versión no implemente todo el modelo multi-tenant.

## D-006 — Seguridad real

La UI no es una barrera de seguridad. RLS/backend deben impedir acceso no autorizado.

## D-007 — Sin datos ficticios

No presentar registros inventados como si fueran datos reales del taller.

## D-008 — Desarrollo por fases

El sistema se construye por módulos y fases, revisando cada fase antes de iniciar la siguiente.

## D-009 — Supervisión centralizada

El arquitecto/supervisor decide el orden y alcance. Lovable ejecuta tareas concretas y reporta resultados.

## D-010 — Transferencia de supervisor

Este repositorio temporal existe para permitir cambiar de cuenta de ChatGPT y transferir el contexto del proyecto al nuevo arquitecto sin depender de la memoria de la conversación anterior.

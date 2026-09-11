# NEXT ACTION — TallerOS

## Objetivo inmediato

Cerrar correctamente la transición de FASE 00 y preparar FASE 01 sin rehacer trabajo ya realizado.

## Única prioridad actual

**Verificar el estado real de las integraciones antes de modificar código.**

### Verificar GitHub

Confirmar cuál es el repositorio principal exacto conectado actualmente al proyecto TallerOS de Lovable.

No asumir que el repositorio temporal de transferencia es el repositorio del producto.

### Verificar Supabase

Confirmar cuál es el proyecto Supabase que pertenece al propietario y si TallerOS está conectado a ese proyecto.

No crear otro proyecto de Supabase si ya existe uno correcto.

## Después de verificar

Diseñar FASE 01 con este orden:

1. esquema base;
2. relaciones;
3. roles;
4. perfiles/usuarios;
5. `workshop_id`;
6. RLS;
7. autenticación;
8. generación de tipos reales;
9. clientes;
10. vehículos.

## Esquema conceptual mínimo esperado

El diseño debe analizar como mínimo estas entidades:

- workshops;
- profiles/users;
- roles o estrategia equivalente de autorización;
- customers;
- vehicles.

Las relaciones deben permitir que un cliente tenga uno o varios vehículos y que los datos queden correctamente asociados al taller.

## No continuar todavía con

- órdenes de trabajo;
- inventario;
- proveedores;
- facturación;
- CRM avanzado;
- reportes complejos;
- automatizaciones avanzadas.

Esas áreas dependen de una base de datos y autorización correctas.

## Criterio de salida de FASE 01

No declarar FASE 01 completa hasta tener:

- esquema reproducible/versionado;
- RLS probada;
- autenticación real;
- autorización coherente con roles;
- tipos sincronizados con el esquema real;
- CRUD funcional y seguro para clientes/vehículos;
- verificación de que un usuario no puede acceder a datos de otro taller;
- build y pruebas básicas sin errores.

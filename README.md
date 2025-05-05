# curso-SQL
Este curso es una serie de pasos que he seguido desde el canal de pildoras informáticas

# Proyecto de Migración de Datos a BigQuery

## Índice
- [Proceso de Migración](#proceso-de-migración-de-datos-a-bigquery)
- [Limpieza de Datos](#limpieza-y-normalización-de-datos)

---

## Proceso de Migración de Datos a BigQuery

### Situación Actual
Subí dos bases de datos desde Google Sheets a BigQuery. Durante la importación, los nombres de columnas en la tabla `CLIENTES` se transformaron automáticamente.

### Problema Identificado
Los caracteres especiales se reemplazaron con underscores:

| Nombre Original   | Nombre en BigQuery  |
|-------------------|---------------------|
| CÓDIGOCLIENTE     | C__DIGOCLIENTE      |
| DIRECCIÓN         | DIRECCI__N          |
| POBLACIÓN         | POBLACI__N          |
| TELÉFONO          | TEL__FONO           |

[↑ Volver al índice](#índice)

---

## Limpieza y Normalización de Datos

### Solución Implementada
Creé una vista estandarizada con nombres simplificados:

```sql
CREATE OR REPLACE VIEW `sql1-458915.data_base.clientes_clean` AS
SELECT 
  C__DIGOCLIENTE AS codigocliente,
  EMPRESA AS empresa,
  DIRECCI__N AS direccion,
  POBLACI__N AS poblacion,
  TEL__FONO AS telefono,
  RESPONSABLE AS responsable,
  HISTORIAL AS historial
FROM `sql1-458915.data_base.clientes`

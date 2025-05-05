# curso-SQL
Este curso es una serie de pasos que he seguido desde el canal de pildoras informáticas

# Limpieza y Normalización de Estructura de Datos
He subido dos bases de datos desde hojas de cálculo de Google Drive a BigQuery. Al conectar y revisar los datos, noté que los nombres de las columnas en la tabla CLIENTES han cambiado automáticamente durante el proceso de importación.

Problema Identificado
Los nombres originales de las columnas (con tildes y caracteres especiales) se han transformado en BigQuery de la siguiente manera:

Nombre Original	Nombre en BigQuery
CÓDIGOCLIENTE	C__DIGOCLIENTE
DIRECCIÓN	DIRECCI__N
POBLACIÓN	POBLACI__N
TELÉFONO	TEL__FONO
Solución Implementada
Para mantener consistencia y evitar problemas con caracteres especiales, crearé una vista con nombres simplificados (minúsculas y sin tildes):

sql
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

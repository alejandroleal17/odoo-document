# Respaldo de Schema

## 1. Conexión a EC2
- **Paso 1**: Conectarnos al EC2 de Prod.

ssh usuario@10.0.22.233

## 2. Respaldo del Esquema
- **Paso 2**: Una vez conectados, ejecutamos el siguiente comando para realizar el respaldo del esquema:

pg_dump -h navigator-production-tf.cngboma1n4ol.us-east-2.rds.amazonaws.com -p 5432 -U troc_pgdata -W --schema-only -d navigator_production > bk_schemas_production.sql

- **Paso 3**: Colocamos la contraseña de la base de datos cuando se solicite.

## 3. Descarga del Esquema
- **Paso 4**: Nos bajamos al esquema.

> **Nota**: Podemos usar Screen en algunas ocasiones para dejar la terminal corriendo en segundo plano.

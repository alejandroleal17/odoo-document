

---

# Respaldo de Tablas en Base de Datos en Navigator

Este manual proporciona los pasos para realizar el respaldo y restauración de tablas en la base de datos de Navigator.

## Conexión a EC2

1. **Conexión SSH al servidor EC2**

   Conéctate al servidor EC2 de producción utilizando SSH:

   ```bash
   ssh usuario@10.0.22.233
   ```

## Respaldo de Tablas

2. **Realizar el Respaldo**

   Una vez conectado, ejecuta el siguiente comando para respaldar una tabla específica:

   ```bash
   pg_dump -h navigator-production-tf.cngboma1n4ol.us-east-2.rds.amazonaws.com -p 5432 -U troc_pgdata -W --format=c -d navigator_production -t schema.tabla > bk_schemas_production.backup
   ```

   Para respaldar varias tablas (ejemplo para Hisense):

   ```bash
   pg_dump -h navigator-production-tf.cngboma1n4ol.us-east-2.rds.amazonaws.com -p 5432 -U troc_pgdata -W --format=c -d navigator_production -t hisense.products -t hisense.inventory -t hisense.all_products -t hisense.form_data > bk_schemas_production.backup
   ```

3. **Ingreso de Contraseña**

   Ingresa la contraseña de la base de datos cuando se solicite.

4. **Descarga del Esquema**

   Descarga el esquema de la base de datos a tu máquina local.

   > Nota: Puedes usar `screen` para dejar la terminal corriendo en segundo plano.

## Restauración de Tablas

5. **Preparación para la Restauración**

   Antes de restaurar, si es necesario, elimina las tablas existentes:

   ```sql
   DROP TABLE IF EXISTS schema.tabla;
   ```

   O para múltiples tablas (ejemplo para Hisense):

   ```sql
   DROP TABLE IF EXISTS hisense.form_data;
   DROP TABLE IF EXISTS hisense.inventory;
   DROP TABLE IF EXISTS hisense.all_products;
   ```

6. **Realizar la Restauración**

   Ejecuta el siguiente comando para restaurar las tablas:

   ```bash
   pg_restore -h navigator-staging-tf.cp0qwiwsxfog.us-east-2.rds.amazonaws.com -p 5432 -U troc_pgdata -d navigator_dev -v bk_schemas_hisense_production.backup
   ```

---

Fin del tutorial.

---




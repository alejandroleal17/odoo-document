## Manipulacion de Bases de Datos Navagitor -- 
 - Resturar una Base de datos.

1 - Descargamos el dump en produccion (ftp) 
2 - Subimos el archivo FTP en DEV - 10.0.22.66  - usuario - puerto: 22 
3 - Una vez tenemos el dump en EC2 de DEV procedemos a restuarlo  en en el ambiente a utilizar.
      en Produccion.
      o en DEV si vamos a restuarala. 
      o en Stating. 

Nota: usar Screen para evitar tener la cosola de activa por mucho tiempo. 

-----------------------------------
  1 - DROPEAR BD 
      dropdb -h navigator-staging-tf.cp0qwiwsxfog.us-east-2.rds.amazonaws.com  -p 5432 -U troc_pgdata -W navigator_staging ( o la que aplique)
 
      opcional: 

      con este query podemos desconectar las sesioens que esten usando al DB.

        SELECT pg_terminate_backend(pg_stat_activity.pid)
        FROM pg_stat_activity
        WHERE pg_stat_activity.datname = 'temp'
        AND pid <> pg_backend_pid()

 Segun aplique: 
     
------------------------------------------
  2 - CREAR BD
    createdb -h navigator-staging-tf.cp0qwiwsxfog.us-east-2.rds.amazonaws.com  -p 5432 -U troc_pgdata -W   navigator_staging  ( o la que aplique)

------------------------------------------
  3 - RESTAURAR UN BACKUO EN BD  QUE HEMOS CREADO - PARA ESTE EJEMPLO TEMP 

   pg_restore  -h navigator-staging-tf.cp0qwiwsxfog.us-east-2.rds.amazonaws.com   -p 5432 -U troc_pgdata -d navigator_staging  -v  ARCHIVO_A_RESTURAR.backup

------------------------------------------

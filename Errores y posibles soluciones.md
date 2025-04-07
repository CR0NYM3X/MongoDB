
 
 ### Error al levantar el mongoDB - Posibles soluciones 
```
1. **Eliminar el archivo de socket**:
   - A veces, el archivo de socket puede causar problemas. Intenta eliminarlo y reiniciar el servicio MongoDB:

     sudo rm /tmp/mongodb-27017.sock
     sudo systemctl restart mongod


2. **Verificar permisos de directorio y archivo**:
   - Asegúrate de que los permisos del directorio y archivo de registro sean correctos:

     sudo chown -R mongod:mongod /var/lib/mongodb
     sudo chown mongod:mongod /tmp/mongodb-27017.sock
     sudo chown mongod:mongod /var/log/mongodb/mongod.log
     sudo chmod 644 /var/log/mongodb/mongod.log


3. **Revisar la configuración del servicio**:
   - Verifica la configuración del servicio MongoDB (`/etc/systemd/system/mongod.service`) y asegúrate de que no esté configurada para no bifurcar el proceso. Puedes editar este archivo y eliminar la línea que establece `MONGODB_CONFIG_OVERRIDE_NOFORK=1`:

     sudo nano /etc/systemd/system/mongod.service

   - Busca y elimina la línea:

     Environment=MONGODB_CONFIG_OVERRIDE_NOFORK=1

     
   - Guarda los cambios y recarga el demonio de systemd:

     sudo systemctl daemon-reload
     sudo systemctl restart mongod


4. **Revisar los registros de MongoDB**:
   - Revisa los registros de MongoDB para obtener más detalles sobre el error. Los registros se encuentran en `/var/log/mongodb/mongod.log`.
 ```
 
 

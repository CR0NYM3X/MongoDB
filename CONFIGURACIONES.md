

## Habilitar el pretty default 
Esto sirve para cuando realices una consulta , la salida del texto en consola se muestre en un bonito formato y sin la necesidad de poner al final de la consulta la funcion pretty()
```
echo DBQuery.prototype._prettyShell = true >> ~/.mongorc.js

es un archivo de configuración que puedes personalizar para ajustar el comportamiento de mongosh, la nueva shell de MongoDB. Aunque en versiones anteriores se utilizaba .mongorc.js


```


```sql
// Establecer un prompt personalizado
prompt = function() {
    return 'MiMongoDB> ';
};

// Crear un alias para mostrar las bases de datos
alias.showDbs = function() {
    db.adminCommand({ listDatabases: 1 });
};
```

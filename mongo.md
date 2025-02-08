#consula recurrente para actualizar 

db.transferencia_detalle.updateOne(
  { _id: ObjectId('677c0bc15d1b1004fff9eee3') },
  {
    $set: {
      tipo: 'RECEPCION_TRANSFERENCIA',
      referencia: 'Recepción de transferencia - Salida de Almacen - TRA-20250106-974'
    }
  }
);

# Consulta para eliminar en la fechas 

```javascript
// 1. Primero obtenemos los IDs de las transferencias
var transferenciasIds = db.transferencia.find({
    fecha: {
        $gte: ISODate("2025-01-07T00:00:00.000Z"),
        $lt: ISODate("2025-01-09T00:00:00.000Z")
    }
}).toArray();

// 2. Obtenemos los IDs de los detalles
var detalleIds = db.transferencia_detalle.find({
    transferencia_id: { 
        $in: transferenciasIds.map(function(t) { return t._id; })
    }
}).toArray();

// 3. Eliminamos los registros en orden (de hijo a padre)

// 3.1 Eliminamos primero transferencia_recurso
db.transferencia_recurso.deleteMany({
    transferencia_detalle_id: { 
        $in: detalleIds.map(function(d) { return d._id; })
    }
});

// 3.2 Eliminamos transferencia_detalle
db.transferencia_detalle.deleteMany({
    transferencia_id: { 
        $in: transferenciasIds.map(function(t) { return t._id; })
    }
});

// 3.3 Finalmente eliminamos las transferencias
db.transferencia.deleteMany({
    fecha: {
        $gte: ISODate("2025-01-07T00:00:00.000Z"),
        $lt: ISODate("2025-01-09T00:00:00.000Z")
    }
});

// Para verificar el resultado, puedes usar:
print("Documentos eliminados correctamente");
```

Este código:
1. Obtiene primero todos los IDs necesarios
2. Elimina los registros en el orden correcto para mantener la integridad referencial
3. Usa el mismo enfoque que funcionó para transferencia_recurso en todas las eliminaciones

Puedes ejecutar estos comandos uno por uno en la terminal de MongoDB para asegurarte de que cada paso se complete correctamente.

### Pasos para ejecutar mongo en local terminal

2. **Install MongoDB:**

   After updating the package list, you can install MongoDB using:

   ```bash
   sudo apt install -y mongodb-org
   ```

3. **Start and Enable MongoDB:**

   Once MongoDB is installed, you can start the MongoDB service and enable it to start on boot with the following commands:

   ```bash
   sudo systemctl start mongod
   sudo systemctl enable mongod
   ```

4. **Verify the Installation:**

   To ensure that MongoDB is running, you can check the status of the service:

   ```bash
   sudo systemctl status mongod
   ```
  Una vez que el servicio esté en funcionamiento, puedes acceder a la consola de MongoDB simplemente escribiendo:

   ```bash
   mongo

   ```
  *** consulta para listar colleccines con like 
  
```  
db.getCollectionNames().filter(c => c.includes('pago'))

db.getCollectionNames().filter(c => /pago/i.test(c))
```

# PruebaPractica2PU3
# Analisi Profesional 

1. Atomicidad
La atomicidad es una propiedad ACID que garantiza que una transacción se ejecuta completamente o no se ejecuta en absoluto. Si alguna instrucción falla a mitad de la transacción (por ejemplo, un INSERT falla por violación de FK), Oracle deshace todos los cambios realizados hasta ese punto con ROLLBACK, dejando la base de datos en su estado previo consistente.

2. DELETE sin WHERE
Ejecutar DELETE FROM tabla; sin cláusula WHERE elimina absolutamente todos los registros de la tabla. En Oracle, si hay FK con ON DELETE CASCADE, también se eliminarán los registros de las tablas hijas. Es una de las operaciones más peligrosas en producción. La penalización en esta prueba es de -0.25 puntos por cometer este error.

3. ON DELETE CASCADE
ON DELETE CASCADE es una regla de integridad referencial que indica que cuando se elimina un registro padre, Oracle elimina automáticamente todos los registros hijos relacionados vía FK. En este escenario, eliminar una AEROLINEA elimina automáticamente sus VUELOS y, en cascada, los BOLETOS asociados a esos vuelos. Es útil para mantener consistencia sin errores ORA-02292.

# Descripcion del trabajo
Se diseñó e implementó una base de datos relacional para el escenario de Aeropuerto Internacional, compuesta por cinco tablas: AEROLINEA, PASAJERO, VUELO, BOLETO y EQUIPAJE.

El trabajo incluyó:

    Modelado lógico con definición de claves primarias, foráneas, restricciones CHECK, UNIQUE y NOT NULL

    Integridad referencial aplicando ON DELETE CASCADE en todas las relaciones padre-hijo

    Manipulación de datos con INSERT, UPDATE seguro con WHERE, y DELETE con eliminación en cascada

    Prueba de integridad provocando intencionalmente el error ORA-02291 al insertar un vuelo con una aerolínea inexistente

    Consultas SQL utilizando IN, LIKE, BETWEEN, AVG/MAX y JOIN entre tres tablas

    Análisis profesional de los conceptos de Atomicidad, DELETE sin WHERE y ON DELETE CASCADE
# Prueba Técnica - Java Senior (Arquitectura Hexagonal / Microservicios)

## Descripción

Esta prueba técnica consiste en implementar una solución basada en
**arquitectura hexagonal**, aplicando **buenas prácticas de desarrollo
(Clean Code, patrones de diseño, repositorios, manejo de excepciones,
pruebas unitarias e integración)** y desplegándola en **contenedores
Docker**.\
El objetivo es demostrar la capacidad de diseño, desarrollo e
integración de microservicios en un entorno distribuido.

------------------------------------------------------------------------

## Requerimientos

-   Implementar al menos **dos microservicios**:
    -   **Clientes / Personas**\
    -   **Cuentas / Movimientos**\
-   La comunicación entre microservicios debe ser **asíncrona**.
-   Incluir pruebas unitarias y de integración.
-   Generar script de base de datos (`BaseDatos.sql`).
-   Exponer los servicios como **API REST** utilizando verbos: `GET`,
    `POST`, `PUT`, `PATCH`, `DELETE`.
-   La solución debe ejecutarse en **Docker**.

------------------------------------------------------------------------

## Entidades

### Persona

-   nombre, género, edad, identificación, dirección, teléfono.\
-   Clave primaria única.

### Cliente

-   Hereda de Persona.\
-   Atributos: `clienteId`, `contraseña`, `estado`.\
-   Clave única.

### Cuenta

-   Atributos: `númeroCuenta`, `tipoCuenta`, `saldoInicial`, `estado`.\
-   Clave única.

### Movimiento

-   Atributos: `fecha`, `tipoMovimiento`, `valor`, `saldo`.\
-   Clave única.

------------------------------------------------------------------------

## Funcionalidades de la API

-   **F1**: CRUD en Cliente. CRU en Cuenta y Movimiento.\
    Endpoints:
    -   `/clientes`\
    -   `/cuentas`\
    -   `/movimientos`
-   **F2**: Registro de movimientos (depósitos/retiros).
    -   Actualiza saldo disponible.\
    -   Registro de transacciones.
-   **F3**: Validación de saldo disponible.
    -   Si no hay saldo suficiente, retornar mensaje
        `"Saldo no disponible"`.
-   **F4**: Reportes de estado de cuenta.
    -   Endpoint: `/reportes?fecha={rango}&cliente={id}`\
    -   Respuesta en formato JSON con detalle de cuentas y movimientos.
-   **F5**: Al menos 1 prueba unitaria en Cliente.\
-   **F6**: Al menos 1 prueba de integración.\
-   **F7**: Despliegue en contenedores.

------------------------------------------------------------------------

## Casos de uso

### Creación de Usuarios

  -----------------------------------------------------------------------------
  Nombre             Dirección            Teléfono     Contraseña   Estado
  ------------------ -------------------- ------------ ------------ -----------
  José Lema          Otavalo sn y         098254785    1234         Verdadero
                     principal                                      

  Marianela Montalvo Amazonas y NN.UU     097548965    5678         Verdadero

  Juan Osorio        13 de junio y        098874587    1245         Verdadero
                     equinoccial                                    
                     
  -----------------------------------------------------------------------------

### Creación de Cuentas

  --------------------------------------------------------------------------
  Número Cuenta  Tipo        Saldo Inicial  Estado      Cliente
  -------------- ----------- -------------- ----------- --------------------
  478758         Ahorros     2000           Verdadero   José Lema

  225487         Corriente   100            Verdadero   Marianela Montalvo

  495878         Ahorros     0              Verdadero   Juan Osorio

  496825         Ahorros     540            Verdadero   Marianela Montalvo
  
  --------------------------------------------------------------------------

------------------------------------------------------------------------

## Ejemplo JSON

``` json
{
  "Fecha": "10/2/2022",
  "Cliente": "Marianela Montalvo",
  "Número de cuenta": "225487",
  "Tipo": "Corriente",
  "Saldo Inicial": 100,
  "Estado": true,
  "Movimiento": 600,
  "Saldo disponible": 700
}
```

------------------------------------------------------------------------

## Entregables

1.  Script de base de datos: `BaseDatos.sql`\
2.  Colección de Postman (JSON).\
3.  Código fuente en repositorio público GitHub.\
4.  Pruebas unitarias e integración (JUnit/Karate DSL).\
5.  Archivo comprimido `.zip` o `.rar` con la solución completa.

------------------------------------------------------------------------

## Despliegue

-   Construir imagen con Dockerfile.\
-   Levantar microservicios con **docker-compose**.\
-   Asegurar que los servicios sean accesibles vía
    `http://localhost:{puerto}/api/{endpoint}`.\
-   Instrucciones adicionales deben incluirse en este README.

------------------------------------------------------------------------

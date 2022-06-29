
# Cree una Base de Datos Azure SQL Database a través del Portal de Azure

Guía paso por paso para crear una base de datos única en Azure SQL 
Database, sin necesidad de instalar PowerShell o CLI, desde cualquier dispositivo que soporte un navegador.

## Resumen
En este artículo encontrará:
- Requisitos previos
- Cómo crear una base de datos única
- Cómo limpiar los recursos
- Configuración de Firewall recomendada 
- Información relevante

## Antes de comenzar


- Si tiene que decidir si los Servicios en la Nube de Azure son apropiados para su proyecto, revise los [beneficios y consideraciones de la nube](https://docs.microsoft.com/es-mx/learn/modules/fundamental-azure-concepts/benefits-of-cloud-computing).
- Podrá crear una suscripción y acceder a todos sus recursos desde el [Portal de Azure](https://portal.azure.com/)
- Mantenga sus prioridades en mente, siempre puede almacenar sus credenciales en *Azure Key Vault*, si la Privacidad y la Seguridad son procupaciones importantes para el proyecto.
- El modelo de cobro de Azure es de pago por uso, asegúrese de borrar cualquier recurso innecesario. Aprenderá cómo hacerlo más adelante en este módulo.

## Requisitos previos
- Una suscripción activa de Azure.
- Comprensión básica de conceptos y terminología informática. Se sugiere una comprensión básica del cómputo en la nube, pero no es esencial.
- Puede usar cualquier dispositivo que soporte un navegador web.


## Cómo crear una Base de Datos Única

1. Inicie sesión en su cuenta de Azure.
2. Seleccione Crear nuevo recurso>>Bases de Datos>SQL Database.

     Es probable que pueda sólo seleccionar las Bases de Datos SQL Database en recursos populares.

![Alt Text](https://media.giphy.com/media/LFH4ZF67GcPMu8CpTR/giphy.gif)

Verá el panel de SQL Database.

3. Seleccione su suscripción de Azure y asigne su Base de Datos al Grupo de Recursos de su proyecto o *cree uno nuevo*.
4. Asigne los siguientes valores a cada opción:
5. Cree un nombre para su Base de Datos. Tenga presente las siguientes especificaciones:

       El nombre de la Base de Datos no debe coincidir con ningún patrón especial o palabras reservadas de Azure.
       El nombre de la Base de Datos está limitado a 128 carácteres.
       El nombre de la Base de Datos deberá ser único en el servidor.


Después, tendrá que asignar su Base de Datos a un servidor. 
Si ya cuenta con un servidor para su proyecto, pase directamente al *paso 7*.

6. Haga click en `Crear nuevo` bajo la lista de servidores y asigne los siguientes valores:

## 

| **Configuración** | **Valor**     |
| :------ | :-------- | 
| *Detalles de servidor* ||
| Nombre del servidor | sqlservernnnn (Reemplazando con letras y números para obtener un nombre único)|
| Ubicación | Seleccione la ubicación más cercana, para disminuir la latencia|
| *Autenticación* ||
| Método de autenticación | `Use la autenticación de SQL` |
| Inicio de sesión del administrador del servidor | Necesitará este usuario para acceder a su Base de Datos|
| Contraseña | Las contraseñas más seguras incluyen letras mayúsculas y minúsculas, así como números y signos|



7. Regresará entonces al panel de creación de su Base de Datos y se le ofrecerá usar SQL elastic pool. Seleccione `No`

8. Haga click en `Configurar Base de Datos` en Proceso y Almacenamiento, seleccione `Sin servidor`. Puede dejar los otros valor como establecidos por defecto. Haga click en `Aplicar` para regresar al panel.

![Alt Text](https://www.linkpicture.com/q/Captura1_4.png)

9. Seleccione la redundancia de respaldo de su preferencia para mejorar la disponibilidad del servicio.
Si la disponibilidad no es una preocupación importante para su Base de Datos, puede seleccionar `Almancenamiento localmente redundante`.
Para másinformación acerca de disponibilidad en el servicio, [revise el Acuerdo de Nivel de Servicio de SQL Database](https://azure.microsoft.com/es-mx/blog/understanding-and-leveraging-azure-sql-database-sla/) 

10. Vaya a la pestaña de Redes y seleccione `Endpoint público` como Método de Conectividad.
Puede dejar los campos no específicados como establecidos por defecto.

![Alt Text](https://www.linkpicture.com/q/Captura_32.png)

11. Salte la pestaña de Seguridad por ahora. Vaya directamente a la pestaña de Configuración adicional y asigne los siguientes valores:

| **Configuración** | **Valor**     |
| :------ | :-------- | 
| *Orígenes de datos* ||
| Usar datos existentes | Ejemplo|
| *Database collation* ||
| Colación | `SQL_Latin1_General_CP1_CI_AS (default)` |

12. Haga click en `Continuar` y cree etiquetas, según las Buenas Prácticas de su Organización. Para mayor información, consulte la [Estrategia para nombrar y asignar etiquetas de Azure](https://docs.microsoft.com/es-mx/azure/cloud-adoption-framework/ready/azure-best-practices/naming-and-tagging).


13. Seleccione `Revisar y Crear` para validar su Configuración. Azure automáticamente buscará errores e inconsistencias.

14. Seleccione `Crear` y espere a que su Base de Datos se despliegue. Podría tomar hasta 5 minutos, dependiendo de la disponibilidad del servicio.

![Alt Text](https://www.linkpicture.com/q/Deployment.png)

## Configuración de Firewall recomendada

Una vez haya creado su Base de Datos SQL Database, se recomienda permitir que los servicios y recursos de Azure puedan acceder al Servidor.
Para hacerlo:
- Seleccione `Ir a recurso`.

![Alt Text](https://www.linkpicture.com/q/Deployed.png)

- Haga click en `Vista General` en el Menú del lado izquierdo.
- Selecciones `Establecer servidor firewall` en la barra de comandos.
- Baje hasta encontrar `Excepciones` y seleccione la opción de **Permitir a los servicios y recursos de Azure acceder a este Servidor**.
- Guarde los cambios.

![Alt Text](https://media.giphy.com/media/OplxC8RWhXOtpDugZE/giphy.gif)


## Cómo limpiar los recursos
Cuando termine de usar los recursos, se recomienda eliminar el Grupo de Recursos que ha creado, para ahorrar en costos de Cómputo. Esta acción también eliminará el Servidor y la Base de Datos única que contiene.

Para borrar un Grupo de Recursos y los recursos que contiene:

        - Seleccione el Grupo de Recursos.
        - Seleccione `Borrar Grupo de Recursos`.

**Este paso no puede deshacerse: Asegúrese de sólo eliminar los recursos con que ya haya terminado. 
Azure le pedirá teclear el nombre del Grupo de Recursos como confirmación para proceder.**

![Alt Text](https://www.linkpicture.com/q/delete_3.png)


## Adaptado de

 - [Create a SQL database Exercise on Microsoft Learn](https://docs.microsoft.com/en-us/learn/modules/azure-database-fundamentals/exercise-create-sql-database)
 - [Quickstart: Create an Azure SQL Database single database](https://docs.microsoft.com/en-us/azure/azure-sql/database/single-database-create-quickstart?view=azuresql&tabs=azure-portal)

# Hola, mi nombre es Sarahí Sancliment! 👋

## 🚀 Acerca de mí
Soy una fanática del código con un título en Filosofía.

## 🔗 ¡Estoy ansiosa su retroalimentación!
### sasn6970@protonmail.com 
#### (+52) 55-3247-2299
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/sara-sancliment-garcia-4336b1235/)
[![github](https://img.shields.io/badge/github-1DA1F2?style=for-the-badge&logo=github&logoColor=white)](https://github.com/sasn6970)


# Flujo de n8n. 

Este flujo n8n automatiza desde una entrada que es un n8n form.
Toma un pedido de un empleado que pide una licencia, ya sea por enfermedad o por Vacaciones para una fecha de inicio y una fecha de retorno determinadas.

El flujo obtiene de una db postgres en Neon Tech los datos del empleado. Primero verifica que sea un empleado si no informa un error por email a RRHH.
-Luego verifica si el pedido de licencia es por Vacaciones o por enfermedad.

# Ruta 1
## Pedido por Vacaciones
-Primero verifica si los dias solicitados son mas que 0. Sino informa un error por email al empleado.
-Segundo si hay 7 dias de preaviso entre la fecha actual y el inicio de la licencia por vacaciones. Sino informa un error por email al empleado.
-Verifica en base a los datos tomados de la db si el empleado tiene los dias disponibles para las Vacaciones pedidas. Sino informa un error por email al empleado.

-Solicita a traves de discord a RRHH que autorice o no la licencia por Vacaciones.
-Espera la respuesta con un nodo wait.

    -Si RRHH desaprueba se informa un error por email al empleado.
    -Si RRHH aprueba:
        -Se Accede a Google Calendar y se marca las vacaciones.
        -Se actualiza los dias que le quedan al empleado luego de usar las vacaciones.
        -Se envia email confirmando la licencia por vacaciones al empleado.


# Ruta 2
## Pedido por Enfermedad
-Primero verifica si los dias solicitados son mas que 0. Sino informa un error por email al empleado.
-Segundo si hay 7 dias de preaviso entre la fecha actual y el inicio de la licencia por enfermedad. Sino informa un error por email al empleado.
-Verifica en base a los datos tomados de la db si el empleado tiene los dias disponibles por Enfermedad pedidos. Sino informa un error por email al empleado.

-Solicita a traves de discord a RRHH que autorice o no la licencia por Enfermedad.
-Espera la respuesta con un nodo wait.

    -Si RRHH desaprueba se informa un error por email al empleado.
    -Si RRHH aprueba:
        -Se Accede a Google Calendar y se marca la licencia por enfermedad.
        -Se actualiza los dias que le quedan al empleado luego de usar la licencia por enfermedad.
        -Se envia email confirmando la licencia por enfermedad al empleado.

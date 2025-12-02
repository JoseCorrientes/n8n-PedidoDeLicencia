# Flujo de n8n. 

Este flujo n8n automatiza desde una entrada que es un n8n form.
Toma un pedido de un empleado que pide una licencia, ya sea por enfermedad o por Vacaciones para una fecha de inicio y una fecha de retorno determinadas.

El flujo obtiene de una db postgres en Neon Tech los datos del empleado. Primero verifica que sea un empleado si no informa un error por email a RRHH.
-Luego verifica si el pedido de licencia es por Vacaciones o por enfermedad.

## Pedido por Vacaciones


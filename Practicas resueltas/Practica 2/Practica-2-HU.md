# Practica 2

## Problema 1: Alquiler de mobiliario

Suponga que trabaja en una consultora la cual ha sido recientemente contactada por una empresa de alquiler de mobiliario para eventos para la realización de una app. De las diferentes entrevistas se ha obtenido la siguiente información: El gerente nos dijo que resulta fundamental tener una aplicación móvil que nos permita manejar la agenda de la empresa, sabiendo qué disponibilidad tenemos y permitiendo que nuestros clientes alquilen a través de la app. Para esta primera versión de la app, el gerente nos pidió que sea posible dar de alta los diferentes mobiliarios, así como la posibilidad de que los usuarios puedan realizar una reserva de alquiler desde sus dispositivos. Para el detalle de cómo se realiza la carga de los muebles, el gerente nos sugirió hablar con el encargado del departamento de mobiliario. El encargado de mobiliario nos comentó que de cada mueble se debe cargar código de inventario, tipo de mueble, fecha de creación, fecha de último mantenimiento, estado (libre, de baja, alquilado) y el precio de alquiler. Además, no pueden existir códigos repetidos y por el contrato de la franquicia, el precio debe cargarse en dólares. Para que el encargado pueda dar de alta el mobiliario debe autenticarse en el sistema. El registro de los usuarios de carga no debe modelarse. El encargado del departamento de alquileres no comentó acerca de las reservas de los alquileres. Por una política comercial de la marca una reserva tiene que incluir como mínimo 3 muebles. La reserva debe tener una fecha, lugar del evento, cantidad de días y mobiliario junto a su cantidad. Para realizar una reserva se debe abonar el 20% del total del alquiler. El pago de la reserva se realiza únicamente con tarjeta de crédito validando número de tarjeta y fondos a través de un servicio del banco. Luego de efectuado el pago, se emite un número de reserva único que será luego utilizado por el cliente para hacer efectivo el alquiler.

### Historia de usuario 1

ID: Cargar mueble

Título: Como encargado quiero dar de alta los diferentes mobiliarios para poder mostrarlos en la aplicación.

Reglas de negocio:

- No pueden existir códigos de mobiliarios repetidos.

Criterios de aceptacion:

**Escenario 1:** Carga de mueble exitosa

Dado un mueble con código 111 que no está registrado en el sistema.

Cuando la persona ingresa: código 111, tipo silla, fecha de creación 2022, fecha de último mantenimiento 2024, estado libre y precio USD 500 y presiona "Cargar".

Entonces el sistema redirige a la página principal donde se refleja el mueble en pantalla.

**Escenario 2:** Carga fallida por código repetido

Dado que el código 111 del mueble ya está cargado.

Cuando la persona ingresa: código 111, tipo casa, fecha de creación 2022, fecha de último mantenimiento 2024, estado libre y precio USD 500 y presiona "Cargar".

Entonces el sistema informa que el mueble ya se encuentra cargado.

### Historia de usuario 2

ID: Reserva mueble

Título: Como cliente quiero reservar varios muebles a través de la aplicación para un evento.

Reglas de negocio:

- Como mínimo debe incluir 3 muebles.
- Abonar el 20% del total del alquiler.

**Criterios de aceptacion:**

**Escenario 1:** Reserva de mueble exitosa

Dado una reserva que incluye 3 muebles y se abona el 20% del total del alquiler.

Cuando la persona ingresa: Fecha 2022, lugar La Plata, cantidad de días 1, sillas cantidad 50, mesas cantidad 4, bancos cantidad 20 y presiona "Reservar".

Entonces el sistema informa que la reserva se realizó exitosamente y redirige a la página principal donde se muestra la reserva.

**Escenario 2:** Reserva fallida por falta de muebles

Dado una reserva que tiene una insuficiencia de muebles.

Cuando la persona ingresa: Fecha 2022, lugar La Plata, cantidad de días 1, sillas cantidad 50, mesas cantidad 4, bancos cantidad 20 y presiona "Reservar".

Entonces el sistema informa que la reserva no se pudo realizar debido a la falta de muebles.

**Escenario 3:** Reserva fallida por no abonar el 20% del total del alquiler

Dado que no se hizo el abono del 20%.

Cuando la persona ingresa: Fecha 2022, lugar La Plata, cantidad de días 1, sillas cantidad 50, mesas cantidad 4, bancos cantidad 20 y presiona "Reservar".

Entonces el sistema informa que la reserva no se realizó debido a la falta del abono del 20%.

**Escenario 4:** Reserva fallida por no abonar con tarjeta de crédito

Dado que la reserva no fue abonada con tarjeta de crédito.

Cuando la persona ingresa: Fecha 2022, lugar La Plata, cantidad de días 1, sillas cantidad 50, mesas cantidad 4, bancos cantidad 20 y presiona "Reservar".

Entonces el sistema informa que la reserva no se realizó debido a la utilización de un método incorrecto de pago.

### Historia de usuario 3

ID: Pago con tarjeta de crédito

Título: Como persona quiero pagar con tarjeta para poder reservar un mueble.

Reglas de negocio:

- Solo se aceptan números correspondientes a tarjetas de crédito.

**Criterios de aceptacion:**

**Escenario 1:** Pago exitoso

Dado un pago realizado con tarjeta de crédito, número de tarjeta 1234 y la tarjeta tiene saldo.

Cuando la persona ingresa la tarjeta con número 1234 y presiona pagar.

Entonces el sistema registra el pago y la página informa que el pago fue exitoso.

**Escenario 2:** Pago fallido por tarjeta inválida

Dado que la conexión con el servidor del banco es exitosa y el número 1234 no corresponde a un número de tarjeta de crédito.

Cuando se ingresa la tarjeta con número 1234.

Entonces el sistema informa un error diciendo que la tarjeta no corresponde a una tarjeta de crédito.

### Historia de usuario 4

ID: Iniciar sesión

Título: Como encargado quiero iniciar sesión para poder dar de alta muebles.

Reglas de negocio:

- Completar los campos de inicio de sesión.

**Criterios de aceptacion:**

**Escenario 1:** Inicio exitoso

Dado un usuario y contraseña que pertenecen a alguien registrado en el sistema.

Cuando la persona ingresa su usuario y contraseña.

Entonces permitirá entrar en la página con el rol de encargado y sus correspondientes herramientas.

**Escenario 2:** Inicio fallido

Dado un usuario y contraseña que no pertenecen a alguien registrado en el sistema.

Cuando la persona ingresa su usuario y contraseña incorrectos.

Entonces el sistema informará que el usuario o la contraseña son incorrectos.

### Historia de usuario 5

ID: Cerrar sesión

Título: Como usuario alumno quiero cerrar sesión para salir de mi cuenta.

Reglas de negocio:

**Criterios de aceptacion:**

**Escenario 1:** Cierre exitoso

Dado que un usuario alumno tiene la sesión iniciada.

Cuando el alumno presiona "Cerrar sesión".

Entonces el sistema lo redirige a la página principal con el rol de usuario no registrado.

## Problema 2: Posgrado

Suponga que trabaja en el área de sistemas de la Facultad de Informática y se le solicitó la automatización del pago de carreras de posgrado. Inicialmente se coordinó una reunión con el director del posgrado y se obtuvo la siguiente información: Ya que no se desea seguir cobrando el dinero en la secretaría, es necesario que los alumnos puedan pagar las carreras vía web. Como el director de posgrado no realiza tareas administrativas nos recomendó hablar con el secretario académico. De la entrevista con el secretario académico se obtuvo la siguiente información: Es necesario cargar las carreras a un sistema. En esta primera versión del sistema sólo se nos pidió esta funcionalidad, sin la modificación ni eliminación. De cada carrera se conoce: nombre de la carrera (no puede repetirse), duración en años (a partir de la consulta del estatuto de posgrado se obtuvo que como máximo son 5 años), costo y cantidad máxima de cuotas para el pago. La carga de las carreras no la realiza el secretario académico sino un empleado administrativo. Al preguntarle por la dinámica del sistema, el secretario académico nos derivó con el jefe del área administrativa, con el cual hicimos otra entrevista y pudimos obtener la siguiente información: El requerimiento fue que el alumno ingrese a la web de posgrado y pueda registrarse ingresando: nombre, apellido, nombre de usuario (único) y contraseña (más de 6 dígitos). Cualquier alumno previamente registrado, puede iniciar sesión  con su nombre de usuario y contraseña, habilitándose la inscripción a alguna de las carreras. Para ejemplificar esta funcionalidad nos otorgaron acceso al sistema SIGEF, el cual realiza funcionalidades similares para las carreras de grado. Para inscribirse, el alumno deberá seleccionar la carrera, ingresar la cantidad de cuotas a pagar, ingresar el número de tarjeta y, en caso de que la tarjeta sea válida y tenga fondos, se hará efectivo el cobro y la inscripción. La tarjeta de crédito se valida a través de un servicio del banco con el cual la universidad tiene convenio. Luego de efectuado el cobro, el sistema debe imprimir dos comprobantes, uno de inscripción y otro de pago. La única forma que tiene el alumno de pagar es con tarjeta de crédito.

### Historia de usuario 1

ID: cargar las carreras.
Titulo: como empleado administrativo quiero cargar las carreras al sistema para poder automatizar el pago de ellas.
**Reglas de negocio:**
- No pueden repetirse el nombre de las carreras.
- Una carrera no puede durar mas de 5 anios.

**Criterios de aceptacion:**
    **Escenario 1**: carga exitosa.
    Dado una carrera Letras que no existe con una duracion de 5 años. //NO DEBE TENER QUERER, TIENEN QUE IR LOS QUE TIENEN ALGUN PROBLEMA
    Cuando ingresa el nombre "Letras", duracion "5 anios", costo "50.000$" y cantidad maxima de cuotas "12". //ESTA BIEN
    Entonces el sistema registra la nueva carrera e informa que la carrera ha sido cargada.

    **Escenario 2**: carga fallida por nombre repetido.
    Dado una carrera letras que existe con una duracion de 5 años
    Cuando ingresa el nombre "Letras", duracion "5 anios", costo "50.000$" y cantidad maxima de cuotas "12".
    Entonces el sistema informa un error que el nombre de la carrera ya esta cargado y no se registra la carrera.

    **Escenario 3**: carga fallida por duracion de la carrera.
    Dado una carrera “Letras” cuya duracion es mayor a 5 anios.
    Cuando ingresa el nombre "Letras", duracion "7 anios", costo "50.000$" y cantidad maxima de cuotas "12".
    Entonces el sistema informa un error que la duracion de la carrera es mayor a 5 anios y no se registra la carrera.

### Historia de usuario 2

ID: registrarse.
Titulo: como alumno no registrado quiero registrarme para anotarme a las carreras.
**Reglas de negocio:**
- Que el nombre de usuario sea unico.
- Que la contraseña tenga mas de 6 digitos.

**Criterios de aceptacion:**
    **Escenario 1:** registro exitoso.
    Dado un alumno con nombre de usuario unico y con contraseña con mas de 6 digitos.
    Cuando ingresa nombre "Valentin", apellido "Aruanno", nombre de usuario "valengamer" y contraseña "pepito123", al presionar enter.
    Entonces el sistema informa que el alumno fue registrado exitosamente y registra al alumno.

    **Escenario 2**: registro fallido por nombre de usuario existente.
    Dado un alumno con nombre de usuario existente.
    Cuando ingresa nombre "Valentin", apellido "Aruanno", nombre de usuario "valengamer" y contraseña "pepito123",
    al presionar enter.
    Entonces el sistema informa que el nombre de usuario ingresado ya esta en uso, que ingrese uno distinto. No se registra al alumno.

    **Escenario 3**: registro fallido por contraseña invalida.
    Dado un alumno con una contraseña invalida.
    Cuando ingresa nombre "Valentin", apellido "Aruanno", nombre de usuario "valengamer" y contraseña "pep", al presionar enter.
    Entonces el sistema informa que la contraseña debe tener mas de 6 digitos y que ingrese una nueva. No se registra al alumno.

### Historia de usuario 3

ID: iniciar sesion.
Titulo: como usuario quiero iniciar sesion para hacer uso de mi cuenta registrada.
Reglas de negocio:

**Criterios de aceptacion:**
    **Escenario 1:** inicio exitoso.
        Dado una usuario y contraseña que pertenecen a alguien registrado en el sistema.
        Cuando la persona ingrese su usuario "valentin" y contraseña "xxxxx" y presiona enter.
        Entonces permitira entrar en la pagina con el rol de alumno y sus correspondientes herramientas.

    **Escenario 2:** inicio fallido.
        Dado una usuario y contraseña que no pertenecen a alguien registrado en el sistema.
        Cuando la persona ingrese su usuario "fabio" y contraseña "yyyyyy" y presiona enter.
        Entonces el sistema informara que el usuario o la contraseña son incorrectos.

### Historia de usuario 4

ID: cerrar sesion.
Titulo: como usuario alumno quiero cerrar sesion para salir de mi cuenta.
Reglas de negocio:

**Criterios de aceptacion:**

**Escenario 1:** cierre exitoso.
Dado que un usuario alumno con la sesion iniciada.
Cuando el alumno presiona cerrar sesion.
Entonces el sistema lo redirige a la pagina principal con el rol de usuario no registrado.

### Historia de usuario 5

Id: inscribirse a una carrera.
Titulo: como alumno quiero inscribirme a una carrera para poder cursarla.
Reglas de negocio:

**Escenario 1:** inscripcion exitosa.
    Dado un alumno que inicio sesion y quiere anotarse a una carrera.
    Cuando selecciona la carrera "Nutricion", cantidad de cuotas "12", numero de tarjeta "112233" y presiona enter.
    Entonces el sistema redirige al usuario al pago de inscripción con tarjeta de crédito, espera respuesta e informa que la inscripcion fue exitosa.

**Escenario 2:** Inscripción fallida por error en el pago
    Dado un alumno que inicio sesion y quiere anotarse a una carrera pero las condiciones no son las adecuadas para un pago exitoso.
    Cuando selecciona la carrera "Nutricion", cantidad de cuotas "12", numero de tarjeta "112233" y presiona enter.
    Entonces el sistema redirige al usuario al pago de inscripción con tarjeta de crédito, espera respuesta e informa que hubo un error en el pago por lo que no se pudo llevar a cabo la inscripción.

### Historia de usuario 6

Id: pago de la carrera.
Titulo: como alumno quiero pagar la carrera para poder cursarla.
Reglas de negocio:
- Que el numero de la tarjeta pertenezca a la de una tarjeta de credito.

**Escenario 1:** pago exitoso.
    Dado que la conexión con el servidor del banco es exitosa, el número 1234 corresponde a una tarjeta de crédito y la tarjeta tiene saldo.
    Cuando el usuario ingresa la tarjeta "1234" y presiona pagar.
    Entonces el sistema imprime el comprobante de pago y el de inscripcion.

**Escenario 2:** pago fallido por número de tarjeta de crédito inexistente
    Dado que la conexión con el servidor del banco es exitosa y el número :3456" no
    corresponde a un número de tarjeta de crédito.
    Cuando el matriculado o la persona ingresa el número de tarjeta "3456" y presiona "Pagar".
    Entonces el sistema retorna un error por número de tarjeta inexistente.

**Escenario 3**: pago fallido por saldo insuficiente de tarjeta de crédito.
    Dado que la conexión con el servidor del banco es exitosa y el número de tarjeta 2134 corresponde a una tarjeta de crédito y no tiene saldo para el pago que se solicita hacer.
    Cuando el usuario ingresa el número de tarjeta 2134 y presiona “Pagar”.
    Entonces el sistema retorna un error por saldo insuficiente.

**Escenario 4**: Pago fallido por fallo en la conexión con el servidor externo del banco.
    Dado que no se pudo realizar la conexión con el servidor del banco.
    Cuando el usuario ingresa un número de tarjeta y presiona “Pagar”.
    Entonces el sistema retorna un error por conexión fallida.

## Problema 3: Contratos

Suponga que trabaja en un grupo en el área de sistemas de una organización y está por comenzar un nuevo proyecto para desarrollar un sistema que depende del departamento contable. El sistema deberá administrar los contratos realizado con terceros. En una de las reuniones con el jefe de departamento nos dijo que él no usará el sistema pero que recibirá listados del personal contratado ya que deberá firmarlos para elevarlos a las autoridades. Para obtener más información generamos una reunión con el empleado de mesa de entradas. Nos contó que el problema que tienen actualmente es que realizan todas las minutas a mano por lo cual desean automatizar esta tarea. Las minutas son el paso previo a un contrato. Para confeccionar una minuta, el empleado de mesa de entradas debe ingresar nombre y número de CUIT de una persona a contratar, tipo de contrato, fecha de comienzo, duración y monto, a lo que el sistema le asociará un número de minuta automáticamente. Nos recomendó leer la reglamentación vigente acerca de contratos de la que obtuvimos que los montos de los mismos no pueden superar los $25.000 y que la duración debe ser como máximo de 6 meses. Una vez confeccionada la minuta por parte del empleado de mesa de entradas, la misma queda pendiente de aprobación. El que puede aprobar una minuta es el empleado de rendiciones. Realizamos una reunión con él y nos contó que su tarea consiste en evaluar las minutas para determinar su aprobación. También nos dijo que en otro trabajo que tiene usan un sistema llamado MiMiNuTa al que nos puede dar acceso para ver como hacen esa tarea. Después del análisis de este sistema, se concluyó que para aprobar una minuta necesitaría ingresar un número de minuta y que el sistema muestre los datos de la misma para poder aprobarla. Nos dijo que no puede aprobar la minuta si la persona a contratar tiene 3 contratos vigentes (minutas aprobadas) ni tampoco si el CUIT de la persona a contratar está inhabilitado por la AFIP. Actualmente se comunica telefónicamente con la AFIP para realizar esta verificación, pero sabe que ésta provee un servicio para aplicaciones que permite hacer la verificación en línea. Esto último nos obligó a generar una reunión con el administrador de servidores de la AFIP. Nos dijo que para poder conectarnos con un servidor de la AFIP, el sistema debe mandar un token (código que identificará de manera única a nuestra aplicación) y CUIT, si el token es correcto, el servidor responde si el CUIT está habilitado o no. Por último el empleado de rendiciones será el responsable de imprimir los listados con las minutas aprobadas, es decir, un listado con el personal contratado para poder dárselo al jefe de departamento para que lo firme

### Historia de usuario 1

ID: Realizar minuta

Titulo: Como empleado quiero automatizar la confeccion de minutas para ahorrarme el trabajo de hacerlo a mano

Reglas de negocio:

- Los montos no pueden superar los $25.000
- Duracion debe ser como maximo de 6 meses

**Escenario 1**: Minuta cargada exitosamente

Dada una minuta de un empleado con CUIT “45579759-5” cuyo monto no supera los $25.000 y duracion menor de 6 meses.

Cuando se ingresa el empleado con CUIT “45579759-5”, tipo de contrato “trainee”, fecha de comienzo 4/9/2024,  duracion 4 meses y monto $20000.

Entonces el sistema carga la minuta e informa que la minuta ha sido cargada al sistema.

**Escenario 2:** Carga de minuta fallida por monto superior a $25.000

Dada una minuta de un empleado con CUIT “45579759-5” cuyo monto supera los $25.000.

Cuando se ingresa el empleado con CUIT “45579759-5”, tipo de contrato “trainee”, fecha de comienzo 4/9/2024,  duracion 4 meses y monto $29000.

Entonces el sistema no carga la minuta e informa error por monto superior a $25.000.

**Escenario 3**: Carga de minuta fallida por duracion mayor a 6 meses 

Dada una minuta de un empleado con CUIT “45579759-5” cuyo duracion es mayor a 6 meses.

Cuando se ingresa el empleado con CUIT “45579759-5”, tipo de contrato “trainee”, fecha de comienzo 4/9/2024,  duracion 12 meses y monto $18000.

Entonces el sistema no carga la minuta e informa error por duracion mayor a 6 meses.

### Historia de usuario 2

La comunicacion con la AFIP la hace el sistema, por lo tanto no es una historia de usuario.

ID: Aprobar minuta

Titulo: Como empleado de rendiciones quiero automatizar la aprobacion de minutas para poder generar un listado del personal contratado.

Reglas de negocio:

- Una persona contratada no puede tener mas de 3 minutas
- El CUIT de la persona debe estar habilitado por la AFIP

**Escenario 1**: Minuta aprobada exitosamente

Dada un numero de minuta “44444”  que esta pendiente de aprobar, no tiene  3 minutas vigentes y  la conexion con la AFIP ha sido exitoso.

Cuando se ingresa el numero de minuta “44444” y se presiona “aprobar”.

Entonces el sistema registra el nuevo contrato e informa que la minuta ha sido aprobada.

**Escenario 2**: Minuta fallida de aprobación porque el usuario posee 3 minutas.

Dada un numero de minuta “6666666666”  que esta pendiente de aprobar y tiene 3 minutas vigentes.

Cuando se ingresa el numero de minuta “6666666666” y se presiona “aprobar”.

Entonces el sistema informa que la minuta no se puede aprobar debido a que el usuario ya posee el maximo de minutas.

**Escenario 3**: Minuta fallida de aprobación porque el usuario posee el CUIT habilitado.

Dada un numero de minuta “6666666666”  que esta pendiente de aprobar y cuyo usuario posee el CUIT deshabilitado.

Cuando se ingresa el numero de minuta “6666666666” y se presiona “aprobar”.

Entonces el sistema informa que la minuta no se puede aprobar debido a que el usuario no posee el numero de CUIT habilitado.

**Escenario 4**: Minuta fallida de aprobación porque el token enviado al sistema de la AFIP no es correcto.

Dada un numero de minuta “6666666666”  que esta pendiente de aprobar y el token que se envio durante la conexion al servidor de la AFIP es incorrecto.

Cuando se ingresa el numero de minuta “6666666666” y se presiona “aprobar”.

Entonces el sistema informa que la minuta no se puede aprobar debido a que no se ha podido conectar con el servidor de la AFIP.

**Escenario 5**: Minuta fallida de aprobación debido a que el numero de minuta no existe.

Dada un numero de minuta “6666666666”  que no existe.

Cuando se ingresa el numero de minuta “6666666666” y se presiona “aprobar”.

Entonces el sistema informa que el numero de minuta no corresponde a una minuta que esta pendiente de aprobacion.

### Historia de usuario 3

ID: Imprimir listado.

Titulo: Como empleado de rendiciones quiero imprimir un listado con las minutas para poder enviarselo al jefe de departamento.

Reglas de negocio:

**Escenario 1**: Listado armado exitosamente

Dado el listado de minutas aprobadas.

Cuando presiono imprimir.

Entonces el sistema imprime el listado e informa que la impresion se ha completado.

## Problema 4: Venta de bebidas

Se desea modelar un sistema para el manejo de venta de bebidas alcohólicas en linea. Para poder empezar a comprar en el sitio, es necesario que las personas se registren ingresando nombre, apellido, mail (será utilizado como nombre de usuario por lo tanto debe ser único) y edad. Solo se permite que se registren al sitio personas mayores a 18 años, de lo contrario el sistema debe mostrar en pantalla el texto de la ley que impide la venta de bebidas alcohólicas a menores. Si el registro es exitoso el sistema genera una contraseña que es enviada al mail ingresado en el registro. Para comprar el usuario debe iniciar sesión y una vez logueado el sistema muestra una lista de bebidas, una vez que el usuario selecciona todos los productos que desea comprar, si el usuario es premium se le hace un descuento del 20% y se informa en pantalla el total menos el 20%. Ademas si el usuario seleccionó productos por un monto superior a los $4500 se le hace un 10% de descuento y se informa en pantalla el total menos el 10%. Tenga en cuenta que si el usuario es premium y compra por un monto superior a $4500 se deben aplicar ambos descuentos.

### Historia de usuario 1

ID: Registrar usuario

Titulo: Como usuario quiero registrarme para poder comprar en la tienda.

Reglas de negocio: 

- Ley que impide la venta de bebidas a menores de 18.

**Criterios de aceptacion:**

**Escenario 1:** Registro exitoso 

Dado un usuario con mail “pepitogamer1244@gmial.com”  que es mayor a 18 años.

Cuando ingresa el nombre “Pepe”, apellido “Guardiola”, mail “pepitogamer1234@gmail.com” y edad 19 y presiona registrarse.

Entonces el sistema registra el usuario, le envia su contraseña al mail ingresado e informa que el usuario se ha registrado correctamente.

**Escenario 2:** Registro fallido porque el usuario es menor de edad

Dado un usuario con mail “pepitofocus@gmail.com” que es menor de edad.

Cuando ingresa el nombre “Pepe”, apellido “Guardiola”, mail “pepitofocus@gmail.com” y edad 17 y presiona registrarse.

Entonces el sistema sistema muestra en pantalla la ley que impide la venta de bebidas alcoholicas a menores de 18 años.

### Historia de usuario 2

ID: iniciar sesion.
Titulo: como usuario quiero iniciar sesion para poder comprar en la tienda de bebidas.
Reglas de negocio:

**Criterios de aceptacion:**
    **Escenario 1:** inicio exitoso.
        Dado una usuario “pepito” y contraseña “12345”que pertenecen a alguien registrado en el sistema.
        Cuando la persona ingrese su usuario "pepito" y contraseña "12345" y presiona enter.
        Entonces el sistema redirige a la pagina principal donde se pueden ver todas las bebidas disponibles.

    **Escenario 2:** inicio fallido.
        Dado una usuario “fabio” y contraseña “yyyyyy” que no pertenecen a alguien registrado en el sistema.
        Cuando la persona ingrese su usuario "fabio" y contraseña "yyyyyy" y presiona enter.
        Entonces el sistema informara que el usuario o la contraseña son incorrectos.

### Historia de usuario 3

ID: cerrar sesion.
Titulo: como usuario alumno quiero cerrar sesion para salir de mi cuenta.
Reglas de negocio:

**Criterios de aceptacion:**

**Escenario 1:** cierre exitoso.
Dado un usuario “pepito ”con la sesion iniciada.
Cuando el usuario presiona cerrar sesion.
Entonces el sistema lo redirige a la pagina de login y signin. 

### Historia de usuario 4

ID: Comprar productos

Titulo: como usuario quiero seleccionar los productos para poder realizar mi compra

Reglas de negocio: 

**Criterios de aceptacion**

**Escenario 1:** Compra usuario premium

Dado un usuario con nombre de usuario "valentin", que es cliente premium
Cuando arma su lista de productos y presionar "Comprar"
Entonces el sistema calcula el costo de la compra, aplica el 20% al total a pagar e informa el monto.

**Escenario 2**: Compra usuario comun
    Dado un usuario con nombre de usuario "fabio", que es cliente comun
    Cuando arma su lista de productos y presionar "Comprar"
    Entonces el sistema calcula el costo de la compra e informa el monto.

**Escenario 3**: Compra superior a $4.500
    Dado un usuario con nombre de usuario "valentin", que es cliente comun y cuya compra es superior a $4.500
    Cuando arma su lista de productos y presionar "Comprar"
    Entonces el sistema calcula el costo de la compra, aplica el 10% al total a pagar e informa el monto.

**Escenario 3**: Compra superior a $4.500 de un cliente premium
    Dado un usuario con nombre de usuario "diego", que es cliente premium y cuya compra es superior a $4.500
    Cuando arma su lista de productos y presionar "Comprar"
    Entonces el sistema calcula el costo de la compra, aplica el 30% al total a pagar e informa el monto.

## Problema 5: Casa de fotografia

Se desea desarrollar un sistema para la impresión de fotos para una casa fotográfica. Los clientes pueden subir sus fotos, pagar por internet y luego ser retiradas personalmente por el local. Para subir las fotos la persona debe registrarse en el sitio, ingresando sus datos personales, nombre, apellido, email, domicilio, nombre de usuario y contraseña. Una vez autenticado, el usuario puede subir un máximo de 50 fotos para ser impresas. Las fotos se ingresan de a una. Una vez subidas, el usuario debe abonar el monto total (el valor de cada foto es de $15). El pago se realiza con tarjeta de crédito, ingresando los datos de la misma (número de tarjeta, código de seguridad y nombre del titular), la cual debe ser validada a través del sistema del banco. Una vez que se realiza el pago se le otorga al cliente un código único que le servirá posteriormente para retirar las fotos. Un cliente debe acercarse a la sucursal para retirar las fotos enviadas previamente. Para esto debe presentar el código único a un empleado. Este registra el código, la fecha de retiro y entrega las fotos al cliente.

### Historias de usuario 1

ID: Registrar cliente

Titulo: Como cliente quiero registrarme en el sistema para subir mis fotos

Reglas de negocio:

**Criterios de aceptacion:**

**Escenario 1:** Registro exitoso

Dado un cliente con email “valentinaruanno@gmail.com” que aun no esta registrado.

Cuando ingresa nombre "Valentin", apellido "Aruanno", email “valentinaruanno@gmail.com, domicilio “7 y 49”, nombre de usuario "valengamer" y contraseña "pepito123", al presionar enter.

Entonces el sistema informa que el alumno fue registrado exitosamente y registra al alumno.

### Historias de usuario 2

ID: Iniciar sesion

Titulo: Como usuario quiero iniciar sesion para subir mis fotos

Reglas de negocio:

**Criterios de aceptacion:**

**Escenario 1**: Inicio de sesion exitoso

Dado un cliente con email “fabiotorrejon@gmail.com” que ya esta registrado.

Cuando ingresa con su email “fabiotorrejon@gmail.com” y contraseña “ColePalmer10” al presionar enter.

Entonces el sistema lo redirige a la pagina principal del sistema.

**Escenario 2:** Error en el inicio de sesion por datos incorrectos

Dado un cliente con email “capellivalentin@gmail.com” que ya esta registrado.

Cuando ingresa con su email “capellivalentin@gmail.com” y contraseña “Messi10” al presionar enter.

Entonces el sistema informa un mensaje de error, correo o contraseña incorrectos

### Historias de usuario 3

ID: Cerrar sesion

Titulo: Como usuario quiero cerrar sesion para salir de mi cuenta

Reglas de negocio:

**Criterios de aceptacion:**

**Escenario 1**: Cierre de sesion exitoso

Dado que un usuario tiene la sesión iniciada.

Cuando el usuario presiona "Cerrar sesión".

Entonces el sistema lo redirige a la página de login.

### Historias de usuario 4

ID: Subir fotos

Titulo: Como usuario quiero subir mis fotos para imprimirlas

Reglas de negocio:

- Un usuario puede subir como maximo 50 fotos

**Criterios de aceptacion:**

**Escenario 1**: Fotos subidas exitosamente

Dado “35” fotos subidas al sistema por el usuario “DJ_ValenHD” que realizo el abono con exito.

Cuando el usuario “DJ_ValenHD” presiona el boton “Comprar”.

Entonces el sistema registra la compra de las fotos y le asigna un codigo unico para que las pueda retirar.

**Escenario 2**: Carga fallida por pasar el maximo de fotos

Dado “52” fotos subidas al sistema por el usuario “keznit” que realizo el abono con exito.

Cuando el usuario “keznit” presiona el boton “Comprar”.

Entonces el sistema informa que no se pudieron registrar las fotos debido a que sobrepaso el maximo de 50 fotos.

**Escenario 3**: Carga fallida por error en el pago

Dado “23” fotos subidas al sistema por el usuario “fabio” pero las condiciones no son las adecuadas para un pago exitoso.

Cuando el usuario con número de tarjeta “4352-2323-2323-1211”, código de seguridad “777” y nombre del titular “SERGIO”.

Entonces el sistema redirige al usuario al pago con tarjeta de crédito, espera respuesta e informa que hubo un error en el pago.

### Historias de usuario 5

ID: Realizar pago

Titulo: Como usuario quiero realizar el pago de las fotos para poder retirarlas

Reglas de negocio:

- El pago debe realizarse con tarjeta de credito

**Criterios de aceptacion:**

**Escenario 1**: Pago realizado exitosamente

Dado que la conexion con el banco es exitosa, el numero de tarjeta “4352-2323-2323-1211“ corresponde a una tarjeta de credito y la misma tiene saldo.

Cuando el usuario con número de tarjeta de credito “4352-2323-2323-1211”, código de seguridad “777” y nombre del titular “PEPE”.

Entonces el sistema informa que el pago se ha realizado con exito, genera un codigo unico de compra y se lo asigna.

**Escenario 2**: Error en el pago por tarjeta de credito existente

Dado que la conexion con el banco es exitosa pero el numero de tarjeta “7777-7777-7777-7777” no corresponde a una tarjeta de credito.

Cuando el usuario con numero de tarjeta de credito “7777-7777-7777-7777”, codigo de seguridad “777” y nombre del titular “FABIO”

Entonces el sistema informa que hubo un error en el pago debido a que el numero de tarjeta no coincide con ninguna.

**Escenario 3**: Error en el pago por saldo insuficiente

Dado que la conexion con el banco es exitosa, el numero de tarjeta “4352-2323-2323-1266” corresponde a una tarjeta de credito y la misma no tiene saldo.

Cuando el usuario con número de tarjeta de credito “4352-2323-2323-1266”, código de seguridad “666” y nombre del titular “MILTON”

Entonces el sistema informa que el pago no se ha realizo debido a que la tarjeta de credito no tiene el saldo suficiente.

**Escenario 4**: Error en el pago por mala conexion con el banco

Dado que la conexion con el banco no es la ideal.

Cuando el usuario con numero de tarjeta de credito “444-7777-7777-7777”, codigo de seguridad “619” y nombre del titular “JORGE”

Entonces el sistema informa que hay un error en la conexion con el banco.

### Historias de usuario 6

ID: Retirar fotos

Titulo: Como cliente quiero retirar mis fotos para tenerlas impresas fisicamente

Reglas de negocio:

Criterios de aceptacion:

**Escenario 1:** Retiro exitoso

Dado el codigo “333” del cliente “Valentin Aruanno” que realizo exitosamente el pago.

Cuando el cliente “Valentin Aruanno” le muestra el codigo al empleado.

Entonces el empleado verifica que el codigo coincide con una compra ya realizada y le entrega las fotos impresas.

## Problema 6: Biblioteca

 La biblioteca de una escuela primaria realiza su trabajo de forma manual y requiere un sistema informático que automatice su funcionamiento. La bibliotecaria recibe libros por donaciones de los padres de los chicos que asisten a la escuela. De un mismo libro se pueden tener varios ejemplares. Para que un alumno pueda asociarse debe presentar el DNI y certificado de alumno regular. Una vez asociado, se le otorga un carnet con su correspondiente número de socio. Los préstamos se realizan exclusivamente a socios habilitados, que no posean más de tres préstamos vigentes y no tengan préstamos vencidos. La bibliotecaria presta libros que se encuentren en buen estado. Cuando un libro se encuentra deteriorado ya no se presta.Cuando el socio retorna un libro se verifica si el préstamo se encuentra vencido. En este caso, la bibliotecaria suspende al socio, que por 15 días no podrá solicitar nuevos préstamos.

### Historias de usuario 1

ID: Asociar alumno

Titulo: Como alumno quiero asociarme para poder retirar libros

Reglas de negocio:

- Tener certificado de alumno regular

**Criterios de aceptacion:**

**Escenario 1**: Asociación exitosa

Dado un alumno con DNI “65.323.353” que posee certificado de alumno regular.

Cuando el alumno ingrese su DNI “65.323.353”, su certificado de alumno regular y presione asociarse

Entonces el sistema registra al alumno y le genera su carnet con su numero de socio.

**Escenario 2**: Asociacion fallida por falta de certificado regular

Dado un alumno con DNI “63.777.777” que no posee certificado de alumno regular

Cuando el alumno ingrese su DNI “63.777.777” y presione asociarse

Entonces el sistema no registrara al alumno y le informara que le falta subir su certificado de alumno regular

### Historias de usuario 2

ID: Realizar prestamo

Titulo: Como usuario asociado quiero realizar un prestamo para conseguir un libro que quiero

Reglas de negocio:

- Un socio no puede tener mas de 3 prestamos vigentes
- Un socio no puede tener prestamos vencidos

**Criterios de aceptacion**:

**Escenario 1**: Prestamo exitoso

Dado un socio con DNI “65.323.353” que posee menos de 3 prestamos vigentes y no tiene prestamos vencidos.

Cuando el socio con 2 prestamos vigentes selecciona el libro que desea y presiona realizar prestamo.

Entonces el sistema registra el prestamo y le suma un prestamo vigente al socio.

**Escenario 2**: Prestamo fallido por tener 3 prestamos vigentes

Dado un socio con DNI “64.444.353” que posee 3 prestamos vigentes y no tiene prestamos vencidos.

Cuando el socio con DNI “64.444.353” selecciona el libro que desea y presiona realizar prestamo.

Entonces el sistema le informa que el prestamo no se puede realizar debido a que ya tiene 3 prestamos vigentes.

**Escenario 3**: Prestamo fallido por tener prestamos vencidos

Dado un socio con DNI “64.444.777” que posee menos de 3 prestamos vigentes y tiene prestamos vencidos.

Cuando el socio con DNI “64.444.777” selecciona el libro que desea y presiona realizar prestamo.

Entonces el sistema le informa que el prestamo no se puede realizar debido a que tiene prestamos vencidos.

### Historias de usuario 3

ID: Devolver libro

Titulo: Como socio quiero devolver un libro porque ya cumplio con lo que necesitaba

Reglas de negocio:

- No pasarse del tiempo pactado

**Criterios de aceptacion:**

**Escenario 1**: Devolucion exitosa

Dado un socio con DNI “77.777.777” que esta al dia con el prestamo.

Cuando el socio con DNI “77.777.777” presiona devolver libro.

Entonces el sistema registra el retorno del libro y lo descuenta de los prestamos vigentes del socio.

**Escenario 2**: Devolucion fallida

Dado un socio con DNI “77.777.777” que no esta al dia con el prestamo.

Cuando el socio con DNI “77.777.777” presiona devolver libro.

Entonces el sistema suspende por 15 dias al socio, registra el retorno del libro y lo descuenta de los prestamos vigentes.

## Problema 7: Mutual

Una mutual necesita automatizar el manejo de las prestaciones que ofrece a sus afiliados. Una persona puede afiliarse sólo si posee una tarjeta de crédito para que se pueda hacer el pago de la cuota mensual automáticamente. Una vez que la persona se ha afiliado, puede pasar a tener a cargo a su pareja e hijos (hasta 18 años, luego es dado de baja). A cada uno se le otorga un número de afiliado. Las prestaciones que brinda, siempre y cuando esté asentado el pago del mes anterior al que es solicitado, son:

- Ortodoncia: Se reconoce sólo una y a los afiliados menores de 15 años que estén afiliados desde al menos
nueve meses. Debe presentarse historia clínica elaborado por el profesional.
- Plantillas: A cualquier afiliado, hasta dos por año calendario. Debe presentarse la indicación del profesional y
factura del comercio que la confeccionó.
- Anteojos: A cualquier afiliado con fecha de afiliación superior a tres meses, un par cada 18 meses.
- Internación: A cualquier afiliado, sin límite.
- Consultas médicas: A cualquier afiliado, hasta 2 por mes.

### Historias de usuario 1

ID: Afiliar persona

Titulo: Como persona quiero afiliarme parar obtener ciertos servicios

Reglas de negocio:

- Pagar por mes con tarjeta de credito

**Criterios de aceptacion**:

**Escenario 1**: Afiliacion exitosa

Dado una persona “HUGO” que posee una tarjeta de credito y aun no esta afiliado

Cuando la persona “HUGO” presiona afiliarse.

Entonces el sistema permite la afiliacion, otorga un numero de afiliado y si tiene pareja y/o hijos menos a 18 años, estos son afiliados

**Escenario 2:** Afiliacion fallida por tarjeta de credito invalida

Dado una persona “PEPE” que posee una tarjeta de credito invalida y aun no esta afiliado

Cuando la persona “PEPE” presiona afiiarse

Entonces el sistema no permite la afiliacion debido a que la tarjeta de credito no pertenece a una tarjeta valida.

### Historias de usuario 2

ID: Prestar ortodoncia

Titulo: Como afiliado quiero ponerme ortodoncia para mejorar el aspecto de mi sonrisa

Reglas de negocio:

- Debe estar afiliado al menos por 9 meses
- Debe presentarse historia clinica elaborada por un profesional
- Debe estar pago el mes anterior
- Afiliado menor a 15 años
- Se puede realizar este prestamo una vez por afiliado

**Criterios de aceptacion**:

**Escenario 1**: Prestamo exitoso

Dado un afiliado “FABIO” que esta afiliado hace 10 meses, esta al dia con el pago, tiene 13 años, nunca solicito el prestamo y presento la historia clinica elaborada por un profesional

Cuando el afiliado “FABIO” presiona pedir prestamo.

Entonces el sistema registra el prestamo de la ortodoncia y le informa que el prestamo se ha realizado con exito

**Escenario 2**: Prestamo fallido por falta de meses de afiliacion

Dado un afiliado “JORGE” que esta afiliado hace 7 meses, esta al dia con el pago, tiene 13 años, nunca solicito el prestamo y presento la historia clinica elaborada por un profesional

Cuando el afiliado “JORGE” presiona pedir prestamo.

Entonces el sistema no registra el prestamo de la ortodoncia y le informa que el prestamo no se ha realizado debido a que no cumple con el minimo de 9 meses afiliado.

**Escenario 3**: Prestamo fallido por falta de historia clinica

Dado un afiliado “PEPE” que esta afiliado hace 12 meses, esta al dia con el pago, tiene 13 años, nunca solicito el prestamo y no presento la historia clinica elaborada por un profesional

Cuando el afiliado “PEPE” presiona pedir prestamo.

Entonces el sistema no registra el prestamo de la ortodoncia y le informa que el prestamo no se ha realizado debido a que no presento la historia clinica elaborada por un profesional.

**Escenario 4**: Prestamo fallido por no estar al dia con el pago

Dado un afiliado “LIONEL” que esta afiliado hace 12 meses, no esta al dia con el pago, tiene 13 años, nunca solicito el prestamo y presento la historia clinica elaborada por un profesional

Cuando el afiliado “LIONEL” presiona pedir prestamo.

Entonces el sistema no registra el prestamo de la ortodoncia y le informa que el prestamo no se ha realizado debido a que no esta al dia con el pago

**Escenario 5**: Prestamo fallido por ser mayor de 15 años

Dado un afiliado “MARTIN” que esta afiliado hace 12 meses, esta al dia con el pago, tiene 34 años, nunca solicito el prestamo y presento la historia clinica elaborada por un profesional

Cuando el afiliado “MARTIN” presiona pedir prestamo.

Entonces el sistema no registra el prestamo de la ortodoncia y le informa que el prestamo no se ha realizado debido a que supera el maximo de edad permitida.

**Escenario 6**: Prestamo fallido por ya haberlo solicitado

Dado un afiliado “VALENTIN” que esta afiliado hace 12 meses, esta al dia con el pago, tiene 10 años, solicito el prestamo una vez y presento la historia clinica elaborada por un profesional

Cuando el afiliado “VALENTIN” presiona pedir prestamo.

Entonces el sistema no registra el prestamo de la ortodoncia y le informa que el prestamo no se ha realizado debido a que ya se realizo el prestamo en algun momento y no es posible realizarlo nuevamente

### Historias de usuario 3

ID: Prestar plantillas

Titulo: Como afiliado quiero obtener plantillas para caminar mejor y no tener problemas de columna.

Reglas de negocio:

- Estar al dia con el pago
- Hasta dos por año
- Presentar indicacion del profesional
- Presentar factura del comercio que la confecciono

**Criterios de aceptacion**:

**Escenario 1**: Prestamo exitoso

Dado un afiliado “JORGE” que esta al dia con el pago, realizo el prestamo una vez, presenta indicacion del profesional y factura del comercio que la confecciono

Cuando el afiliado “JORGE” presiona pedir prestamo.

Entonces el sistema registra el prestamo de las plantillas y le informa que el prestamo se ha realizado con exito.

**Escenario 2**: Prestamo fallido por no estar al dia con el pago

Dado un afiliado “CAPE” que no esta al dia con el pago, realizo el prestamo una vez, presenta indicacion del profesional y factura del comercio que la confecciono

Cuando el afiliado “CAPE” presiona pedir prestamo.

Entonces el sistema rechaza el prestamo y le informa que el prestamo no se ha realizado debido a que debe pagar el mes anterior.

**Escenario 3**: Prestamo fallido por pasar el limite de prestamos

Dado un afiliado “SANTI” que esta al dia con el pago, realizo el prestamo dos veces, presenta indicacion del profesional y factura del comercio que la confecciono

Cuando el afiliado “SANTI” presiona pedir prestamo.

Entonces el sistema rechaza el prestamo y le informa que el prestamo no se ha realizado debido a que solo se pueden realizar 2 prestamos por año.

**Escenario 4**: Prestamo fallido por no presentar indicacion de un profesional

Dado un afiliado “JULIAN” que esta al dia con el pago, realizo el prestamo una vez, no presenta indicacion del profesional y presenta factura del comercio que la confecciono

Cuando el afiliado “JULIAN” presiona pedir prestamo.

Entonces el sistema rechaza el prestamo y le informa que el prestamo no se ha realizado debido a que no presenta indicacion de un profesional

**Escenario 5**: Prestamo fallido por no presentar factura del comercio que la confecciono

Dado un afiliado “PEPITO” que esta al dia con el pago, realizo el prestamo una vez, presenta indicacion del profesional y no presenta factura del comercio que la confecciono

Cuando el afiliado “PEPITO” presiona pedir prestamo.

Entonces el sistema rechaza el prestamo y le informa que el prestamo no se ha realizado debido a que no presenta factura del comercio que la confecciono

### Historias de usuario 4

ID: Prestar anteojos

Titulo: Como afiliado quiero obtener anteojos para poder ver mejor y descansar la vista

Reglas de negocio:

- Estar al dia con el pago
- Estar afiliado por mas de 3 meses
- Un par cada 18 meses

**Criterios de aceptacion:**

**Escenario 1**: Prestamo realizado exitosamente

Dado un afiliado “LUCAS” que esta al dia con el pago, esta afiliado hace 5 meses y solicito un par hace 2 años

Cuando el afiliado “LUCAS” presiona pedir prestamo

Entonces el sistema registra el prestamo de los anteojos y le informa que el prestamo se ha realizado con exito.

**Escenario 2**: Prestamo fallido por no estar al dia con el pago

Dado un afiliado “CAPE” que no esta al dia con el pago, esta afiliado hace 5 meses y solicito un par hace 2 años

Cuando el afiliado “CAPE” presiona pedir prestamo

Entonces el sistema rechaza el prestamo de los anteojos y le informa que no se ha realizado el prestamo debido a que debe el pago del mes anterior

**Escenario 3**: Prestamo fallido por no estar afiliado por mas de 3 meses

Dado un afiliado “RYAN GARCIA” que esta al dia con el pago, esta afiliado hace 2 meses y solicito un par hace 2 años

Cuando el afiliado “RYAN GARCIA” presiona pedir prestamo

Entonces el sistema rechaza el prestamo de los anteojos y le informa que no se ha realizado el prestamo debido a que no cumple con el minimo de meses de afiliacion

**Escenario 4**: Prestamo fallido por solicitar mas de uno en 18 meses

Dado un afiliado “COLE PALMER” que esta al dia con el pago, esta afiliado hace 5 meses y solicito un par hace 3 meses

Cuando el afiliado “COLE PALMER” presiona pedir prestamo

Entonces el sistema rechaza el prestamo de los anteojos y le informa que solo se puede realizar un prestamo cada 18 meses.

### Historias de usuario 5

ID: Prestar internacion

Titulo: Como afiliado quiero internarme porque estoy en graves condiciones 

Reglas de negocio:

- Estar al dia con el pago

**Criterios de aceptacion:**

**Escenario 1**: Prestamo de internacion exitoso

Dado un afiliado “NICOLAS” que esta al dia con el pago

Cuando el afiliado “NICOLAS” presiona pedir prestamo

Entonces el sistema registra la solicitud de internacion y le informa que el prestamo se realizo con exito

**Escenario 2**: Prestamo fallido por no estar al dia con el pago

Dado un afiliado “VALENTIN” que no esta al dia con el pago

Cuando el afiliado “VALENTIN” presiona pedir prestamo

Entonces el sistema rechaza la solicitud de internacion y le informa que no se ha podido realizar el prestamo debido a que debe el pago del mes anterior

### Historias de usuario 6

ID: Prestar consultas medicas

Titulo: Como afiliado quiero tener consultas medicas para tenerlas en el caso de enfermarme

Reglas de negocio: 

- Estar al dia con el pago
- Hasta 2 por mes

**Criterios de aceptacion:**

**Escenario 1**: Prestamo exitoso

Dado un afiliado “MESSI” que esta al dia con el pago y realizo una unica consulta en el mes

Cuando el afiliado “MESSI” presiona pedir prestamo

Entonces el sistema registra el prestamo y le informa que el prestamo se ha realizado con exito

**Escenario 2**: Prestamo fallido por no deber pago del mes anterior

Dado un afiliado “SERGIO” que no esta al dia con el pago y realizo una unica consulta en el mes

Cuando el afiliado “SERGIO” presiona pedir prestamo

Entonces el sistema rechaza el prestamo y le informa que debe el pago del mes anterior

**Escenario 3**: Prestamo fallido por solicitar mas de 2 veces en un mismo mes

Dado un afiliado “CAPE” que esta al dia con el pago y realizo 2 consultas en el mes

Cuando el afiliado “CAPE” presiona pedir prestamo

Entonces el sistema rechaza el prestamo y le informa que ya realizo el maximo de consultas en el mes

## Problema 8 - teatro

Se desea modelar un sistema de gestión de ventas de entradas para un teatro. Las personas compran sus entradas a través de una página web, o personalmente. El sistema permite, sólo de modo personal en el teatro, la reserva de entradas de forma gratuita. El empleado debe ingresar los datos de la obra (fecha, hora, y nombre) junto el nombre y DNI del espectador. En este caso, sólo se podrá reservar hasta 2 entradas. Las entradas reservadas no compradas caducarán tres horas antes del evento. Para seleccionar el nombre de la obra, el sistema muestra una grilla de funciones disponibles para que el usuario seleccione una. Para comprar una entrada vía web, el sistema muestra la grilla de funciones disponibles. El usuario selecciona una opción, ingresa su DNI, la cantidad de lugares solicitados y selecciona la opción “pagar”. El pago se realiza con tarjeta de crédito. Para esto debe ser autorizada a través del sistema del banco. Este pide el número de tarjeta, vencimiento, y código de seguridad. Verifica todos los campos y autoriza la compra. Autorizada la tarjeta, se emite un código de compra con el que el cliente podrá retirar sus entradas en la boletería del cine. Para comprar una entrada personalmente, el vendedor de la boletería solicita los datos de la función al cliente, procediendo de un modo similar a la compra web, con la diferencia que en este caso no se muestra el código de compra sino que se imprimen directamente la/s entrada/s. El pago es unicamente con tarjeta de crédito, igual que en el caso anterior. Para retirar las entradas reservadas previamente, el empleado solicita nombre y DNI del espectador, el sistema valida que la persona posea entradas reservadas, y que no estén caducas. El resto del procedimiento se realiza igual que la compra de entradas descriptas anteriormente. Cuando una persona llega con el código de compra, el vendedor debe ingresar el código para que el sistema, luego de verificarlo, imprima las entradas correspondientes. Además se desea administrar la programación de las salas. El administrador ingresa la distribución semanal de las obras en las salas de manera que se encuentre disponible para la realización de la venta de entradas.

### Historias de usuario 1

ID: Reservar entradas

Titulo: Como cliente quiero reservar una entrada para ver una obra

Regla de negocio:

- Solo se pueden reservar como maximo dos entradas
- Caducan 3 horas antes del evento

Criterios de aceptacion:

Escenario 1: Reserva exitosa

Dado que la obra “ZZZ” existe, el cliente quiere 1 entrada y faltan 4 horas para la obra
Cuando el empleado ingresa la fecha de la obra 6/6/2024, hora 20:00, nombre “ZZZ” nombre del cliente “Pepe” y DNI 45.579.759
Entonces el sistema registra una reserva de entrada y lo informa

Escenario 2: Reserva fallida por pasar el maximo de entradas

Dado que la obra “333” existe, el cliente quiere 3 entrada y faltan 4 horas para la obra
Cuando el empleado ingresa la fecha de la obra 3/3/2024, hora 20:00, nombre “333” nombre del cliente “Lolo” y DNI 43.573.753
Entonces el sistema informa que como maximo puede reservar 2 entradas

Escenario 3: Reserva fallida por tiempo indebido

Dado que la obra “XXX” existe, el cliente quiere 2 entrada y faltan 2 horas para la obra
Cuando el empleado ingresa la fecha de la obra 2/2/2024, hora 20:00, nombre “XXX” nombre del cliente “Messi” y DNI 77.777.777
Entonces el sistema informa que solo se pueden reservar entradas hasta 3 horas antes de la obra

### Historias de usuario 2

ID: Comprar entradas via web

Titulo: Como cliente quiero comprar entradas via web para ver una obra

Reglas de negocio

- El pago se con tarjeta de credito

Criterios de aceptacion 

Escenario 1: Compra exitosa

Dado que la obra “333” existe y quedan lugares disponibles 
Cuando el cliente ingresa DNI 45.579.759, cantidad de lugares 3 e ingresa los datos de una tarjeta de credito valida
Entonces el sistema registra la compra y lo notifica 

Escenario 2: Compra fallida por tarjeta invalida

Dado que la obra “111” existe y quedan lugares disponibles
Cuando el cliente ingresa DNI 45.577.777, cantidad de lugares 1 e ingresa los datos de una tarjeta de credito invalida
Entonces el sistema notifica un error por tarjeta de credito invalida

Escenario 3: Compra fallida por lugares no disponibles

Dado que la obra “777” existe y no quedan lugares disponibles
Cuando el cliente ingresa DNI 45.579.666, cantidad de lugares 1 e ingresa los datos de una tarjeta de credito valida
Entonces el sistema notifica un error por sold out

### Historias de usuario 3

ID: Realizar pago

Titulo: Como cliente quiero realizar el pago para comprar mis entradas

Reglas de negocio:

- Tarjeta de credito valida

Criterios de aceptacion:

**Escenario 1**: Pago realizado exitosamente

Dado que la conexion con el banco es exitosa, el numero de tarjeta “4352-2323-2323-1211“ corresponde a una tarjeta de credito y la misma tiene saldo.

Cuando el usuario con número de tarjeta de credito “4352-2323-2323-1211”, código de seguridad “777” y vencimiento 2/28.

Entonces el sistema informa que el pago se ha realizado con exito, genera un codigo unico de compra y se lo asigna.

**Escenario 2**: Error en el pago por tarjeta de credito inexistente

Dado que la conexion con el banco es exitosa pero el numero de tarjeta “7777-7777-7777-7777” no corresponde a una tarjeta de credito.

Cuando el usuario con numero de tarjeta de credito “7777-7777-7777-7777”, codigo de seguridad “777” y vencimiento 2/21

Entonces el sistema informa que hubo un error en el pago debido a que el numero de tarjeta no coincide con ninguna.

**Escenario 3**: Error en el pago por saldo insuficiente

Dado que la conexion con el banco es exitosa, el numero de tarjeta “4352-2323-2323-1266” corresponde a una tarjeta de credito y la misma no tiene saldo.

Cuando el usuario con número de tarjeta de credito “4352-2323-2323-1266”, código de seguridad “666” y vencimiento 3/28

Entonces el sistema informa que el pago no se ha realizo debido a que la tarjeta de credito no tiene el saldo suficiente.

**Escenario 4**: Error en el pago por mala conexion con el banco

Dado que la conexion con el banco no es la ideal.

Cuando el usuario con numero de tarjeta de credito “444-7777-7777-7777”, codigo de seguridad “619” y vencimiento 5/29

Entonces el sistema informa que hay un error en la conexion con el banco.

### Historias de usuario 4

ID: Comprar entradas personalmente

Titulo: Como usuario quiero comprar entradas personalmente para ver una obra

Reglas de negocio:

- El pago se realiza con tarjeta de credito

Criterios de aceptacion

Escenario 1: Compra exitosa

Dado que la obra “333” existe y quedan lugares disponibles 
Cuando el empleado ingresa DNI 45.579.759, cantidad de lugares 3 e ingresa los datos de una tarjeta de credito valida
Entonces el sistema registra la compra e imprime las entradas

Escenario 2: Compra fallida por tarjeta invalida

Dado que la obra “111” existe y quedan lugares disponibles
Cuando el empleado ingresa DNI 45.577.777, cantidad de lugares 1 e ingresa los datos de una tarjeta de credito invalida
Entonces el sistema notifica un error por tarjeta de credito invalida

Escenario 3: Compra fallida por lugares no disponibles

Dado que la obra “777” existe y no quedan lugares disponibles
Cuando el empleado ingresa DNI 45.579.666, cantidad de lugares 1 e ingresa los datos de una tarjeta de credito valida
Entonces el sistema notifica un error por sold out

### Historias de usuario 5

ID: Retirar entradas reservadas

Titulo: Como cliente quiero retirar mis entradas reservadas para ver la obra

Reglas de negocio:

- El pago se realiza con tarjeta de credito

Criterios de aceptacion

Escenario 1: Retiro exitoso

Dado que el cliente posee 1 entrada reservada, tarjeta de credito valida y faltan 5 horas para la obra
Cuando el empleado Ingresa nombre Pepe, DNI 45.579.759 e ingresa los datos de una tarjeta de credito valida
Entonces el sistema registra la compra e imprime las entradas

Escenario 2: Retiro fallido por entradas caducas

Dado que el cliente posee 1 entrada reservada, tarjeta de credito valida y falta 1 hora para la obra
Cuando el empleado ingresa nombre Cape, DNI 10.100.100 e ingresa los datos de una tarjeta de credito valida
Entonces el sistema notifica que no se pudo realizar la compra por entradas caducas

Escenario 3: Retiro fallido por tarjeta invalida

Dado que el cliente posee 1 entrada reservada, tarjeta de credito invalida y falta 7 hora para la obra
Cuando el empleado ingresa nombre Fabio, DNI 77.777.777 e ingresa los datos de una tarjeta de credito invalida
Entonces el sistema notifica un error por tarjeta de credito invalida

Escenario 4: Retiro fallido por entradas no reservadas

Dado que el cliente no posee entradas reservadas
Cuando el empleado ingresa nombre Agus, DNI 66.666.666 e ingresa los datos de una tarjeta de credito valida
Entonces el sistema notifica un error por entradas reservadas inexistentes

### Historias de usuario 6

ID: Retirar entradas compradas

Titulo: Como cliente quiero retirar mis entradas compradas para ver la obra

Reglas de negocio:

Criterios de aceptacion

Escenario 1: Retiro exitoso

Dado que el cliente posee 1 entrada comprada
Cuando el empleado ingresa el codigo de compra 777
Entonces el sistema imprime las entradas

Escenario 2: Retiro fallido por codigo inexistente

Dado que el cliente no posee ninguna entrada
Cuando el empleado ingresa el codigo 999
Entonces el sistema notifica que no encontro dicho codigo en el sistema

### Historias de usuario 7

ID: Administrar programacion de salas

Titulo: Como administrador quiero ingresar la distribucion semanal de las obras en las salas para que se encuentre disponible la realizacion de la venta de entradas

Reglas de negocio:

Criterios de aceptacion

Escenario 1: Ingreso exitoso

Dado una distribucion semanal
Cuando el administrador ingresa la distribucion semanal de las obras en las salas
Entonces el sistema registra el ingreso y pone disponible la venta de las entradas

## Problema 9 - Pago electronico

Se desea modelar un sistema de pago electrónico de impuestos y servicios en efectivo. Cuando un cliente llega para realizar un pago, el empleado o el gerente de la sucursal ingresa el código de pago electrónico, y el sistema se conecta con la central de cobro para recuperar los datos de la factura. Los datos incluyen: empresa, número de cliente, primera fecha de vencimiento, segunda fecha de vencimiento, recargo y monto original. Una vez recuperados los datos, el sistema debe verificar los vencimientos para determinar el monto a cobrar. Si el segundo vencimiento está vencido, se debe informar que la factura no se puede cobrar. Si el primer vencimiento está vencido, hay que aplicar el recargo al monto original. Si la factura no está vencida, se cobra el monto original. Además, una vez al día, el gerente de la sucursal debe registrar en la central de cobros los pagos realizados por los clientes. Para hacer esto, el sistema requiere la clave maestra, y, si es correcta, recupera las transacciones de impuestos y servicios cobrados durante el día. Luego, se conecta a la central de cobro y envía las transacciones. Cuando la central confirma la recepción exitosa, el sistema las marca como enviadas. Es importante que las transacciones no puedan enviarse dos veces, por lo que si el gerente intenta hacerlo, el sistema no debe permitirlo. Finalmente, el gerente puede consultar las estadísticas de los impuestos y servicios cobrados. Para ello, ingresa la clave maestra y un rango de fechas sobre las cuales se deben calcular las estadísticas. El sistema mostrará los montos y la cantidad de cobros realizados, agrupando por empresa. Es importante tener en cuenta que, cada vez que el sistema debe conectarse a la central, debe enviar un token (código que identifica al sistema). Una vez que la central valida el token, el sistema puede enviar el requerimiento para recuperar los datos de la factura o registrar los pagos del día, según corresponda.

### Historias de usuario 1

ID: Realizar pago

Titulo: Como cliente quiero realizar el pago de mis impuestos o servicios para cumplir con mi deber de ciudadano

Reglas de negocio:

- Si la factura se vencio una vez, se le agregar un recargo al monto total
- Si la factura se vencio dos veces, no se puede pagar

Criterios de aceptacion

Escenario 1: Pago exitoso

Dado una factura con codigo 111 sin vencimiento
Cuando el empleado o gerente ingresa el codigo de la factura 111
Entonces el sistema recupera los datos de la factura y registra del pago

Escenario 2: Pago con vencimiento

Dado una factura con codigo 333 con un vencimiento
Cuando el empleado o gerente ingresa el codigo de la factura 333
Entonces el sistema recupera los datos de la factura y registra el pago con el recargo adicional

Escenario 3: Pago fallido por 2 vencimientos

Dado una factura con codigo 444 con 2 vencimientos
Cuando el empleado o gerente ingresa el codigo de la factura 444
Entonces el sistema recupera los datos de la factura y notifica que no se puede efectuar el pago por 2 vencimientos

Escenario 4: Pago fallido por error de conexion con el servidor de central de cobro

Dado una factura con codigo 555 sin vencimiento
Cuando el empleado o gerente ingresa el codigo de la factura 555
Entonces el sistema informa que no puedo recuperar los datos de la factura por mala conexion con el sistema

### Historia de usuario 2

ID: Recuperar factura

Titulo: Como empleado o gerente quiero recuperar las facturas para registrar el pago de las mismas

Reglas de negocio:

Criterios de aceptacion

Escenario 1: Recuperacion exitosa

Dado que el codigo de pago electronico 777 pertenece a una factura y la conexion con el servidor de central de cobro es exitosa
Cuando el empleado o gerente ingresa el codigo de pago electronico 777
Entonces el sistema registra la recuperacion de la factura

Escenario 2: Recuperacion fallida por codigo de pago electronico inexistente

Dado que el codigo de pago electronico 999 no pertenece a una factura y la conexion con el servidor de central de cobro es exitosa
Cuando el empleado o gerente ingresa el codigo de pago electronico 999
Entonces el sistema notifiica que ese codigo de pago electronico no existe

Escenario 3: Recuperacion fallida por mala conexion con el servidor de central de cobro

Dado que el codigo de pago electronico 666 pertenece a una factura y la conexion con el servidor de central de cobro es dificultosa
Cuando el empleado o gerente ingresa el codigo de pago electronico 666
Entonces el sistema notifica que no se ha podido conectar con el servidor de cobro por mala conexion

### Historias de usuario 3

ID: Registrar pagos

Titulo: Como gerente quiero registrar los pagos para enviar las transacciones realizadas

Reglas de negocio

- Clave maestra valida
- No se pueden enviar las transacciones del dia mas de una vez

Criterios de aceptacion

Escenario 1: Registro de pagos exitoso

Dado que la clave maestra 111 es correcta, el registro aun no se ha realizado y la conexion con el servidor de central de cobros es exitosa
Cuando el gerente ingresa la clave maestra 111 
Entonces el sistema recupera las transacciones realizadas en el dia y se las envia al servidor de central de cobros

Escenario 2: Registro de pago fallido por clave maestra incorrecta

Dado que la clave maestra 333 es incorrecta, el registro aun no se ha realizado y la conexion con el servidor de central de cobros es exitosa
Cuando el gerente ingresa la clave maestra 333 
Entonces el sistema notifica que la clave maestra es incorrecta

Escenario 3: Registro de pago fallido por mala conexion con el servidor de central de cobros

Dado que la clave maestra 777 es correcta, el registro aun no se ha realizado y la conexion con el servidor de central de cobros es mala
Cuando el gerente ingresa la clave maestra 777
Entonces el sistema notifica que no se pudo establecer conexion con el servidor de central de cobros

Escenario 4: Registro de pago fallido por segunda vez consecutiva en el dia

Dado que la clave maestra 666 es correcta, el registro ya se ha realizado y la conexion con el servidor de central de cobros es exitosa
Cuando el gerente ingresa la clave maestra 666
Entonces el sistema notifica que no se puede volver a realizar el registro dos veces en un mismo dia

### Historias de usuario 4

ID: Ver estadisticas

Titulo: Como gerente quiero ver las estadisticas de los impuestos y servicios cobrados para ver cuantos pagos se realizaron

Reglas de negocio:

- Clave maestra valida

Criterios de aceptacion

Escenario 1: Muestra exitosa

Dado que la clave maestra 777 es correcta y el rango de fechas ingresado es valido 6/04/2024-6/10/2024
Cuando el gerente ingresa la clave maestra 777 y las fechas 6/04/2024-6/10/2024
Entonces el sistema muestra los montos y la cantidad de cobros realizados, agrupando por empresa.

Escenario 2: Muestra fallida por clave maestra incorrecta

Dado que la clave maestra 666 es incorrecta y el rango de fechas ingresado es valido
Cuando el gerente ingresa la clave maestra 666 y las fechas 6/04/2024-6/10/2024
Entonces el sistema notifica que la clave maestra ingresada es incorrecta

Escenario 3: Muestra fallida por rango de fechas invalido

Dado que la clave maestra 111 es correcta y el rango de fechas ingresado es invalido
Cuando el gerente ingresa la clave maestra 111 y las fechas 66/66/666-6/66/6666
Entonces el sistema notifica que el rango de fechas ingresado es incorrrecto

## Problema 10 - Un Aventón

Se desea desarrollar un sistema que permita compartir un vehículo para un viaje. La idea es que cuando una persona tiene que realizar un viaje lo publique en la aplicación. Luego, el resto de los usuarios se postulan para acompañarla y el
chofer podrá seleccionar quienes viajan. El objetivo es abaratar costos y evitar congestiones en el tránsito. El sistema es gratuito.
Para utilizar el sistema, una persona debe registrarse y estar correctamente identificado antes de poder utilizarlo. Al registrarse, se pide un nombre de usuario, un correo electrónico y una contraseña. No puede haber dos correos electrónicos iguales en el sistema. Una vez autenticado, podrá dar de alta diferentes viajes, identificando la fecha, hora y el automóvil que utilizará. Los diferentes viajes que una persona publique no pueden superponerse. Un usuario que adeuda calificaciones tampoco podrá publicar un viaje.
Cualquier usuario identificado podrá postularse a un viaje. Luego, el usuario dueño del viaje podrá aceptar o rechazar los candidatos para que realicen el viaje con él.
En el sistema existe una política de reputaciones que permiten a los usuarios conocer la opinión del resto sobre los viajes realizados. Luego de terminado un viaje, tanto el piloto como los copilotos que viajaron deberán calificarse entre sí. El piloto califica a todos sus copilotos. Cada copiloto califica al piloto del viaje. Las calificaciones podrán ser positivas (suma un punto de reputación) o negativas (restan un punto de reputación).

### Historias de usuario 1

ID: Registrarse

Titulo: Como persona quiero registrarme en el sistema para poder usar la aplicacion de viajes

Reglas de negocio:

- El correo se utiliza como nombre de usuario

Criterios de aceptacion

Escenario 1: Registro exitoso

Dado que el correo electronico [torrejonfabio@gmail.com](mailto:torrejonfabio@gmail.com) no se encuentra en el sistema
Cuando ingresa nombre de usuario fabiooo66, correo electronico [torrejonfabio@gmail.com](mailto:torrejonfabio@gmail.com) y contraseña DemaciaGaren777
Entonces el sistema registra el registro de un nuevo usuario al sistema

Escenario 2: Registro fallido por correo repetido

Dado la persona Fabio posee una cuenta en el sistema
Cuando ingresa nombre de usuario fabiooo66, correo electronico [torrejonfabio@gmail.com](mailto:torrejonfabio@gmail.com) y contraseña DemaciaGaren777
Entonces el sistema notifica que el correo electronico ingresado ya pertenece a un cuenta registrada

### Historias de usuario 2

ID: Iniciar sesion

Titulo: Como usuario registrado quiero iniciar sesion en el sistema para usar la aplicacion

Reglas de negocio 

Criterios de aceptacion:

Escenario 1: Inicio de sesion exitoso

Dado un usuario con email “fabiotorrejon@gmail.com” y contraseña “ColePalmer10” que es correcta.

Cuando ingresa con su email “fabiotorrejon@gmail.com” y contraseña “ColePalmer10” al presionar enter.

Entonces el sistema lo redirige a la pagina principal del sistema.

Escenario 2: Error por contraseña incorrecta

Dado un cliente con email “capellivalentin@gmail.com” y contraseña “Messi10” que es incorrecta.

Cuando ingresa con su email “capellivalentin@gmail.com” y contraseña “Messi10” al presionar enter.

Entonces el sistema informa un mensaje de error, correo o contraseña incorrectos

Escenario 3: Error por usuario inexistente

Dado un cliente con email “capellivalentin@gmail.com” inexistente y contraseña “Messi10” que es correcta.

Cuando ingresa con su email “capellivalentin@gmail.com” y contraseña “Messi10” al presionar enter.

Entonces el sistema informa un mensaje de error, correo o contraseña incorrectos

### Historias de usuario 3

ID: Cerrar sesion 

Titulo: Como usuario quiero cerrar sesion en el sistema para que no queden guardados mis datos en la maquina

Reglas de negocio

Criterios de aceptacion 

Escenario 1: Cierre de sesion exitoso

Dado que un usuario [torrejonfabio@gmail.com](mailto:torrejonfabio@gmail.com) tiene la sesión iniciada.

Cuando el usuario presiona "Cerrar sesión".

Entonces el sistema lo redirige a la página de login.

### Historias de usuario 4

ID: Dar de alta viajes

Titulo: Como usuario quiero dar de alta un viajes para abaratar costos

Reglas de negocio

- Dos viajes no pueden tener la misma fecha
- No puede adeudar calificaciones

Criterios de aceptacion

Escenario 1: Alta exitosa

Dado que el usuario “fabioo66” no tiene ningun viaje registrado para el 8/12/2024 y no adeuda calificaciones
Cuando el usuario “fabiooo66” ingresa fecha del viaje 8/12/2024, hora 6:00 y automovil f-150 raptor
Entonces el sistema registra el alta de un viaje

Escenario 2: Alta fallida por superposicion de fecha

Dado que el usuario “DJVALENHD” tiene un viaje registrado para el 12/12/2024 y no adeuda calificaciones
Cuando el usuario “DJVALENHD” ingresa fecha del viaje 12/12/2024, hora 6:00 y automovil Gol Trend
Entonces el sistema notifica que el usuario ya posee un viaje para esa misma fecha

Escenario 3: Alta fallida por adeudar calificaciones

Dado que el usuario “BETO BULLICIO” no tiene ningun viaje registrado para el 8/12/2024 y adeuda calificaciones
Cuando el usuario “BETO BULLICIO” ingresa fecha del viaje 04/12/2024, hora 6:00 y automovil honda civic
Entonces el sistema notifica que el usuario adeuda calificaciones

### Historias de usuario 5

ID: Postularse a un viaje

Titulo: Como usuario quiero postularme a un viaje para abaratar costos

Reglas de negocio:

Criterios de aceptacion

Escenario 1: Postulamiento exitoso

Dado que existe un viaje valido
Cuando el usuario selecciona postularse
Entonces el sistema registra al postulante y se le notifica al dueño del viaje

Escenario 2: No existe el viaje

Dado que un viajes es invalido
Cuando el usuario selecciona postularse
Entonces el sistema notifica que no hay asientos disponibles

### Historias de usuario 6

ID: Aceptar candidato

Titulo: Como Dueño del viaje quiero aceptar un candidato para que viaje conmigo

Reglas de negocio:

Criterios de aceptacion

Escenario 1: Aceptacion exitosa

Dado que el dueño del viaje Raul posee candidatos 
Cuando Raul selecciona uno de ellos y presiona aceptar
Entonces se registra la aceptacion de un nuevo postulante No tiene candidatos

Escenario 2: Aceptacion fallida por no tener candidatos

Dado que el dueño del viaje Hugo no posee candidatos
Cuando Hugo selecciona aceptar candidatos
Entonces el sistema notifica que aun no tiene candidatos disponibles

### Historias de usuario 7

ID: Calificar usuario

Titulo: Como usuario quiero calificar a otro para dar mi opinion de el

Reglas de negocio

Criterios de aceptacion

Escenario 1: Calificacion positiva

Dado el viaje 123 en el que participaron pepito, carlitos, juan
Cuando el usuario pepito califica positivamente a carlitos
Entonces el sistema registra la calificacion y le suma un punto a “carlitos”

Escenario 2: Calificacion negativa

Dado que el usuario “cape77” realizo un viaje
Cuando el usuario “cape77” califica negativamente a “fabio66”
Entonces el sistema registra la calificacion y le resta un punto a “fabioo66”

## Problema 11: Concursos

Suponga que el área para la cual trabaja fue contactada para implementar un sistema para el manejo de concursos de los
docentes de la Facultad de Informá�ca.
El docente que quiera inscribirse a un concurso deberá registrarse previamente en el sistema. Para esto deberá ingresar
los siguientes datos: Dni, nombre, apellido y dirección de mail. Una vez completado los datos el sistema mandará a la
casilla de correo ingresada la contraseña asignada automá�camente. El mail debe ser único y será u�lizado como
nombre de usuario. Según el estatuto de la UNLP los dni permi�dos para concursar son aquellos menores a 55 millones y
mayores a 12 millones.
Una vez registrado el docente puede inscribirse al concurso, para lo cual, una vez que haya ingresado al sistema, deberá
seleccionar la materia a la cual desea inscribirse. Según el reglamento interno de la Facultad de informá�ca que nos
facilitó el jefe del área de personal, el docente no podrá inscribirse a más de 3 concursos. Cuando el docente acepta la
inscripción el sistema deberá imprimir un comprobante.
Por úl�mo, para cumplir con la ordenanza número 123/19 de la UNLP, el jefe del área de concursos, el cual ya cuenta con
un nombre de usuario y contraseña, deberá poder imprimir un listado con los inscriptos a una materia determinada para
poder enviar dicho listado al secretario administra�vo quien lo firma y eleva al decano de la Facultad. Suponga que el
sistema Siu-Guarani realiza una tarea similar a la solicitada y que puede consultar su implementación y registros.

### Historia de usuario 1

ID: Registrar docente

Titulo: Como docente quiero registrarme en el sistema para inscribirme en un concurso

Reglas de negocio:

- El mail debe ser unico
- DNI entre 12 millones a 55 millones

Criterios de aceptacion

Escenario 1: Registro exitoso

Dado el docente Raul con Dni 50.777.777, direccion de mail raulperez@gmail.com que aun no se ha registrado
Cuando ingresa DNI 50.777.777, nombre Raul, apellido Perez y direccion de mail raulperez@gmail.com
Entonces el sistema registra un nuevo registro en el sistema y por mail le envia una contraseña generada automaticamente

Escenario 2: Registro fallido por Dni que no cumple el rango

Dado el docente Alberto con Dni 66.666.666, direccion de mail alberto@gmail.com que aun no se ha registrado
Cuando ingresa DNI 66.666.666, nombre Alberto, apellido Fernandez y direccion de mail alberto@gmail.com
Entonces el sistema notifica que el Dni no cumple con el rango permitido

Escenario 3: Registro fallido por mail existente

Dado el docente Pedro con Dni 45.455.455,  direccion de mail pedro77@[gmail.com](mailto:raulperez@gmail.com) que ya se registro
Cuando ingresa DNI 45.455.455, nombre Pedro, apellido Pepe y direccion de mail pedro77@gmail.com
Entonces el sistema notifica que el mail ya existe en el sistema

### Historias de usuario 2

ID: Iniciar sesion

Titulo: Como docente quiero iniciar sesion en el sistema para inscribirme a un concurso

Reglas de negocio:

Criterios de aceptacion

Escenario 1: Inicio de sesion exitoso

Dado un docente con email “fabiotorrejon@gmail.com” y contraseña “ColePalmer10” que ya esta registrado.

Cuando ingresa con su email “fabiotorrejon@gmail.com” y contraseña “ColePalmer10” al presionar enter.

Entonces el sistema lo redirige a la pagina principal del sistema.

Escenario 2: Error en el inicio de sesion por datos incorrectos

Dado un docente con email “capellivalentin@gmail.com”  y contraseña “Messi10” que no esta registrado en el sistema 

Cuando ingresa con su email “capellivalentin@gmail.com” y contraseña “Messi10” al presionar enter.

Entonces el sistema informa un mensaje de error, correo o contraseña incorrectos

### Historias de usuario 3

ID: Cerrar sesion

Titulo: Como docente quiero cerrar sesion en el sistema para que no persistan mis datos en la maquina

Reglas de negocio:

Criterios de aceptacion

Escenario 1: Cierre exitoso

Dado un correo “cape@gmail.com” que tiene una sesion iniciada
Cuando el usuario presiona cerrar sesion y confirmar
Entonces el sistema lo redirige a la pagina de login y signin. 

Escenario 1: Cierre fallido

Dado un correo “cape@gmail.com” que tiene una sesion iniciada
Cuando el usuario presiona cerrar sesion y no confirmar
Entonces el sistema cancela el cierre de sesion

### Historias de usuario 4

ID: Inscribir a concurso

Titulo: Como docente quiero inscribirme a un concurso para aprender

Reglas de negocio:

- No podra inscribirse a mas de 3 concursos

Criterios de aceptacion

Escenario 1: Inscripcion exitosa

Dado un docente que se inscribio a 1 (un) concurso previamente
Cuando seleccione la materia a la que desea inscribirse y acepta la inscripcion
Entonces el sistema registra la inscripcion e imprime un comprobante

Escenario 2: Inscripcion fallida por mas de 3 concursos inscriptos

Dado un docente que se inscribio a 3 (tres) concursos previamente
Cuando seleccione la materia a la que desea inscribirse y acepta la inscripcion
Entonces el sistema notifica que ya se inscribio al maximo de concursos permitidos

### Historias de usuario 5

ID: Imprimir listado

Titulo: Como jefe del area de concursos quiero imprimir un listado con los inscriptos para
poder enviar dicho listado al secretario administrativo

Reglas de negocio:

Criterios de aceptacion

Escenario 1: Impresion de listado exitoso

Dado un jefe de area de concursos y la materia “MATE 2” con 777 inscriptos
Cuando selecciona la materia “MATE 2” y presiona imprimir listado
Entonces el sistema imprime un listado con los inscriptos a una materia determinada

Escenario 2: Impresion nula

Dado un jefe de area de concursos y la materia “AYED” con 0 inscriptos
Cuando selecciona la materia “AYED” y presiona imprimir listado
Entonces el sistema notifica que no hay inscriptos a dicha materia

## Problema 12: Créditos bancarios

Se desea modelar mediante historias de usuario el manejo de créditos otorgados por un banco a sus clientes.

Los clientes que desean pedir un crédito deben iniciar un trámite a través de un sitio web del banco, ingresando DNI, nombre, apellido, email, tipo de crédito (personal, vivienda, etc.) y monto solicitado. El sistema acepta el inicio de trámite si el DNI ingresado corresponde a un cliente del banco y si el crédito solicitado no supera los $400.000. En caso de que no sea cliente del banco, el sistema deberá enviar un correo electrónico al email ingresado con un instructivo para hacerse cliente del banco. Si el monto supera los $400.000, el sistema rechaza el inicio de trámite y muestra el mensaje: “El monto solicitado excede el límite permitido”. Si los datos son correctos, el sistema almacena el trámite para que sea analizado por el área económica e imprime un número de comprobante para el cliente.

Por otro lado, los clientes pueden consultar el estado de un trámite. Para esto, es necesario que ingresen un número de comprobante. Si el número de comprobante es válido, el sistema retorna un informe con el estado del mismo. De lo contrario, se mostrará un mensaje: “Trámite inexistente”. Si el cliente ingresa tres veces un código inexistente, el sistema bloquea la IP (dirección de red de la máquina que efectúa la consulta) del cliente por 24 horas, mostrando un mensaje: “Usted ha excedido el número de consultas inválidas”.

Por último, el gerente del banco puede pedir un listado de créditos aprobados entre fechas. Si las fechas ingresadas son válidas, el sistema mostrará un listado con los créditos aprobados. De lo contrario, se mostrará un mensaje: “Las fechas ingresadas no son válidas”. El sistema utiliza un sistema de autenticación general del banco, por lo que no es necesario modelar el iniciar y cerrar sesión. Si no hay créditos aprobados para las fechas ingresadas, el sistema mostrará el mensaje: “No hay créditos aprobados en las fechas ingresadas”.

### Historias de usuario 1

ID: Pedir credito

Titulo: Como cliente del banco quiero pedir un credito para realizar una inversion

Reglas de negocio:

- Ser cliente del banco
- El monto no puede superar los $400000

Criterios de aceptacion

Escenario 1: Solicitud exitosa

Dado el tipo de credito “Personal” que tiene un monto de $350000 y la persona es cliente del banco
Cuando la persona ingresa DNI 45.579.759, nombre Fabio, apellido Torrejon, email torrejonfabio@gmail.com, tipo de credito personal, monto $350000 y selecciona solicitar credito
Entonces el sistema almacena el trámite para que sea analizado por el área económica e imprime un número de comprobante para el cliente

Escenario 2: Solicitud fallida por monto mayor a $400000

Dado el tipo de credito “Personal” que tiene un monto de $450000 y la persona es cliente del banco
Cuando la persona ingresa DNI 77.777.777, nombre Sergio, apellido Torrejon, email torrejonsergio@gmail.com, tipo de credito personal, monto $450000 y selecciona solicitar credito
Entonces el sistema rechaza el trámite y notifica que el monto solicitado excede el límite permitido

Escenario 3: Solicitud fallida por cuenta inexistente

Dado el tipo de credito “Personal” que tiene un monto de $350000 y la persona no es cliente del banco
Cuando la persona ingresa DNI 45.579.759, nombre Valentin, apellido Capelli, email valentincapelli@gmail.com, tipo de credito personal, monto $350000 y selecciona solicitar credito
el sistema envia un correo electrónico al email ingresado con un instructivo para hacerse cliente del banco

### Historias de usuario 2

ID: Consultar estado del tramite

Titulo: Como cliente quiero consultar el estado del tramite para ver como va

Reglas de negocio:

- numero de comprobante valido

Criterios de aceptacion

Escenario 1: Consulta exitosa

Dado el numero de comprobante “777” que es valido
Cuando el cliente ingresa el numero de comprobante “777” y selecciona “consultar estado de un tramite”
Entonces el sistema retorna un informe con el estado del mismo

Escenario 2: Consulta fallida por comprobante inexistente

Dado el numero de comprobante “333” que es invalido
Cuando el cliente ingresa el numero de comprobante “333” y selecciona “consultar estado de un tramite”
Entonces el sistema notifica tramite inexistente

Escenario 3: Consulta fallida y bloqueo de ip

Dado el numero de comprobante “222” que es invalido y ya ingreso dos veces un codigo inexistente
Cuando el cliente ingresa el numero de comprobante “222” y selecciona “consultar estado de un tramite”
Entonces el sistema bloquea la ip del cliente por 24 horas y notifica que excedio el numero de consultas validas

### Historias de usuario 3

ID: Pedir listado de creditos aprobados entre fechas

Titulo: Como gerente del banco quiero pedir un listado de creditos aprobados entre fechas para analizar los montos a pagar

Reglas de negocio:

- fechas ingresadas deben ser validas

Criterios de aceptacion

Escenario 1: Listado exitoso

Dadas las fechas validas 15/09/2024-15/10/2024 y creditos aprobados existentes
Cuando el gerente ingresa las fechas 15/09/2024-15/10/2024 y selecciona pedir listado
Entonces el sistema muestra un listado de creditos aprobados

Escenario 2: Listado fallido por fechas no validas

Dadas las fechas no validas 77/77/7777-66/66/666 y creditos aprobados existentes
Cuando el gerente ingresa las fechas 77/77/7777-66/66/666 y selecciona pedir listado
Entonces el sistema notifica que las fechas ingresadas no son validas

Escenario 3: Listado fallido por creditos inexistentes

Dadas las fechas validas 15/04/2024-15/05/2024 y creditos aprobados inexistentes
Cuando el gerente ingresa las fechas 15/04/2024-15/05/2024 y selecciona pedir listado
Entonces el sistema notifica que no hay creditos aprobados en las fechas ingresadas

## Problema 12: Venta de libros

Una nueva empresa de venta de libros en línea está diseñando su sitio web. Cualquier visitante puede acceder a su catálogo de libros y navegar por los distintos títulos que se encuentren disponibles. Sin embargo, solo los usuarios registrados pueden realizar compras.

Para comprar libros, es necesario estar registrado. El proceso de registro se realiza en dos pasos. En el primer paso, el sistema solicita Nombre, Apellido, DNI, correo electrónico (que no exista previamente en el sistema) y una clave de 6 caracteres para dar de alta al usuario de forma parcial. Durante este proceso, el sistema genera un código de 16 dígitos y lo envía por correo electrónico para que el visitante confirme su cuenta.

En el segundo paso, el visitante debe ingresar a la página de confirmación e introducir su dirección de correo y el código de 16 dígitos. Si estos datos son correctos, el sistema completa el registro y lo define como usuario definitivo.

Una vez registrado, para autenticarse, el sistema requiere el correo del usuario y la clave de 6 caracteres.

Para realizar la compra de un libro, el sistema solicita ingresar el ISBN del mismo, muestra al usuario la portada con una descripción del libro y la opción “Comprar”. Cuando el usuario selecciona “Comprar”, se le solicitan los datos de la tarjeta: Nombre, Apellido y Número de tarjeta. Es importante tener en cuenta que, por disposición del Banco Central, solo el titular de la tarjeta puede realizar la compra, por lo que el nombre y apellido registrados deben coincidir con los de la tarjeta.

Una vez realizada esta verificación, los datos se envían al servidor de la tarjeta para efectuar el cobro. Si todo es correcto, se genera un enlace de descarga que se envía al correo del usuario.

### Historias de usuario 1

ID: Registrar usuario

Titulo: Como visitante quiero registrarme para poder comprar libros

Reglas de negocio:

- El correo se utiliza como nombre de usuario

Criterios de aceptacion

Escenario 1: Registro exitoso

Dado que el correo electronico [torrejonfabio@gmail.com](mailto:torrejonfabio@gmail.com) no se encuentra en el sistema y la clave 123456 tiene 6 caracteres
Cuando el visitante ingresa nombre Fabio, apellido Torrejon, DNI 45.579.759, correo [torrejonfabio@gmail.com](mailto:torrejonfabio@gmail.com), clave 123456 y selecciona registrarse
Entonces el sistema lo registra de forma parcial y le envia un codigo de 16 digitos para confimar la cuenta

Escenario 2: Registro fallido por correo repetido

Dado que el correo electronico [torrejonfabio@gmail.com](mailto:torrejonfabio@gmail.com) se encuentra en el sistema y la clave 123456 tiene 6 caracteres
Cuando el visitante ingresa nombre Fabio, apellido Torrejon, DNI 45.579.759, correo [torrejonfabio@gmail.com](mailto:torrejonfabio@gmail.com), clave 123456 y selecciona registrarse
Entonces el sistema notifica que ya existe una cuenta con el mismo nombre de usuario

Escenario 3: Registro fallido por clave no valida

Dado que el correo electronico [valentincapelli@gmail.com](mailto:valentincapelli@gmail.com) no se encuentra en el sistema y la clave garendemacia123 no tiene 6 caracteres
Cuando el visitante ingresa nombre Valentin, apellido Capelli, DNI 45.575.759, correo valentincapelli@gmail.com clave garendemacia123 y selecciona registrarse
Entonces el sistema notifica que la clave debe contener exactamente 6 caracteres

### Historias de usuario 2

ID: Confirmar cuenta 

Titulo: Como visitante quiero confimar mi registro en el sistema para poder comprar libros

Reglas de negocio

Criterios de aceptacion

Escenario 1: Confirmacion exitosa

Dado un codigo 123…16 valido y nombre de usuario [torrejonfabio@gmail.com](mailto:torrejonfabio@gmail.com) existente
Cuando el visitante ingresa correo electronico torrejonfabio@gmail.com y codigo 123...16
Entonces el sistema registra definitivamente al usuario

Escenario 2: Confirmacion fallida por codigo invalido

Dado un codigo 777…123 valido y nombre de usuario [torrejonfabio@gmail.com](mailto:torrejonfabio@gmail.com) existente
Cuando el visitante ingresa correo electronico torrejonfabio@gmail.com y codigo 777...123
Entonces el sistema notifica que el codigo ingresado no es valido

Escenario 3: Confirmacion fallida por cuenta inexistente

Dado un codigo 123…16 valido y nombre de usuario [valentincapelli@gmail.com](mailto:valentincapelli@gmail.com) inexistente
Cuando el visitante ingresa correo electronico valentincapelli@gmail.com y codigo 123..16
Entonces el sistema notifica que la cuenta no existe

### Historias de usuario 3

ID: Iniciar sesion

Titulo: Como usuario registrado quiero iniciar sesion en el sistema para usar la aplicacion

Reglas de negocio 

Criterios de aceptacion:

Escenario 1: Inicio de sesion exitoso

Dado un usuario con email “fabiotorrejon@gmail.com” y contraseña “Palmer” que es correcta.

Cuando ingresa con su email “fabiotorrejon@gmail.com” y contraseña “Palmer” al presionar enter.

Entonces el sistema lo redirige a la pagina principal del sistema.

Escenario 2: Error por contraseña incorrecta

Dado un cliente con email “capellivalentin@gmail.com” y contraseña “Messi1” que es incorrecta.

Cuando ingresa con su email “capellivalentin@gmail.com” y contraseña “Messi1” al presionar enter.

Entonces el sistema informa un mensaje de error, correo o contraseña incorrectos

Escenario 3: Error por usuario inexistente

Dado un cliente con email “capellivalentin@gmail.com” inexistente y contraseña “Messi1” que es correcta.

Cuando ingresa con su email “capellivalentin@gmail.com” y contraseña “Messi1” al presionar enter.

Entonces el sistema informa un mensaje de error, correo o contraseña incorrectos

### Historias de usuario 4

ID: Cerrar sesion 

Titulo: Como usuario quiero cerrar sesion en el sistema para que no queden guardados mis datos en la maquina

Reglas de negocio

Criterios de aceptacion 

Escenario 1: Cierre de sesion exitoso

Dado que un usuario [torrejonfabio@gmail.com](mailto:torrejonfabio@gmail.com) tiene la sesión iniciada.
Cuando el usuario presiona "Cerrar sesión".
Entonces el sistema lo redirige a la página de login.

### Historias de usuario 5

ID: Comprar libros

Titulo: Como usuario registrado quiero comprar libros para tener el habito de leer

Reglas de negocio:

Criterios de aceptacion

Escenario 1: Compra exitosa

Dado el ISBN 777 que corresponde a un libro valido y las condiciones son las adecuadas para un pago exitoso
Cuando el usuario ingresa el ISBN 777 y selecciona comprar
Entonces el sistema redirige al usuario al pago con tarjeta, espera respuesta, y efectua la compra

Escenario 2: Compra fallida por ISBN inexistente

Dado el ISBN 666 que no corresponde a un libro valido y las condiciones son las adecuadas para un pago exitoso
Cuando el usuario ingresa el ISBN 666 y selecciona comprar
Entonces el sistema notifica que no existe un libro con ese ISBN

Escenario 3: Compra fallida por error en el pago

Dado el ISBN 777 que corresponde a un libro valido y las condiciones no son las adecuadas para un pago exitoso
Cuando el usuario ingresa el ISBN 777 y selecciona comprar
Entonces el sistema redirige al usuario al pago con tarjeta, espera respuesta, y notifica que el pago no ha sido correcto

### Historias de usuario 6

ID: Pagar

Titulo: Como usuario quiero pagar mi compra para tener el libro que quiero

Reglas de negocio

Criterios de aceptacion

Escenario 1: Pago exitoso 

Dado que la conexion con el servidor del banco es exitosa, el numero 1234 corresponde a una tarjeta, la tarjeta tiene saldo y el nombre y apellido “Fabio Torrejon” es valido
Cuando el usuario ingresa el numero de tarjeta 1234, nombre Fabio y apellido Torrejon
Entonces el sistema registra el pago y retorna un resultado de exito

Escenario 2: Pago fallido por numero de tarjeta de credito inexistente

Dado que la conexion con el servidor del banco es exitosa, el numero 3333 no corresponde a una tarjeta y el nombre y apellido “Fabio Torrejon” es valido
Cuando el usuario ingresa el numero de tarjeta 3333, nombre Fabio y apellido Torrejon
Entonces el sistema retorna un error por numero de tarjeta inexistente

Escenario 3: Pago fallido por saldo insuficiente

Dado que la conexion con el servidor del banco es exitosa, el numero 1111 corresponde a una tarjeta, la tarjeta no tiene saldo y el nombre y apellido “Fabio Torrejon” es valido
Cuando el usuario ingresa el numero de tarjeta 1111, nombre Fabio y apellido Torrejon
Entonces el sistema retorna un error por saldo insuficiente

Escenario 4: Pago fallido por fallo en la conexion con el servidor externo del banco

Dado que no se pudo realizar la conexion con el servidor de banco
Cuando el usuario selecciona pagar
Entonces el sistema retorna un error por conexion fallida

Escenario 5: Pago fallido por tarjeta de otro titular

Dado que la conexion con el servidor del banco es exitosa, el numero 1234 corresponde a una tarjeta, la tarjeta tiene saldo y el nombre y apellido “Fabio Torrejon” es invalido
Cuando el usuario ingresa el numero de tarjeta 1234, nombre Fabio y apellido Torrejon
Entonces el sistema retorna que el usuario no es el titular de la tarjeta
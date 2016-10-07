![](images/header.png)

# **SISTEMA DE TURNOS**
<br>
<br>

# Manual de usuario

<br>
Este manual describe la utilización del sistema de turnos en su versión MVP.  El término MVP se refiere a la posibilidad de entregar un producto con los mínimos requerimientos pero funcional, de manera de ir testeando en vivo si lo primero que se desarrolló es lo que se buscaba y sobre una base testeada de trabajo, ir agregando funcionalidades que enriquezcan el producto.

<br>
## Tabla de contenidos
  * [1. Descripción de entidades del sistema](#entidades)
  * [2. Carga inicial de datos](#cargaInicial)
  * [3. Turnos](#turnos)
    * [3.1 Dar un nuevo turno](#nuevoTurno)
    * [3.2 Dar un sobreturno](#sobreTurno)
    * [3.3 Ver turnos de un profesional](#turnosDeProfesional)
    * [3.4 Ver turnos de un paciente](#turnosDePaciente)
    * [3.5 Cancelar un turno](#cancelarTurno)
    * [3.6 Informar turnos cancelados a pacientes](#informarCancelados)
    * [3.7 Marcar presente un turno](#marcarPresente)
  * [4. Pacientes](#pacientes)
    * [4.1 Listado de pacientes](#listadoPacientes)
    * [4.2 Alta de paciente](#altaPaciente)
    * [4.3 Modificar o eliminar paciente](#modificarEliminarPaciente)
  * [5. Agendas](#agendas)
    * [5.1 Alta de agenda](#altaAgenda)
    * [5.2 Modificación o eliminar agenda](#modificarEliminarAgenda)
    * [5.3 Calendario](#calendario)
    * [5.4 Imprimir agenda de un profesional](#imprimirAgenda)
  * [6. Profesionales](#profesionales)
    * [6.1 Listado de profesionales](#listadoProfesionales)
    * [6.2 Alta de profesional](#altaProfesionales)
    * [6.3 Modificar o eliminar profesional](#modificarEliminarProfesional)
    * [6.4 Ver turnos de un profesional](#turnosDeProfesional)
    * [6.5 Ausencias](#ausencias)
      * [6.5.1 Ver ausencias de un profesional](#listadoAusencias)
      * [6.5.2 Cargar nueva ausencia de un profesional](#nuevaAusencia)
  * [7. Especialidades](#especialidades)
    * [7,1 Listado de especialidades](#especialidades)
    * [7.2 Alta de especialidades](#altaEspecialidades)
    * [7.3 Modificar o eliminar una especialidad](#modificarEliminarEspecialidad)
  * [8. Prestaciones](#prestaciones)
    * [8.1 Listado de prestaciones](#prestaciones)
    * [8.2 Alta de prestaciones](#altaPrestaciones)
    * [8.3 Modificar o eliminar una prestación](#modificarEliminarEspecialidad)
<br>

<br>
<a id="entidades"/>
## 1. Descripción de entidades del sistema
<br>
●	Profesional: son los médicos, enfermeras o cualquier persona que brinde un servicio para el cual se necesite asignar un turno

●	Especialidad: generalmente es la especialidad del médico, por ejemplo: Infectología, Dermatología, Clínica Médica, etc.

●	Prestación: es el servicio en sí que se asocia a un único turno. Una especialidad debe tener una o más prestaciones relacionadas; además una prestación tiene una duración, que representa la duración del turno.

Cada prestación puede tener una duración distinta, siguiendo el ejemplo mencionado, se podría asignar una duración de 40min a la prestación “Consulta primera vez”, y una duración de 20min a la prestación “Seguimiento”.


●	Turno: se debe ingresar por lo menos el nombre, apellido y teléfono de un paciente. A su vez, se debe seleccionar la especialidad/prestación, profesional, fecha y hora del turno elegido.

●	Agenda: representan los días y horarios que tiene disponible un profesional para cada especialidad/prestación que atiende

●	Ausencia: un profesional puede estar ausente por Congreso, Vacaciones, Otros. El sistema permite registrar dicha ausencia para evitar dar turnos que no se podrán atender y/o listar los turnos cancelados por ese registro de ausencia. Tener en cuenta que si se está dando un sobreturno, no se toma en cuenta si el profesional estará ausente.

●	Sobreturno: son turnos que se dan sin tener en cuenta si el profesional tiene una agenda abierta, si ya tiene un turno tomado o si estará ausente. Estos turnos funcionan por fuera de la agenda del profesional.


<br>
<a id="cargaInicial"/>
## 2. Carga inicial de datos
<br>
Para que se puedan dar turnos, se deben cargar previamente determinados datos en el siguiente orden:

 1. [Dar de alta las nuevas especialidades](#altaEspecialidades)

 2. [Dar de alta las nuevas prestaciones de cada especialidad](#altaPrestaciones)

 3. [Dar de alta los nuevos profesionales](#altaProfesionales)

 4. [Abrir agendas de cada profesional, especialidad/prestación](#abrirAgenda)

<br>

<a id="turnos" />
## 3. Turnos


<a id="nuevoTurno" />
### 3.1 Dar un nuevo turno

Hay tres pasos que deben seguirse para poder dar un turno:

<a id="datosPacienteTurnos" />
#### Paso 1: Ingresar los datos del paciente



**a.	Paciente nuevo**

Si se quiere dar un turno a un paciente que no existe en el sistema se debe ingresar obligatoriamente el nombre, apellido y número de teléfono.
Además de estos datos también se pueden agregar el tipo de documento, número de documento, email y fecha de nacimiento

![](images/turnoPacienteNuevo.png)

Luego se procede con el paso 2. [Búsqueda de turnos disponibles](#buscarTurno)

**b.	Paciente ya existente**

Para buscar un paciente ya existente hay dos opciones:

i.	_Nombre y apellido_: se deben ingresar al menos las 3 primeras letras del nombre y del apellido

ii.	_Tipo y número de documento_: seleccionar el tipo de documento e ingresar el número de documento

Una vez seleccionado el paciente del listado, se procede con el paso 2. [Búsqueda de turnos disponibles](#buscarTurno)

<a id="buscarTurno" />
#### Paso 2: Búsqueda de turnos disponibles

Se pueden buscar turnos disponibles de dos formas:

**a.	Por especialidad/prestación**

Se pueden buscar turnos para una especialidad/prestación sin indicar el profesional. Por ej, si se buscan turnos para Infectología/Seguimiento se mostrarán los turnos de _todos los profesionales_ que atienden esta especialidad/prestación

**b.	Por profesional**

Si el paciente solicita un turno con un médico se puede seleccionar el profesional junto con la especialidad/prestación para que sólo se busquen turnos de ese profesional.

Si además es necesario, buscar un turno a partir de una fecha dada, se puede utilizar el campo “A partir del día”

![](images/buscarTurno.png)
<br>
<br>
#### Paso 3: Seleccionar turno disponible
<br>

Se debe seleccionar el turno disponible ya sea en el Calendario o el Listado.

<br>
![](images/seleccionarTurno.png)


<br>
Luego, al clickear el botón Confirmar se mostrará la información del nuevo turno dado.
<br><br>


![](images/turnoConfirmado.png)

<br>
<br>
<br>
<a id="sobreTurno" />
### 3.2 Dar un sobreturno

<br>
Es importante tener en cuenta que un sobreturno puede ser dado aún si el profesional está ausente o si no posee agendas abiertas.

El sobreturno puede ser para cualquier día y horario futuro, y se manejará por fuera de las agendas de los profesionales.

Para poder dar un sobre turno se debe ir a la opción Turnos del menú principal y luego elegir la pestaña Sobreturnos.

<br>  
![](images/sobreturno.png)

Allí primero se deben ingresar los datos del paciente tal como se realiza al dar un nuevo turno: [ingresar los datos del paciente](#datosPacienteTurnos)

Luego se deberá ingresar el profesional, prestación, fecha y horario del sobreturno.

Al hacer click en Confirmar, se mostrará la información del sobreturno dado.

<br>  
![](images/sobreturnoConfirmacion.png)


<br>
<a id="turnosDeProfesional" />
### 3.3 Ver turnos de un profesional

<br>
Para ver los turnos de un profesional se debe ir a la opción de menú Admin -> Profesionales donde se deberá seleccionar el profesional del cual se quiere ver los turnos.

![](images/verTurnosProfesional1.png)
<br>

Al clickear el botón de Turnos se verá lo siguiente:
<br>

![](images/verTurnosProfesional2.png)
<br>
<br>
<a id="turnosDePaciente" />
### 3.4 Ver turnos de un paciente

<br>
Los turnos de un paciente se pueden ver al visualizar el Detalle de un paciente. En el detalle se ven los datos personales del paciente,  y además los turnos del mismo.

Para ver los turnos de un paciente, se debe ir a la opción Admin -> Pacientes, y de allí seleccionar el paciente:
<br>
<br>
![](images/verTurnosPaciente1.png)
<br>
<br>
Al clickear el botón de Turnos se verá el detalle del paciente y los turnos del mismo:

<br>

![](images/verTurnosPaciente2.png)
<br>
<a id="cancelarTurno" />
### 3.5 Cancelar un turno

<br>
Haciendo click en el botón ![](images/botonCancelar.png), se puede cancelar un turno desde:
* [3.3 Ver turnos de un profesional](#turnosDeProfesional)
* [3.4 Ver turnos de un paciente](#turnosDePaciente)

<br>
![](images/cancelarTurno1.png)

<br>
<br>
También se puede cancelar desde la vista **Agendas -> Calendario**

![](images/cancelarCalendario1.png)

Al hacer click sobre el turno tomado, se puede ver el detalle del turno, y el botón para cancelar el mismo

![](images/cancelarCalendario.png)


<br>
<a id="informarCancelados" />
### 3.6 Informar turnos cancelados a pacientes
<br>
Hay turnos que son cancelados **_por el sistema_**, esto ocurre únicamente:

a. Por ingreso de **nueva ausencia**

Cuando el usuario ingresa una nueva ausencia del profesional, se cancelan los turnos tomados de este profesional para los días de la ausencia. Por ejemplo, si ya hay turnos tomados para el 1/10 para un profesional, y se le carga una ausencia para el 1/10, éstos serán cancelados automáticamente y se deberá **informar al paciente** lo ocurrido.


b. Por **modificación en la agenda** de un profesional

Cuando se modifica los días u horarios de atención de un profesional, los turnos tomados serán cancelados por el sistema. Por ejemplo, si hay un turno tomado para el miércoles 1/10 a las 10am; y se modifica la agenda de forma tal que el profesional deja de atender los miércoles 10am, este turno tomado pasa a cancelado automáticamente y se deberá **informar al paciente** de lo ocurrido.

<br>
_En ambos casos, los turnos que son cancelados por el sistema se pasan a un estado de "Turnos a Informar" que se pueden ver en la opción de menú Admin -> Turnos a informar_

Allí se puede ver los datos de contacto (teléfono) de los pacientes cuyos turnos fueron cancelados automáticamente para que el usuario pueda ponerse en contacto con el mismo e informarle que su turno ha sido cancelado.

<br>
<br>

![](images/turnosAInformar.png)

<br>
<br>
<br>
<br>
Una vez que el paciente es informado de la cancelación de su turno, se debe clickear el botón "Informar" para poder marcar el turno como "Ya informado"

![](images/turnosAInformar2.png)
<br>
<br>
<br>
<br>
Luego, si se cambia el filtro para ver únicamente los turnos ya informados, se podrá ver el turno que recientemente se marcó como "Ya informado"

<br>
![](images/turnosAInformar4.png)

<br>
<br>
<br>
<br>
<br>
<br>
_Nota: En la lista de turnos a informar, no se ven aquellos turnos que son cancelados por usuarios del sistema, por ejemplo, cuando un paciente llama por teléfono para cancelar el turno, el usuario debe ingresar la cancelación "manualmente" como se describe en [Cancelar un turno](#cancelarTurno)_

<br>
<br>
<a id="marcarPresente" />
### 3.7 Marcar presente un turno
<br>
Para marcar como presente un turno se debe ir a Agendas -> Calendario
<br>

![](images/cancelarCalendario1.png)

Se debe hacer click en el turno para ver el detalle del mismo y marcarlo como presente

![](images/marcarPresenteDetalle.png)

<br>
En el calendario, se podrá distinguir el turno marcado como presente ya que está pintado de verde suave

![](images/calendarioTurnoPresente.png)

<a id="pacientes"></a>
## 4. Pacientes

<a id="listadoPacientes" />
### 4.1 Listado de pacientes

<a id="altaPaciente" />
### 4.2 Alta de paciente

<a id="modificarEliminarPaciente" />
### 4.3 Modificar o eliminar paciente

<a id="agendas" />
## 5. Agendas
<br>
Un profesional puede tener una o varias agendas. Cada agenda representa los turnos disponibles que tiene un profesional para una especialidad/prestación especificando los días y horarios de atención.



<a id="altaAgenda" />
### 5.1 Alta de agenda

Para abrir una nueva agenda de un profesional se debe elegir la opción Agendas -> Listado, y hacer click en el botón Nueva Agenda

![](images/listadoAgendas.png)

<br>
<br>
<br>
Al clickear el botón Nueva Agenda, se mostrará la siguiente pantalla dónde se deberá elegir el profesional, especialidad y prestación de la agenda a abrir:

![](images/nuevaAgenda.png)
<br>
<br>
<br>

Se deberá hacer click en el botón Cargar para poder elegir los horarios y días de atención para esta agenda.

Por ejemplo:

![](images/nuevaAgenda2.png)

<br>
<br>
<br>
La grilla horaria, indica que el profesional Brey, Gustavo atenderá Nutrición/Primera vez los días Lunes, de 8 a 13hs.

Luego se deberá hacer click en el botón Confirmar, y se verá la nueva agenda en el listado.

![](images/nuevaAgenda3.png)

<a id="modificarEliminarAgenda" />
### 5.2 Modificar o eliminar agenda

<br>
<br>
<br>
<a id="calendario" />
### 5.3 Calendario

<br>

La vista Calendario se utiliza para poder ver los turnos de un profesional e imprimir su agenda. Primero se deben ingresar los filtros de nombre de profesional, especialidad y prestación y hacer click en el botón Buscar. Se deben ingresar los filtros para poder ver los turnos en el calendario, de lo contrario, no se mostrará ningún turno.


![](images/agendaCalendario.png)

<a id="imprimirAgenda" />
### 5.4 Imprimir agenda de un profesional

<br>
Para imprimir la agenda de un médico se deberá hacer click en el botón derecho y elegir la opción de Imprimir.

![](images/imprimirAgenda.png)

<br>
<br>
<br>
<a id="profesionales" />
## 6. Profesionales

<br>
Se debe ir a Admin -> Profesionales

<a id="listadoProfesionales" />
### 6.1 Listado de profesionales

Allí se mostrará el listado de profesionales, y se podrá:
o	buscar un profesional por nombre
o	filtrar listado por profesional activos/inactivos
o	crear nuevo profesional
o	modificar profesional

Al hacer click en cada profesional del listado se verá mas información, junto con las opciones de Turnos, Asistencias y Detalle

![](images/listadoProfesionales.png)


<a id="altaProfesionales" />
### 6.2 Alta de profesional

<a id="modificarEliminarProfesional" />
### 6.3 Modificar o eliminar profesional

<a id="turnosDeProfesional" />
### 6.4 Ver turnos de un profesional

Se muestran los turnos del día del profesional, como así también los turnos futuros

![](images/turnosDeProfesional.png)

Para cancelar el turno hacer click en el botón X

<a id="ausencias" />
<a id="listadoAusencias" />
### 6.5 Ausencias

#### 6.5.1 Ver ausencias de un profesional

Para ver el listado de ausencias de un profesional se deberá ir a Admin -> Profeisonales, y de allí seleccionar el botón de Ausencias del profesional que mostrará lo siguiente:

![](images/listadoAusencias.png)

<br>
<br>
<br>


<a id="nuevaAusencia" />
#### 6.5.2 Cargar nueva ausencia de un profesional

Clickeando el botón de Nueva Ausencia que se ve en el listado, se cargará el siguiente formulario:

![](images/nuevaAusencia.png)

Se puede dar el caso, que la ausencia ingresada cancele turnos ya tomados. Para ver los turnos cancelados que deben informarse se deberá ir a [Turnos a informar](#informarCancelados)

<br>
<br>
<br>
<a id="especialidades"></a>
## 7. Especialidades
<br>

<a id="especialidades"></a>
### 7.1 Listado de especialidades
Para ver las especialidades se debe ir a Admin -> Especialidades

Se muestra el listado de especialidades donde se puede:
-	buscar una especialidad por nombre
-	filtrar listado por especialidades activas/inactivas
-	crear nueva especialidad
-	modificar una especialidad

![](images/listadoEspecialidades.png)

<a id="altaEspecialidades" />
### 7.2 Alta de especialidades

Al hacer click en el botón Nueva especialidad.
<br>

![](images/nuevaEspecialidad.png)
<br>
<br>
Se debe ingresar obligatoriamente el nombre de la especialidad. A su vez, se puede ingresar una descripción de la nueva especialidad.


![](images/nuevaEspecialidad2.png)
<br>
<br>
<a id="campoDefault" />
El campo Default se utiliza para definir si la especialidad ingresada debe aparecer primera en los combos donde se muestre el listado de especialidades. Por ejemplo, si frecuentemente se utiliza la especialidad Infectología, se marca el checkbox y luego en la pantalla de Nuevo Turno, se verá esta especialidad primera en el combo, tal como se muestra a continuación:
<br>
<br>
![](images/turnosEspecialidadDefault.png)

<br>
<br>
<br>
<a id="modificarEliminarEspecialidad" />
### 7.3 Modificar o eliminar una especialidad
<br>
Primero se debe seleccionar una especialidad del listado y luego hacer click en el botón Modificar
<br>

![](images/modificarEspecialidad.png)
<br>
<br>
<br>
Para modifcar la especialidad, ingresar los cambios en nombre y descripción, luego hacer click en el botón Confirmar
<br>
![](images/modificarEspecialidad2.png)
<br>
<br>
<br>
Para borrar la especialidad, hacer click en el botón Eliminar

<br>


<a id="prestaciones" />
## 8. Prestaciones

### 8.1 Listado de prestaciones

Para ver las prestaciones se debe ir a Admin -> Prestaciones

Se muestra el listado de prestaciones donde se puede:
-	buscar una prestación por nombre
-	filtrar listado por prestaciones activas/inactivas
-	crear nueva prestación
- modificar una prestación

![](images/listadoPrestaciones.png)

<a id="altaPrestaciones" />
### 8.2 Alta de prestaciones

<br>
Se deberá hacer click en el botón Nueva Prestación
<br>
![](images/nuevaPrestacion.png)
<br>
<br>
Al clickear el botón Nueva Prestación se deben ingresar obligatoriamente el nombre, duración y especialidad.
Opcionalmente se puede utilizar el [campo Default](#campoDefault) tal como en Nueva Especialidad.
En el campo Notas se debe ingresar información propia de la prestación, por ejemplo si la prestación es un análisis de sangre, se pueden ingresar las indicaciones para poder realizarlo. Otro ejemplo, puede ser en Consulta de primera vez, se puede indicar que se le informe al paciente que debe venir antes para poder registrarse y abrir una nueva historia clínica.
<br>
<br>

![](images/nuevaPrestacion2.png)
<br>
<br>
<br>
<br>
<br>
En la pantalla nuevo turno, se puede ver el campo Notas, como Observaciones:
<br>
![](images/turnosObservaciones.png)
<br>
<br>

<a id="modificarEliminarEspecialidad" />
### 8.3 Modificar o eliminar una prestación

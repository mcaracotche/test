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
### 3.5 Ver turnos de un paciente
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

También se puede cancelar desde la vista Agendas -> Calendario

![](images/cancelarCalendario1.png)

Al hacer click sobre el turno tomado, se puede ver el detalle del turno, y el botón para cancelar el mismo

![](images/cancelarCalendario.png)


<br>
<a id="informarCancelados" />
### 3.6 Informar turnos cancelados a pacientes

<br>
<br>
<a id="marcarPresente" />
### 3.7 Marcar presente un turno

Para marcar como presente un turno
<a id="especialidades"></a>
## Especialidades
<br>
Para ver las especialidades se debe ir a Admin -> Especialidades

Se muestra el listado de especialidades donde se puede:
-	buscar una especialidad por nombre
-	filtrar listado por especialidades activas/inactivas
-	crear nueva especialidad
-	modificar una especialidad

![](images/listadoEspecialidades.png)

<a id="altaEspecialidades" />
### Alta de especialidad

Al hacer click en el botón Nueva especialidad.
<br>

![](images/nuevaEspecialidad.png)

<br>
Se debe ingresar obligatoriamente el nombre de la especialidad. A su vez, se puede ingresar una descripción de la nueva especialidad.


![](images/nuevaEspecialidad2.png)
<br>
<a id="campoDefault" />
El campo Default se utiliza para definir si la especialidad ingresada debe aparecer primera en los combos donde se muestre el listado de especialidades. Por ejemplo, si frecuentemente se utiliza la especialidad Infectología, se marca el checkbox y luego en la pantalla de Nuevo Turno, se verá esta especialidad primera en el combo, tal como se muestra a continuación:
<br>
![](images/turnosEspecialidadDefault.png)

<a id="modificarEliminarEspecialidad" />
### Modificar o Eliminar una especialidad
<br>
Primero se debe seleccionar una especialidad del listado y luego hacer click en el botón Modificar
<br>
![](images/modificarEspecialidad.png)
<br>

Para modifcar la especialidad, ingresar los cambios en nombre y descripción, luego hacer click en el botón Confirmar
<br>
![](images/modificarEspecialidad2.png)
<br>
Para borrar la especialidad, hacer click en el botón Eliminar

<br>
<a id="prestaciones" />
## Prestaciones

Para ver las prestaciones se debe ir a Admin -> Prestaciones

Se muestra el listado de prestaciones donde se puede:
-	buscar una prestación por nombre
-	filtrar listado por prestaciones activas/inactivas
-	crear nueva prestación
- modificar una prestación

![](images/listadoPrestaciones.png)

<a id="altaPrestaciones" />
### Alta de prestación
<br>
Se deberá hacer click en el botón Nueva Prestación
<br>
![](images/nuevaPrestacion.png)
<br>
Al clickear el botón Nueva Prestación se deben ingresar obligatoriamente el nombre, duración y especialidad.
Opcionalmente se puede utilizar el [campo Default](#campoDefault) tal como en Nueva Especialidad.
En el campo Notas se debe ingresar información propia de la prestación, por ejemplo si la prestación es un análisis de sangre, se pueden ingresar las indicaciones para poder realizarlo. Otro ejemplo, puede ser en Consulta de primera vez, se puede indicar que se le informe al paciente que debe venir antes para poder registrarse y abrir una nueva historia clínica.
<br>
![](images/nuevaPrestacion2.png)
<br>
En la pantalla nuevo turno, se puede ver el campo Notas, como Observaciones:
<br>
![](images/turnosObservaciones.png)
<br>


## Profesionales
<br>
Se debe ir a Admin -> Profesionales

Allí se mostrará el listado de profesionales, y se podrá:
o	buscar un profesional por nombre
o	filtrar listado por profesional activos/inactivos
o	crear nuevo profesional
o	modificar profesional

Al hacer click en cada profesional del listado se verá mas información, junto con las opciones de Turnos, Asistencias y Detalle

![](images/listadoProfesionales.png)

#### a. Turnos de un Profesionales
Se muestran los turnos del día del profesional, como así también los turnos futuros

![](images/turnosDeProfesional.png)

Para cancelar el turno hacer click en el botón X

#### b. Ausencias de profesional

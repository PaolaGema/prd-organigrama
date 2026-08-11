# PRD — Organigrama

**Souly HR / Trabajito · Gestión de Personas**

| | |
|---|---|
| **Versión** | 2.1 |
| **Fecha** | 11 de agosto de 2026 |
| **Estado** | Borrador para revisión |
| **Autoría** | **Paola Gema** — Diseñadora UX |
| **Revisan y aprueban** | **Naihara Rocha** — reglas de negocio, nombres y uso real de RR.HH. · **Israel Chávez** — viabilidad técnica y plazos |

**Historial de versiones**

| Versión | Fecha | Qué cambió |
|---|---|---|
| 1.0 | 4 ago 2026 | Primera versión completa |
| 1.1 | 4 ago 2026 | Se agregan no‑objetivos, enlaces a diseño, supuestos con consecuencia y fechas límite |
| 2.0 | 10 ago 2026 | Reescrito de cero: lenguaje directo, autocontenido. **Se agrega** visión a largo plazo, seguridad y privacidad, casos de uso clave y el camino hasta desarrollo. **Contrastado contra la transcripción del 1 de agosto:** la coordinación pasa a llevar calidad —par o supervisor funcional— (`RF‑36`, `RF‑61`), la capa funcional se habilita por empresa (`RF‑62`), los de Outsourcing se dibujan al costado (`RF‑21`), se nombran los seis módulos bloqueados y se registra el riesgo del nodo único de multi‑sede |
| **2.1** | 11 ago 2026 | **Reordenado en nueve secciones, de Glosario a Recursos visuales**, y **corregidas dos afirmaciones que eran falsas.** Se agrega el glosario al frente, los principios de diseño, el detalle de integración con cada módulo y el modelo de datos. *(a)* Souly HR ya tiene app publicada y el documento decía lo contrario: el organigrama entra ahí como vista de consulta en solo lectura (`RNF‑23`, `RNF‑24`), y el equipo de la app pasa a ser dependencia. *(b)* Ningún requisito cubría **crear unidades organizacionales ni sedes**, así que una empresa nueva no podía llegar a crear su primer cargo y el objetivo 5 no era alcanzable: se agregan `RF‑63` a `RF‑69` y la regla 9. Tres pantallas nuevas —puesta en marcha, ubicaciones y consulta en la app—. Ningún requisito heredado cambia de contenido ni de número. **Sin revisar todavía** |

**Cómo leer este documento.** Está escrito para leerse de corrido, sin haber leído ningún otro. Empieza por el glosario a propósito: casi todos los malentendidos de este submódulo vienen de llamar distinto a la misma cosa.

Los requisitos llevan un número —`RF‑01`, `RNF‑01`— para poder citarlos en desarrollo y en pruebas. Es el único código del documento; todo lo demás se llama por su nombre. **Los números no cambian nunca**, aunque el requisito cambie de sección.

**Quién lee qué.** El documento sirve a dos lectores a la vez y ninguno necesita leerlo entero:

| Si sos… | Empezá por | Y no te saltees |
|---|---|---|
| **Diseño UX** | `0` Glosario · `1.4` Principios de diseño · `8` Recursos visuales | `3.11` Sistema visual y `4` Reglas de negocio: son lo que la maqueta tiene que respetar |
| **Desarrollo** | `0` Glosario · `5` Modelo de datos · `3` Funcionalidades | `2` Integraciones y `4` Reglas de negocio: definen qué se expone y qué se valida |
| **Negocio y RR.HH.** | `1` Contexto · `7` Historias de usuario | `6.7` Preguntas abiertas: son las decisiones que faltan y varias son suyas |

---

# 0 · Glosario

Todo el documento se apoya en estas definiciones. No son formalismos: cada una de ellas resuelve una confusión que apareció en la sesión de trabajo.

| Término | En una línea |
|---|---|
| **Cargo** | La posición de trabajo. Es la unidad del organigrama y existe aunque nadie la ocupe |
| **Ocupante** | La persona que ocupa un cargo durante un tiempo |
| **Unidad organizacional** | El área a la que pertenece el cargo. **Forma el árbol** |
| **Ubicación** | La sede donde se desempeña el cargo. **Solo filtra, nunca forma el árbol** |
| **Tipo de cargo** | Colaborador, Jefe / Director, Staff u Outsourcing |
| **Vacante** | Un estado, no un tipo: cargo activo con cero ocupantes |
| **Relación** | El vínculo declarado entre dos cargos. Son cuatro y son independientes |
| **Calidad** | Con qué carácter se coordina: como *par* o como *supervisor funcional* |
| **Vigencia** | El período en que una relación estuvo activa. Es lo que hace reconstruible el pasado |

## 0.1 Cargo

La posición formal o el puesto de trabajo que ocupa una persona dentro de la estructura de la empresa. Define funciones específicas, un nivel de autoridad y un lugar en la jerarquía. Es lo que representa cada cuadro del organigrama.

> **Y existe aunque nadie lo ocupe.** "Analista Contable" es un cargo tenga o no tenga a alguien sentado. De ahí salen tres consecuencias que sostienen el modelo entero: un cargo puede estar **vacante**, puede admitir **más de un ocupante**, y las relaciones se declaran **entre cargos, no entre personas**. Esto último no es un detalle técnico: hoy la dependencia se guarda de persona a persona, y cuando rota el ocupante la relación se pierde.

## 0.2 Ocupante

El colaborador que ocupa un cargo, con fecha de inicio y, si corresponde, de salida. Un cargo puede admitir más de un ocupante —cuatro cajeros en el mismo cargo— y declara cuántos como máximo. Cuando alguien se retira, el registro no se borra: queda en el histórico del cargo.

## 0.3 Unidad organizacional

El área de la empresa a la que pertenece el cargo, en hasta cuatro niveles: **Área → Subárea → Departamento → Equipo**. Ninguna empresa está obligada a usar los cuatro; los que no usa se saltan. *(El cuarto nivel está por confirmar — ver `6.7`.)*

## 0.4 Ubicación

La sede donde se desempeña el cargo, en hasta cinco niveles: **Empresa → Unidad de negocio → Región → Sucursal → Oficina**. Es la sede de trabajo, no el domicilio del ocupante — ese dato vive en la ficha del colaborador y no interviene acá.

> **La distinción más importante del modelo: la unidad organizacional forma el árbol, la ubicación solo filtra.** Sucursal y región nunca son niveles del organigrama. Si lo fueran, una empresa con tres sedes tendría el mismo cargo dibujado tres veces y ninguna de las tres sería la verdadera.

## 0.5 Los cuatro tipos de cargo

Se eligen al crear el cargo y se pueden cambiar después.

| Tipo | Qué es | Particularidad |
|---|---|---|
| **Colaborador** | Puesto sin gente a cargo | No puede tener subordinados |
| **Jefe / Director** | Puesto con línea de mando | Sin restricciones |
| **Staff** | Asiste a un cargo sin estar en su línea de mando: una controller, una asistente de gerencia | Se dibuja al costado, no debajo. No tiene gente a cargo |
| **Outsourcing** | Servicio prestado por alguien externo | No genera planilla, salarios ni asistencia. Lleva motivo de contratación. Se puede dibujar al costado, igual que un cargo Staff |

**Vacante no es un tipo: es un estado.** Un cargo activo con cero ocupantes está vacante, sea del tipo que sea — un Jefe / Director puede estar vacante igual que un Colaborador. El sistema lo deduce; nadie lo declara a mano y no aparece como opción al crear un cargo.

En pantalla son **cinco codificaciones visuales**: los cuatro tipos más el estado de vacante, que se superpone al tipo que el cargo ya tenía.

## 0.6 Las cuatro relaciones

Son independientes entre sí. Declarar una no modifica a las otras.

| Relación | Qué significa | Cuántas admite |
|---|---|---|
| **Depende de** | Su jefe. La línea de mando | Exactamente una |
| **Coordina con** | Trabaja en conjunto sin depender. Cada contraparte se declara **en qué calidad**: como *par* o como *supervisor funcional* | Todas las que haga falta |
| **Le aprueba los permisos** | Quién autoriza sus vacaciones, permisos y salidas | Una, más un suplente si la empresa lo habilita |
| **Asiste a** | La relación del personal Staff con el cargo que asiste | Una |

> **Por qué la coordinación lleva calidad y no es una sola cosa.** Un cargo puede coordinar con alguien de su mismo nivel o con alguien que, sin ser su jefe, le supervisa una parte del trabajo. Son dos situaciones distintas y Desempeño necesita distinguirlas: en una el contraparte evalúa como par, en la otra evalúa como supervisor. Si la relación se guarda sin calidad, el dato se captura y no sirve para lo que se lo capturó.

> **Por qué el aprobador es una relación aparte y no se deduce del jefe.** Porque en la práctica no coinciden. El jefe directo de un cajero puede ser el supervisor de sucursal, y quien firma sus vacaciones, la gerencia de operaciones. Deducirlo habría sido más simple y habría dado la respuesta equivocada en la mitad de los casos — que es justamente la pregunta que originó el proyecto.

## 0.7 Cómo se nombra cada cosa según dónde aparezca

Un mismo concepto se llama distinto en pantalla, en la documentación y en la base. No es descuido: cada lector es otro.

| Concepto | En pantalla | En documentación y reportes | En la base de datos |
|---|---|---|---|
| Línea de mando | `Depende de` | *dependencia estructural* | `estructural` |
| Coordinación | `Coordina con` | *dependencia funcional* | `funcional` |
| Aprobación | `Le aprueba los permisos` | *relación de aprobación* | `aprobacion` |
| Staff | `Asiste a` | *relación de asistencia* | `asistencia` |

"Puesto de línea" es vocabulario de especialista. El jefe de área que declara su equipo no lo usa. En pantalla se entiende el verbo; el término técnico vive donde el lector es otro.

---

# 1 · Contexto

## 1.1 ¿Qué es un organigrama?

Un organigrama es la representación de la **estructura formal** de una organización: qué cargos existen, cómo se relacionan entre sí y quién responde ante quién. Es un mapa, y como todo mapa vale por lo que decide dejar afuera.

Responde tres preguntas y ninguna más:

| Pregunta | Qué la contesta |
|---|---|
| **¿Qué cargos existen?** | La unidad organizacional: en qué área vive cada cargo |
| **¿Cómo se relacionan?** | Las cuatro relaciones: jefe, coordinación, aprobación y asistencia |
| **¿Dónde se desempeñan?** | La ubicación: la sede, que filtra la vista sin alterar el árbol |

**La unidad es el cargo, no la persona.** Es la decisión que ordena todo lo demás. Un organigrama construido sobre personas se desarma cada vez que alguien renuncia: desaparece el cuadro, desaparecen las líneas que salían de él y desaparece el registro de que ese puesto existía. Construido sobre cargos, la rotación es lo que es —un cambio de ocupante— y la estructura queda intacta.

**Lo que un organigrama no dice.** No dice cómo se trabaja de verdad, ni quién tiene influencia, ni cuánto gana nadie. Describe la estructura declarada, que es una parte de la organización y no toda. Confundir las dos cosas es el error clásico: se le pide al organigrama que explique por qué algo no funciona, y el organigrama solo sabe quién le reporta a quién.

> **Por qué esto importa acá.** Todo lo que sigue —las cuatro relaciones, la vigencia, el estado de vacante, el modelo de datos de la sección `5`— es consecuencia de haber puesto el cargo en el centro en vez de la persona. Es también la diferencia con lo que hay hoy en Trabajito, donde la dependencia se guarda de persona a persona.

## 1.2 ¿Por qué un organigrama?

**Lo que ya existe y funciona.** El organigrama estructural. Dibuja la línea de mando, se ve bien, y hoy ya lo consumen tres módulos: **Desempeño** saca de ahí jefes, pares y subordinados; **Gestión de Personas** lo usa para dar de alta a un colaborador; **Onboarding** lo usa para visualizar la estructura. Nada de eso se toca.

**Lo que falta es todo lo que no sea la línea de mando.**

| Qué falta | Qué no se puede hacer hoy |
|---|---|
| **La capa funcional** — quién coordina con quién sin ser su jefe | Desempeño solo evalúa por línea estructural. Los evaluadores funcionales que RR.HH. necesita agregar se cargan a mano, fuera del sistema |
| **Las aprobaciones** — quién autoriza los permisos de cada cargo | Asistencia no tiene de dónde leer al aprobador. Es lo que habilitaría que las jefaturas aprueben permisos dentro de la plataforma |
| **El tipo Outsourcing** — no existe | El personal externo no figura en la estructura, aunque esté fijo y bajo contrato de servicio. Queda fuera de la vista de auditoría |
| **Reglas para Staff** — el tipo existe, su comportamiento no está definido | No está establecido que no tenga línea descendente ni que se dibuje al costado de quien asiste. Cada empresa lo interpreta a su manera |
| **El estado de Vacante** | Los puestos por cubrir no se distinguen, así que Reclutamiento no puede disparar requisiciones desde la estructura |
| **El centro de costo en el cargo** | Planillas y Salarios no lo reciben declarado desde la estructura |

**El dolor del usuario.** La responsable de RR.HH. no puede responder "¿quién le firma las vacaciones a este cajero?" sin preguntar. Cuando arma el reporte de estructura para gerencia, lo hace a mano en una planilla aparte. Y cuando rota un ocupante, la dependencia que había cargado se pierde, porque el sistema la guardó de persona a persona en vez de cargo a cargo.

> **No estamos construyendo un organigrama desde cero: estamos completando el que existe.** La línea de mando ya está resuelta y ya alimenta a tres módulos. Lo que se agrega son las otras tres relaciones, los dos tipos de cargo que faltan y el estado de vacante.
>
> **Eso vale para el submódulo, no para el cliente.** Una empresa que recién entra a Souly HR sí empieza de cero: sin áreas, sin sedes y sin cargos. Que pueda llegar sola hasta su estructura completa es el objetivo 5 y está cubierto por `RF‑63` a `RF‑69`.

**Cómo lo sabemos.** Sesión de trabajo con la especialista de dominio del 1 de agosto de 2026, revisión del submódulo actual, y las capturas del formulario de alta vigente —que pide cuatro campos: nombre, unidad, reporta a y ocupante.

## 1.3 Visión del submódulo

> **Dónde vive.** Organigrama **no es un módulo: es un submódulo de Gestión de Personas.** No se vende ni se activa por separado, y no tiene menú propio en la plataforma. Esa distinción importa en tres lugares de este documento: cuando se habla de "los otros módulos" —Desempeño, Asistencia, Reclutamiento, Planillas, Onboarding, Comunicación—, que sí lo son; cuando se define quién puede escribir estructura (`2.1`); y cuando se corta el alcance, porque un submódulo no puede pedirle a la plataforma que cambie por él.

### Qué vamos a construir

Hoy el organigrama dibuja bien **una** relación: la línea de mando. Lo evolucionamos para que declare **todas las demás** —quién coordina con quién, quién aprueba los permisos de quién, quién solo apoya— y para que le permita a cada empresa modelar su estructura real sin tener que simplificarla. Cinco piezas:

| # | Pieza | Qué es |
|---|---|---|
| 01 | **Identificación visual inmediata** | Cuatro tipos de cargo —Colaborador, Jefe / Director, Staff y Outsourcing— más el estado de Vacante, que el sistema deduce y nadie declara a mano. Las cinco codificaciones se distinguen por color, forma e ícono a la vez |
| 02 | **Tres vistas sobre la misma estructura** | Estructura oficial: la línea de reporte. Red funcional: las coordinaciones que cruzan el árbol sin cambiar de quién depende cada cargo. Matriz de aprobaciones: quién autoriza permisos y vacaciones |
| 03 | **Filtros por sede, región y unidad de negocio** | Aislar la vista de Santa Cruz o de Cochabamba sin romper el árbol global de la empresa: los cargos que no corresponden se atenúan, no desaparecen |
| 04 | **Alta guiada en cuatro pasos** | El jefe, el aprobador de permisos y el centro de costo se declaran durante el alta, no como una configuración posterior que nadie completa |
| 05 | **Panel de estructura** | Cargos y personas, contadores por tipo, vacantes con salida directa a requisición, y la lista de lo que falta declarar, que es lo que hace medibles los dos primeros objetivos |

### Hacia dónde va

El organigrama deja de ser un dibujo y pasa a ser **la fuente de la que leen todos los módulos de Gestión de Personas**. Esa es la apuesta estratégica: en vez de que cada módulo pregunte por su cuenta quién depende de quién, hay un solo lugar donde eso está declarado, versionado y auditable.

| Horizonte | Hacia dónde |
|---|---|
| **Esta versión** | La estructura existe, está completa y otros módulos la pueden leer |
| **Siguiente** | La estructura tiene historia navegable: ver cómo estaba la organización en cualquier fecha pasada, para auditoría y para análisis de rotación |
| **Más adelante** | La estructura alimenta decisiones: costo por área, tramos de control, detección de áreas sin sucesor |

El efecto multiplicador es el argumento de negocio: con un solo desarrollo, tres módulos que hoy leen la estructura a medias pasan a leerla completa —Desempeño, Gestión de Personas y Onboarding— y tres que hoy no la leen empiezan a hacerlo: Asistencia, Reclutamiento y Planillas. Es la pieza del roadmap con mejor relación entre esfuerzo y alcance. El detalle de cada integración está en la sección `2`.

## 1.4 Principios de diseño

Ocho decisiones que se tomaron una vez y valen para todo el submódulo. Cuando aparezca un caso que este documento no previó, se resuelve con estos principios y no con criterio nuevo. El argumento largo de cada uno está en el anexo *Por qué decidimos así*.

| # | Principio | Qué implica en la práctica |
|---|---|---|
| 1 | **El cargo es la unidad, no la persona** | Las relaciones se declaran entre cargos. La rotación no borra estructura |
| 2 | **Una relación por vez en pantalla** | Las tres vistas no se superponen. Superponerlas es el camino más corto a un diagrama ilegible |
| 3 | **Ninguna señal depende solo del color** | Cada codificación lleva color, forma e ícono. Tiene que sobrevivir a una fotocopia, a un proyector y al daltonismo |
| 4 | **Atenuar antes que ocultar** | Filtrar cambia la opacidad, nunca la forma del árbol. Ocultar deja subordinados colgando de la nada |
| 5 | **Lo mínimo utilizable primero** | El alta se puede terminar en el paso 3. El perfil completo puede esperar; un cargo sin jefe declarado bloquea a otros módulos |
| 6 | **Antes de un cambio grande, mostrar el alcance** | La confirmación de un movimiento no está para que el usuario dude: está para que **vea** cuántos cargos y personas arrastra |
| 7 | **Se llama como lo llama el usuario** | "Jefe directo", no "nodo padre". El vocabulario técnico vive en la base de datos y en esta documentación, no en pantalla |
| 8 | **El organigrama vive fuera de la pantalla** | Se imprime y se proyecta. Un requisito que solo se cumple en un monitor no está cumplido |

> **El principio 5 es el que más se va a discutir.** Deja entrar cargos incompletos a propósito. La alternativa —exigir los dieciséis campos— produce estructuras vacías, que es peor: un cargo sin rango salarial le sirve a cuatro módulos, un cargo que nunca se creó no le sirve a ninguno. La lista "Sin declarar" del panel de estructura existe para que lo incompleto sea visible y se complete, no para que se olvide.

## 1.5 Objetivos y métricas de éxito

### Objetivos de negocio

| # | Objetivo | Por qué importa |
|---|---|---|
| 1 | **Que la estructura sirva para que otros módulos la usen** | Habilita a Asistencia y Reclutamiento, que hoy no la leen, y completa lo que Desempeño y Onboarding ya leen a medias |
| 2 | **Que ningún permiso se trabe por falta de datos** | Un flujo de aprobación que falla en producción erosiona la confianza en toda la plataforma |
| 3 | **Que declarar un cargo no sea una carga** | Si cargar la estructura cuesta, queda incompleta, y una estructura incompleta no le sirve a nadie |
| 4 | **Que el organigrama sirva para presentar** | Es lo que convierte al submódulo en algo que RR.HH. usa todas las semanas y no una vez al año |
| 5 | **Acortar la puesta en marcha de cada cliente nuevo** | Hoy la implantación se traba en el primer paso: sin estructura no se puede dar de alta gente |

### Indicadores

| Indicador | Hoy | Meta | Cuándo se mide | Objetivo que verifica |
|---|---|---|---|---|
| Cargos con jefe, aprobador y centro de costo declarados | Sin medir | **90 % o más** | 60 días después del despliegue | 1 |
| Cargos activos sin aprobador declarado | Sin medir | **Cero** | 60 días | 2 |
| Tiempo típico de alta de un cargo | Sin medir | **90 segundos o menos** | 30 días | 3 |
| Formularios de alta abandonados a mitad | Sin medir | **15 % o menos** | 30 días | 3 |
| Exportaciones por empresa al mes | Cero — la función no existe | **2 o más** | 60 días | 4 |
| Empresas que activan la vista de coordinaciones | — | Se observa, no se fija meta | 90 días | — |
| Días desde el alta de la empresa hasta el primer colaborador cargado | Sin medir | Se establece línea base | 90 días | 5 |

### Cómo se van a medir

Ninguna cifra de hoy está medida porque el submódulo actual no registra estos eventos. Por eso `RF‑57` —registrar la actividad— es un requisito obligatorio y no una mejora: **sin él, este documento promete resultados que nadie va a poder comprobar.**

Los eventos mínimos a registrar son: alta iniciada, alta completada, alta abandonada y en qué paso, cambio de vista, aplicación de filtro, exportación y movimiento de cargo.

## 1.6 A quién sirve

### Usuarios principales

| Quién | Qué hace acá | Cada cuánto | Qué le importa |
|---|---|---|---|
| **Responsable de RR.HH.** | Arma y mantiene la estructura, declara relaciones, revisa vacantes, exporta para gerencia | Semanal | Que esté completo y sea presentable. Es la usuaria principal |
| **Gerente o jefe de área** | Consulta su equipo, declara las relaciones de su gente, revisa quién aprueba | Mensual | Que sea rápido y no le pida datos que no tiene |
| **Colaborador** | Consulta de quién depende y quién le aprueba los permisos | De vez en cuando, **casi siempre desde la app** | Encontrar una respuesta concreta en dos toques |
| **Auditoría** | Consulta cómo estaba la estructura en una fecha pasada | Trimestral | Que el histórico no se pise |

### Persona de referencia

**Fabiola Gutiérrez · Responsable de RR.HH., especialista de dominio.**

Mantiene la estructura de una empresa de unos 40 cargos con varias sucursales. Cada trimestre presenta el organigrama a gerencia: proyectado en sala y repartido impreso. Hoy arma ese material a mano, fuera del sistema.

Sus dos exigencias condicionan buena parte de este documento: **que se entienda de un vistazo** y **que funcione impreso y proyectado**. De ahí salen el sistema visual con señales redundantes y que la exportación sea un requisito de negocio y no una mejora.

Lo que la haría abandonar el submódulo: que cargar un cargo le lleve más de un minuto y medio, o que el organigrama impreso salga ilegible.

### Casos de uso clave

Las cinco situaciones más frecuentes, en orden de frecuencia esperada:

| # | Situación | Quién | Con qué frecuencia |
|---|---|---|---|
| 1 | **Consultar quién aprueba un permiso** antes de tramitarlo | Colaborador, jefe de área | Diaria |
| 2 | **Dar de alta un cargo nuevo** y dejarlo utilizable de inmediato | RR.HH. | Semanal |
| 3 | **Revisar qué falta declarar** y completarlo | RR.HH. | Semanal |
| 4 | **Mover un cargo** cuando hay una reorganización, sabiendo qué se arrastra | RR.HH. | Mensual |
| 5 | **Exportar la estructura** para presentarla a gerencia | RR.HH. | Trimestral |

Un sexto caso, menos frecuente pero crítico: **cargar la estructura completa de un cliente nuevo** desde cero. Es el que decide si la implantación arranca en una semana o en un mes.

Cada situación está desarrollada como historia de usuario con condiciones de aceptación en la sección `7`.

## 1.7 Alcance y límites

### Dentro del alcance

Plataforma: **web de escritorio** para todo, **web móvil en solo lectura**, y una **vista de consulta dentro de la app de Souly HR**, también en solo lectura. No se construye una aplicación propia del organigrama: se suma una vista a la app que ya existe.

| Funcionalidad |
|---|
| **Crear y mantener las unidades organizacionales y las sedes** |
| **Puesta en marcha guiada para una empresa que empieza de cero** |
| Lienzo del organigrama, navegación y zoom |
| Los cuatro tipos de cargo y el estado de vacante, con su codificación visual |
| Las tres vistas: jerarquía, coordinaciones y aprobaciones |
| Ubicación como filtro sobre el lienzo |
| Alta y edición de cargo en cuatro pasos |
| Mover, duplicar y eliminar, con validaciones |
| Panel de estructura con contadores, vacantes y pendientes |
| Exportación a PDF, PNG y CSV |
| Historial de cambios en la ficha del cargo |
| Lectura desde el celular |

### Fuera del alcance

Se deja deliberadamente afuera para que el proyecto no crezca sin control. Cada punto está registrado, no descartado.

| Queda afuera | Por qué |
|---|---|
| Rehacer el motor de dibujo del lienzo | Se extiende el actual. Rehacerlo multiplicaría el esfuerzo sin beneficio visible |
| Que cada empresa edite la paleta | Rompería la garantía de accesibilidad e impresión |
| Ver dos tipos de relación a la vez | Es el camino más corto a un diagrama ilegible |
| Ubicación como nivel del árbol | Duplicaría cargos en pantalla |
| Alta masiva por formulario | La importación desde Excel cubre el caso, si se aprueba |
| Deshacer varios pasos seguidos | Alcance técnico grande; se cubre con confirmación previa e historial |
| Navegar el árbol de una fecha pasada | El dato se guarda desde el día uno; la pantalla llega después |
| Editar desde el celular | Nadie reorganiza una empresa desde el teléfono |
| Reportes analíticos de estructura | Otro módulo, otro documento |
| Una aplicación propia del organigrama | La consulta vive dentro de la app de Souly HR que ya existe (`RNF‑23`) |
| Editar la estructura desde la app | Misma razón que arriba: nadie reorganiza una empresa desde el teléfono |

### Lo que este submódulo no pretende ser

- **No es una herramienta para diseñar la organización.** Representa la estructura que existe; no simula reorganizaciones ni escenarios hipotéticos.
- **No reemplaza el directorio de personas.** Acá la unidad es el cargo; la persona es quien lo ocupa durante un tiempo.
- **No abre la edición a todo el mundo.** Cualquiera consulta; editar es de RR.HH. y de las jefaturas.
- **No modela estructuras matriciales con doble jefe.** Cada cargo tiene un jefe y uno solo. Lo matricial se expresa con coordinaciones.
- **No decide por nadie.** El sistema valida reglas; no sugiere reorganizaciones ni señala cargos "innecesarios".
- **No copia el organigrama impreso que cada empresa ya usa.** Proponemos un sistema visual propio y consistente.

### Escala de prioridades

Vale para todos los requisitos de la sección `3`.

| Prioridad | Criterio |
|---|---|
| **Obligatorio** | Sin esto, la estructura no le sirve a los otros módulos |
| **Importante** | Mejora sustantiva; entra si el plazo lo permite |
| **Deseable** | Entra en la primera iteración posterior |
| **Fuera** | Registrado, pero no en esta versión |

---

# 2 · Integraciones

## 2.1 El principio: el organigrama es la fuente, los demás leen

El organigrama no le pide datos a nadie. **Declara la estructura y la expone**; los otros módulos la consultan. La única escritura que recibe desde afuera es la asignación de ocupantes, que llega de Gestión de Personas, y el cierre de requisiciones, que llega de Reclutamiento.

Esto es una decisión de arquitectura, no una preferencia. Si cada módulo pudiera escribir estructura, habría siete lugares donde cambiar de jefe y ninguno sería el verdadero.

```
                        ┌──────────────────────────┐
     escriben  ────────▶│                          │
                        │       ORGANIGRAMA        │
  Gestión de Personas   │                          │
  (ocupantes)           │  cargos · relaciones     │──────▶  leen
  Reclutamiento         │  unidades · ubicaciones  │
  (cierre de requisición)│  vigencias              │   Desempeño
                        └──────────────────────────┘   Onboarding
                                                       Asistencia
                                                       Reclutamiento
                                                       Planillas y Salarios
                                                       Gestión de Personas
                                                       Comunicación (por confirmar)
```

**Qué expone.** El detalle de cada campo está en la sección `5`; en resumen, cualquier módulo puede preguntar:

| Pregunta | Qué devuelve |
|---|---|
| ¿Qué cargos tiene esta empresa? | Cargos activos con tipo, unidad, ubicación y centro de costo |
| ¿De quién depende este cargo? | El cargo jefe, y su ocupante actual si lo tiene |
| ¿Con quién coordina? | Los cargos contraparte **y en qué calidad**: par o supervisor funcional |
| ¿Quién le aprueba los permisos? | El cargo aprobador, y el suplente si la empresa lo habilitó |
| ¿Quién ocupa este cargo? | Los ocupantes vigentes, que pueden ser varios |
| ¿Cómo estaba esto en tal fecha? | La estructura reconstruida a partir de las vigencias |

> **La última fila es la que hace distinto a este organigrama.** Toda relación se cierra con fecha en vez de borrarse (regla 8, `RF‑41`, `RF‑45`). Eso significa que la pregunta "¿quién era el jefe de este cargo en marzo?" tiene respuesta, y de ahí salen la auditoría y el análisis de rotación. El dato se guarda desde la primera etapa aunque la pantalla para navegarlo llegue después.

## 2.2 Desempeño

**Es el módulo que más gana y el que hoy está peor servido.**

| | |
|---|---|
| **Qué lee hoy** | Jefes, pares y subordinados, por línea estructural únicamente |
| **Qué le falta** | Las coordinaciones, y sobre todo **la calidad de cada una** |
| **Qué escribe** | Nada |
| **Requisitos** | `RF‑19` · `RF‑22` · `RF‑24` · `RF‑36` · `RF‑61` |

Una evaluación 360 necesita saber si el contraparte evalúa **como par** o **como supervisor funcional**, porque el peso de la respuesta no es el mismo. Hoy ese dato no existe en la estructura, así que RR.HH. carga los evaluadores funcionales a mano, por fuera del sistema, cada vez que arma un ciclo.

Los dos casos que aparecieron en la sesión del 1 de agosto son exactamente esto:

- La **analista contable** que depende de su gerente pero coordina con las gestoras de otra región — coordinación de *par*.
- La **responsable de RR.HH.** a quien evalúan el gerente administrativo y la gerente comercial, sin que ninguno sea su jefe — coordinación de *supervisor funcional*.

> **Guardar las dos como la misma relación es barato de construir y deja a Desempeño sin poder distinguirlas.** Como la calidad vive en la misma tabla que la relación, agregarla después obliga a migrar datos. Por eso `RF‑61` entra ahora y no en una versión posterior.

## 2.3 Gestión de Personas

**Es el único módulo que además escribe.**

| | |
|---|---|
| **Qué lee** | Los cargos disponibles al dar de alta a un colaborador, con su unidad y su máximo de ocupantes |
| **Qué escribe** | La asignación de un ocupante a un cargo, con fecha de inicio y de salida |
| **Qué le falta hoy** | Que el cargo traiga declarados el aprobador y el centro de costo, para no pedirlos de nuevo |
| **Requisitos** | `RF‑33` · `RF‑46` · `RF‑47` · Regla 5 |

El alta de un colaborador pasa por elegir su cargo. Si el cargo ya trae jefe, aprobador y centro de costo declarados, el alta se completa sin preguntar nada de eso — que es el objetivo 3 de `1.5`.

**La regla del máximo de ocupantes se valida acá.** Un cargo "Cajero" con máximo cuatro no admite un quinto: el intento se rechaza y se ofrece crear otro cargo o subir el máximo. Es la regla 5 de la sección `4`, y es del organigrama aunque quien la choque sea Gestión de Personas.

**Y hay dos efectos de vuelta:** cuando entra el primer ocupante de un cargo vacante, el cargo deja de estar vacante y se ofrece cerrar la requisición (`RF‑46`); cuando se va el último, el cargo vuelve a vacante y se ofrece abrirla (`RF‑47`).

## 2.4 Onboarding

**Hoy lo usa solo para dibujar. Puede usarlo para responder.**

| | |
|---|---|
| **Qué lee hoy** | La estructura, para visualizarla |
| **Qué podría leer** | El jefe, el aprobador, el equipo y los cargos con los que coordina el puesto de quien entra |
| **Qué escribe** | Nada |
| **Requisitos** | `RF‑17` · `RF‑19` · `RF‑23` · `RNF‑04` |

Las tres preguntas de la primera semana de cualquier persona nueva son de quién dependo, quién me aprueba los permisos y quiénes son mi equipo. Las tres las contesta el organigrama y ninguna necesita pantalla nueva: la ficha del cargo (`RF‑17`) ya las tiene.

**La alternativa en lista anidada (`RNF‑04`) importa especialmente acá.** Buena parte del onboarding se hace desde el celular, y en una pantalla de cinco pulgadas un árbol dibujado es un mapa que se arrastra a ciegas. La lista responde mejor la pregunta que la persona lleva al teléfono.

## 2.5 Asistencia

**Es el módulo bloqueado, y la razón por la que este proyecto empezó.**

| | |
|---|---|
| **Qué lee hoy** | Nada. No tiene de dónde leer |
| **Qué necesita** | El cargo aprobador de cada cargo, y su suplente si existe |
| **Qué escribe** | Nada |
| **Requisitos** | `RF‑23` · `RF‑33` · `RF‑34` · `RF‑37` · `RF‑51` |

Sin la relación de aprobación declarada, un permiso o una solicitud de vacaciones no tiene a quién ir. Hoy eso se resuelve por fuera de la plataforma.

> **Por qué no alcanza con deducir el aprobador del jefe.** Porque en la práctica no coinciden: el jefe directo de un cajero puede ser el supervisor de sucursal, y quien le firma las vacaciones, la gerencia de operaciones. Deducirlo da la respuesta equivocada en la mitad de los casos. Por eso el aprobador se propone igual al jefe (`RF‑34`) pero se puede cambiar, y por eso los cargos sin aprobador aparecen marcados en el lienzo y en la lista "Sin declarar" (`RF‑51`).

**El indicador que verifica esta integración** es "cargos activos sin aprobador declarado = cero", en `1.5`. Mientras ese número no sea cero, Asistencia va a fallar para alguien.

## 2.6 Reclutamiento

| | |
|---|---|
| **Qué lee** | Los cargos en estado vacante, con su unidad, su ubicación y su perfil |
| **Qué escribe** | El cierre de la requisición cuando el cargo se cubre |
| **Qué le falta hoy** | El estado de vacante, que no existe |
| **Requisitos** | `RF‑14` · `RF‑46` · `RF‑47` · `RF‑50` · Regla 4 |

La vacante **no se declara: se deduce** de que el cargo esté activo y tenga cero ocupantes (regla 4). Eso hace que la lista de vacantes esté siempre al día sin que nadie la mantenga, que es la única forma de que sirva.

El circuito completo, en los dos sentidos:

```
  Cargo activo, 0 ocupantes
        │
        ▼
   ● VACANTE ──────▶ Panel de estructura: lista de vacantes  (RF‑50)
        │                        │
        │                        ▼
        │              Crear requisición  ──────▶  RECLUTAMIENTO
        │                                                 │
        │                                                 ▼
        │                                          Se cubre el puesto
        │                                                 │
        ▼                                                 ▼
   Entra el primer ocupante ◀──────────────  GESTIÓN DE PERSONAS
        │
        ▼
   ● OCUPADO ──────▶ Se ofrece cerrar la requisición  (RF‑46)
```

## 2.7 Planillas y Salarios

| | |
|---|---|
| **Qué lee** | El centro de costo declarado en el cargo, y el tipo de cargo |
| **Qué escribe** | Nada |
| **Qué le falta hoy** | Que el centro de costo venga del cargo y no se cargue aparte |
| **Requisitos** | `RF‑31` · `RF‑33` · Regla 3 |

El centro de costo es **obligatorio en el tercer paso del alta** (`RF‑33`) justamente por esto: si no se declara al crear el cargo, se convierte en una configuración posterior que nadie completa, y Planillas termina pidiéndolo de nuevo.

> **Los cargos de Outsourcing son la excepción y hay que respetarla en los dos lados.** Un cargo de Outsourcing está en la estructura pero no en la nómina: no genera planilla, ni salarios, ni asistencia (regla 3). El formulario de alta lo refleja ocultando esos campos y pidiendo en su lugar el motivo de contratación (`RF‑31`). Si Planillas lee la estructura sin filtrar por tipo, va a intentar liquidar a personal externo.

**La parametrización de centro de costo ya existe** del lado de Planillas — es la única dependencia de la sección `6.4` que no está pendiente.

## 2.8 Comunicación

| | |
|---|---|
| **Qué lee** | **Por confirmar** |
| **Estado** | Pregunta abierta con fecha: 15 de agosto (`6.7`) |

No está confirmado si Comunicación usa el organigrama ni qué leería de él. Los usos plausibles —segmentar destinatarios por unidad, por sucursal o por línea de mando— no requieren nada que las otras integraciones no pidan ya, así que **la respuesta no debería cambiar el alcance**. Se registra igual porque una integración descubierta tarde sí lo cambiaría.

## 2.9 Resumen

| Módulo | Lee | Escribe | Hoy | Con este submódulo |
|---|---|---|---|---|
| **Desempeño** | Jefes, pares, subordinados **y la calidad de cada coordinación** | — | Solo línea estructural | 360 completo sin carga manual |
| **Gestión de Personas** | Cargos, máximo de ocupantes, aprobador, centro de costo | **Ocupantes** | Alta con datos repetidos | Alta sin volver a preguntar |
| **Onboarding** | Jefe, aprobador, equipo, coordinaciones | — | Solo visualiza | Contesta las tres preguntas del primer día |
| **Asistencia** | **Aprobador y suplente** | — | **Bloqueado** | Permisos aprobados dentro de la plataforma |
| **Reclutamiento** | Cargos vacantes con perfil | **Cierre de requisición** | **Bloqueado** | Requisición disparada desde la estructura |
| **Planillas y Salarios** | Centro de costo, tipo de cargo | — | Centro de costo cargado aparte | Lo recibe declarado desde el cargo |
| **Comunicación** | Por confirmar | — | Por confirmar | Por confirmar |

**Lo que todas tienen en común, y es la dependencia crítica del proyecto:** ninguna de estas integraciones funciona sin una **tabla de relaciones entre cargos con tipo, calidad y vigencia**. No es que falten funciones si no está: no hay submódulo. Está registrada como dependencia en `6.4`, como riesgo crítico en `6.6` y detallada en `5.4`.

---

# 3 · Funcionalidades

Los requisitos que definen qué tiene que hacer el submódulo. Cada uno lleva prioridad —según la escala de `1.7`— y una condición de comprobación, que es lo que QA va a verificar.

Los números son estables: `RF‑01` es `RF‑01` en cualquier versión de este documento. Las pantallas donde vive cada requisito están en `8.1`.

## 3.1 Ver la estructura

| # | Requisito | Prioridad | Cómo se comprueba |
|---|---|---|---|
| `RF‑01` | El lienzo dibuja la estructura como un árbol, con un solo jefe por cargo | Obligatorio | Un cargo con jefe declarado aparece debajo de él, unido por línea continua |
| `RF‑02` | Se puede acercar, alejar y desplazar el lienzo | Obligatorio | `Ctrl` + rueda y pellizco hacen zoom; arrastrar el fondo desplaza |
| `RF‑03` | El nodo muestra más o menos información según el zoom, en cuatro tramos | Importante | Por debajo del 40 % no se dibuja texto; por encima del 110 % aparecen unidad, sucursal y código |
| `RF‑04` | Los cargos con gente debajo se pueden plegar, indicando cuántos esconden | Obligatorio | El control muestra el total de descendientes ocultos |
| `RF‑05` | Al abrir se despliegan los tres primeros niveles | Importante | En una estructura de cinco niveles, el cuarto y el quinto llegan plegados |
| `RF‑06` | Cada usuario se reencuentra el árbol como lo dejó | Deseable | Al reabrir se respeta lo que había plegado |
| `RF‑07` | El árbol se puede ver en vertical o en horizontal | Importante | El cambio no recarga la página |
| `RF‑08` | Hay densidad cómoda y compacta | Deseable | La compacta reduce el alto del nodo y el espaciado |
| `RF‑09` | Buscar por cargo o por persona centra y resalta el nodo | Obligatorio | El resultado queda centrado y se resalta dos segundos |
| `RF‑10` | Doble clic aísla una rama y `Esc` vuelve atrás | Importante | Al aislar, las ramas hermanas se pliegan |
| `RF‑11` | Hay minimapa y botón de ajustar a pantalla | Deseable | El minimapa refleja qué parte se está viendo |

## 3.2 El nodo

| # | Requisito | Prioridad | Cómo se comprueba |
|---|---|---|---|
| `RF‑12` | El nodo muestra **la etiqueta de su tipo**, el nombre del cargo, el ocupante y cuántos puestos están cubiertos | Obligatorio | Un cargo Staff con un ocupante muestra `STAFF`, el nombre del cargo, el del ocupante y `1/1` |
| `RF‑13` | Cada tipo se distingue por **color, forma de borde e ícono** a la vez | Obligatorio | En escala de grises las cinco codificaciones se siguen distinguiendo |
| `RF‑14` | Un cargo activo sin ocupantes se dibuja como vacante | Obligatorio | Sin relleno y con borde discontinuo, sobre el tipo que ya tenía |
| `RF‑15` | El nodo tiene tratamiento propio para: normal, cursor encima, seleccionado, enfocado por teclado, resultado de búsqueda, fuera del filtro, arrastrándose y destino inválido | Obligatorio | Los ocho estados están definidos en `8.6` |
| `RF‑16` | Un cargo sin jefe declarado lleva una marca de aviso | Importante | La marca lleva directo a completar el dato |
| `RF‑17` | Seleccionar un nodo abre su ficha en un panel lateral, sin salir del lienzo | Obligatorio | Muestra relaciones, ocupantes, unidad, ubicación e historial |
| `RF‑18` | El menú del nodo conserva las acciones actuales y suma tres: declarar coordinación, declarar aprobador y ver historial | Obligatorio | Las acciones que ya existían no se pierden |

## 3.3 Las tres vistas

| # | Requisito | Prioridad | Cómo se comprueba |
|---|---|---|---|
| `RF‑19` | Tres vistas conmutables: jerarquía, coordinaciones y aprobaciones | Obligatorio | El conmutador está siempre visible y dice cuál está activa |
| `RF‑20` | Las vistas no se superponen: al activar una, las otras no se dibujan | Obligatorio | En coordinaciones, la jerarquía queda de fondo atenuada y no compite |
| `RF‑21` | **Jerarquía:** línea de mando con trazo continuo. Los cargos Staff y los de Outsourcing van al costado, no debajo | Obligatorio | Un cargo Staff nunca aparece como subordinado del cargo que asiste |
| `RF‑22` | **Coordinaciones:** la jerarquía se atenúa y se dibujan las coordinaciones punteadas, curvas y sin cruzar nodos | Obligatorio | En un árbol de 40 cargos las líneas se siguen distinguiendo |
| `RF‑23` | **Aprobaciones:** flecha hacia quien aprueba, y marca en los cargos sin aprobador | Importante | Responde de un vistazo la pregunta que originó el proyecto |
| `RF‑24` | Con un nodo seleccionado, solo se dibujan sus propias relaciones | Obligatorio | Evita que el lienzo se sature. Es la mitigación del riesgo de saturación de `6.6` |
| `RF‑61` | La vista de coordinaciones y la ficha distinguen **par** de **supervisor funcional**: la de supervisión lleva flecha hacia el supervisor, la de par no lleva flecha | Importante | Es lo que Desempeño lee para saber si el contraparte evalúa como par o como jefe |
| `RF‑62` | La capa de coordinaciones se puede **habilitar o deshabilitar por empresa**. Deshabilitada, no aparece ni el conmutador ni el bloque del formulario | Importante | Hay empresas que solo quieren la línea jerárquica; no se les debe cobrar el costo de un campo que no usan |

## 3.4 El filtro por ubicación

| # | Requisito | Prioridad | Cómo se comprueba |
|---|---|---|---|
| `RF‑25` | Los cinco niveles de ubicación son selectores encadenados sobre el lienzo, nunca niveles del árbol | Obligatorio | Elegir una región limita las sucursales que se ofrecen |
| `RF‑26` | Al filtrar, lo que no corresponde se **atenúa**, no se oculta, y el árbol no se reordena | Obligatorio | Ningún cargo queda colgando sin su jefe a la vista |
| `RF‑27` | Un cargo asignado a varias sucursales se resalta al filtrar por cualquiera de ellas, y lo indica cuando no hay filtro | Importante | Muestra `3 sedes` de forma discreta |

## 3.5 Unidades, ubicaciones y puesta en marcha

Un cargo necesita una unidad organizacional para existir (`RF‑32`) y las sedes son selectores encadenados (`RF‑25`). **Las dos cosas hay que poder crearlas**, o una empresa nueva no puede dar el primer paso.

| # | Requisito | Prioridad | Cómo se comprueba |
|---|---|---|---|
| `RF‑63` | Crear, renombrar, mover y desactivar **unidades organizacionales**, hasta cuatro niveles | Obligatorio | Un cliente nuevo llega a tener su árbol de áreas sin ayuda de soporte |
| `RF‑64` | Crear, renombrar, mover y desactivar **ubicaciones**, hasta cinco niveles | Obligatorio | Ídem con empresa, unidad de negocio, región, sucursal y oficina |
| `RF‑65` | Cada empresa declara **cuántos niveles usa** de cada árbol. Los que no usa no aparecen en ningún selector | Obligatorio | Una empresa de una sola sede no ve cinco desplegables vacíos |
| `RF‑66` | Una unidad o una ubicación **con cargos asignados no se elimina**: se desactiva, o se reasignan los cargos primero | Obligatorio | Es la regla 9 de la sección `4`. Mismo criterio que `RF‑43` con los ocupantes |
| `RF‑67` | Mover una unidad **arrastra los cargos que contiene**, e informa cuántos antes de confirmar | Importante | Mismo patrón que `RF‑41`: mostrar el alcance antes, no después |
| `RF‑68` | La puesta en marcha guía en orden —**unidades → ubicaciones → primer cargo**— y deja saltar lo que ya esté resuelto | Obligatorio | Es lo que sostiene el objetivo 5 de `1.5` y el sexto caso de uso de `1.6` |
| `RF‑69` | Desde el alta de cargo se puede **crear una unidad nueva sin abandonar el formulario** | Importante | Descubrir que falta un área a mitad de carga no obliga a perder lo escrito |

> **Por qué esto no estaba y ahora sí.** El submódulo se pensó para clientes que ya tienen su estructura cargada, donde unidades y sedes existen desde antes. Pero el objetivo 5 y el sexto caso de uso hablan de **empresas nuevas**, y ahí el recorrido terminaba en un callejón: la pantalla vacía ofrecía crear el primer cargo, el alta exigía una unidad, y no había forma de crearla. `RF‑63` a `RF‑69` cierran ese hueco.

> **`RF‑69` es el que más ahorra.** Nadie conoce el árbol de áreas completo antes de empezar a cargar cargos; se descubre a mitad de camino. Obligar a salir del formulario para crear un área es exactamente el tipo de fricción que produce el abandono que mide `1.5`.

## 3.6 Alta y edición de cargo

| # | Requisito | Prioridad | Cómo se comprueba |
|---|---|---|---|
| `RF‑28` | El alta tiene cuatro pasos: tipo → identificación → relaciones → perfil | Obligatorio | El cuarto es opcional |
| `RF‑29` | El botón de crear se habilita al terminar el tercer paso | Obligatorio | Un cargo creado sin el cuarto paso es un cargo válido |
| `RF‑30` | El primer paso ofrece cuatro tipos. **Vacante no se puede elegir** | Obligatorio | Vacante se deduce de tener cero ocupantes |
| `RF‑31` | El tipo elegido cambia el resto del formulario | Obligatorio | Outsourcing oculta centro de costo y planilla, y pide motivo de contratación |
| `RF‑32` | Segundo paso: nombre *(obligatorio)*, código, unidad organizacional *(obligatorio)*, máximo de ocupantes *(obligatorio)* y descripción | Obligatorio | Los selectores de unidad se encadenan y saltan los niveles que la empresa no usa |
| `RF‑33` | Tercer paso, obligatorios: `Depende de`, `¿Quién le aprueba los permisos?` y `Centro de costo` | Obligatorio | Son los tres datos que los otros módulos necesitan |
| `RF‑34` | El aprobador se propone igual al jefe, y se puede cambiar | Importante | Reduce los cargos sin aprobador sin imponer una regla falsa |
| `RF‑35` | `Depende de` muestra primero el cargo y al lado quién lo ocupa | Obligatorio | Pedido explícito en la sesión: se elige por cargo, no por persona |
| `RF‑36` | Tercer paso, bloque plegado: `Coordina con` **(varios)**, `Proyecto` y `Cliente`. Cada contraparte se declara como *par* o como *supervisor funcional* | Importante | Plegado por defecto para no cargar el paso obligatorio |
| `RF‑37` | `Aprobador suplente` aparece solo si la empresa lo habilitó | Deseable | |
| `RF‑38` | El formulario valida al momento de declarar, no al guardar | Obligatorio | Cambiar a Colaborador un cargo con subordinados avisa en ese momento |
| `RF‑39` | Un cargo se puede guardar sin jefe declarado, con aviso | Importante | No bloquear la carga por falta de un dato que puede llegar después |

## 3.7 Operar la estructura

| # | Requisito | Prioridad | Cómo se comprueba |
|---|---|---|---|
| `RF‑40` | Un cargo se puede mover arrastrándolo, además de por la acción actual | Importante | Al empezar a arrastrar se marcan los destinos válidos |
| `RF‑41` | Antes de confirmar, el sistema informa cuántos cargos y personas se mueven y cuántos aprobadores cambian | Obligatorio | El aviso también advierte que la relación anterior se cierra con fecha |
| `RF‑42` | Un destino inválido se marca durante el arrastre, con el motivo | Obligatorio | Cubre las reglas 1, 2 y 6 de la sección `4`, y los círculos |
| `RF‑43` | No se puede eliminar un cargo con gente adentro; se indica quién lo ocupa | Obligatorio | Ofrece ir directo al ocupante |
| `RF‑44` | Al eliminar un cargo con gente debajo, hay que decidir si se eliminan o suben un nivel | Obligatorio | La decisión se toma en el diálogo, no por defecto |
| `RF‑45` | La ficha tiene pestaña de historial: qué cambió, cuándo, quién y qué relación se cerró | Obligatorio | Es el insumo de auditoría |
| `RF‑46` | Al asignar el primer ocupante a un cargo vacante, se ofrece cerrar la requisición | Deseable | Depende de la integración con Reclutamiento — ver `2.6` |
| `RF‑47` | Cuando se va el último ocupante, el cargo pasa a vacante y se ofrece crear la requisición | Importante | |

## 3.8 Panel de estructura

| # | Requisito | Prioridad | Cómo se comprueba |
|---|---|---|---|
| `RF‑48` | Total de cargos y de personas | Obligatorio | `41 cargos · 38 personas` |
| `RF‑49` | Contador por tipo de cargo; cada línea filtra el lienzo | Obligatorio | Es el insumo directo del reporte que RR.HH. presenta a gerencia |
| `RF‑50` | Lista de vacantes con enlace a crear la requisición | Obligatorio | |
| `RF‑51` | Lista **"Sin declarar"**: cargos sin jefe, sin aprobador o sin centro de costo | Obligatorio | Es la lista de trabajo que sostiene los dos primeros objetivos de `1.5` |
| `RF‑52` | Distribución por región y sucursal | Deseable | |

## 3.9 Exportación

| # | Requisito | Prioridad | Cómo se comprueba |
|---|---|---|---|
| `RF‑53` | Exportar a **PDF apaisado**, paginado por unidad cuando no entra en una hoja, con índice | Obligatorio | La especialista presenta esto a gerencia |
| `RF‑54` | Exportar a **PNG** en la resolución del lienzo, con fondo transparente opcional | Importante | Para pegar en una diapositiva |
| `RF‑55` | Exportar a **CSV o Excel**: un cargo por fila, con las relaciones en columnas | Importante | Reporte de estructura |
| `RF‑56` | Toda exportación refleja **la vista y el filtro activos** e incluye leyenda, empresa, fecha y filtro | Obligatorio | Sin leyenda, un organigrama impreso no se puede leer |

## 3.10 Registro, carga y error

| # | Requisito | Prioridad | Cómo se comprueba |
|---|---|---|---|
| `RF‑57` | El submódulo registra los eventos necesarios para medir los objetivos | Obligatorio | Alta iniciada, completada y abandonada; cambio de vista; exportación; movimiento |
| `RF‑58` | Las pantallas vacías explican qué pasa y ofrecen qué hacer | Obligatorio | "Empresa sin estructura" ofrece crear el primer cargo o importar |
| `RF‑59` | Mientras carga se dibuja el esqueleto del árbol, no un indicador genérico | Deseable | |
| `RF‑60` | Si falla el guardado, el cambio no se pierde y se ofrece reintentar | Obligatorio | |

## 3.11 Sistema visual

### Qué tiene que cumplir

| Condición | Cómo se verifica |
|---|---|
| Se distingue en color | Contraste de 3:1 entre categorías vecinas |
| Se distingue en escala de grises | Fotocopia y proyector desteñido |
| Se distingue con daltonismo | Las tres variantes: deuteranopía, protanopía, tritanopía |
| Se lee al 50 % de zoom | Los trazos no se funden entre sí |
| Se lee a tres metros de un proyector | Grosor mínimo de 1.5 px |

### Colores

| Uso | Color | Señal que lo acompaña |
|---|---|---|
| Línea de mando y cargo base | `#23408E` | Trazo continuo |
| Coordinación | `#0F6E6C` | Trazo punteado con flecha |
| Aprobación de permisos | `#6B3FA0` | Trazo continuo fino con flecha |
| Staff | `#5A6B7C` | Punteado lateral y esquina cortada |
| Outsourcing | `#B8501B` | Borde punteado |
| Vacante | `#8E969C` | Borde discontinuo, sin relleno |
| Sin declarar | `#B0740A` | Ícono de aviso |

El naranja del personal de Outsourcing es el que propuso la especialista en la sesión. Se conserva tal cual.

### La paleta corporativa de Souly HR

| Color | Hex | Contraste sobre blanco | ¿Puede cargar significado en el lienzo? |
|---|---|---|---|
| Blanco | `#FFFFFF` | — | Es el fondo |
| **Azul uniform** *(principal)* | `#0C2D40` | 14.3:1 | **Sí** — texto, líneas y bordes |
| **Verde primavera** *(secundario)* | `#00E091` | **1.7:1** | **No sobre blanco.** Sí como relleno o texto sobre el azul, donde llega a 8.2:1 |
| **Neo Mint** *(apoyo)* | `#9FFFD8` | **1.2:1** | **No.** Solo como fondo, con texto oscuro encima |
| **Negro** *(apoyo)* | `#000000` | 21:1 | Sí |

> **De los cinco colores de marca, solo dos superan el mínimo de 3:1 que exige `RNF‑06` para líneas y bordes:** el azul uniform y el negro. Con la paleta corporativa sola **no se pueden codificar cinco codificaciones de cargo ni cuatro trazos de relación** — no hay colores distinguibles suficientes.
>
> Esto no invalida la marca, la ubica. El azul uniform es el color natural de la línea de mando y del nodo base. El verde primavera funciona como acento sobre fondo oscuro —cabeceras, botones, estados activos— pero **no como trazo sobre el lienzo blanco**: a 1.7:1 desaparece al imprimir y es invisible para buena parte de los casos de daltonismo. Los demás colores del sistema tienen que venir de fuera de la paleta de marca.
>
> **Ésta es la respuesta a la pregunta abierta del 12 de agosto.** La paleta corporativa no reemplaza al sistema visual del organigrama: lo enmarca. La decisión que hay que tomar no es "corporativa o propia", sino confirmar que el azul uniform pasa a ser el color estructural y que los otros seis se mantienen como están.

### Cómo se distingue cada tipo de cargo

| Tipo | Color | Forma | Borde | Ícono |
|---|---|---|---|---|
| **Colaborador** | Azul | Rectángulo redondeado | Continuo 1 px | 👤 |
| **Jefe / Director** | Azul | Rectángulo con barra superior de 4 px | Continuo 2 px | ⭐ |
| **Staff** | Gris azulado | Esquina superior izquierda cortada | Continuo 1.5 px | 🎯 |
| **Outsourcing** | Naranja | Rectángulo redondeado | **Punteado** 2 px | 🤝 |
| **Vacante** | Gris | Rectángulo **sin relleno** | **Discontinuo** 2 px | ⬜ |

**Tres señales, no una.** Cada tipo lleva color, forma e ícono. Con eso el organigrama sobrevive a una fotocopia, a un proyector desteñido y a un revisor con daltonismo. Si el color fuera la única señal, el documento impreso que se lleva a gerencia sería ilegible justo cuando más importa. Es el principio 3 de `1.4`.

**Cómo se verificó**

| Prueba | Resultado |
|---|---|
| Escala de grises | Las cinco codificaciones se distinguen por el borde: fino, grueso con barra, esquina cortada, punteado, discontinuo |
| Daltonismo | El par crítico es coordinación / Outsourcing. Se separan porque uno es una **línea** y el otro un **borde de nodo**: nunca compiten en el mismo elemento |
| Proyector | Grosor mínimo 1.5 px, contraste 4.5:1 sobre blanco |

**Para Diseño.** Los colores se pueden reemplazar por los corporativos siempre que se conserven el contraste mínimo, la separación de los trazos y la redundancia de forma más color. Lo único no negociable es que ningún tipo se distinga **solo** por color.

## 3.12 Cómo se escriben los textos

| Regla | Ejemplo |
|---|---|
| Llamar las cosas como las llama el usuario | "Jefe directo", no "nodo padre" |
| El error dice qué pasó y cómo se arregla | "Tiene una persona adentro. Reasignala antes de eliminar" |
| Las consecuencias se cuentan antes, no después | "Se mueven 3 cargos y 3 personas" |
| El botón dice lo que hace | "Mover cargo", no "Aceptar" |
| Nada de vocabulario de base de datos | "Coordina con", no "relación de tipo funcional" |

La tabla de cómo se nombra cada relación según dónde aparezca está en `0.7`.

## 3.13 Requisitos no funcionales

### Rendimiento y escalabilidad

| # | Requisito | Prioridad | Cómo se comprueba |
|---|---|---|---|
| `RNF‑01` | Una estructura de 200 cargos se dibuja en un segundo y medio o menos | Obligatorio | Medición con datos de prueba |
| `RNF‑02` | Zoom y desplazamiento fluidos hasta 400 cargos | Obligatorio | Sin trabas perceptibles |
| `RNF‑03` | Por encima de 400 cargos se entra ya filtrado por unidad, y el panorama se dibuja sin texto | Importante | |
| `RNF‑15` | Varias personas de la misma empresa pueden editar la estructura a la vez sin pisarse | Importante | Si dos usuarios mueven el mismo cargo, el segundo recibe aviso de conflicto y no pierde su cambio |

### Seguridad y privacidad

Un organigrama completo es información sensible de la empresa: revela la estructura de mando, los puestos vacíos y quién depende de quién.

| # | Requisito | Prioridad | Cómo se comprueba |
|---|---|---|---|
| `RNF‑13` | Un colaborador ve la estructura pero no la edita | Obligatorio | Permisos por rol, verificados en el servidor y no solo en la interfaz |
| `RNF‑16` | Una empresa nunca ve la estructura de otra | Obligatorio | Aislamiento verificado con pruebas explícitas entre empresas |
| `RNF‑17` | El jefe de área solo puede editar los cargos de su propia rama | Obligatorio | Un intento fuera de su rama se rechaza en el servidor |
| `RNF‑18` | Todo cambio de estructura queda registrado con qué cambió, quién y cuándo, y ese registro no se puede editar ni borrar | Obligatorio | Es lo que hace auditable la regla 8 |
| `RNF‑19` | Las exportaciones quedan registradas: quién exportó, cuándo y con qué filtro | Importante | Un PDF con toda la estructura sale de la plataforma; tiene que quedar rastro |
| `RNF‑20` | El organigrama muestra el dato mínimo: nombre del ocupante y cargo. Nunca salario, documento de identidad ni datos de contacto privados | Obligatorio | Revisión de cada campo expuesto en nodo, ficha y exportaciones |
| `RNF‑21` | Los datos viajan cifrados y se almacenan según el estándar vigente de la plataforma | Obligatorio | Igual que el resto de Trabajito. Sin excepciones para este submódulo |
| `RNF‑22` | Cuando una persona ejerce su derecho a que se borren sus datos, el histórico conserva el cargo y las fechas, y sustituye la identidad por una referencia anónima | Obligatorio | La estructura pasada se sigue pudiendo reconstruir sin conservar datos personales |

> **Pendiente para Legal.** `RNF‑22` está redactado sobre el principio general de minimizar datos personales conservando la trazabilidad. **Qué normativa de protección de datos aplica a cada cliente es una pregunta abierta** (ver `6.7`): la respuesta puede cambiar los plazos de retención y hay que confirmarla antes de cerrar la primera etapa.

### Compatibilidad y accesibilidad

| # | Requisito | Prioridad | Cómo se comprueba |
|---|---|---|---|
| `RNF‑04` | El árbol tiene una **alternativa en lista anidada**, navegable por lector de pantalla | Obligatorio | Un árbol dibujado no se puede recorrer de otra manera. Es la misma vista del celular |
| `RNF‑05` | Se opera entero con el teclado: `Tab` en orden jerárquico, flechas entre hermanos y niveles, `Enter` abre la ficha, `Esc` sale | Obligatorio | Recorrido completo sin usar el ratón |
| `RNF‑06` | Contraste de 4.5:1 en textos y 3:1 en bordes y líneas | Obligatorio | Norma WCAG 2.1 nivel AA |
| `RNF‑07` | **Ningún significado depende solo del color** | Obligatorio | Verificado en escala de grises y con simulación de los tres tipos de daltonismo |
| `RNF‑08` | Escritorio completo, tablet con panel plegado, celular en solo lectura —tanto en el navegador como en la app | Obligatorio | |
| `RNF‑23` | **La app de Souly HR incorpora la vista de consulta del organigrama**: la lista anidada de `RNF‑04`, en solo lectura | Obligatorio | Es donde el colaborador va a entrar de verdad. Sin esto, la respuesta móvil del submódulo queda en una superficie que casi nadie abre |
| `RNF‑24` | La app y la web **leen la misma fuente**. Un cambio en la estructura se ve en las dos sin sincronización manual ni copia | Obligatorio | Un organigrama que dice dos cosas distintas según el dispositivo deja de ser fuente de verdad |
| `RNF‑09` | El foco del teclado se ve sobre cualquier fondo | Obligatorio | Anillo de 2 px con separación |
| `RNF‑10` | Con el navegador al 200 % no se pierde ninguna función | Obligatorio | |
| `RNF‑11` | Las animaciones respetan la preferencia de movimiento reducido del sistema | Importante | |
| `RNF‑12` | Los controles del lienzo se pueden tocar cómodamente: 44 px mínimo | Obligatorio | |
| `RNF‑14` | Las líneas tienen 1.5 px como mínimo y se leen a tres metros de un proyector | Obligatorio | |

**Navegadores y dispositivos soportados:** las dos últimas versiones de Chrome, Edge, Firefox y Safari. En móvil, Chrome en Android y Safari en iOS, en solo lectura. Es el mismo estándar del resto de Trabajito; si esa política cambia, cambia acá también.

**Y la app.** Souly HR ya tiene aplicación móvil publicada. El organigrama entra ahí como **vista de consulta en solo lectura** (`RNF‑23`), con la misma lista anidada que sirve al lector de pantalla y a la web móvil. No se construye una app propia del organigrama: se suma una vista a la que ya existe, lo que hace que el equipo que la mantiene sea una dependencia del proyecto (ver `6.4`).

---

# 4 · Reglas de negocio

No son preferencias de diseño: son las condiciones que hacen que la estructura sea confiable. El sistema las valida siempre, y avisa **en el momento de declarar**, no al guardar (`RF‑38`).

| # | Regla | Dónde se implementa |
|---|---|---|
| 1 | **Un colaborador no tiene personal a cargo.** Si tiene subordinados, no es un colaborador | `RF‑38` · `RF‑42` |
| 2 | **Un cargo Staff no tiene línea descendente.** Asiste a alguien; no manda sobre nadie | `RF‑21` · `RF‑31` · `RF‑42` |
| 3 | **Un cargo de Outsourcing no genera planilla, salarios ni asistencia.** Está en la estructura, no en la nómina | `RF‑31` |
| 4 | **Un cargo activo sin ocupantes está vacante.** Se deduce, no se marca a mano | `RF‑14` · `RF‑47` · `RF‑50` |
| 5 | **Un cargo no admite más ocupantes que su máximo declarado** | `RF‑38` |
| 6 | **Cada cargo depende de un jefe y de uno solo.** Los "reporta a dos" son un jefe más coordinaciones | `RF‑21` · `RF‑33` · `RF‑42` |
| 7 | **Un cargo con gente adentro no se elimina.** Primero se reasigna a quien lo ocupa | `RF‑43` |
| 8 | **Cambiar la estructura no borra la anterior.** Toda relación se cierra con fecha y el pasado se puede reconstruir | `RF‑41` · `RF‑45` |
| 9 | **Una unidad o una ubicación con cargos asignados no se elimina.** Se desactiva, o se reasignan los cargos primero | `RF‑66` |

**Dónde se valida cada una.** Las reglas 1, 2 y 6 se validan al mover un cargo y al cambiarle el tipo. La 3 se valida en el formulario de alta y del lado de Planillas. La 4 la deduce el sistema y nadie la puede contradecir. La 5 se valida cuando Gestión de Personas asigna un ocupante. La 7, la 8 y la 9 se validan al eliminar y al mover.

> **La regla 8 es la que sostiene la auditoría.** Nada se borra: las relaciones se cierran con fecha de fin y las nuevas abren con fecha de inicio. Es lo que hace que la pregunta "¿cómo estaba la estructura en marzo?" tenga respuesta, y es la base del modelo de vigencias de `5.5`. `RNF‑18` completa la regla del lado de seguridad: ese registro no se puede editar ni borrar.

**Reglas de permisos**

| Rol | Puede |
|---|---|
| Colaborador | Consultar la estructura y las fichas. Nada más |
| Jefe de área | Lo anterior, más editar las relaciones de los cargos de su rama |
| RR.HH. | Todo dentro de su empresa: crear, editar, mover, eliminar, exportar |
| Auditoría | Consultar la estructura y el historial, incluso a fechas pasadas. No edita |

Los tres requisitos que hacen cumplir esta tabla del lado del servidor —y no solo escondiendo botones— son `RNF‑13`, `RNF‑16` y `RNF‑17`.

---

# 5 · Modelo de datos

Esta sección es para desarrollo. Describe **qué se guarda, qué se deduce y qué se expone**; no prescribe motor de base de datos ni nombres de tabla definitivos.

Todo lo que sigue es consecuencia del principio 1 de `1.4`: **el cargo es la unidad, no la persona.**

## 5.1 Las entidades

```
   ┌──────────────┐
   │   EMPRESA    │  el aislamiento vive acá — RNF‑16
   └──────┬───────┘
          │ 1..n
   ┌──────┴───────────────────────────────────────────┐
   │                                                  │
┌──▼─────────────────┐                      ┌─────────▼──────────┐
│ UNIDAD ORGANIZAC.  │                      │     UBICACIÓN      │
│ Área → Subárea →   │                      │ Empresa → U.negocio│
│ Depto. → Equipo    │                      │ → Región → Sucursal│
│                    │                      │ → Oficina          │
│  FORMA EL ÁRBOL    │                      │   SOLO FILTRA      │
└──┬─────────────────┘                      └─────────┬──────────┘
   │ 1..n                                             │ n..n
   │                ┌──────────────┐                  │
   └───────────────▶│    CARGO     │◀─────────────────┘
                    │              │
                    │ tipo         │
                    │ máx. ocup.   │
                    │ centro costo │
                    └──┬────────┬──┘
                       │ 1..n   │ n..n  (cargo → cargo)
              ┌────────▼───┐ ┌──▼────────────────────┐
              │  OCUPANTE  │ │      RELACIÓN         │
              │            │ │                       │
              │ persona_id │ │ tipo   · calidad      │
              │ desde/hasta│ │ desde  · hasta        │
              └────────────┘ └───────────────────────┘
                    │
                    ▼
             PERSONA (vive en Gestión de Personas,
                      el organigrama solo la referencia)
```

| Entidad | Qué representa | Nota |
|---|---|---|
| **Empresa** | El cliente. Es la frontera de aislamiento | Toda consulta lleva empresa. `RNF‑16` |
| **Unidad organizacional** | El área. Jerárquica, hasta 4 niveles | Es lo que forma el árbol |
| **Ubicación** | La sede. Jerárquica, hasta 5 niveles | **Nunca** forma el árbol. `RF‑25` |
| **Cargo** | La posición de trabajo | La unidad del modelo |
| **Ocupante** | Que una persona ocupa un cargo, entre dos fechas | Un cargo admite varios |
| **Relación** | Un vínculo entre dos cargos, entre dos fechas | Las cuatro de `0.6` viven en una sola tabla |
| **Persona** | El colaborador | **No es de este submódulo.** Se referencia, no se duplica |

## 5.2 El cargo

| Campo | Tipo | Obligatorio | De dónde sale |
|---|---|---|---|
| `empresa` | referencia | Sí | Contexto de sesión |
| `nombre` | texto | Sí | `RF‑32`, paso 2 del alta |
| `codigo` | texto | No | `RF‑32` |
| `tipo` | `colaborador` · `jefatura` · `staff` · `outsourcing` | Sí | `RF‑30`, paso 1 |
| `unidad_organizacional` | referencia | Sí | `RF‑32` |
| `maximo_ocupantes` | entero ≥ 1 | Sí | `RF‑32`. Sostiene la regla 5 |
| `descripcion` | texto | No | `RF‑32` |
| `centro_costo` | referencia | Sí *(salvo Outsourcing)* | `RF‑33`. Lo consume Planillas — `2.7` |
| `motivo_contratacion` | texto | Solo Outsourcing | `RF‑31` |
| `perfil` | rango salarial, requisitos, competencias | No | Paso 4, opcional — `RF‑29` |
| `estado` | `activo` · `inactivo` | Sí | Un cargo eliminado no se borra: se inactiva |

**Ubicaciones del cargo.** Un cargo se asocia a **una o varias** ubicaciones. Es una relación n..n a propósito: es lo que permite que una gerencia responsable de dos regiones sea **un solo cargo** con el indicador `2 sedes` (`RF‑27`) en vez de dos cuadros duplicados.

> **Ese punto está sin validar y es un riesgo abierto.** La especialista hoy replica el cargo a mano por sucursal. El modelo soporta las dos formas —un cargo con dos ubicaciones, o dos cargos distintos— y la elección la hace quien conoce la organización, no el sistema. Ver el riesgo en `6.6` y la pregunta en `6.7`.

## 5.3 Lo que se guarda y lo que se deduce

Es la distinción que más consecuencias tiene en este modelo.

| Dato | ¿Se guarda? | Cómo se obtiene |
|---|---|---|
| Tipo de cargo | **Sí** | Lo declara el usuario en el paso 1 |
| **Vacante** | **No** | Se deduce: cargo activo con cero ocupantes vigentes. Regla 4 |
| Ocupación `2/4` | **No** | Se cuenta: ocupantes vigentes sobre `maximo_ocupantes` |
| Jefe | **Sí** | Relación `estructural` vigente |
| Subordinados | **No** | Se consultan: las relaciones `estructural` que apuntan a este cargo |
| Aprobador | **Sí** | Relación `aprobacion` vigente. **No se deduce del jefe** |
| "Sin declarar" | **No** | Se deduce: sin jefe, sin aprobador o sin centro de costo. `RF‑51` |

> **Vacante no se guarda a propósito.** Si fuera un campo, alguien tendría que mantenerlo, y una lista de vacantes desactualizada es peor que no tenerla — Reclutamiento abriría requisiciones para puestos ya cubiertos. Deducirlo la mantiene correcta sin que nadie haga nada. Es también la razón por la que Vacante no aparece como opción en el alta (`RF‑30`).

## 5.4 La tabla de relaciones

**Es la pieza crítica del proyecto.** Sin ella no hay submódulo — no es que falten funciones.

| Campo | Valores | Nota |
|---|---|---|
| `empresa` | referencia | `RNF‑16` |
| `cargo_origen` | referencia a cargo | El cargo que declara |
| `cargo_destino` | referencia a cargo | La contraparte |
| `tipo` | `estructural` · `funcional` · `aprobacion` · `asistencia` | Las cuatro relaciones de `0.6` |
| `calidad` | `par` · `supervisor_funcional` | **Solo si `tipo = funcional`.** Es lo que lee Desempeño — `RF‑61` |
| `es_suplente` | sí / no | Solo si `tipo = aprobacion`. `RF‑37` |
| `desde` | fecha | Cuándo empezó a regir |
| `hasta` | fecha o vacío | Vacío = vigente. Regla 8 |

**Las cuatro relaciones en una sola tabla, no en cuatro.** Comparten forma —dos cargos, una vigencia— y la consulta que más se usa es "dame todas las relaciones de este cargo", que con cuatro tablas son cuatro consultas y una unión.

**Reglas de integridad que el modelo tiene que garantizar:**

| # | Regla del modelo | De dónde viene |
|---|---|---|
| 1 | Un cargo tiene **como máximo una** relación `estructural` vigente como origen | Regla 6 · `RF‑33` |
| 2 | Un cargo tiene **como máximo una** relación `aprobacion` vigente no suplente | `RF‑33` · `RF‑34` |
| 3 | Las relaciones `estructural` **no pueden formar un ciclo** | `RF‑42` |
| 4 | `calidad` es obligatorio si `tipo = funcional`, y vacío en cualquier otro caso | `RF‑36` · `RF‑61` |
| 5 | Un cargo `colaborador` o `staff` no puede ser destino de una relación `estructural` | Reglas 1 y 2 |
| 6 | Los dos cargos de una relación pertenecen a la **misma empresa** | `RNF‑16` |
| 7 | Una unidad organizacional **no puede ser su propio ancestro**. Lo mismo para las ubicaciones | `RF‑63`, `RF‑64` |

> **Por qué la calidad entra ahora y no después.** Vive en la misma tabla que la relación. Agregarla más adelante no es sumar una columna: es migrar todas las coordinaciones ya cargadas sin saber cuál era par y cuál supervisor, o sea perder el dato y volver a pedirlo. El costo de incluirla hoy es una columna; el de postergarla es una migración con pérdida.

## 5.5 Vigencia: cómo se reconstruye el pasado

**Nada se borra. Las relaciones se cierran.** Cuando un cargo cambia de jefe, la relación anterior recibe `hasta` con la fecha del cambio y se crea una nueva con `desde`. Es la regla 8, y es lo que hace que la estructura de cualquier fecha pasada sea reconstruible.

```
  Cargo: ANALISTA CONTABLE

  relación estructural → GERENTE ADMINISTRATIVO
  ├── desde 01‑02‑2025   hasta 14‑03‑2026     ← cerrada
  │
  relación estructural → GERENTE DE FINANZAS
  └── desde 15‑03‑2026   hasta —              ← vigente

  «¿De quién dependía en enero de 2026?»
     → la relación cuya vigencia contiene esa fecha → Gerente Administrativo
```

| Qué se pregunta | Cómo se responde |
|---|---|
| ¿Cuál es la estructura hoy | Relaciones con `hasta` vacío |
| ¿Cómo estaba en una fecha | Relaciones cuya vigencia contiene esa fecha |
| Qué cambió y quién lo cambió | El registro de cambios de `RNF‑18`, que es inmutable |

**Lo que entra en la primera etapa es el dato, no la pantalla.** El modelo guarda vigencias desde el día uno; navegar el árbol de una fecha pasada está fuera de esta versión (`1.7`). Esto no es un rodeo: si el dato no se guardara desde el principio, la pantalla futura no tendría historia que mostrar y habría que empezar a contar desde cero.

**Y es lo que hace posible `RNF‑22`.** Cuando una persona pide que se borren sus datos, se sustituye su identidad por una referencia anónima: el cargo, las fechas y la forma de la estructura se conservan; el nombre no. La estructura pasada se sigue pudiendo reconstruir sin conservar datos personales.

## 5.6 Lo que cada empresa configura

No todas las empresas usan lo mismo. Estas opciones son por empresa, no globales.

| Opción | Efecto | Requisito |
|---|---|---|
| **Capa funcional activa** | Si está apagada, no aparecen ni la vista de coordinaciones ni el bloque del formulario | `RF‑62` |
| **Aprobador suplente** | Si está apagada, el campo no se ofrece | `RF‑37` |
| **Niveles de unidad organizacional en uso** | Los niveles que la empresa no usa se saltan en los selectores | `RF‑32`, `RF‑65` |
| **Niveles de ubicación en uso** | Ídem, para el filtro | `RF‑25`, `RF‑65` |

> **Apagar es más honesto que dejar vacío.** Para una empresa que trabaja solo con línea jerárquica, el bloque de coordinaciones es un campo más que nadie completa y una vista que nadie abre.

---

# 6 · Roadmap

## 6.1 El camino hasta desarrollo

**Este documento no va a desarrollo. Lo que recibe desarrollo es el prototipo.**

```
    PRD              Prototipo          Validación         Correcciones        Desarrollo
     ●───────────────────●──────────────────●──────────────────●────────────────────●
  Naihara e           Diseño UX         Fabiola y quien     Diseño UX         Recibe el
  Israel             12 pantallas       corresponda                          prototipo
  aprueban            en alta           aprueban                             aprobado
                      fidelidad
```

Este PRD existe para que el prototipo se construya sobre decisiones acordadas, y para poder rastrear después por qué cada pantalla es como es. Pero **lo que se construye es lo que está en el prototipo**: si un requisito de este documento no llegó a la maqueta, no se va a desarrollar.

| Fase | Qué pasa | Quién | Cuándo |
|---|---|---|---|
| **PRD** | Este documento: decisiones, reglas y requisitos | Diseño UX | En revisión |
| **Prototipo** | Las doce pantallas de `8.1` en alta fidelidad y navegables | Diseño UX | Arranca cuando la paleta esté aprobada — 12 de agosto |
| **Validación** | Se recorre el prototipo con la especialista de dominio y con quien corresponda según la pantalla | Fabiola Gutiérrez + Diseño UX | Por definir |
| **Correcciones** | Se ajusta el prototipo con lo que salga de la validación | Diseño UX | Por definir |
| **Entrega a desarrollo** | Se pasa el prototipo aprobado | Diseño UX → Desarrollo | Por definir |
| **Desarrollo, pruebas y lanzamiento** | Por etapas, según `6.2`. Incluye pruebas funcionales, de accesibilidad, de rendimiento con 200 y 400 cargos, y de aislamiento entre empresas | Desarrollo + QA | Por definir con Proyecto |

> **Quién aprueba qué.** Naihara Rocha e Israel Chávez aprueban **este documento**: las reglas, los nombres y la viabilidad. Fabiola Gutiérrez aprueba **el prototipo**, no el PRD — su validación es sobre pantallas, no sobre requisitos escritos. Es la razón por la que la maquetación en alta fidelidad no puede empezar antes de cerrar la paleta.

> **Las fechas de desarrollo están sin definir a propósito.** No se pueden estimar antes de saber cuándo se entrega el prototipo. Las únicas fechas firmes hoy son las de las preguntas abiertas de `6.7`.

## 6.2 Las tres entregas

Las tres etapas ordenan **qué se construye primero**, no cuándo. El prototipo se maqueta completo; el corte por etapas es para desarrollo.

| Etapa | Qué incluye | Cuándo se considera lista |
|---|---|---|
| **1 · Estructura utilizable** | `RF‑01`, `02`, `04`, `09`, `12`–`21`, `24`, `28`–`36`, `38`–`39`, `41`–`45`, `48`–`51`, `53`, `56`–`58`, `60`, `63`–`66`, `68`–`69` · `RNF‑01`–`02`, `04`–`10`, `12`–`14`, `16`–`18`, `20`–`22` | Una empresa que empieza de cero llega sola a tener su estructura completa con jefe y aprobador, y exportarla |
| **2 · Relaciones completas** | `RF‑03`, `05`, `07`, `10`, `22`, `23`, `25`–`27`, `40`, `47`, `52`, `54`, `55`, `61`, `62`, `67` · `RNF‑15`, `19`, `23`–`24` | Las tres vistas funcionando, el filtro por sede y la consulta desde la app |
| **3 · Escala y comodidad** | `RF‑06`, `08`, `11`, `37`, `46`, `59` · `RNF‑03`, `11` | Estructuras de más de 400 cargos y decisiones pendientes cerradas |
| **Fuera de esta versión** | Navegar el árbol de una fecha pasada · Editar desde el celular · Alta masiva · Deshacer varios pasos | Registrado para más adelante |

**Por qué el corte de la primera etapa está donde está.** No es por dificultad, es por utilidad: es exactamente lo que los otros módulos necesitan para leer la estructura completa. Las vistas de coordinaciones y aprobaciones son valiosas pero no bloquean a nadie — los datos se cargan igual en la primera etapa y se dibujan en la segunda.

**Qué se desbloquea en cada etapa**, leído desde `2`:

| Etapa | Módulos que pasan a funcionar |
|---|---|
| **1** | Gestión de Personas y Planillas reciben cargo, aprobador y centro de costo declarados. Reclutamiento recibe las vacantes |
| **2** | Desempeño recibe las coordinaciones con su calidad. Asistencia recibe la vista de aprobaciones |
| **3** | Nada nuevo se desbloquea: es comodidad y escala |

## 6.3 Hitos de control

Cada hito es una puerta: no se pasa al siguiente sin cerrar el anterior.

| Hito | Qué tiene que estar cerrado para pasar | Cuándo |
|---|---|---|
| **PRD aprobado** | Naihara e Israel firman reglas, nombres y viabilidad | Por definir |
| **Paleta aprobada** | Validada **proyectada e impresa**, no en pantalla | 12 de agosto |
| **Alcance de la primera etapa congelado** | Respondidas todas las preguntas abiertas que la bloquean | 22 de agosto |
| **Prototipo terminado** | Las doce pantallas de `8.1`, navegables, con los estados de cada nodo | Por definir |
| **Prototipo validado** | Fabiola lo recorre y aprueba; las correcciones ya están aplicadas | Por definir |
| **Entrega a desarrollo** | El prototipo aprobado cubre todo lo obligatorio de la primera etapa | Por definir |
| **Piloto con un cliente** | Estructura completa cargada por su propia RR.HH. | Por definir |

## 6.4 Dependencias

| Qué hace falta | De quién | Sin eso no hay | Estado |
|---|---|---|---|
| Una tabla de relaciones entre cargos, con **tipo, calidad y vigencia** | Backend | `RF‑19` a `RF‑24`, `RF‑33`, `RF‑36`, `RF‑61`. **Sin esto no hay submódulo — no es que falten funciones.** El detalle está en `5.4` | Por confirmar |
| Parametrización de centro de costo desde Planillas | Planillas | `RF‑33` — ver `2.7` | Ya existe |
| Requisición en Reclutamiento | Reclutamiento | `RF‑46`, `RF‑50` — ver `2.6` | Por confirmar |
| Confirmación de la paleta corporativa | Diseño | `RF‑13` y todo el sistema visual de `3.11` | Pendiente — bloquea la maquetación |
| El motor de dibujo actual del lienzo | Proyecto | `RF‑01` a `RF‑11` | Por confirmar |
| **Espacio en la app de Souly HR para la vista del organigrama** | Equipo de la app | `RNF‑23`, `RNF‑24`. Sin esto, la respuesta móvil del submódulo queda solo en el navegador, que es donde el colaborador no entra | Por confirmar |
| Criterio de retención de datos personales | Legal | `RNF‑22` | Por consultar |

## 6.5 Suposiciones

Cada una dice quién la valida y qué pasa si resulta falsa. Un supuesto sin consecuencia declarada es una nota al pie.

| Suposición | Valida | Si es falsa |
|---|---|---|
| El lienzo actual se conserva y se extiende; no se reconstruye | Israel | El esfuerzo de la primera etapa crece bastante y hay que replanificar |
| El tamaño habitual está entre 20 y 200 cargos | Fabiola | El comportamiento por encima de 400 cargos pasa a obligatorio y entra en la primera etapa |
| Se opera desde el escritorio; en el celular y en la app se lee, no se edita | Producto | Hay que rediseñar la versión móvil y la vista de la app, y aparecen requisitos de edición táctil |
| La exportación es requisito de negocio, no una mejora | Fabiola | La exportación a PDF baja de obligatoria y sale de la primera etapa |
| Las pantallas nuevas se construyen sobre los componentes que ya existen | Israel | Se suma trabajo de componentes nuevos a las tres etapas |
| Los usuarios tienen conexión estable durante la edición | Proyecto | Hace falta guardado parcial y recuperación de borradores, que hoy no están en el alcance |

## 6.6 Riesgos

| Riesgo | Probabilidad | Impacto | Qué hacemos | Quién |
|---|---|---|---|---|
| El lienzo se satura por encima de 60 cargos con relaciones dibujadas | Alta | Alto | Dibujar solo las relaciones del cargo seleccionado (`RF‑24`), niveles de detalle y plegado. Prototipar con datos reales antes de la segunda etapa | Diseño |
| La tabla de relaciones no llega a tiempo | Baja | **Crítico** | Sin ella no hay submódulo. Confirmar en la planificación de la primera etapa. Ver `5.4` | Israel |
| El alta de dieciséis campos genera abandono | Media | Alto | Cuatro pasos, salida temprana y bloque plegable. Se mide, y se prueba con dos usuarias antes de la primera etapa | Diseño |
| La vista de aprobaciones suma esfuerzo no previsto | Media | Medio | Decisión de Producto antes de planificar la segunda etapa. Sin ella, el dato se carga y no se puede leer | Producto |
| Hay clientes con más de 400 cargos y no está medido | Media | Medio | Consultar la base de clientes actual antes de cerrar la primera etapa | Israel |
| La paleta corporativa no cumple los contrastes | Media | Medio | La redundancia de forma e ícono sostiene el sistema aunque cambien los colores | Diseño |
| Los íconos emoji se ven distinto en cada sistema operativo y no se controlan al imprimir | Alta | Bajo | Definir un set propio antes de maquetar | Diseño |
| **El nodo único de multi‑sede le cambia el método a quien hoy arma los organigramas.** La especialista replica a mano el mismo cargo en cada sucursal para no perder control; el sistema propone un nodo con indicador de sedes | Media | Alto | Mostrarle las dos formas sobre su propia estructura antes de cerrar la primera etapa. Si el nodo único no le sirve, el filtro por sede se rediseña | Diseño |

## 6.7 Preguntas abiertas

| Pregunta | Bloquea | Quién responde | Fecha propuesta |
|---|---|---|---|
| ¿La paleta se aprueba tal cual o se ajusta a la corporativa? | La maquetación en alta fidelidad | Diseño + Fabiola | 12 de agosto |
| ¿Íconos emoji o un set propio? | La maquetación | Diseño | 15 de agosto |
| ¿La importación desde Excel entra en esta versión? | Primera etapa | Producto + Israel | 15 de agosto |
| ¿Cuál es la estructura más grande entre los clientes actuales? | El comportamiento a gran escala | Israel | 15 de agosto |
| **¿El tipo de cargo `Colaborador` se renombra?** Choca con la palabra que la plataforma usa para todo empleado | El contenido de la primera etapa | Naihara + Fabiola | 15 de agosto |
| ¿Cuáles son los cuatro niveles de unidad organizacional? El ejemplo de la sesión termina en Departamento, no en Equipo | `RF‑32`, el alta de cargo | Naihara + Fabiola | 15 de agosto |
| ¿Comunicación usa el organigrama? Si lo usa, ¿qué lee de él? | El alcance de la primera etapa — ver `2.8` | Producto | 15 de agosto |
| ¿El nodo único con indicador de sedes reemplaza la práctica de replicar el cargo por sucursal? | Primera etapa, filtro por sede | Diseño + Fabiola | 15 de agosto |
| ¿Qué normativa de protección de datos aplica y qué plazo de retención exige? | `RNF‑22`, primera etapa | Legal + Producto | 20 de agosto |
| ¿Entra la vista de aprobaciones? | Segunda etapa | Producto | 22 de agosto |
| ¿Se aprueban los nombres propuestos para las relaciones? | El contenido de la primera etapa | Producto | 22 de agosto |
| **¿Quién construye la vista del organigrama dentro de la app?** ¿El equipo de la app o este proyecto? | `RNF‑23`, segunda etapa | Producto + Israel | 22 de agosto |
| ¿Se implementa el aprobador suplente? | Tercera etapa | Producto | 30 de septiembre |

**La primera es la más urgente.** Bloquea la maquetación en alta fidelidad, y la validación tiene que hacerse **proyectada e impresa**, no en pantalla.

---

# 7 · Historias de usuario

Cada historia lleva sus condiciones de aceptación pegadas: si cambia la historia, cambian con ella. Las situaciones de las que salen están en `1.6`.

## Ver quién aprueba los permisos

> Como **responsable de RR.HH.**, quiero ver quién aprueba los permisos de cada cargo, para detectar los que quedarían sin aprobador antes de que el flujo falle.

- Con las aprobaciones declaradas, al activar esa vista se dibujan con una flecha que apunta al aprobador.
- Un cargo activo sin aprobador aparece marcado en el lienzo y figura en la lista "Sin declarar".
- Si exporto desde esa vista, el PDF sale con las aprobaciones y no con la jerarquía.

*Requisitos: `RF‑19` · `RF‑23` · `RF‑51` · `RF‑53`*

## Declarar una coordinación sin cambiar de jefe

> Como **jefe de área**, quiero declarar que mi cargo coordina con otros, sin que eso altere de quién dependo.

- En el alta o la edición puedo elegir varios cargos como contraparte.
- Un cargo con coordinaciones declaradas no se mueve de lugar en el árbol.
- Con un nodo seleccionado, solo se dibujan sus coordinaciones y no las del resto.

*Requisitos: `RF‑22` · `RF‑24` · `RF‑36`*

## Encontrar los puestos vacíos

> Como **responsable de RR.HH.**, quiero identificar los cargos vacantes de un vistazo, para iniciar la requisición sin revisar cargo por cargo.

- Un cargo activo sin ocupantes se dibuja con la codificación de vacante.
- El panel de estructura muestra cuántos hay y cuáles son.
- Con un cargo vacante seleccionado, se ofrece crear la requisición en Reclutamiento.

*Requisitos: `RF‑14` · `RF‑47` · `RF‑50`*

## Presentar la estructura a gerencia

> Como **responsable de RR.HH.**, quiero exportar el organigrama para presentarlo impreso y proyectado, sin que se pierda el significado de los colores.

- El PDF refleja la vista y el filtro que había en pantalla.
- Impreso en blanco y negro, las cinco codificaciones se siguen distinguiendo.
- El archivo incluye leyenda, empresa, fecha y filtro aplicado.
- Si la estructura no entra en una hoja, se pagina por unidad y lleva índice.

*Requisitos: `RF‑53` · `RF‑56` · `RNF‑07`*

## Mover un cargo entendiendo qué se rompe

> Como **responsable de RR.HH.**, quiero saber qué consecuencias tiene mover un cargo antes de confirmarlo.

- Al soltar el nodo en un destino válido, una confirmación dice cuántos cargos y personas se mueven y cuántos aprobadores cambian.
- Un destino que rompe alguna regla se marca como inválido y explica por qué.
- Una vez confirmado, el cambio queda en el historial con fecha y autor.

*Requisitos: `RF‑40` · `RF‑41` · `RF‑42` · `RF‑45`*

## Ver la estructura de una sucursal

> Como **gerente**, quiero ver qué cargos corresponden a una sucursal sin perder de vista la estructura completa.

- Con el filtro puesto, los cargos de esa sucursal quedan en primer plano y el resto atenuado.
- Al cambiar el filtro, el árbol no se reordena.
- Un cargo que pertenece a varias sedes lo indica cuando no hay filtro activo.

*Requisitos: `RF‑25` · `RF‑26` · `RF‑27`*

## Consultar de quién dependo, desde el celular

> Como **colaborador**, quiero saber de quién dependo y quién me aprueba los permisos, desde el teléfono.

- En pantallas chicas veo una lista anidada navegable, no un diagrama.
- Al buscar a una persona y abrir su ficha, veo su cargo, su jefe y su aprobador.
- Desde el celular no se edita.

*Requisitos: `RNF‑04` · `RNF‑08` · `RNF‑13`*

## Crear un cargo sin llenar dieciséis campos

> Como **responsable de RR.HH.**, quiero crear un cargo utilizable rápido y completar el perfil después.

- Con el tipo, la identificación y las relaciones obligatorias ya puedo crear el cargo.
- Si elijo Colaborador, el formulario avisa que no va a poder tener subordinados.
- Si elijo Outsourcing, desaparecen los campos de planilla y aparece el motivo de contratación.

*Requisitos: `RF‑28` · `RF‑29` · `RF‑30` · `RF‑31`*

---

# 8 · Recursos visuales

> ⚠️ **Pendiente de maquetación.** Los esquemas de esta sección sirven para revisar y aprobar el documento, **no para construir**. Son esquemas de estructura y de comportamiento: dicen qué hay en cada pantalla y qué pasa al operarla, no cómo se ve. Cuando exista el archivo de diseño, la tabla de `8.1` lleva el enlace y el nombre exacto de cada pantalla.

## 8.1 Las doce pantallas

| Pantalla | Requisitos | Archivo de diseño | Estado |
|---|---|---|---|
| **Puesta en marcha** | `RF‑68` | *pendiente* | Por maquetar |
| **Unidades organizacionales** | `RF‑63` · `RF‑65` a `RF‑67` · `RF‑69` | *pendiente* | Por maquetar |
| **Ubicaciones y sedes** | `RF‑64` a `RF‑66` | *pendiente* | Por maquetar |
| Lienzo del organigrama | `RF‑01` a `RF‑27` · `RF‑61` · `RF‑62` | *pendiente* | Por maquetar |
| Panel de estructura | `RF‑48` a `RF‑52` | *pendiente* | Por maquetar |
| Alta y edición de cargo | `RF‑28` a `RF‑39` · `RF‑62` · `RF‑69` | *pendiente* | Por maquetar |
| Ficha del cargo | `RF‑17` · `RF‑45` · `RF‑61` | *pendiente* | Por maquetar |
| Mover y eliminar cargo | `RF‑40` a `RF‑44` · `RF‑67` | *pendiente* | Por maquetar |
| Asignación de ocupante | `RF‑46` · `RF‑47` | Ya existe en Trabajito | Se ajusta |
| Exportar y compartir | `RF‑53` a `RF‑56` | *pendiente* | Por maquetar |
| Estados del submódulo | `RF‑57` a `RF‑60` | *pendiente* | Por maquetar |
| **Consulta en la app** | `RNF‑04` · `RNF‑08` · `RNF‑23` · `RNF‑24` | *pendiente* | Por maquetar |

**Qué pasa si el prototipo y este documento no coinciden.** Como desarrollo construye desde el prototipo, una diferencia entre los dos no se resuelve declarando un ganador: se decide cuál de los dos está mal y se corrige ése. Lo que no puede pasar es entregar el prototipo con una diferencia sin resolver, porque entonces el requisito que está escrito acá no lo va a ver nadie. **Antes de la entrega a desarrollo, cada requisito obligatorio de la primera etapa tiene que estar visible en alguna pantalla del prototipo.**

## 8.2 La puesta en marcha

La primera pantalla que ve una empresa que recién entra. Es la que decide si la implantación arranca en una semana o en un mes.

```
┌────────────────────────────────────────────────────────────────┐
│  Vamos a armar el organigrama de Constructora Andina           │
│  Tres pasos. Podés salir cuando quieras y seguir después.      │
│                                                                │
│    ● 1 · Áreas          ○ 2 · Sedes          ○ 3 · Cargos      │
│    ──────────────────────────────────────────────────────      │
│                                                                │
│    ¿Cómo se divide la empresa?                                 │
│    Empezá por las áreas grandes. Las subáreas vienen después.  │
│                                                                │
│    ┌──────────────────────────────────────────┐                │
│    │  Administración                     ✎  ✕ │                │
│    │  Comercial                          ✎  ✕ │                │
│    │  Operaciones                        ✎  ✕ │                │
│    └──────────────────────────────────────────┘                │
│    + Agregar área                                              │
│                                                                │
│    3 áreas creadas                                             │
│                                                                │
│  [ Importar desde Excel ]              [ Siguiente: sedes → ]  │
└────────────────────────────────────────────────────────────────┘
```

| Paso | Qué pide | Qué pasa si se salta |
|---|---|---|
| **1 · Áreas** | Al menos una unidad organizacional | **No se puede saltar.** Un cargo no existe sin área (`RF‑32`) |
| **2 · Sedes** | Al menos una ubicación | Se puede saltar: la empresa queda con una sola sede implícita y el filtro no aparece |
| **3 · Cargos** | El primer cargo | Se puede saltar: se cae al lienzo vacío, que ofrece volver |

> **Por qué este orden y no otro.** Es el único que funciona: el alta de cargo exige unidad (`RF‑32`), y el filtro por sede exige ubicaciones (`RF‑25`). Ponerlo al revés obliga a interrumpir el alta para crear un área, que es exactamente el callejón que `RF‑69` viene a evitar.

> **Se puede abandonar y retomar.** Nadie carga una estructura de cuarenta cargos de una sentada. El progreso se guarda al terminar cada paso, y el lienzo vacío recuerda en cuál quedó.

## 8.3 Crear una unidad organizacional

```
┌────────────────────────────────────────────────────────────────┐
│  Áreas de la empresa                          [ + Nueva área ] │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  ▾ Administración                              3 cargos   ✎ ✕  │
│    ├─ ▾ Contabilidad                           2 cargos   ✎ ✕  │
│    │     └─ Cuentas por pagar                  0 cargos   ✎ ✕  │
│    └─ Recursos Humanos                         1 cargo    ✎ ✕  │
│                                                                │
│  ▸ Comercial                                  12 cargos   ✎ ✕  │
│  ▸ Operaciones                                24 cargos   ✎ ✕  │
│                                                                │
│  ────────────────────────────────────────────────────────────  │
│  Niveles en uso:  ● Área  ● Subárea  ● Departamento  ○ Equipo  │
│  Los niveles apagados no aparecen en ningún formulario.        │
└────────────────────────────────────────────────────────────────┘
```

| Acción | Qué hace | Requisito |
|---|---|---|
| **Nueva área** | Crea en el nivel que corresponda; hereda el padre donde se la creó | `RF‑63` |
| **Renombrar** ✎ | Cambia el nombre en todos lados a la vez. No rompe cargos | `RF‑63` |
| **Arrastrar** | Mueve la unidad y **todo lo que cuelga de ella**. Avisa cuántos cargos arrastra antes de confirmar | `RF‑67` |
| **Eliminar** ✕ | Solo si no tiene cargos. Si los tiene, ofrece desactivar o reasignar | `RF‑66` · Regla 9 |
| **Niveles en uso** | Enciende y apaga cada uno de los cuatro niveles para esta empresa | `RF‑65` |

> **Cuántos cargos cuelgan de cada área va a la vista.** Es el dato que decide si se puede borrar y cuánto arrastra un movimiento. Esconderlo obliga a descubrirlo con un error.

> **Mover un área no es como mover un cargo, y por eso avisa distinto.** Mover un cargo arrastra su rama; mover un área arrastra **todos los cargos de todas sus subáreas**. El aviso de `RF‑67` dice el número antes de soltar, igual que `RF‑41`.

## 8.4 Crear una sede

Mismo editor, otro árbol, y una regla que no se negocia: **la ubicación nunca es un nivel del organigrama.**

```
┌────────────────────────────────────────────────────────────────┐
│  Sedes                                        [ + Nueva sede ] │
├────────────────────────────────────────────────────────────────┤
│                                                                │
│  ▾ Constructora Andina                     (empresa)      ✎    │
│    ├─ ▾ División Construcción       (unidad de negocio)   ✎ ✕  │
│    │     ├─ ▾ Santa Cruz                     (región)     ✎ ✕  │
│    │     │     ├─ Casa Matriz               (sucursal)    ✎ ✕  │
│    │     │     └─ Sucursal Norte            (sucursal)    ✎ ✕  │
│    │     └─ ▸ Cochabamba                     (región)     ✎ ✕  │
│    └─ ▸ División Inmobiliaria       (unidad de negocio)   ✎ ✕  │
│                                                                │
│  ────────────────────────────────────────────────────────────  │
│  Niveles en uso:  ● Empresa ● U. negocio ● Región              │
│                   ● Sucursal  ○ Oficina                        │
└────────────────────────────────────────────────────────────────┘
```

> **Esto no dibuja nada en el lienzo.** Las sedes solo alimentan los selectores del filtro (`RF‑25`). Un cargo se asigna a una o a varias, y con el filtro puesto se atenúa lo que no corresponde — el árbol no cambia de forma. Si esto se volviera un nivel del árbol, una empresa con tres sedes tendría el mismo cargo dibujado tres veces.

## 8.5 El lienzo

```
┌──────────────────────────────────────────────────────────────────────┐
│  Organigrama            🔍 Buscar cargo o persona        [Exportar]  │
├──────────────────────────────────────────────────────────────────────┤
│  VISTA:  [●Jerarquía] [ Coordinaciones ] [ Aprobaciones ]            │
│  UBICACIÓN:  Empresa ▾   Unidad de negocio ▾   Región ▾   Sucursal ▾ │
├─────────────────┬────────────────────────────────────────────────────┤
│  ESTRUCTURA     │                  ⭐ GERENTE GENERAL                 │
│  41 cargos      │                          │                         │
│  ─────────────  │            ┌─────────────┼─────────────┐           │
│  👤 Colab.  24  │      ⭐ GER. ADM.   ⭐ GER. COM.   🎯 CONTROLLER    │
│  ⭐ Jefe    15  │            │             │                         │
│  🎯 Staff    2  │       ┌────┴────┐        │                         │
│  ⬜ Vacante  3  │   👤 CONTAB. ⬜ ANALISTA │                         │
│  ─────────────  │                                                    │
│  Sin declarar 7 │                                    ⊕ ⊖  ⤢  ⊞      │
└─────────────────┴────────────────────────────────────────────────────┘
```

**Cuánto se muestra según el zoom.** Sin esto, un organigrama de 200 cargos al 30 % es una mancha de texto ilegible que igual hay que dibujar.

| Zoom | Qué se ve en el nodo |
|---|---|
| Menos de 40 % | Solo forma y color. Sin texto |
| 40 – 70 % | Ícono del tipo y nombre del cargo |
| 70 – 110 % | Se suman la **etiqueta de tipo**, el ocupante y la ocupación. **Vista por defecto** |
| Más de 110 % | Se suman unidad, sucursal y código |

**Cómo se comporta según el tamaño de la empresa**

| Cargos | Al abrir |
|---|---|
| Menos de 50 | Todo desplegado |
| 50 a 150 | Tres niveles abiertos, el resto plegado |
| 150 a 400 | Se sugiere filtrar por unidad de negocio o sucursal |
| Más de 400 | Se entra por unidad. El panorama se dibuja sin texto |

**Cómo se navega**

| Gesto | Qué hace |
|---|---|
| Arrastrar el fondo | Mueve el lienzo |
| `Ctrl` + rueda, o pellizcar | Acerca y aleja |
| Doble clic en un cargo | Lo aísla: lo centra y pliega las ramas hermanas |
| `Esc` | Sale del aislamiento |
| Buscar | Salta al cargo, lo centra y lo resalta dos segundos |
| `Tab` | Recorre los cargos en orden jerárquico |
| Flechas | Entre hermanos (← →) y entre niveles (↑ ↓) |

## 8.6 El nodo

```
┌───────────────────────────────┐
│ ▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔▔ │ ← barra de tipo, solo en jefaturas
│  JEFE / DIRECTOR              │ ← etiqueta de tipo
│  ⭐  GERENTE ADMINISTRATIVO   │ ← ícono del tipo y nombre del cargo
│  ─────────────────────────    │
│  Luis Mamani                  │ ← quién lo ocupa
│  Administración · 1/1         │ ← unidad · puestos cubiertos
│              ⊖ 8        ⋮     │ ← plegar (8 debajo) · acciones
└───────────────────────────────┘
```

**La etiqueta de tipo es la cuarta señal.** Color, forma de borde e ícono permiten distinguir las cinco codificaciones sin leer; la etiqueta los nombra para quien recién llega al organigrama y todavía no aprendió el código. Las cinco etiquetas son: `COLABORADOR`, `JEFE / DIRECTOR`, `STAFF`, `OUTSOURCING` y `VACANTE`.

**Los ocho estados** que la maqueta tiene que entregar — es lo que exige `RF‑15`:

| Estado | Cómo se ve |
|---|---|
| Normal | Según su tipo |
| Cursor encima | Se eleva un poco y aparece el menú |
| Seleccionado | Contorno de 2 px y ficha abierta al costado |
| Enfocado por teclado | Anillo de foco visible sobre cualquier fondo |
| Resultado de búsqueda | Resaltado dos segundos; el resto del lienzo se apaga |
| Fuera del filtro | Atenuado, nunca oculto |
| Arrastrándose | Semitransparente, con los destinos válidos marcados |
| Destino inválido | Cursor de bloqueo y el motivo en un globo |
| Sin jefe declarado | Marca de aviso en la esquina |

> **Por qué atenuar y no ocultar.** Si los cargos filtrados desaparecen, el árbol se rompe: se van los jefes y los subordinados quedan colgando de la nada. Atenuar conserva la forma y el contexto. Es la diferencia entre filtrar un diagrama y filtrar una tabla.

## 8.7 Las tres vistas

| Vista | Qué dibuja | Trazo |
|---|---|---|
| **Jerarquía** *(por defecto)* | La línea de mando. Los cargos Staff y los de Outsourcing van al costado | Continuo, ortogonal |
| **Coordinaciones** | Quién trabaja con quién. La jerarquía queda de fondo, atenuada | Punteado y curvo. **Con flecha** si el contraparte es supervisor funcional; **sin flecha** si es par |
| **Aprobaciones** | Quién autoriza los permisos de quién, y quién no tiene aprobador | Continuo fino, curvo, con flecha |

**Una vista por vez.** La tentación es dibujar las coordinaciones encima de la jerarquía porque "así se ve todo junto". En un árbol de 40 cargos eso son 40 líneas verticales más quince que lo cruzan en diagonal. El usuario deja de distinguir cuál es cuál y la conclusión que saca es que el organigrama está mal.

## 8.8 El filtro por sede

| Selección | Qué pasa |
|---|---|
| Ninguna | Se ve la estructura completa |
| Sucursal = Casa Matriz | Los cargos de Casa Matriz quedan en primer plano, el resto atenuado. **El árbol no cambia de forma** |
| Región = Santa Cruz | Igual, con todas las sucursales de la región |
| Cambiar el filtro | Solo cambia la opacidad. Nada se reordena |

Un cargo asignado a tres sucursales se resalta al filtrar por cualquiera de las tres, y sin filtro muestra un indicador discreto: `3 sedes`. Es un cargo en la base y un cargo en pantalla. Si una gerencia se replica por sucursal y son cargos distintos, se declaran como cargos distintos: la diferencia la decide quien conoce la organización, no el sistema.

> **Esto le cambia el método a quien hoy arma los organigramas.** Una gerencia comercial responsable de dos regiones se dibuja hoy, a mano, como dos cajas — para que ninguna de las dos gerencias sienta que perdió el control. El sistema propone una sola caja con el indicador de sedes y el filtro. Es más limpio y es un cargo en la base, pero **hay que validarlo sobre una estructura real antes de darlo por cerrado**, no descubrirlo en la demo. Está registrado como riesgo en `6.6` y como pregunta abierta en `6.7`.

## 8.9 Alta de cargo

```
  ① Tipo        ② Identificación     ③ Relaciones      ④ Perfil
     ●───────────────●───────────────────●───────────────○
  obligatorio    obligatorio         obligatorio       opcional

                          [ Crear cargo ] ← se habilita desde el paso 3
```

Entre los campos que ya existían y los que suma el modelo de relaciones, el formulario pasa de cuatro campos a dieciséis. En un formulario plano, dieciséis campos no se completan.

Los tres primeros pasos son lo mínimo para que el cargo le sirva a los demás módulos. El perfil —rango salarial, requisitos, competencias— es importante, pero puede esperar sin bloquear a nadie. Es el principio 5 de `1.4`.

**Qué cambia según el tipo elegido en el paso 1** (`RF‑31`):

| Si el tipo es… | El formulario |
|---|---|
| **Colaborador** | Avisa que no va a poder tener subordinados |
| **Jefe / Director** | Sin cambios |
| **Staff** | Pide `Asiste a` en vez de permitir línea descendente |
| **Outsourcing** | Oculta centro de costo y planilla, y pide `Motivo de contratación` |

## 8.10 El paso 3: declarar las relaciones

**Es la pantalla más importante del prototipo.** Acá se declaran las cuatro relaciones que son la razón de ser del proyecto. Si esta pantalla sale mal, el resto no sirve.

```
 ③ RELACIONES                                        obligatorio
 ────────────────────────────────────────────────────────────────

 Depende de *                                     ← estructural
 ┌──────────────────────────────────────────────────────┐
 │ 🔍 Gerente Administrativo                            │
 │    ocupa: Luis Mamani                                │
 └──────────────────────────────────────────────────────┘
 Se elige el cargo. La persona se muestra al lado, no se elige.

 ¿Quién le aprueba los permisos? *                 ← aprobación
 ┌──────────────────────────────────────────────────────┐
 │ Gerente Administrativo           ✓ igual al jefe     │
 └──────────────────────────────────────────────────────┘
 Viene propuesto igual al jefe. Cambialo si no coinciden.

 Centro de costo *
 ┌──────────────────────────────────────────────────────┐
 │ ADM‑001 · Administración                             │
 └──────────────────────────────────────────────────────┘

 ▸ Coordinaciones y contexto                         (opcional)
 ────────────────────────────────────────────────────────────────
                                    [ Crear cargo ] ← ya se habilita
```

**El bloque plegado, abierto.** Es donde vive la capa funcional, y solo aparece si la empresa la tiene habilitada (`RF‑62`):

```
 ▾ Coordinaciones y contexto                         (opcional)

   Coordina con                                   ← funcional
   ┌────────────────────────────────────────────────────────┐
   │ Gestora Regional Norte    ○ es par   ● me supervisa  ✕ │
   │ Gestora Regional Sur      ● es par   ○ me supervisa  ✕ │
   └────────────────────────────────────────────────────────┘
   + Agregar coordinación

   «Me supervisa» quiere decir que evalúa parte de mi trabajo
   sin ser mi jefe. Desempeño lo lee distinto según cuál elijas.

   Proyecto                      Cliente
   ┌───────────────────────┐     ┌───────────────────────┐
   │ Torre Equipetrol      │     │ —                     │
   └───────────────────────┘     └───────────────────────┘
```

**Las cuatro relaciones, cómo se declara cada una**

| Relación | Dónde se declara | Obligatoria | Cuántas | Requisito |
|---|---|---|---|---|
| **Depende de** *(estructural)* | Paso 3, arriba | Sí *(se puede diferir con aviso)* | Exactamente una | `RF‑33` · `RF‑35` · `RF‑39` |
| **Le aprueba los permisos** *(aprobación)* | Paso 3, arriba | Sí | Una, más suplente | `RF‑33` · `RF‑34` · `RF‑37` |
| **Coordina con** *(funcional)* | Paso 3, bloque plegado | No | Las que haga falta, **cada una con su calidad** | `RF‑36` · `RF‑61` · `RF‑62` |
| **Asiste a** *(asistencia)* | Reemplaza a `Depende de` cuando el tipo es Staff | Sí, para Staff | Una | `RF‑31` · Regla 2 |

> **La calidad de la coordinación es un radio, no una casilla.** Par y supervisor funcional son excluyentes: una coordinación es una cosa o la otra, nunca las dos ni ninguna. Dejarlo como casilla opcional produce coordinaciones sin calidad, que es exactamente el dato que Desempeño no puede usar (`RF‑61`).

> **El botón de crear se habilita apenas se completan los tres campos de arriba.** El bloque plegado no lo bloquea. Es el principio 5 de `1.4` puesto en una pantalla: lo mínimo utilizable primero.

## 8.11 El alta según el tipo de cargo

El primer paso cambia el resto del formulario (`RF‑31`). Son cuatro recorridos distintos y el prototipo tiene que mostrar los cuatro.

```
 ① ¿Qué tipo de cargo es?

 ┌──────────────┐ ┌──────────────┐ ┌──────────────┐ ┌──────────────┐
 │      👤      │ │      ⭐      │ │      🎯      │ │      🤝      │
 │ COLABORADOR  │ │ JEFE /       │ │    STAFF     │ │ OUTSOURCING  │
 │              │ │ DIRECTOR     │ │              │ │              │
 │ Sin gente    │ │ Con línea    │ │ Asiste, no   │ │ Servicio     │
 │ a cargo      │ │ de mando     │ │ manda        │ │ externo      │
 └──────────────┘ └──────────────┘ └──────────────┘ └──────────────┘

 Vacante no está acá: es un estado que el sistema deduce.  (RF‑30)
```

| Si elegís… | Qué cambia en los pasos siguientes | Qué se avisa |
|---|---|---|
| **👤 Colaborador** | Nada se agrega | "Este cargo no va a poder tener gente a cargo." Si después se le cuelga alguien, el sistema avisa en ese momento (Regla 1 · `RF‑38`) |
| **⭐ Jefe / Director** | Nada se quita. Es el recorrido completo | — |
| **🎯 Staff** | `Depende de` **se reemplaza por** `Asiste a` | "Un cargo Staff se dibuja al costado de quien asiste, no debajo. No va a tener línea descendente." (Regla 2 · `RF‑21`) |
| **🤝 Outsourcing** | **Se ocultan** centro de costo y datos de planilla. **Aparece** `Motivo de contratación` | "Este cargo no genera planilla, salarios ni asistencia." (Regla 3) |

```
  PASO 3, SEGÚN EL TIPO

  Colaborador · Jefe            Staff                    Outsourcing
  ┌─────────────────────┐   ┌─────────────────────┐  ┌─────────────────────┐
  │ Depende de *        │   │ Asiste a *       ◀──┼──┤ Depende de *        │
  │ Aprueba permisos *  │   │ Aprueba permisos *  │  │ Aprueba permisos *  │
  │ Centro de costo *   │   │ Centro de costo *   │  │ Motivo contrat. * ◀─┤
  │ ▸ Coordinaciones    │   │ ▸ Coordinaciones    │  │ ▸ Coordinaciones    │
  └─────────────────────┘   └─────────────────────┘  └─────────────────────┘
                              cambia el campo          sin centro de costo
                              de dependencia           sin planilla
```

> **El tipo se puede cambiar después, y ahí el sistema valida de nuevo.** Pasar a Colaborador un Jefe que tiene gente debajo choca con la regla 1: se avisa en el momento de elegir, no al guardar (`RF‑38`).

## 8.12 Mover y eliminar

Los dos flujos destructivos del submódulo. Los dos existen para cumplir el principio 6 de `1.4`: **antes de un cambio grande, mostrar el alcance.**

```
  MOVER UN CARGO                            RF‑40 · RF‑41 · RF‑42

  Se arrastra el nodo
        │
        ▼
  Se marcan los destinos válidos ────▶ ¿destino inválido?
        │                                      │
        │                                      ▼
        │                             Cursor de bloqueo + motivo
        │                             «Un colaborador no puede
        │                              tener personal a cargo»
        ▼                                   (reglas 1, 2 y 6)
  Se suelta en un destino válido
        │
        ▼
  ┌──────────────────────────────────────────────┐
  │  Se mueven 3 cargos y 3 personas.            │
  │  Cambian 2 aprobadores.                      │
  │  La relación anterior se cierra con fecha.   │
  │                                              │
  │            [ Cancelar ]  [ Mover cargo ]     │
  └──────────────────────────────────────────────┘
        │
        ▼
  Queda en el historial: qué cambió, cuándo y quién   (RF‑45)
```

```
  ELIMINAR UN CARGO                              RF‑43 · RF‑44

  Se pide eliminar
        │
        ▼
  ¿Tiene ocupantes? ──── sí ──▶  No se elimina.
        │                        «Tiene una persona adentro.
        │                         Reasignala antes de eliminar»
        no                        [ Ir al ocupante ]
        │
        ▼
  ¿Tiene cargos debajo? ── no ──▶  Se elimina
        │
        sí
        ▼
  ┌──────────────────────────────────────────────┐
  │  Este cargo tiene 4 cargos debajo.           │
  │                                              │
  │   ○ Subirlos un nivel                        │
  │   ○ Eliminarlos también                      │
  │                                              │
  │   Hay que elegir. No hay opción por defecto. │
  └──────────────────────────────────────────────┘
```

## 8.13 La consulta en la app

Lo que ve el colaborador en el teléfono. **No es el lienzo achicado: es una lista que contesta tres preguntas** (`RNF‑04` · `RNF‑23`).

```
        ┌─────────────────────────┐
        │  ←   Mi organigrama     │
        ├─────────────────────────┤
        │  MI CARGO               │
        │  Analista Contable      │
        │  Administración         │
        │  Casa Matriz            │
        ├─────────────────────────┤
        │  DEPENDO DE             │
        │  ⭐ Gerente Admin.    → │
        │     Luis Mamani         │
        ├─────────────────────────┤
        │  ME APRUEBA LOS         │
        │  PERMISOS               │
        │  ⭐ Gerencia Operac.  → │
        │     Ana Quispe          │
        ├─────────────────────────┤
        │  COORDINO CON       (2) │
        │  Gestora Norte          │
        │     me supervisa        │
        │  Gestora Sur            │
        │     es par              │
        ├─────────────────────────┤
        │  MI EQUIPO          (4) │
        │  ▸ ver los 4            │
        ├─────────────────────────┤
        │  🔍 Buscar a alguien    │
        └─────────────────────────┘
```

| Sí muestra | No muestra |
|---|---|
| Mi cargo, mi área y mi sede | El árbol dibujado |
| De quién dependo y quién me aprueba | Ningún botón de editar (`RNF‑08`) |
| Con quién coordino, **y en qué calidad** | Salario, documento ni datos de contacto (`RNF‑20`) |
| Mi equipo, plegado | La estructura de otra empresa (`RNF‑16`) |
| Buscar a cualquier persona y ver su ficha | |

> **Es la misma lista que usa el lector de pantalla.** No se construyen dos cosas: `RNF‑04` pide una alternativa en lista anidada por accesibilidad, y resulta ser exactamente lo que sirve en una pantalla de cinco pulgadas. Una sola vista cubre las dos necesidades.

> **Y lee la misma fuente que la web** (`RNF‑24`). Si RR.HH. cambia un aprobador a las diez, el colaborador lo ve a las diez y un minuto, sin sincronizar nada.

## 8.14 Cuando no hay nada que mostrar

| Situación | Qué se dice | Qué se ofrece |
|---|---|---|
| **Empresa sin estructura** | "Todavía no hay nada cargado. Empecemos por las áreas: después vienen las sedes y recién ahí los cargos." | Empezar la puesta en marcha · Importar desde Excel |
| **Empresa sin unidades** | "Un cargo necesita un área a la que pertenecer. Creá la primera." | Crear área |
| Unidad sin cargos | "Esta unidad no tiene cargos todavía." | Agregar cargo |
| Filtro sin resultados | "Ningún cargo está asignado a Sucursal Norte." | Quitar el filtro |
| Búsqueda sin resultados | "No encontramos *contador*. Probá con el nombre del cargo o de la persona." | — |
| Cargando | El esqueleto del árbol | — |
| Error al guardar | "No se pudo guardar el cambio de estructura." El cambio no se pierde | Reintentar |

**Los dos primeros son los críticos.** Sin estructura, el alta de colaboradores no se puede completar. El orden de puesta en marcha de cada cliente es **empresa → unidades → sedes → cargos → personas**, y estas dos pantallas son donde se le explica eso a un cliente nuevo. `RF‑68` convierte ese orden en un recorrido guiado en vez de dejarlo librado a que alguien lo adivine.

## 8.15 Quién hace qué, de un vistazo

Los cuatro roles de `4` contra las funciones del submódulo. Es el resumen que usa Diseño para saber qué esconder y Desarrollo para saber qué rechazar en el servidor.

```
                      Consultar  Editar rama  Crear/Mover  Exportar  Ver historial
                      estructura   propia      /Eliminar              a fecha pasada
  Colaborador             ●            ·            ·          ·           ·
  Jefe de área            ●            ●            ·          ·           ·
  RR.HH.                  ●            ●            ●          ●           ·
  Auditoría               ●            ·            ·          ●           ●

  ● puede    · no puede
```

**Se verifica en el servidor, no escondiendo botones** — `RNF‑13`, `RNF‑16` y `RNF‑17`.

---

## Cómo se mantiene este documento

Este PRD es la única fuente de verdad del submódulo mientras dure el proyecto. Para que siga siéndolo:

- **Cada decisión que se toma en una reunión entra acá**, con fecha, en el historial de versiones. Una decisión que solo vive en un chat no existe.
- **Cuando exista el prototipo**, la tabla de `8.1` lleva el enlace y el nombre exacto de cada pantalla.
- **Cuando se responda una pregunta abierta**, se borra de `6.7` y la respuesta se incorpora al cuerpo. La lista de preguntas abiertas debería vaciarse, no crecer.
- **Si el prototipo y este documento no coinciden**, se corrige el que esté mal, y se corrige antes de entregarle nada a desarrollo.
- **Los números de requisito no se reutilizan.** Si un requisito se elimina, su número queda libre y vacío. Citar `RF‑33` tiene que significar lo mismo dentro de un año.
- **La versión sube cuando cambia lo que el documento promete**, no cuando se corrige una palabra. La 2.1 subió porque agrega nueve requisitos y una regla de negocio, y porque corrige dos afirmaciones que eran falsas — no por haberse reordenado. **Todavía no la revisó nadie:** los comentarios de Naihara y de Israel son los que van a producir la 2.2.

---

## Anexo · Por qué decidimos así

Los argumentos que sostienen las decisiones, separados del cuerpo para que el cuerpo prescriba y el anexo explique. Cada uno desarrolla alguno de los principios de `1.4`.

**Por qué tres vistas y no dos.** La primera necesidad que se enunció fue ver quién aprueba permisos y salidas. La aprobación es una relación propia que no siempre coincide con la línea de mando — por eso el aprobador se declara aparte del jefe. Sin vista propia, ese dato se carga y no se puede leer, y la necesidad que originó el proyecto queda sin resolver en pantalla.

**Por qué una capa por vez.** En un árbol de 40 cargos, superponer las relaciones son 40 líneas verticales más quince diagonales. El usuario deja de distinguirlas y concluye que el organigrama está mal.

**Por qué la forma además del color.** El modelo apoya cinco codificaciones de cargo y cuatro relaciones. Entre el daltonismo, el proyector de sala y la impresión en blanco y negro, el color solo no alcanza. La forma del borde es la señal que sobrevive a los tres casos.

**Por qué atenuar y no ocultar al filtrar.** Ocultar rompe el árbol: desaparecen los jefes y los subordinados quedan colgando. Atenuar conserva la estructura y el contexto.

**Por qué el alta en cuatro pasos.** El formulario pasa de cuatro campos a dieciséis. Un cargo utilizable necesita tipo, nombre, unidad y jefe; el rango salarial puede esperar. La salida temprana evita que el peso del formulario se traduzca en abandono.

**Por qué se confirma un movimiento.** Arrastrar es un gesto de un segundo con consecuencias en permisos, planillas y desempeño. La confirmación no está para que el usuario piense: está para que **vea el alcance**, que es información que no tenía antes de soltar.

**Por qué vacante no se puede elegir en el alta.** Es un estado que se deduce de tener cero ocupantes. Ofrecerlo como tipo elegible invita a crear cargos "de tipo vacante" que después nunca se convierten en nada. En la leyenda del lienzo sí figura, porque ahí sí es algo que se ve.

**Por qué un solo jefe.** Los casos de "reporta a dos" que aparecieron en la sesión son, mirados de cerca, un jefe y una o más coordinaciones. La interfaz no debe ofrecer un segundo `Depende de`; debe ofrecer un `Coordina con` que admita varios.

**Por qué la coordinación lleva calidad.** En la sesión aparecieron los dos casos mezclados: alguien que coordina de igual a igual y alguien que, sin ser jefe, supervisa parte del trabajo — el caso de la analista contable que responde a su gerente pero coordina con las gestoras de otra región, y el de la responsable de RR.HH. a quien evalúan el gerente administrativo y la gerente comercial sin ser ninguno su jefe. Guardar las dos como la misma relación es barato de construir y deja a Desempeño sin poder distinguir una evaluación de par de una de supervisor. Como la calidad vive en la misma tabla que la relación, agregarla después obliga a migrar datos: por eso entra ahora.

**Por qué la capa funcional se apaga por empresa.** No todas la usan. Para las que trabajan solo con línea jerárquica, el bloque de coordinaciones es un campo más que nadie completa y una vista que nadie abre. Apagarla es más honesto que dejarla vacía.

**Por qué la lista anidada no es una versión degradada.** El organigrama es la fuente de quién aprueba qué. Un árbol dibujado no lo puede leer un lector de pantalla, y en una pantalla de cinco pulgadas es un mapa que se arrastra a ciegas. La lista responde mejor la pregunta que la gente lleva al celular: de quién dependo y quién me aprueba.

**Por qué el glosario va primero y no en un anexo.** Casi todos los desacuerdos de la sesión del 1 de agosto fueron de vocabulario, no de criterio: "cargo" y "puesto", "coordina" y "reporta", "sucursal" como nivel del árbol o como filtro. Un glosario al final es un diccionario que se consulta cuando ya hubo un malentendido. Al principio es un acuerdo que lo previene.

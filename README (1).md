# DevCore Solutions: Módulo de Gestión de Tareas y Control de Tiempos

Trabajo Práctico Integrador de **Organización Empresarial**, Tecnicatura Universitaria en Programación a Distancia, UTN.

## Qué es este proyecto

DevCore Solutions es una software factory ficticia que hace sistemas a medida para PyMEs. Lo más caro que tiene son las horas de sus desarrolladores, y hoy las controla con planillas de Excel.

El módulo que propongo sirve para cargar las horas reales de cada tarea, compararlas con las estimadas, validarlas y calcular lo que hay que facturar y qué tan rentable es cada proyecto. Está planificado para 20 semanas.

## Integrante

Abril Durand Azul

Docentes: Prof. Gabriela Martínez (titular); Prof. Carolina Bruno, Prof. Mario Raúl López y Prof. Andrea Ramos (adjuntos).

## Enlaces

- Tablero de GitHub Projects: [PEGAR LINK DEL TABLERO]
- Diagrama BPMN: [`docs/bpmn/BPMN_DevCore.png`](docs/bpmn/BPMN_DevCore.png)

## El proceso (BPMN)

Modelé el proceso de registro, validación y liquidación de horas, que es el que el módulo reemplaza. Hay dos pools (DevCore y el Cliente PyME) y cuatro lanes dentro de DevCore: Desarrollador, Sistema, Líder de proyecto y Administración y Facturación. Las excepciones están resueltas con compuertas: datos inválidos, desvío mayor al 20 %, horas no aprobadas, cliente que observa la factura y factura no cobrada.

![BPMN del proceso](docs/bpmn/BPMN_DevCore.png)

## Historias de usuario

**HU-01.** Como desarrollador, quiero registrar las horas que dedico a cada tarea, para que el tiempo real quede documentado y pueda compararse con lo estimado.
- El sistema rechaza el registro si faltan datos.
- La carga responde en 2 segundos o menos.

**HU-02.** Como líder de proyecto, quiero validar las horas de mi equipo y ver el desvío contra lo estimado, para reasignar tareas antes de que se afecte el plazo.
- Si el desvío supera el 20 %, el sistema me avisa.
- Solo las horas aprobadas pasan a facturación.

**HU-03.** Como analista de Administración y Facturación, quiero que el sistema genere la liquidación a partir de las horas validadas, para emitir la factura sin planillas manuales y sin errores.
- La liquidación suma solo horas validadas y facturables.
- Busca reducir al menos un 70 % el tiempo de preparar la facturación.

Cada historia es un Issue y se sigue en el tablero (Por Hacer, En Progreso, Listo). Para esta etapa, una historia está "Listo" cuando tiene criterios de aceptación y aparece en el BPMN.

## Indicadores de control

Los valores son supuestos, porque DevCore es una empresa ficticia.

| Indicador | Estándar |
|---|---|
| Tiempo de respuesta con 30 usuarios | 95 % de las operaciones en 2 s o menos |
| Escalabilidad (50.000 registros, 50 usuarios) | Respuesta de 3 s o menos |
| Defectos críticos abiertos al lanzar | 0 |
| Reducción del tiempo de preparar la facturación | 70 % o más |
| Registros rechazados en la validación | 10 % o menos |
| Desvío promedio entre horas reales y estimadas | 20 % o menos |
| Facturas observadas por el cliente | 5 % o menos |
| Cambios que entran a `main` por Pull Request | Todos, después de crear el repositorio |

## Cómo trabajé en el repositorio

- Nada entra directo a `main`: cada cambio va en una rama (por ejemplo `docs/bpmn`) y se incorpora con un Pull Request.
- Los commits tienen la forma `tipo: descripción`, con tipos como `docs`. Ejemplo: `docs: agrega diagrama BPMN del proceso de registro y liquidación de horas`.

## Declaración de uso de IA

Usé Claude (Anthropic) y Gemini como ayuda. Les pedí que me ayudaran a ordenar la entrega según las consignas, que me propusieran borradores del diagrama BPMN, de las historias de usuario y de los indicadores, y que me ayudaran a dibujar el diagrama. No tuvieron acceso al repositorio ni al tablero: los creé y manejé yo.

| Qué le pedí | Qué hizo la IA | Qué corregí o decidí yo |
|---|---|---|
| Ayuda con la Entrega 4 pasándole la consigna, la plantilla y mis TPI 1, 2 y 3. | Propuso el proceso a modelar, el diagrama BPMN, borradores de historias, de indicadores y del README. | Revisé el diagrama contra mi organigrama y mi diccionario de datos del TPI 3, y adopté el proceso porque cubre las áreas que ya había definido. |
| Un texto de la Consigna 1 (BPMN). | Gemini escribió un borrador con frases como "a pulmón" y con la gerencia mal nombrada. | Corregí el nombre de la Gerencia de Desarrollo y Tecnología, saqué el tono coloquial y completé la descripción del cliente, que no solo paga sino que también puede observar la factura. |
| Un texto de las Consignas 2, 3 y 4. | Los borradores contaban como ya hechas cosas que todavía no habían pasado y usaban frases vagas. | Ajusté la redacción para que describa solo lo que hice de verdad, y acorté el material del repositorio a un solo README. |

La IA me sirvió para armar borradores. La coherencia entre mis entregas la revisé yo, y soy responsable de lo que entrego.

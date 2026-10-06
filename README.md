```text
liga
│
└── jornada
    │
    ├── partido
    │   ├── equipoLocal
    │   ├── equipoVisitante
    │   ├── marcador
    │   └── estadisticas
    ├── partido
    └── partido

| Información | Elemento/Atributo | Justificación |
| --- | --- | --- |
| **Jornada** | Elemento | Es un contenedor lógico que agrupa múltiples entidades complejas (los partidos).

 |
| **Fecha** | Atributo | Es un metadato simple que describe una propiedad específica de la jornada, no contiene sub-datos.

 |
| **ID del partido** | Atributo | Sirve como un identificador único para el nodo. En XML, los identificadores (ID) son el caso de uso clásico para los atributos.

 |
| **Equipo local** | Elemento | Es una entidad compleja que necesita anidar más información en su interior, como sus estadísticas.

 |
| **Equipo visitante** | Elemento | Al igual que el equipo local, agrupa sub-datos y requiere su propia estructura anidada.

 |
| **Goles** | Elemento | Aunque es un número, dejarlo como elemento permite su futura expansión (por ejemplo, anidar quién anotó y en qué minuto).

 |
| **Estadio** | Elemento | Representarlo como elemento permite ampliar la estructura en el futuro si se requiere (ej. añadir ciudad o capacidad).

 |
| **Estado del partido** | Atributo | Es una clasificación simple (ej. "Finalizado", "En_curso") que describe el estatus general del partido.

 |
| **Posesión** | Elemento | Es un dato estadístico específico que pertenece al nodo de estadísticas de cada equipo.

 |
| **Tarjetas** | Elemento | Es información que puede dividirse en categorías (amarillas, rojas) o incluso listar jugadores, por lo que requiere estructura de elemento.

 |

Se decidió anidar el elemento <estadisticas> dentro de los nodos <equipoLocal> y <equipoVisitante> siguiendo el diagrama jerárquico propuesto. Este diseño ofrece las siguientes ventajas:   Es más comprensible: Agrupa lógicamente los datos bajo la entidad que los generó (el equipo en lugar del partido completo).
 Reduce duplicación: Permite reutilizar las mismas etiquetas (ej. <goles>, <tarjetasAmarillas>) para ambos equipos sin necesidad de inventar y duplicar variantes con sufijos como <golesLocal> y <golesVisitante>.   Facilita el procesamiento: Al analizar el documento DOM o consultar con XPath, es mucho más directo iterar sobre un nodo de equipo y extraer sus hijos, manteniendo el contexto de a quién pertenecen los datos.   Permite agregar estadísticas fácilmente: Si en el futuro se requieren nuevas métricas (como <posesion> o <tiros>), solo se añade la nueva etiqueta dentro de la definición compartida de estadisticas y esta aplicará automáticamente de forma estandarizada para ambos equipos. 
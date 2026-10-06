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


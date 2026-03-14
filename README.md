# Entornos-7.5

Caso de uso del ejercicio 1

```mermaid
%% Diagrama de Casos de Uso - Gimnasio
%% CU1, CU2... para los casos de uso

flowchart LR
    %% Actores
    Member([Member])
    Administrator([Administrator])
    Instructor([Instructor])

    %% Sistema
    subgraph System["Gym Class Management System"]
        CU1(("Login"))
        CU2(("Book Class"))
        CU3(("Waiting List"))
        CU4(("Add Class"))
        CU5(("Cancel Session"))
        CU6(("Instructor Absent"))
        CU7(("Class Full"))
    end

    %% Relaciones Actores
    Member --> CU2
    Administrator --> CU4
    Instructor --> CU6
    Member --> CU7
    Administrator --> CU5

    %% Include (acciones que requieren login)
    CU2 -.->|<<include>>| CU1
    CU4 -.->|<<include>>| CU1
    CU5 -.->|<<include>>| CU1

    %% Extend (acciones opcionales o condicionales)
    CU3 -.->|<<extend>>| CU2
    CU5 -.->|<<extend>>| CU6
    CU7 -.->|<<extend>>| CU3

```

Ejercicio 2. Parte 1

```mermaid

sequenceDiagram
    %% Objetos / Participantes
    participant Member
    participant WebInterface
    participant ReservationManager
    participant Database

    %% Flujo principal
    Member->>WebInterface: Press "Confirm Reservation"
    WebInterface->>ReservationManager: Request reservation
    ReservationManager->>Database: Check availability
    Database-->>ReservationManager: Availability result

    %% Fragmento combinado: Clase disponible o llena
    alt Class available
        ReservationManager->>Database: Confirm reservation
        Database-->>ReservationManager: Reservation confirmed
        ReservationManager-->>WebInterface: Show message "Reservation successful"
        WebInterface-->>Member: Display confirmation
    else Class full
        ReservationManager-->>WebInterface: Show message "Class full, added to waiting list"
        WebInterface-->>Member: Display waiting list notice
    end
```

Ejercicio 2. Parte 2

```mermaid
sequenceDiagram
autonumber
actor Member
participant WebInterface as Web Interface
participant ReservationManager as Reservation Manager
participant Database as Database

¡Member->>WebInterface: Press "Confirm Reservation"
activate WebInterface
WebInterface->>ReservationManager: Request reservation
activate ReservationManager
ReservationManager->>Database: Check availability
activate Database
Database-->>ReservationManager: Availability result
deactivate Database

alt Class available
    ReservationManager->>Database: Confirm reservation
    activate Database
    Database-->>ReservationManager: Reservation confirmed
    deactivate Database
    ReservationManager-->>WebInterface: Show message "Reservation successful"
    WebInterface-->>Member: Display confirmation
else Class full
    ReservationManager-->>WebInterface: Show message "Class full, added to waiting list"
    WebInterface-->>Member: Display waiting list notice
end
deactivate ReservationManager
deactivate WebInterface
```
Ejercicio 3 en inglés
```mermaid
flowchart TD

A([Start]) --> B[Receive reservation request]

B --> C{Is the member fee paid?}

C -- No --> D[Reject reservation]
D --> Z([End])

C -- Yes --> E{Is there available capacity?}

E -- No --> F[Inform that there are no available spots]
F --> Z

E -- Yes --> G[Block spot]

G --> H[Send confirmation email]

H --> Z([End])
```

Ejercicio 4 en inglés

´´´mermaid
stateDiagram-v2

[*] --> Pending : createReservation()

Pending --> Confirmed : confirm()
Pending --> Cancelled : cancel()

Confirmed --> Cancelled : cancel()
Confirmed --> Completed : checkIn()
Confirmed --> No_Show : noShow()

Completed --> [*]
Cancelled --> [*]
No_Show --> [*]
```

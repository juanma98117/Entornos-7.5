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

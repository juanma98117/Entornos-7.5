# Entornos-7.5

Caso de uso del ejercicio 1

```mermaid
LR flowchart
%% Actores
member([member])
Administrator([Administrator])
Monitor([Monitor])

%% Sistema
subgraph System["Class Management System"]
CU1(("Log in"))
CU2(("Book class"))
CU3(("Waiting list"))
CU4(("Add class"))
CU5(("Cancel session"))
CU6(("No attendance"))
CU7(("Class full"))
end

%% Relacion de los actores
Members --> CU2
Administrator --> CU4
Monitor --> CU6
Members --> CU7
Administrator --> CU5

%% Include 
CU2-.->|<<include>>| CU1
CU4-.->|<<include>>| CU1
CU5-.->|<<include>>| CU1

%% Extend
CU3-.->|<<extends>>| CU2
CU5-.->|<<extend>>| CU6
CU7-.->|<<extend>>| CU3

```

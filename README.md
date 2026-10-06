# Temario_Azuredevops

## ¿Qué es un Process en Azure DevOps?

Cuando creamos un proyecto en Azure DevOps, tenemos que decidir cómo vamos a organizar el trabajo.
Azure DevOps nos permite elegir un Process.
Process = la plantilla/reglas que Azure DevOps utiliza para definir cómo vamos a representar y organizar nuestro trabajo.

Es decir, el Process determina principalmente:
- qué tipos de Work Items tendremos;
- cómo podemos organizar el trabajo;
- qué campos tendrá cada Work Item;
- qué estados y relaciones podremos utilizar.


                    AZURE DEVOPS
                         │
                      PROCESS
                         │
          ┌──────────────┼──────────────┐
          │              │              │
        BASIC          AGILE          SCRUM       CMMI
          │              │              │            │
       Simple         Agile          Scrum       Formal
       gestión       desarrollo      explícito    control
       
       
### BASIC
¿Qué significa?
Basic es el Process más sencillo.
Su filosofía es:
"Quiero registrar y organizar el trabajo sin meter demasiada complejidad."

EPIC
│
├── ISSUE
│   ├── TASK
│   └── TASK
│
├── ISSUE
│   └── TASK
│
└── ISSUE
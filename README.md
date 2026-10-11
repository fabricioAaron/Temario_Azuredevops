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

## Credential manager

sirve para que no tengas que meter la contraseña de azure devops cada vez que hagas un git push o git pull

``git config --global credential.helper manager``

git config --global user.name "name"
git config --global user.email "[EMAIL_ADDRESS]"


# antigravity o vscode 

En el apartado de soucer control cuanod hagamos foscambios de archivos diferente 

<img width="429" height="300" alt="imagen" src="https://github.com/user-attachments/assets/7bf9cef1-2cec-493e-be51-b4a8e94eec14" />

Changes: Modificado en local, pero no seleccionado para guardar.

Staged Changes: Seleccionado y listo para hacer Commit.

Commit: Guardado en el historial de tu máquina; ahora sí está listo para hacer Push.


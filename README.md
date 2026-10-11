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

<img width="843" height="473" alt="imagen" src="https://github.com/user-attachments/assets/f158a304-0f0b-4b52-bb14-96be74db587b" />

## Branches

### de anti a azure 

Se puede trabjaar con brances remotas y loca l en este caso se puede crear un rama de dev desde el main se ha ce una copia luego se sube a remota 

<img width="581" height="407" alt="imagen" src="https://github.com/user-attachments/assets/4265ff49-470c-4c2b-9c97-aac215e8e832" />

luego para poder eliminar lo azuremes de azure devops y desde anti ``ctrl + shift + p`` ponemos : 

``git delete branch`` 

desde alli mismo le damos a : 

``git fetch prune``

Su función principal es limpiar las referencias locales de ramas remotas que ya han sido eliminadas en el servidor (como Azure Repos o GitHub).

## Azure a anti

creamos el branch en azure, luego desde local ``ctrl + shift + p``

``git fetch``

Para poder restaurar un brances que  he eliminado  tiene que tener el mismo nombre. 

<img width="1553" height="747" alt="imagen" src="https://github.com/user-attachments/assets/2e2b39ed-6692-4e99-b63e-bdf6c1c07f01" />

## solicitar un Pull request 

lo que heremos ocmo vimo en el apartado anterior estaremos en en el commit en CHANGE  haremos el commit lo haremos en nuestra rma que estmos trajando para solicitar que nuestro cambio lo revise y lo pasen al master. 

<img width="975" height="788" alt="imagen" src="https://github.com/user-attachments/assets/363031cc-16f0-4f2d-b735-803ef8120bc6" />

Aunque este aprobado la solicitud tenemos que completarlo 

<img width="528" height="353" alt="imagen" src="https://github.com/user-attachments/assets/0227b822-6ad4-4bb6-955f-93cccc156323" />

## Para agregar políticas de seguridad

A nivel de repositorio se puede hacer en 

Project setting > repositories 

se puede crear politicas nivel de branches 



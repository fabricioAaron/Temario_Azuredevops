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


# comando de git : 
inspecciona en profundidad la configuración y el estado de sincronización entre tu repositorio local y el repositorio remoto denominado

``git remote show origin`` 


Propósito: Modificar la dirección de un remoto que ya existe.

Cuándo usarlo: Cuando necesitas cambiar el destino al que apunta un alias existente (por ejemplo, migrar un repositorio clonado desde GitHub hacia Azure DevOps, o tras un cambio de dominio/organización).

``git remote set-url origin``  "https://<organizacion>@dev.azure.com/<organizacion>/<proyecto>/_git/<repositorio>"


## Activar editor clasico en pipeline : 

Tenemos que ir Organization settings pipeline setting y desde alli desactivaremos la opcion y luego ya lo podremo ver en project settings 

Crearemos un pipeline desde 0 con editor clasico y vacío 

<img width="1883" height="658" alt="imagen" src="https://github.com/user-attachments/assets/c3f1ec99-f9b6-465d-9489-620b4c5b1249" />

podemos agregar agente de trabajo ya que hemos usado como agente del propio microsft es por ello esot depende de necesidades 

### Solución en caso de que suceda alguna vez : 

Troubleshooting Runbook: Pantalla por defecto de Azure tras despliegue CI/CD
1. Síntoma

El pipeline en Azure DevOps finaliza en verde con el mensaje Successfully deployed web package to App Service, pero al abrir la URL pública (https://<app>.azurewebsites.net) sigue cargando la página de bienvenida morada/azul de Azure en lugar de la aplicación frontend (React/SPA).
2. Causa raíz

Existen dos motivos principales para este comportamiento:

    Persistencia de caché en App Service (Linux): Azure App Service monta el almacenamiento en red y utiliza copias en caché local en el contenedor para acelerar la lectura. Tras un despliegue rápido, el servidor web interno continúa sirviendo la página por defecto almacenada en memoria caché en vez de refrescar los archivos recién subidos a /home/site/wwwroot.

    Runtime Stack incorrecto: Las aplicaciones React compiladas (npm run build) son sitios estáticos puros (HTML/CSS/JS). Si en la tarea de despliegue se mantiene configurado un runtime de Node.js dinámico (Node 18/Node 20), el servidor espera un proceso backend escuchando en un puerto en lugar de servir directamente los archivos estáticos generados.

3. Procedimiento de resolución
Paso 1: Deshabilitar el caché local en Azure Portal

    Accede a Azure Portal > navega a tu App Service.

    En el menú lateral izquierdo, ve a Settings > Configuration (o Environment variables según la interfaz).

    En la sección Application settings, añade las siguientes dos variables:

        WEBSITE_DYNAMIC_CACHE = 0

        WEBSITE_LOCAL_CACHE_OPTION = Never

    Guarda los cambios haciendo clic en Save y confirma en Continue.

    Ve a Overview y ejecuta Stop seguido de Start para forzar un reinicio limpio del contenedor.

    Verificación: En Configuration, ambas variables deben figurar en la lista con sus valores asignados y el estado del recurso debe volver a marcarse como Running.

    ejecutaremos en este apartado 
    
    <img width="1373" height="681" alt="imagen" src="https://github.com/user-attachments/assets/9fa00f46-42c2-4357-b2e8-fa2ea11507ae" />

    ``npx serve -s /home/site/wwwroot -p 8080``


 [youtube demo-CI.yml](https://github.com/user-attachments/files/33308286/youtube.demo-CI.yml)
```yaml
trigger: 
 - main # es el main branch de donde se dispara el pipeline

stages: # Son las etapas del pipeline
 - stage: Build # Es la etapa de compilación
   jobs: # Son los trabajos que se ejecutan en la etapa
   - job: Build # Es el trabajo de compilación
     pool: # Es el grupo de agentes que se ejecutan en la etapa
      vmImage: 'ubuntu-latest'
     steps:
      - task: Npm@1
        inputs:
         command: 'install'
      - task: Npm@1
        inputs:
         command: 'custom'
         customCommand: 'run build'

      - task: PublishBuildArtifacts@1
        inputs:
          PathtoPublish: 'build'
          ArtifactName: 'drop'
          publishLocation: 'Container'
  
 - stage: Deploy # Es la etapa de despliegue
   jobs: # Son los trabajos que se ejecutan en la etapa
   - job: Deploy # Es el trabajo de despliegue
     pool: # Es el grupo de agentes que se ejecutan en la etapa
      vmImage: 'ubuntu-latest'
     steps:
      - task: DownloadBuildArtifacts@1
        inputs:
          buildType: 'current'
          downloadType: 'single'
          artifactName: 'drop'
          downloadPath: '$(System.ArtifactsDirectory)'
      - task: AzureRmWebAppDeployment@5
        inputs:
          ConnectionType: 'AzureRM'
          azureSubscription: 'Azure subscription 1 (fad7f081-7ad7-4d08-af48-37d28ff187a6)'
          appType: 'webAppLinux'
          WebAppName: 'youtubedemofabri'
          packageForLinux: '$(System.ArtifactsDirectory)/drop'
          RuntimeStack: 'NODE|22-lts'
          DeploymentTypeLinux: 'oneDeploy'
```

| Concepto | Qué hace | Pregunta que responde |
|---|---|---|
| **Build (CI)** | Descarga el código, instala paquetes (`npm install`), compila (`npm run build`) y genera un artefacto empaquetado (`drop`). | ¿El código compila sin errores y pasa las pruebas? |
| **Release (CD)** | Toma ese paquete compilado (`drop`) y lo publica en servidores, App Services, contenedores o clusters. | ¿A qué servidor y bajo qué aprobaciones enviamos la aplicación? |

### Elementos principales de una Release

1. **Artifacts (Entrada):**
   - Es el paquete que generó la etapa de compilación. La Release no vuelve a compilar código fuente; consume directamente el resultado final inmutable.
2. **Stages / Environments (Etapas o Entornos):**
   - Representan los destinos lógicos donde se instala la app.
   - Ejemplo típico de flujo:
     - Artifact $\rightarrow$ Desarrollo (Dev) $\rightarrow$ Preproducción (Staging) $\rightarrow$ Producción (Prod).




<img width="831" height="378" alt="imagen" src="https://github.com/user-attachments/assets/d82f2776-cfdc-43c2-ba44-3993ba9e8ac6" />


- **Test Plan (Plan de Pruebas):** Es el nivel superior, la primera entidad que debes crear.
- **Test Suites (Conjuntos de Pruebas):** Viven dentro del Test Plan (puedes tener uno o varios) y consisten en una combinación de diferentes escenarios de prueba.
- **Test Cases (Casos de Prueba):** Viven dentro del Test Suite. Aquí es donde realmente se escriben los pasos detallados que se van a ejecutar.
- **Conexión con Azure Boards:** Dependiendo de la metodología que uses en tu proyecto, estos Casos de Prueba se asocian a diferentes elementos de trabajo. En Scrum se enlazan a un Product Backlog Item, en Agile a una User Story, y en CMMI a un Requirement. También pueden estar enlazados a errores (Bugs).
- **Shared Steps (Pasos Compartidos):** Ciertos pasos comunes se repiten en muchos tests. Para no tener que escribirlos una y otra vez, se crean "pasos compartidos" que se pueden reciclar y referenciar en múltiples casos de prueba.

## INTEGRANTES.
| Nombre | Cargo | URL GitHub |
|---|:---:|---:|
| Daniel Alquinga | :technologist: Desarrollador | https://github.com/superdavi/Practica4_Grupo2 |
| Daniel Baldeon | :technologist: Desarrollador | https://github.com/debpdhs/Practica4_Grupo2 |
| Bryan Miño | :technologist: Desarrollador | https://github.com/bmiomi/tarea4-grupo2.git |
| Wilson Segovia | :technologist: Desarrollador | https://github.com/segoviawilson/Practica4_Grupo2.git |
| Leonardo Tuguminago | :technologist: Desarrollador | https://github.com/Tuguminago/Practica4_Grupo2.git |

# 1. Despliegue de entorno de automatización con n8n integrados con PostgreSQL en Docker Compose

El objetivo de este trabajo es desplegar una aplicacion con n8n esta esta integrada con su propia base de datos PostgreSQL, utilizando Docker Compose. Se busca aplicar  conceptos de orquestación de contenedores, persistencia de datos, separación de servicios y buenas prácticas en la gestión de entornos

# 2. Configuración e Instalación

### PASO 1: 📂 Estructura de Archivos

<img width="284" height="142" alt="imagen" src="https://github.com/user-attachments/assets/64ae531d-3550-48d9-bd24-7bc7bbcd643d" />


### PASO 2: Creacion de la red de docker

```bash
docker network create n8n-network
```

**Salida Esperada**

<img width="944" height="69" alt="imagen" src="https://github.com/user-attachments/assets/14adffe6-c661-418a-98ce-913c6340d039" />

**Listamos la red creada**

```bash
docker network ls
```

**Salida Esperada**

<img width="819" height="154" alt="imagen" src="https://github.com/user-attachments/assets/c4d40790-df45-48dc-ac4a-b9b47662ffa4" />


### PASO 3: Despliegue de contenedor de n8n

Nos ubicamos en la carpeta n8n

```bash
cd n8n/
```

Ejecutar el siguiente comando

```bash
docker compose -f docker-compose-n8.yml up -d
```

**Salida Esperada**

<img width="992" height="332" alt="imagen" src="https://github.com/user-attachments/assets/b18be456-437e-45a6-868c-8cb456610e4a" />


### PASO 4: Despliege de Contenedor Postgres

Ya que nos encontramos en la carpeta n8n  es necesario ejecutar la siguiente linea de comando.

```bash
docker compose -f ../postgres/compose.postgres.yml  up -d
```

**Salida Esperada**

<img width="1175" height="377" alt="imagen" src="https://github.com/user-attachments/assets/46b1e5b4-6f59-4ce9-88ee-268bb4050cff" />


### PASO 5: Revisamos contenedores levantados

```bash
docker ps
```

**Salida Esperada**

<img width="1195" height="110" alt="imagen" src="https://github.com/user-attachments/assets/60c20c83-fb69-47ae-b4de-7674bc3047ef" />


### PASO 6: Ingreso al portar del Servidor N8N 

```bash
    http://localhost:5678/
```

**Salida Esperada**

<img width="820" height="829" alt="imagen" src="https://github.com/user-attachments/assets/9ca3aab0-87d5-46bd-a418-1893d981da86" />

### PASO 7: Información adicional del Servidor n8n  

<img width="852" height="804" alt="logon n8n con datos" src="https://github.com/user-attachments/assets/6482e24a-85a7-4178-b57d-2a2737a17a6f" />

### PASO 8: Agregar nueva configuracion de Credenciales  

<img width="255" height="296" alt="Captura de pantalla 2025-09-26 084326" src="https://github.com/user-attachments/assets/4550b781-38f3-4d24-a2e7-9deb4807aae8" />

### PASO 9: Seleccionar base de datos postgreSQL  

<img width="561" height="328" alt="Captura de pantalla 2025-09-26 083602" src="https://github.com/user-attachments/assets/68723d70-5a8f-44c6-a186-6c311207adb7" />

### PASO 10: Configuración de credenciales

**Parametros obtenidos del archivos .env del repositorio**

```bash
    Host: postgres-db
    Database: n8n
    User: n8nuser
    Password: Super_Segura123!
```
**Salida Esperada**

<img width="1257" height="690" alt="Captura de pantalla 2025-09-26 083750" src="https://github.com/user-attachments/assets/50341d33-1ec6-41c1-8d63-27210dadc005" />

### PASO 11: Verificar ingresos, conexion sea exitosa

**Salida Esperada**

<img width="1305" height="731" alt="Captura de pantalla 2025-09-26 083814" src="https://github.com/user-attachments/assets/beb69c26-1b04-4971-ba58-877a13624827" />

### PASO 12:  N8N con Postgres. Conexion de la base de datos con el contenedor N8N.

**Salida Esperada**

<img width="1307" height="493" alt="Captura de pantalla 2025-09-26 085635" src="https://github.com/user-attachments/assets/c2d21f3d-3dfe-4283-a4f1-38daee7a1645" />

# 3. Conclusiones

- Se pudo configurar correctamente el despliegue de n8n.

- Se pudo configurar el despliegue en docker de la base de datos postgres.

- Se interactua entre los dos contenedores por medio de una network creada para el caso

- Se realizan pruebas de conexión entre los contenedores al configurar el n8n con la base de datos postgres y esta ser exitosa.

- Es necesario tener en cuenta los dockers activos ya que en el caso dió un error por que tenia un docker arriba con el puerto de la base postgress al que se le paró y se contnuó con el despliegue del contenedor de postgress.

- Tener en cuenta las carpetas donde se encuentran trabajando para evitar errores al momento de ejecutar comandos.

- Uso de credenciales seguras es necesario en ambientes de test y producción.

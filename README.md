## INTEGRANTES.
| Nombre | Cargo | URL GitHub |
|---|:---:|---:|
| Daniel Alquinga | :technologist: Desarrollador |  |
| Daniel Baldeon | :technologist: Desarrollador |  |
| Bryan Miño | :technologist: Desarrollador |  |
| Wilson Segovia | :technologist: Desarrollador |  |
| Leonardo Tuguminago | :technologist: Desarrollador |  |

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

<img width="1192" height="737" alt="image-1" src="https://github.com/user-attachments/assets/0e31d918-7da4-43ad-8f40-5f73810f2d4b" />

### PASO 8: Informacion adicional del Servidor N8N


### PASO 9: Seccion de Gestor de Base de datos en N8N


**Salida Esperada**

<img width="676" height="276" alt="image-3" src="https://github.com/user-attachments/assets/2b2b42aa-f59c-4b24-9d16-bc466b74d5d6" />

### PASO 10: Configuracion de Credenciales 

 Parametros obtenidos del archivos .env del repositorio

```bash
    Host: postgres-db
    Database: postgres
    User: n8nuser
    Password: Super_Segura123!
```
**Salida Esperada**

<img width="1372" height="733" alt="image-4" src="https://github.com/user-attachments/assets/6c3987d2-5bf6-41fe-9ccf-ea62ee83e85a" />

### PASO 11: Verificar Ingresos.
    
   Se verifica  que la conexion sea Exitosa 

**Salida Esperada**

<img width="1331" height="725" alt="image-5" src="https://github.com/user-attachments/assets/1ac4dae2-c47e-4bd6-aa27-381509841bcd" />

### PASO 12:  Verifcacion de N8N con Postgres.

   Se verifica que la conexion de la base de datos este vinculada con el contenedor N8N.

**Salida Esperada**

<img width="1600" height="318" alt="image-6" src="https://github.com/user-attachments/assets/e812f85a-b49c-490b-b8bd-e53ed013a213" />


# 3. Conclusiones

- Se 

- Al ejecutar el análisis en cada push al repositorio, se identifica proactivamente vulnerabilidades en etapas tempranas del desarrollo, reduciendo riesgos de seguridad en producción.

- Docker Scout proporciona visibilidad completa sobre las vulnerabilidades en todas las capas de la imagen, facilitando la identificación de dependencias problemáticas en la aplicación FastAPI.

- GitHub Actions proporciona registros detallados de cada ejecución, creando un historial auditable de los estados de seguridad de la aplicación a lo largo del tiempo.

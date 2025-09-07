# **Airport Gap – API Testing**

Automatización de pruebas de la **[API RESTful Airport Gap](https://airportgap.com/)** usando **Postman y Newman**, validando endpoints principales. Incluye **tests positivos y negativos**, manejo de **autenticación con token**, **variables de entorno** y **reportes HTML/JSON**.

---

## **Tecnologías utilizadas:**

- **Postman** para la creación de la colección de pruebas y ejecución de requests.
- **Variables de entorno** para manejo seguro de tokens de autenticación y parámetros dinámicos.
- **JavaScript (Scripts de prueba)** para la validación de códigos de estado, datos de la respuesta y errores.
- **Newman** para la ejecución de la colección desde terminal y generación de reportes HTML y JSON.

---

## **Estructura del proyecto:**

```plaintext
airportgap-api-testing/
│
├── collections/
│ └── airportgap_postman.json # Colección de requests
├── environments/
│ └── airportgap_env.json # Variables de entorno (sin datos sensibles)
├── reports/
│ └── (reportes generados por Newman)
├── package.json # Dependencias y script de ejecución
└── README.md # Este archivo

---

## **Casos de prueba:**

### **Positivos:**

- Autenticación y obtención de token.
- Listado de aeropuertos y consulta por ID.
- Cálculo de distancias entre aeropuertos.
- Gestión de aeropuertos favoritos (crear, listar, modificar, eliminar).

### **Negativos:**

- Login con credenciales incorrectas.
- Solicitud de aeropuertos inexistentes.
- Cálculo de distancias sin parámetros requeridos.
- Creación de favorito con aeropuerto inválido.
- Obtención de favoritos sin token.

---

## **Cómo importar y ejecutar las pruebas:**

1. ###**Clonar el repositorio:**

```bash
git clone https://github.com/tu-usuario/airportgap-api-testing.git
cd airportgap-api-testing

2. ###**Generar token de autenticación:**

Para acceder a los endpoints que requieren autenticación, es necesario un token de autenticación. 
Para generarlo ingresa al link [Generación de token de la Airport Gap API](https://airportgap.com/tokens/new).

3. ###**Ejecución**: 

**Desde Postman:**

*Importar colección y ambiente*

- Abre Postman → Import → File → selecciona `airportgap_postman.json` y `airportgap_env.json`.  

*Configurar ambiente* 

- Coloca tu email y contraseña en las variables EMAIL y PASSWORD, respectivamente.
- La variable TOKEN se completará automáticamente al obtenerlo desde el endpoint /tokens.

*Ejecutar colección*  

- Selecciona la colección → Run → escoge el ambiente → Run Airport Gap API Tests. 
- Todos los tests se ejecutarán automáticamente y podrás ver los resultados en la ventana de Runner.  

**Desde Newman (CLI)**  

*Instalar dependencias*

```bash
npm install

*Configurar ambiente*

- Completar variables <EMAIL> y <PASSWORD> de tu cuenta Airport Gap en el archivo `airportgap_env.json`.
- La variable <TOKEN> se completará automáticamente al obtenerlo desde el endpoint `/tokens`.

*Ejecutar colección*

```bash
newman run collections/airportgap_postman.json \
-e environments/airportgap_env.example.json \
-r html,json \
--reporter-html-export reports/airportgap_report.html \
--reporter-json-export reports/airportgap_report.json

- Abrir `/reports` para visualizar los reportes HTML y JSON.

---

## **Autora:**

**Cristina Leonor Algañaraz Rosado**
Proyecto para portfolio QA | Automatización de APIs
# Informe de Práctica: Contenerización de Aplicación React con Docker

---

# 1. Título

## Implementación y despliegue de una aplicación React mediante contenedores Docker y servicio backend simulado

---

# 2. Tiempo de duración

**Tiempo estimado:** 120 minutos.

---

# 3. Fundamentos

Docker es una plataforma de virtualización ligera que permite crear, ejecutar y administrar aplicaciones dentro de contenedores. Un contenedor es un entorno aislado que incluye todo lo necesario para ejecutar una aplicación, como librerías, dependencias, archivos de configuración y código fuente. Gracias a esto, las aplicaciones pueden ejecutarse de forma idéntica en distintos sistemas operativos y entornos de desarrollo.

En el desarrollo web moderno, Docker se ha convertido en una herramienta fundamental debido a que facilita el despliegue y mantenimiento de aplicaciones frontend y backend. En esta práctica se trabajó con una aplicación desarrollada en React, una biblioteca JavaScript utilizada para construir interfaces de usuario modernas e interactivas.

El proceso de contenerización consiste en crear un archivo llamado `Dockerfile`, el cual contiene una serie de instrucciones que Docker utiliza para construir una imagen. Una imagen Docker funciona como una plantilla preparada para ejecutar posteriormente uno o varios contenedores.

Además del frontend React, fue necesario utilizar un backend simulado mediante MockAPI. Este backend permite generar datos de prueba para que el frontend pueda consumir información y funcionar correctamente sin necesidad de desarrollar un servidor real.

Docker ofrece múltiples ventajas importantes dentro del desarrollo de software:

- Portabilidad entre diferentes sistemas operativos.
- Facilidad de despliegue.
- Aislamiento de aplicaciones y dependencias.
- Escalabilidad.
- Compatibilidad entre entornos de desarrollo y producción.
- Simplificación de configuraciones complejas.

Durante la práctica también se utilizaron herramientas como Git para clonar repositorios, Node.js y npm para administrar dependencias, además de comandos Docker para construir imágenes y ejecutar contenedores.

La contenerización de aplicaciones web es ampliamente utilizada en entornos empresariales y plataformas cloud, permitiendo automatizar procesos y facilitar el trabajo colaborativo entre desarrolladores.

---

# 4. Conocimientos previos

Para realizar esta práctica el estudiante necesita tener claros los siguientes temas:

- Comandos básicos Linux.
- Manejo de terminal o consola.
- Uso básico de Git y GitHub.
- Manejo de navegador web.
- Conceptos básicos de Docker.
- Uso de Node.js y npm.
- Configuración de puertos.
- Manejo básico de React.
- Creación de archivos Dockerfile.

---

# 5. Objetivos a alcanzar

- Implementar contenedores Docker para aplicaciones frontend.
- Ejecutar aplicaciones React dentro de Docker.
- Crear imágenes Docker personalizadas.
- Manipular archivos Dockerfile.
- Ejecutar múltiples servicios simultáneamente.
- Verificar la comunicación entre frontend y backend.
- Aplicar conceptos básicos de virtualización ligera.

---

# 6. Equipo necesario

- Computador con sistema operativo Windows/Linux/MacOS.
- Docker Desktop instalado.
- Node.js instalado.
- Git instalado.
- Navegador web.
- Editor de código Visual Studio Code.
- Acceso a Internet.

---

# 7. Material de apoyo

- Documentación oficial de Docker.
- Documentación oficial de React.
- Documentación oficial de Node.js.
- Guía de laboratorio.
- Cheat Sheet Linux.

## Repositorios utilizados

### Frontend React

```text
https://github.com/Daviddotcoms/suda-frontend-s6
```

### Backend simulado

```text
https://github.com/Daviddotcoms/mockAPI
```

---

# 8. Procedimiento

## Paso 1: Clonar el repositorio frontend

```bash
git clone https://github.com/Daviddotcoms/suda-frontend-s6.git
```

---

## Paso 2: Ingresar al directorio del proyecto

```bash
cd suda-frontend-s6
```

---

## Paso 3: Instalar dependencias

```bash
npm install
```

---

## Paso 4: Ejecutar el proyecto localmente

```bash
npm run dev
```

Con este comando se verificó que el frontend funcionara correctamente en localhost.

---

## Paso 5: Clonar el backend simulado

```bash
git clone https://github.com/Daviddotcoms/mockAPI.git
```

---

## Paso 6: Ejecutar el backend

```bash
cd mockAPI
npm install
npm start
```

El backend quedó ejecutándose para proporcionar datos al frontend.

---

## Paso 7: Crear el archivo Dockerfile

Se creó el archivo `Dockerfile` con la siguiente configuración:

```Dockerfile
FROM node:20

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 5173

CMD ["npm", "run", "dev", "--", "--host"]
```

---

## Paso 8: Construir la imagen Docker

```bash
docker build -t react-frontend .
```

---

## Paso 9: Verificar imágenes Docker

```bash
docker images
```

---

## Paso 10: Crear el contenedor

```bash
docker run -d -p 5173:5173 --name frontend-react react-frontend
```

---

## Paso 11: Verificar contenedores activos

```bash
docker ps
```

---

## Paso 12: Acceder a la aplicación

Se abrió el navegador en:

```text
http://localhost:5173
```

La aplicación React logró ejecutarse correctamente dentro del contenedor Docker y conectarse al backend simulado.

---

# 9. Resultados esperados

Al finalizar la práctica se obtuvo una aplicación React ejecutándose correctamente dentro de un contenedor Docker. Además, el frontend logró comunicarse correctamente con el backend simulado, permitiendo visualizar la información esperada en el navegador.

Se comprobó que Docker facilita el despliegue y ejecución de aplicaciones web mediante entornos aislados y portables.

---

# 10. Evidencias

 <img width="921" height="606" alt="image" src="https://github.com/user-attachments/assets/3cbdab37-8fa9-4e06-9c22-7285a12360b6" />
 <img width="921" height="603" alt="image" src="https://github.com/user-attachments/assets/821d4714-9777-4012-ba7f-7e33fb48b756" />
<img width="921" height="601" alt="image" src="https://github.com/user-attachments/assets/16f731d7-a567-4662-9aa6-8497cef566c9" />
<img width="921" height="317" alt="image" src="https://github.com/user-attachments/assets/b9be13a8-0d4c-4ac5-bdd8-8300be098dba" />

# 11. Bibliografía

- Merkel, D. (2014). *Docker: lightweight Linux containers for consistent development and deployment*. Linux Journal.
- Turnbull, J. (2014). *The Docker Book*. Docker Series.
- Freeman, E. (2019). *React: Up and Running*. O'Reilly Media.
- Docker Inc. (2026). Docker Documentation.
- React Team. (2026). React Documentation.
- Node.js Foundation. (2026). Node.js Documentation.
- GitHub Documentation. (2026). GitHub Docs.

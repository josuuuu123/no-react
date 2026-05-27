# Informe de Práctica: Contenerización de Aplicación React con Docker

---

# 1. Título

## Implementación y despliegue de una aplicación React mediante contenedores Docker y servicio backend simulado

---

# 2. Tiempo de duración

**Tiempo estimado:** 120 minutos.

---

# 3. Fundamentos

Docker es una plataforma de virtualización ligera que permite crear, ejecutar y administrar aplicaciones dentro de contenedores. Un contenedor es un entorno aislado que incluye todo lo necesario para ejecutar una aplicación, como librerías, dependencias, archivos de configuración y código fuente. Esto permite que las aplicaciones funcionen de manera uniforme en cualquier sistema operativo que tenga Docker instalado.

En el desarrollo web moderno, Docker se ha convertido en una herramienta fundamental debido a que facilita la portabilidad y el despliegue de aplicaciones frontend y backend. En esta práctica se trabajó con una aplicación desarrollada en React, una biblioteca JavaScript utilizada para construir interfaces de usuario dinámicas y modernas.

El proceso de contenerización consiste en crear un archivo llamado Dockerfile, el cual contiene instrucciones para construir una imagen Docker. Esta imagen funciona como una plantilla que posteriormente puede ejecutarse en forma de contenedor.

Además del frontend React, fue necesario utilizar un backend simulado mediante MockAPI, el cual permite proporcionar datos falsos o de prueba para que el frontend pueda consumir servicios API sin necesidad de un backend real.

La arquitectura implementada permite separar responsabilidades entre frontend y backend, simulando un entorno profesional de desarrollo basado en microservicios.

Docker proporciona varias ventajas importantes:

- Portabilidad entre sistemas operativos.
- Facilidad de despliegue.
- Aislamiento de aplicaciones.
- Escalabilidad.
- Compatibilidad entre entornos de desarrollo y producción.

En esta práctica también se utilizaron comandos básicos de Git para clonar repositorios, comandos Docker para construir imágenes y ejecutar contenedores, además de herramientas de desarrollo frontend como Node.js y npm.

La contenerización de aplicaciones React es ampliamente utilizada en entornos cloud, servidores Linux y plataformas DevOps modernas, permitiendo automatizar despliegues y simplificar la administración de aplicaciones web.

---

## Figura 3-1. Arquitectura Docker Frontend + Backend

![Arquitectura Docker](https://www.docker.com/wp-content/uploads/2022/03/Moby-logo.png)

---

## Figura 3-2. Contenedores Docker y React

![Docker React](https://miro.medium.com/v2/resize:fit:1200/1*Xh9fK0A5X0h8p5J8x1z4EA.png)

---

# 4. Conocimientos previos

Para realizar esta práctica el estudiante necesita tener claros los siguientes temas:

- Comandos básicos Linux.
- Manejo de terminal o consola.
- Uso básico de Git y GitHub.
- Manejo de navegador web.
- Conceptos básicos de Docker.
- Conceptos básicos de contenedores.
- Uso de Node.js y npm.
- Conocimientos básicos de React.
- Configuración de puertos en aplicaciones web.
- Manejo de archivos Dockerfile.

---

# 5. Objetivos a alcanzar

- Implementar contenedores Docker para aplicaciones frontend.
- Ejecutar aplicaciones React dentro de Docker.
- Crear imágenes Docker personalizadas.
- Manipular archivos Dockerfile.
- Comprender el funcionamiento de servicios frontend y backend.
- Ejecutar múltiples contenedores simultáneamente.
- Verificar la comunicación entre frontend y backend.
- Aplicar conceptos de virtualización ligera.

---

# 6. Equipo necesario

- Computador con sistema operativo Windows/Linux/MacOS.
- Docker Desktop instalado.
- Node.js instalado.
- Git instalado.
- Navegador web (Google Chrome, Firefox o Edge).
- Acceso a Internet.
- Cuenta de GitHub.
- Visual Studio Code u otro editor de código.

---

# 7. Material de apoyo

- Documentación oficial de Docker.
- Documentación oficial de React.
- Documentación oficial de Node.js.
- Guía de laboratorio.
- Cheat Sheet Linux.

## Repositorios utilizados

Frontend React:

```text
https://github.com/Daviddotcoms/suda-frontend-s6
```

Backend simulado:

```text
https://github.com/Daviddotcoms/mockAPI
```

---

# 8. Procedimiento

## Paso 1: Clonar el repositorio frontend

Se utilizó Git para clonar el repositorio del proyecto React.

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

Se instalaron las dependencias necesarias utilizando npm.

```bash
npm install
```

---

## Paso 4: Ejecutar el proyecto localmente

```bash
npm run dev
```

El proyecto se ejecutó correctamente en el navegador mediante localhost.

---

## Figura 8-1. Ejecución 

<img width="1366" height="636" alt="image" src="https://github.com/user-attachments/assets/1cc6d120-d53e-403b-878e-c5ae37fea8b2" />


---

## Paso 5: Clonar el backend simulado

```bash
git clone https://github.com/Daviddotcoms/mockAPI.git
```

---

## Paso 6: Ejecutar el backend simulado

```bash
cd mockAPI
npm install
npm start
```

El backend quedó ejecutándose para proporcionar datos al frontend.

---

## Figura 8-2. Backend MockAPI en ejecución

<img width="523" height="397" alt="image" src="https://github.com/user-attachments/assets/5b9b05e8-f41c-418a-a4a3-6ca54a52f5f3" />


---

## Paso 7: Crear el archivo Dockerfile

Se creó el archivo Dockerfile con la siguiente configuración:

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

## Figura 8-3. Construcción de imagen Docker

![Docker Build](https://www.docker.com/wp-content/uploads/2022/03/vertical-logo-monochromatic.png)

---

## Paso 9: Verificar imágenes Docker

```bash
docker images
```

---

## Paso 10: Crear y ejecutar el contenedor

```bash
docker run -d -p 5173:5173 --name frontend-react react-frontend
```

---

## Paso 11: Verificar contenedores activos

```bash
docker ps
```

---

## Figura 8-4. Contenedor Docker en ejecución

![Docker Container](https://www.docker.com/wp-content/uploads/2022/03/Moby-logo.png)

---

## Paso 12: Acceder a la aplicación

Se abrió el navegador en la siguiente dirección:

```text
http://localhost:5173
```

La aplicación React se ejecutó correctamente desde el contenedor Docker y logró conectarse al backend simulado.

---

# 9. Resultados esperados

Al finalizar la práctica se obtuvo una aplicación React ejecutándose dentro de un contenedor Docker, permitiendo acceder al sistema desde el navegador mediante localhost.

Además, se logró establecer comunicación entre el frontend y el backend simulado, verificando el correcto funcionamiento de la aplicación.

Los resultados obtenidos permiten comprobar que Docker facilita la implementación de aplicaciones web de forma portable y aislada.

---

## Figura 9-1. Resultado final de la aplicación

![Resultado Final](https://react.dev/images/brand/logo_dark.svg)

---

# 10. Bibliografía

- Merkel, D. (2014). *Docker: lightweight Linux containers for consistent development and deployment*. Linux Journal.
- Turnbull, J. (2014). *The Docker Book*. Docker Series.
- Freeman, E. (2019). *React: Up and Running*. O'Reilly Media.
- Node.js Foundation. (2026). Node.js Documentation.
- Docker Inc. (2026). Docker Documentation.
- React Team. (2026). React Documentation.
- GitHub Documentation. (2026). GitHub Docs.

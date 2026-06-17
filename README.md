# Listener-Notificaciones-App

Microservicio desarrollado en Node.js y Express para el monitoreo en tiempo real de datos almacenados en Firebase Firestore.

El sistema detecta automáticamente nuevas lecturas provenientes de sensores IoT, analiza los parámetros registrados, identifica condiciones fuera de rango y envía notificaciones push a dispositivos móviles mediante Firebase Cloud Messaging (FCM).

Actualmente se encuentra desplegado en Render y opera de forma continua para proporcionar alertas en tiempo real a los usuarios de la plataforma.

---

# Arquitectura General

```text
Sensores IoT
      │
      ▼
Firebase Firestore
      │
      ▼
Realtime Listener
(Node.js + Firebase Admin)
      │
      ▼
Procesamiento de Datos
      │
      ▼
Firebase Cloud Messaging
      │
      ▼
Aplicaciones Móviles
```

---

# Descripción General

Este proyecto implementa una arquitectura basada en eventos utilizando Firebase Firestore como fuente de datos en tiempo real.

Cada vez que se registra una nueva lectura en la base de datos, el sistema:

- Detecta automáticamente el nuevo registro.
- Obtiene los parámetros monitoreados.
- Analiza los datos recibidos.
- Calcula indicadores complementarios para apoyar la toma de decisiones.
- Identifica condiciones anómalas.
- Genera alertas automáticas.
- Envía notificaciones push a los dispositivos registrados.

Todo el proceso ocurre en tiempo real sin necesidad de consultas periódicas.

---

# Tecnologías Utilizadas

## Backend

- Node.js
- Express.js

## Firebase

- Firebase Firestore
- Firebase Admin SDK
- Firebase Cloud Messaging (FCM)

## Servicios Complementarios

- Axios

## Seguridad

- bcryptjs
- crypto

## Infraestructura

- Render

---

# Requisitos Previos

Antes de ejecutar el proyecto es necesario contar con:

- Node.js 18 o superior
- npm
- Proyecto Firebase configurado
- Credenciales de Firebase Admin SDK

Verificar instalación:

```bash
node -v
npm -v
```

---

# Clonar el Proyecto

```bash
git clone https://github.com/BlackFenix937/firestore-realtime-listener-fcm.git
```

Ingresar al directorio:

```bash
cd firestore-realtime-listener-fcm
```

---

# Instalar Dependencias

```bash
npm install
```

---

# Configuración

El proyecto utiliza Firebase Admin SDK para conectarse a Firestore y Firebase Cloud Messaging.

Es necesario configurar las credenciales correspondientes mediante variables de entorno antes de ejecutar el servicio.

Además, para entornos desplegados en Render, puede configurarse una URL pública utilizada por el sistema de mantenimiento de actividad del servicio.

---

# Ejecutar el Proyecto en local

```bash
node index.js
```

Servidor por defecto:

```text
http://localhost:8080
```

---

# Estructura del Proyecto

```text
src/
│
├── config/
│   └── Configuración de Firebase
│
├── listeners/
│   └── Escucha de eventos en Firestore
│
├── services/
│   ├── Procesamiento de datos
│   ├── Notificaciones push
│   └── Servicios auxiliares
│
├── app.js
│
├── index.js
├── package.json
└── package-lock.json
```

---

# Monitoreo en Tiempo Real

El sistema mantiene una suscripción activa sobre Firestore para detectar nuevos registros inmediatamente después de ser almacenados.

Esto permite:

- Procesamiento instantáneo de eventos.
- Baja latencia.
- Menor consumo de recursos.
- Eliminación de procesos de consulta repetitiva.

---

# Procesamiento de Datos

Las lecturas recibidas son evaluadas automáticamente para determinar si los parámetros monitoreados se encuentran dentro de los rangos establecidos.

Entre los datos procesados se encuentran:

- Oxígeno disuelto.
- pH.
- Temperatura.
- Sólidos disueltos.
- Turbidez.

Además, el sistema genera indicadores complementarios que ayudan a interpretar las condiciones observadas y fortalecer la detección temprana de anomalías.

---

# Sistema de Alertas

Cuando se detectan condiciones fuera de los rangos establecidos, el sistema genera alertas automáticas que son enviadas a los dispositivos registrados.

Las notificaciones incluyen información relevante sobre el evento detectado para facilitar una respuesta rápida por parte de los usuarios.

---

# Firebase Cloud Messaging

El envío de alertas se realiza mediante Firebase Cloud Messaging (FCM).

Esto permite distribuir notificaciones push en tiempo real hacia dispositivos móviles conectados a la plataforma, incluso cuando la aplicación se encuentra en segundo plano.

---

# Mantenimiento del Servicio

El proyecto incorpora mecanismos de mantenimiento diseñados para entornos de despliegue en la nube.

Estos procesos permiten:

- Mantener la disponibilidad del servicio.
- Reducir tiempos de respuesta.
- Evitar periodos prolongados de inactividad.
- Garantizar la continuidad de la escucha en tiempo real.

---

# Objetivo del Proyecto

Desarrollar una plataforma de monitoreo en tiempo real capaz de procesar automáticamente lecturas provenientes de sensores, detectar anomalías en parámetros de calidad de agua y notificar de manera inmediata a los usuarios mediante Firebase Cloud Messaging.

El sistema busca facilitar la supervisión remota de estanques y apoyar la toma de decisiones mediante alertas tempranas generadas a partir de datos almacenados en Firebase Firestore.

---

# Licencia

Proyecto desarrollado con fines académicos, tecnológicos y de monitoreo de calidad del agua.

---

# Autor

**BlackFenix937** || **Andy de Jesús González Alcázar**

Microservicio desarrollado en Node.js para monitoreo de sensores, análisis de datos de calidad del agua y generación de alertas en tiempo real mediante Firebase Cloud Messaging.

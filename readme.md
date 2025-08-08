
Este repositorio proporciona una configuración de Docker Compose para desplegar el laboratorio SOC SIEM

---

## 🛠️ Herramientas Incluidas

* **🛡️ Wazuh:** Plataforma de seguridad de código abierto (SIEM & XDR).
* **🐝 TheHive:** Plataforma escalable para respuesta a incidentes (SOAR).
* **🤖 N8N:** Herramienta de automatización de flujos de trabajo "low-code".
* **🚢 Portainer:** Interfaz de usuario para gestionar entornos de contenedores Docker.

---

## ✅ Requisitos

* [**Docker**](https://docs.docker.com/get-docker/)
* [**Docker Compose**](https://docs.docker.com/compose/install/)

---

## 🚀 Instalación y Puesta en Marcha

### 1. Clonar el Repositorio

```bash
git clone [https://github.com/andresmunozdev/labsocsiemipsss.git](https://github.com/andresmunozdev/labsocsiemipsss.git)
cd labsocsiemipsss
```

### 2. Ejecutar Instalación de Wazuh

El despliegue se realiza en dos etapas:

**a) Generar los certificados SSL para Wazuh:**

```bash
docker-compose -f generate-indexer-certs.yml up -d 
```

Espera unos segundos a que finalice. Puedes verificar su estado con `docker-compose logs -f <nombre-contenedor>`. Una vez que veas que ha completado la generación de certificados, puedes detenerlo si lo deseas, o simplemente proceder al siguiente paso.


**b) Ejecutar instalación Wazuh:**

```bash
docker-compose up -d
```

¡Listo! Servicios se iniciarán en segundo plano.

---



## 💻 Acceso a los Servicios

Podrás acceder a las interfaces web de cada herramienta a través de los siguientes puertos (o los que hayas configurado en tu archivo `.env`):

| Servicio      | URL de Acceso               | 
| :------------ | :-------------------------- | 
| **Wazuh**     | `https://localhost:443`     | 
| **TheHive**   | `http://localhost:9002`     | 
| **N8N**       | `http://localhost:5678`     | 
| **Portainer** | `https://localhost:9443`    | 

**Nota:** Reemplaza `localhost` con la IP de tu servidor si accedes de forma remota.

---

## 🛑 Gestionar Contenedores

* **Ver los logs de todos los contenedores:**
    ```bash
    docker-compose logs -f
    ```
* **Detener y eliminar todos los contenedores:**
    ```bash
    docker-compose down
    ```
* **Detener sin eliminar los volúmenes de datos:**
    ```bash
    docker-compose stop
    ```

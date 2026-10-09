# 🚀 CHAT-LIVE2025 — Plataforma Multiservicio & Chat en Tiempo Real

Entorno multi-servicio orientado al despliegue automatizado en servidores Linux (Ubuntu Server). Integra aplicaciones web interactivas, un chat distribuido en tiempo real mediante WebSockets, un catálogo de entretenimiento y un sistema de gestión y enrutamiento con Nginx y PM2.

---

## 🏗️ Arquitectura y Servicios

El sistema organiza múltiples aplicaciones web desacopladas, administradas por un reverse proxy Nginx y orquestadas con scripts de automatización:

| Servicio | Puerto | Stack Tecnológico | Descripción |
| :--- | :---: | :--- | :--- |
| **Sitio 1 — Chat Real-Time** | `81` | **Node.js, Express, Socket.io, JS** | Chat en tiempo real bidireccional con salas y emisión de eventos. |
| **Sitio 2 — Calculadora IMC** | `82` | **HTML5, CSS3, JavaScript** | Herramienta interactiva para cálculo y evaluación del Índice de Masa Corporal. |
| **Sitio 3 — Portal Web** | `83` | **HTML5, Modern CSS, JavaScript** | Portal institucional/landing estática servida de alta velocidad. |
| **Sitio 4 — Movie Catalog** | `3000` | **Node.js, Express, MySQL / Nginx Estático** | Plataforma de catálogo de cine con simulación de datos o backend relacional. |

---

## 📂 Estructura del Repositorio

```bash
CHAT-LIVE2025/
├── .github/workflows/     # Automatización CI/CD con GitHub Actions
├── nginx/                 # Archivos de configuración modular para Nginx
│   ├── sitio2             # Configuración de host virtual para puerto 82
│   └── sitio3             # Configuración de host virtual para puerto 83
├── sitio1/                # Backend y Frontend del Chat (Node.js + Socket.io)
│   ├── server.js          # Servidor HTTP y Socket.io
│   └── public/            # Cliente web interactivo (app.js, index.html)
├── sitio2/                # Calculadora IMC (estático)
├── sitio3/                # Sitio web estático
├── sitio4_static/         # Aplicación de catálogo de cine (versión estática desacoplada)
├── clean_install.sh       # 🛠️ Script maestro de instalación limpia y configuración integral
├── repair_server.sh       # Script de verificación y restauración rápida de servicios
├── setup_server.sh        # Script base de aprovisionamiento
└── setup_db.sql           # Script SQL para base de datos relacional y usuarios
```

---

## 🛠️ Tecnologías Utilizadas

- **Backend:** Node.js, Express, Socket.io
- **Servidor Web & Proxy:** Nginx (Virtual Hosts, Reverse Proxy)
- **Base de Datos:** MySQL
- **Gestor de Procesos:** PM2 / Systemd
- **Frontend:** Vanilla HTML5, CSS3 moderno, JavaScript ES6+
- **DevOps / CI-CD:** Bash scripting, GitHub Actions, Ubuntu Server

---

## 🚀 Despliegue Rápido en Servidor

### 1. Clonar el repositorio en el servidor
```bash
git clone https://github.com/NE0NOE/CHAT-LIVE2025.git
cd CHAT-LIVE2025
```

### 2. Ejecutar el Script Maestro de Instalación
El script `clean_install.sh` automatiza la instalación de dependencias del sistema (Node.js, Nginx, MySQL, PM2), configura los bloques de servidor en Nginx y levanta todos los servicios:

```bash
chmod +x clean_install.sh
sudo ./clean_install.sh
```

### 3. Verificar el estado de los servicios
- Comprobar procesos Node/PM2:
  ```bash
  pm2 list
  ```
- Comprobar estado de Nginx:
  ```bash
  sudo systemctl status nginx
  ```

---

## 🔐 Configuración de Base de Datos (Opcional)

Si utilizas la versión dinámica de la aplicación de cine (`sitio4`), inicializa la base de datos con:
```bash
sudo mysql < setup_db.sql
```

---

## 👤 Autor

- **Mendell Noe Parrales Molina** ([@NE0NOE](https://github.com/NE0NOE))

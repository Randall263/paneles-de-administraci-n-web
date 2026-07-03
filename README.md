# Paneles de Administración Web 🖥️

Este repositorio documenta la transformación de un equipo (ThinkCentre M715q Tiny) en un servidor doméstico completamente funcional e independiente. Aquí se recopilan los scripts y comandos de instalación para desplegar diversas plataformas de gestión web, contenedores y configuraciones de red, ideales para administrar un entorno basado en un sistema operativo de bajos recursos (Low-Resource OS) y un stack LAMP.

## 🛠️ Arquitectura y Herramientas

El servidor está diseñado para contar con un nivel **Avanzado** de gestión remota, integrando las siguientes tecnologías:

* **Hardware Base:** ThinkCentre M715q Tiny.
* **Gestión Remota y Redes:** Tailscale VPN.
* **Paneles y Contenedores:** Webmin, CasaOS, Docker, Cockpit.
* **Entorno de Servidor:** LAMP Stack.

---

## 📦 Guías de Instalación

A continuación, se detallan los comandos necesarios para desplegar los diferentes paneles de administración documentados en este repositorio.

### 1. Webmin

Webmin es una interfaz basada en web para la administración de sistemas Unix.

**A. Debian / Ubuntu**
```bash
# 1. Actualiza los paquetes del sistema
sudo apt update && sudo apt upgrade -y

# 2. Instala las dependencias necesarias
sudo apt install software-properties-common apt-transport-https wget -y

# 3. Descarga e importa la clave GPG de Webmin
wget -q [http://www.webmin.com/jcameron-key.asc](http://www.webmin.com/jcameron-key.asc) -O- | sudo gpg --dearmor -o /usr/share/keyrings/webmin.gpg

# 4. Añade el repositorio oficial
echo "deb [signed-by=/usr/share/keyrings/webmin.gpg] [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge contrib" | sudo tee /etc/apt/sources.list.d/webmin.list

# 5. Actualiza e instala Webmin
sudo apt update
sudo apt install webmin -y

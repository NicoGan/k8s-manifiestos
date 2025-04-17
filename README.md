
---

## 🌐 Proyecto de despliegue web con Kubernetes + Minikube

Este proyecto permite desplegar una página web de forma local usando **Minikube**, **Docker**, y **manifiestos de Kubernetes**. 

---

### ✅ Requisitos previos

Antes de comenzar, asegurate de tener instalado:

- **Docker Desktop**  
- **Minikube**  
- **Git**  
- **Sistema operativo Linux** o una máquina virtual que lo emule (como **WSL** en Windows)

---

### 📦 Clonar los repositorios

Vas a necesitar descargar los siguientes proyectos:

1. **Repositorio del sitio web:**
```bash
git clone https://github.com/NicoGan/web_tp_cn.git
```

2. **Repositorio de los manifiestos de Kubernetes:**
```bash
git clone https://github.com/NicoGan/k8s-manifiestos.git
```

---
### 📁 Importante si usás WSL o una VM

Si estás usando **WSL** o una **máquina virtual Linux**, debés mover las carpetas de los repositorios **dentro del sistema de archivos de Linux** para que Minikube pueda montarlas correctamente.

📌 Por ejemplo:

1. Copiá las carpetas a `/home/tu_usuario/`  
2. Asegurate de que estén accesibles desde el entorno Linux donde vas a correr Minikube.

---


### 🚀 Iniciar Minikube con montaje de archivos

Desde una terminal en Linux (o WSL), posicionado en el mismo nivel donde tenés tu carpeta `web_tp_cn`, ejecutá el siguiente comando:

```bash
minikube start --mount --mount-string="${PWD}/web_tp_cn:/mnt/web"
```

🔹 **Importante:**  
- Reemplazá `web_tp_cn` por la **ruta real donde tengas el index.html** si es diferente.  
- Lo que hace este comando es montar tu carpeta local dentro del entorno de Minikube en la ruta `/mnt/web`.

---

### 🐳 Verificar el montaje

Abrí **Docker Desktop** y verificá que el volumen `/mnt/web` se haya montado correctamente dentro del contenedor de Minikube. Esto asegura que tus archivos están accesibles para servir la web.

---

### 📄 Aplicar los manifiestos de Kubernetes

Estando en el proyecto donde clonaste los manifiestos, ejecutá:

```bash
kubectl apply -R -f k8s-manifiestos/.
```

🔹 Esto aplicará **todos los manifiestos** en esa carpeta de forma recursiva.

---

### 📡 Ver los servicios en ejecución

Verificá qué servicios están activos con:

```bash
kubectl get service
```

---

### 🌍 Acceder a la página web

Finalmente, ejecutá:

```bash
minikube service web-service
```

Esto abrirá tu navegador con la **página desplegada localmente desde Minikube** 🚀

---

### 🏁 ¡Listo!

Ya estás corriendo tu sitio web desde un entorno simulado de Kubernetes usando Minikube, con los archivos montados desde tu máquina local. Ideal para prácticas reales de DevOps/Cloud.

---

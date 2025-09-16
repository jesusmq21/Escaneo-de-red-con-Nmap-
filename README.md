# 🔍 Laboratorio de Escaneo de Red con Nmap

**Autor:** Jesús Eduardo Machuca Quintero  
**Fecha:** 10 Sep 2025  
**Objetivo:** Documentar el uso de Nmap para reconocimiento de red como evidencia para mi portafolio de ciberseguridad (rol: Analista SOC).

---

## 📌 Resumen
En este laboratorio se simuló un entorno con una máquina atacante (Kali Linux) y una máquina víctima (Ubuntu) para ejecutar escaneos de descubrimiento, puertos y servicios con **Nmap**. Aquí se documentan los comandos usados, los resultados (capturas) y un breve análisis.

---

## 🖥️ Entorno del laboratorio
- **Máquina atacante (Kali):** `192.168.0.7`  
- **Máquina víctima (Ubuntu):** `192.168.0.106`  
- Virtualización: VirtualBox (modo NAT/Bridge según configuración)

---

## 📂 Estructura del repositorio
```

/ (repo root)
├─ images/            # capturas de pantalla (pon aquí tus imágenes)
├─ scripts/           # (opcional) comandos o scripts utilizados
└─ README.md          # este archivo

````

---

## 🔎 Comandos ejecutados y resultados (ejemplos)

### 1) Descubrimiento de hosts
Comando:
```bash
nmap -sn 192.168.0.0/24
````

Captura:
![Descubrimiento de hosts.(Images
/descubrimientodehost.png)

---

### 2) Escaneo de puertos específicos

Comando:

```bash
nmap -p 22,80,443 192.168.0.106
```

Captura:
![Escaneo puertos específicos.(images/escaneocondetecciondeservicios.png)

---

### 3) Escaneo con detección de servicios y OS (escaneo completo)

Comando:

```bash
nmap -A 192.168.0.106
```

Captura:
![Escaneo completo -A](images/nmap_A_scan.png)

---

### 4) (Opcional) Escaneo SYN rápido

Comando:

```bash
nmap -sS 192.168.0.106
```

Captura (si la tienes):
![Escaneo SYN](images/nmap_sS.png)

---

### 5) (Opcional) Detección de versiones

Comando:

```bash
nmap -sV 192.168.0.106
```

Captura (si la tienes):
![Detección de versiones](images/nmap_sV.png)

---

## 📋 Resultados resumidos

* Host activo: `192.168.0.106`.
* Puertos/servicios detectados (ejemplo — reemplaza con tus resultados reales):

  * `22/tcp` — open — ssh
  * `80/tcp` — open — http
  * `443/tcp` — closed / filtered (ajusta según tu salida)
* Información adicional: `nmap -A` reportó \[sistema operativo aproximado / versiones] — ver captura.

> **Sustituye la lista anterior con los puertos/servicios exactos que tú encontraste.**

---

## 🧠 Análisis (contexto SOC)

* El descubrimiento de hosts permite identificar activos que deben ser monitorizados.
* Puertos abiertos como SSH/HTTP deben tener control de acceso, parches y logs activados.
* Identificar versiones ayuda a priorizar parches si existen CVE conocidos.
* Documentar estos pasos demuestra capacidad de reconocimiento y reporting para un SOC.

---

## ✅ Recomendaciones

* Cerrar o restringir puertos innecesarios.
* Actualizar servicios con versiones vulnerables.
* Implementar alertas en el SIEM para servicios expuestos.
* Mantener documentación y capturas en el portafolio para mostrar trazabilidad.

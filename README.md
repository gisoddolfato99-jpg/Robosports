![image alt](https://github.com/gisoddolfato99-jpg/Robosports/blob/ad2694a118b114337a687732f3f99ac671aa8314/feature/supoer.jpg)

<br>

---
<br>


# WRO RoboSports - [Kicktronics] 🎾

¡Bienvenidos al repositorio oficial de nuestro equipo para la categoría **WRO RoboSports**! Aquí encontrarás la documentación técnica, el diseño de hardware y el código fuente de nuestros dos robots autónomos.

## Nuestro Equipo
* **Categoría de Edad:** [Ej. 11-19 años / Senior]
* **Integrantes:**
  
* **Yuming Zhen Wang**
  <div align="left">
  <img src="https://github.com/gisoddolfato99-jpg/Robosports/blob/dc21c7bda6b01fd8de196f96a23b14380affde4b/feature/WhatsApp%20Image%202026-08-24%20at%203.07.23%20PM.jpeg" width="300" />
</div>
<br>

* **Valerie Artavia Céspedes**
    <div align="left">
  <img src="https://github.com/gisoddolfato99-jpg/Robosports/blob/dc21c7bda6b01fd8de196f96a23b14380affde4b/feature/WhatsApp%20Image%202026-08-24%20at%203.07.22%20PM.jpeg" width="300" />
</div>
<br>

* **Maykel Gabriel Francis Hernández**
    <div align="left">
  <img src="feature/WhatsApp Image 2026-08-24 at 3.07.22 PM (1).jpeg" width="300" height="400" />
</div>
  
* **Tutor:** Elkira Francis Hernández

---

## Descripción de los Robots 🤖

Para construir los robots, utilizamos dos idénticos, pero con una distinta estructura de sensores y diferente programación.


> [!IMPORTANT]
> **Hardware y Componentes**
> * **Controlador Principal:** LEGO SPIKE Prime
> * **Actuadores:** 2x Motores grandes para tracción, 1x Motor mediano para el mecanismo de golpeo
> * **Sensores:** 1x Giroscopio interno, 2x Sensores de color para detección de bola rosa, 1x sensor de fuerza para los golpes

<br>

--- 

###  Galería de Fotos

<br>

<div align="center"><table><tr>Robot del muro</tr><tr><td>
<img src="https://github.com/gisoddolfato99-jpg/Robosports/blob/fb2c760a20bfd880a7ba884b4ba6023ceec8b445/feature/prototipo/1/WhatsApp%20Image%202026-08-24%20at%203.55.47%20PM.jpeg"/></td><td>
<img src="https://github.com/gisoddolfato99-jpg/Robosports/blob/fb2c760a20bfd880a7ba884b4ba6023ceec8b445/feature/prototipo/1/1a.jpeg"/></td></tr></table></div>

<br>

<div align="center"><table><tr>Robot de la rampa</tr><tr><td>
<img src="https://github.com/gisoddolfato99-jpg/Robosports/blob/5d15b8e690788a2a1fb1196902a3e4971874338b/feature/prototipo/1/WhatsApp%20Image%202026-08-24%20at%203.55.55%20PM.jpeg"/></td><td>
<img src="https://github.com/gisoddolfato99-jpg/Robosports/blob/5d15b8e690788a2a1fb1196902a3e4971874338b/feature/prototipo/1/WhatsApp%20Image%202026-08-24%20at%203.55.59%20PM.jpeg"/></td></tr></table></div>



---
<br>

> [!IMPORTANT]
> ### 🕹️ Roles en la Cancha
> * **Robot 1 (Robot del muro):** Tira las bolas mediante los choques.
> 
> * **Robot 2 (Robot de la rampa):** Tira las bolas cuando detecta un colór en específico.

### 💻 Arquitectura del Código

**El robot de la rampa se divide en estas fases:**

1. **Avance:** El robot avanza hasta que la cámara detecta el color de la rampa.
2. **Tiro:** Cuando el robot está en el color adecuado tira la pelota.
3. **Bucle:** Luego de tirarla, el robot gira y choca contra el muro para crear un ciclo donde queda dando vueltas y tirando las pelotas.

<br>

**El robot del muro se divide en estas fases:**

1. **Avance:** El robot avanza hasta chocar el muro y tira las bolas.
2. **Bucle:** Cuando choca, retrocede y gira. Después de hacer este patrón 4 veces, vuelve a tirar la pelota.

<br>

> [!NOTE]
> El robot frena su recorrido si detecta la bola rosa (en los dos prototipos).
>
> **Está programado en python/bloques**

---

## 🚀 Instalación y Uso

### Requisitos Previos
* Tener Chrome o cualquier navegador compatible con Lego Spike Prime
* Kit de Lego Spike
* Tener computadora

### Pasos para Ejecutar
1. Clona este repositorio:
   ```bash
   git clone https://github.com[tu-usuario]/[tu-repositorio].git
   ```
2. Abre la carpeta del proyecto en tu entorno de desarrollo.
3. Conecta el bloque inteligente del Robot 1 vía USB/Bluetooth y carga el archivo `src/robot1_main.[ext]`.
4. Repite el proceso para el Robot 2 con el archivo `src/robot2_main.[ext]`.

---



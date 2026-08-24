# WRO RoboSports - [Kicktronics] 🎾

¡Bienvenidos al repositorio oficial de nuestro equipo para la categoría **WRO RoboSports**! Aquí encontrarás la documentación técnica, el diseño de hardware y el código fuente de nuestros dos robots autónomos.

## Nuestro Equipo
* **Categoría de Edad:** [Ej. 11-19 años / Senior]
* **Integrantes:**
  * [Yuming Zhen Wang]
  * [Valerie]
  * [Maikel]  
* **Tutor:** [Elkira]

---

## Descripción de los Robots 🤖

Para construir los robots, utilizamos dos idénticos, pero con una distinta estructura de sensores y diferente programación.

### 🛠️ Hardware y Componentes
* **Controlador Principal:** [LEGO SPIKE Prime]
* **Actuadores:** [Ej. 2x Motores grandes para tracción, 1x Motor mediano para el mecanismo de golpeo]
* **Sensores:** [Ej. 1x Giroscopio interno, 2x Sensores de color para detección de bola rosa, 1x sensor de fuerza para los golpes]


### 📐 Galería de Fotos
*(Descomenta y cambia las rutas cuando subas las fotos a tu repositorio)*

![image alt](https://github.com/gisoddolfato99-jpg/Robosports/blob/e5f47aa52c6cea7db0f4fe8c18e818d2528a5866/gta.jpg)

---

## 🧠 Estrategia de Juego y Software

### 🕹️ Roles en la Cancha
* **Robot 1 ([Robot del muro]):** [Tira las bolas mediante los choques].
* **Robot 2 ([Robot de la rampa]):** [Tira las bolas cuando detecta un colór en específico].

### 💻 Arquitectura del Código
El software está programado en **[Lenguaje: ej. Python / C++ / Bloques SPIKE]**. El algoritmo principal utiliza una **Máquina de Estados Finitos (FSM)** dividida en las siguientes fases:
1. **Búsqueda:** El robot gira hasta que la cámara detecta el color de la pelota.
2. **Persecución:** Se alinea con el objeto y avanza utilizando control proporcional.
3. **Ataque:** Activa el mecanismo de golpeo/empuje al estar a la distancia correcta.
4. **Retorno:** Si pierde la pelota o sale de la zona, regresa usando los sensores de línea.

---

## 🚀 Instalación y Uso

### Requisitos Previos
* [Tener Chrome o cualquier navegador compatible con Lego Spike Prime]
* [Kits de Lego Spike]
* [Tener computadoras]

### Pasos para Ejecutar
1. Clona este repositorio:
   ```bash
   git clone https://github.com[tu-usuario]/[tu-repositorio].git
   ```
2. Abre la carpeta del proyecto en tu entorno de desarrollo.
3. Conecta el bloque inteligente del Robot 1 vía USB/Bluetooth y carga el archivo `src/robot1_main.[ext]`.
4. Repite el proceso para el Robot 2 con el archivo `src/robot2_main.[ext]`.

---

## 📺 Demostración en Video
Puedes ver a nuestros robots en acción durante una partida de práctica en el siguiente enlace:
* 🎬 [Ver video de demostración en YouTube](https://youtube.com)

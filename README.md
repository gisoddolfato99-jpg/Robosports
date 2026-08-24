# WRO RoboSports - [Nombre de tu Equipo] 🤖🎾

¡Bienvenidos al repositorio oficial de nuestro equipo para la categoría **WRO RoboSports**! Aquí encontrarás la documentación técnica, el diseño de hardware y el código fuente de nuestros dos robots autónomos.

## 👥 Nuestro Equipo
* **País:** [Tu País]
* **Categoría de Edad:** [Ej. 11-19 años / Senior]
* **Integrantes:**
  * [Nombre Integrante 1] - [Rol: ej. Programador / Mecánico]
  * [Nombre Integrante 2] - [Rol: ej. Diseñador / Programador]
* **Tutor:** [Nombre del Tutor/Entrenador]

---

## 🤖 Descripción de los Robots

Para cumplir con el reto de RoboSports, diseñamos dos robots idénticos/especializados que respetan estrictamente las reglas oficiales de la WRO (**20x20x20 cm** y menos de **1.2 kg**).

### 🛠️ Hardware y Componentes
* **Controlador Principal:** [Ej. LEGO SPIKE Prime / EV3 / Arduino]
* **Actuadores:** [Ej. 2x Motores grandes para tracción, 1x Motor mediano para el mecanismo de golpeo]
* **Sensores:** [Ej. 1x Giroscopio interno, 2x Sensores de color para detección de líneas]
* **Cámara de Visión:** [Ej. Pixy2 / OpenMV] (Configurada para detectar las firmas de color de las pelotas).

### 📐 Galería de Fotos
*(Descomenta y cambia las rutas cuando subas las fotos a tu repositorio)*
<!--

| Vista Frontal | Vista Superior | Vista Lateral |
|---|---|---|
| ![Frontal](fotos/frontal.jpg) | ![Superior](fotos/superior.jpg) | ![Lateral](fotos/lateral.jpg) |
-->

---

## 🧠 Estrategia de Juego y Software

### 🕹️ Roles en la Cancha
* **Robot 1 ([Nombre]):** [Ej. Atacante principal, busca las pelotas usando la cámara y las empuja al campo contrario].
* **Robot 2 ([Nombre]):** [Ej. Defensor / Soporte, se mantiene en la línea trasera cubriendo los espacios vacíos].

### 💻 Arquitectura del Código
El software está programado en **[Lenguaje: ej. Python / C++ / Bloques SPIKE]**. El algoritmo principal utiliza una **Máquina de Estados Finitos (FSM)** dividida en las siguientes fases:
1. **Búsqueda:** El robot gira hasta que la cámara detecta el color de la pelota.
2. **Persecución:** Se alinea con el objeto y avanza utilizando control proporcional.
3. **Ataque:** Activa el mecanismo de golpeo/empuje al estar a la distancia correcta.
4. **Retorno:** Si pierde la pelota o sale de la zona, regresa usando los sensores de línea.

---

## 🚀 Instalación y Uso

### Requisitos Previos
* [Ej. VS Code con extensión LEGO SPIKE / Software de SPIKE Prime]
* [Ej. Librería de Pixy2 para LEGO]

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

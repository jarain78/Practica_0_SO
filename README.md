
# Práctica de Sistemas Operativos — C++ (Proyecto Autocontenido)

## 1. Descripción
Este repositorio contiene una **práctica de Sistemas Operativos** desarrollada en **C++**, cuyo objetivo es aplicar y demostrar conceptos fundamentales de la asignatura, tales como **procesos e hilos**, **sincronización**, **comunicación entre procesos (IPC)** y **gestión de recursos del sistema**.  
El proyecto está diseñado para ser **totalmente autocontenido**, de modo que cualquier usuario pueda **compilar y ejecutar la práctica** siguiendo exclusivamente este documento.

---

## 2. Estructura del repositorio

```
.
├── src/                # Código fuente (.cpp)
│   ├── main.cpp
│   └── opencv_test.cpp
├── include/            # Ficheros de cabecera (.h)
├── data/               # Datos de entrada de ejemplo (opcional)
├── build/              # Directorio de compilación (generado)
├── CMakeLists.txt      # Configuración de compilación (CMake)
├── Makefile            # Alternativa de compilación (opcional)
└── README.md
```


---

## 3. Requisitos del sistema
- Sistema operativo: **Linux** (probado en Ubuntu 22.04)
- Compilador: **g++** con soporte **C++17**
- Herramientas de compilación:
  - `cmake` ≥ 3.16
  - `make`

### Instalación de herramientas básicas
```bash
sudo apt update
sudo apt install -y build-essential cmake


---

## 4. Dependencias externas

### 4.1 OpenCV (equivalente a `cv2` en C++)

> En C++ no se instala `cv2` como en Python.
> Se instalan las **librerías OpenCV** y se enlazan en la compilación.

#### Instalación (Ubuntu/Debian)

```bash
sudo apt update
sudo apt install -y libopencv-dev pkg-config
```

Verificar instalación:

```bash
pkg-config --modversion opencv4
```

---

## 5. Compilación

### 5.1 Compilación con CMake (recomendada)

Desde la raíz del repositorio:

```bash
mkdir -p build
cmake -S . -B build
cmake --build build -j
```

El ejecutable principal se generará en:

```bash
./build/so_practica
```

### 5.2 Compilación alternativa con Makefile (si aplica)

```bash
make
```

---

## 6. Ejecución

### 6.1 Ejecución básica

```bash
./build/so_practica
```

### 6.2 Ejecución con parámetros (ejemplo)

```bash
./build/so_practica --mode=threads --n=4 --iters=100000
```

Parámetros admitidos (ejemplo):

* `--mode=threads|processes|ipc`
* `--n=<num>` número de hilos o procesos
* `--iters=<num>` número de iteraciones
* `--input=<ruta>` fichero de entrada (si procede)

---

## 7. Ejemplo mínimo con OpenCV en C++

Archivo `src/opencv_test.cpp`:

```cpp
#include <opencv2/opencv.hpp>
#include <iostream>

int main() {
    std::cout << "OpenCV version: " << CV_VERSION << std::endl;

    cv::Mat img = cv::Mat::zeros(200, 200, CV_8UC3);
    cv::putText(img, "OK", {50, 110},
                cv::FONT_HERSHEY_SIMPLEX, 1.0,
                {255, 255, 255}, 2);

    cv::imshow("OpenCV Test", img);
    cv::waitKey(0);
    return 0;
}
```

Compilación directa (sin CMake):

```bash
g++ -std=c++17 src/opencv_test.cpp -o opencv_test \
`pkg-config --cflags --libs opencv4`
```

Ejecución:

```bash
./opencv_test
```

---

## 8. Salida esperada

Al ejecutar correctamente el programa:

* El programa finaliza sin errores
* Se muestran mensajes informativos por consola
* En caso de usar OpenCV, se abre una ventana gráfica o se genera un fichero de salida

Ejemplo de salida:

```
[INFO] Mode: threads
[INFO] Threads: 4
[RESULT] Counter final = 400000
[TIME] Execution time: 0.35 s
```

---

## 9. Depuración

Compilar en modo **Debug**:

```bash
cmake -S . -B build -DCMAKE_BUILD_TYPE=Debug
cmake --build build -j
```

Ejecutar con `gdb`:

```bash
gdb ./build/so_practica
```

---

## 10. Problemas comunes

### OpenCV no abre ventanas

* Estás en un entorno sin GUI (WSL, servidor).
* Solución: usar `cv::imwrite()` o ejecutar en un entorno gráfico.

### Error: `opencv4.pc not found`

```bash
sudo apt install -y libopencv-dev pkg-config
```

---

## 11. Autoría

* Alumno/a 1: Nombre y Apellidos
* Alumno/a 2: Nombre y Apellidos

> **Nota**: aunque la práctica se realiza en pareja, **la evaluación es individual**.

---

## 12. Licencia

Proyecto académico con fines docentes. Uso restringido a la asignatura de **Sistemas Operativos**.


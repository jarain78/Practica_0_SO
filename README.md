```markdown
# Práctica de Sistemas Operativos (C++) — README

## 1. Descripción
Este repositorio contiene una práctica de **Sistemas Operativos** desarrollada en **C++**.  
El objetivo principal es implementar y probar conceptos básicos de SO (procesos/hilos, sincronización, IPC, planificación, etc., según el enunciado de la práctica).

> ✅ **Proyecto autocontenido**: incluye instrucciones completas para compilar, ejecutar y verificar el funcionamiento.

---

## 2. Estructura del repositorio
```

.
├── src/                # Código fuente (.cpp, .h)
├── include/            # Cabeceras (opcional)
├── tests/              # Tests (opcional)
├── data/               # Archivos de entrada/salida de ejemplo (opcional)
├── build/              # Carpeta de compilación (generada, no versionar)
├── CMakeLists.txt      # Configuración de build (CMake)
├── Makefile            # Alternativa de build (opcional)
└── README.md

````

---

## 3. Requisitos
### 3.1 Sistema
- Linux (recomendado **Ubuntu 22.04+** o similar)

### 3.2 Dependencias
#### Opción A: CMake (recomendada)
- `g++` (C++17 o superior)
- `cmake` (>= 3.16)
- `make`

Instalación en Ubuntu/Debian:
```bash
sudo apt update
sudo apt install -y build-essential cmake
````

#### Opción B: Makefile (si se proporciona)

* `g++`
* `make`

---

## 4. Compilación

### 4.1 Compilar con CMake (recomendado)

Desde la raíz del repositorio:

```bash
mkdir -p build
cmake -S . -B build
cmake --build build -j
```

El ejecutable se generará en:

```bash
./build/so_practica
```

### 4.2 Compilar con Makefile (si aplica)

```bash
make
```

---

## 5. Ejecución

### 5.1 Ejecución básica

```bash
./build/so_practica
```

### 5.2 Ejecución con argumentos (ejemplo)

```bash
./build/so_practica --mode=threads --n=4 --iters=100000
```

Parámetros soportados (ejemplo):

* `--mode=threads|processes|ipc`
* `--n=<num>` número de hilos/procesos
* `--iters=<num>` iteraciones de trabajo
* `--input=<ruta>` fichero de entrada (si aplica)

> Si tu práctica no usa argumentos, elimina esta sección o ajusta los parámetros reales.

---

## 6. Ejemplos de uso

### 6.1 Ejemplo 1: modo hilos

```bash
./build/so_practica --mode=threads --n=8 --iters=500000
```

### 6.2 Ejemplo 2: modo IPC (pipes/shared memory, etc.)

```bash
./build/so_practica --mode=ipc --input=data/input.txt
```

---

## 7. Salida esperada / Verificación rápida

Al ejecutarse correctamente, el programa debería:

* terminar sin errores
* mostrar un resumen por consola similar a:

  * número de hilos/procesos creados
  * tiempo total de ejecución
  * contadores/resultados finales
  * confirmación de sincronización correcta (si aplica)

Ejemplo:

```
[OK] mode=threads n=8 iters=500000
[RESULT] counter=4000000
[TIME] 0.38s
```

---

## 8. Tests (opcional)

Si hay tests:

```bash
ctest --test-dir build
```

O si existe un binario de tests:

```bash
./build/so_practica_tests
```

---

## 9. Notas de implementación

* Estándar: **C++17**
* Compilación con flags recomendados:

  * `-Wall -Wextra -Wpedantic`
* Para debug:

```bash
cmake -S . -B build -DCMAKE_BUILD_TYPE=Debug
cmake --build build -j
gdb ./build/so_practica
```

---

## 10. Problemas comunes

### 10.1 “cmake: command not found”

Instala CMake:

```bash
sudo apt install -y cmake
```

### 10.2 Permiso denegado al ejecutar

```bash
chmod +x ./build/so_practica
```

### 10.3 “No such file or directory” al ejecutar

Asegúrate de haber compilado:

```bash
cmake --build build -j
```

---

## 11. Autoría

* Alumno/a 1: Nombre Apellidos
* Alumno/a 2: Nombre Apellidos




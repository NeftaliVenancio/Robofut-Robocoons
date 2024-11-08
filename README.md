# Robofut-Robocoons

**Robofut-Robocoons** es un proyecto de robótica que implementa un sistema de control basado en Bluetooth para operar un robot móvil con motores L298N. El robot utiliza la biblioteca [**Bluepad32**](https://github.com/ricardoquesada/bluepad32) para la conexión con gamepads, permitiendo un control intuitivo y preciso.

## Tabla de contenidos
- [Características](#características)
- [Instalación](#instalación)
- [Uso](#uso)
- [Configuración del Hardware](#configuración-del-hardware)
- [Biblioteca Bluepad32](#biblioteca-bluepad32)
- [Licencia](#licencia)

---

## Características

- **Control de motores**: Utiliza un controlador L298N para el manejo preciso de dos motores de tracción.
- **Conexión Bluetooth**: Soporta conexión con gamepads mediante la biblioteca **Bluepad32**, permitiendo hasta 4 controladores simultáneamente.
- **Interfaz de control avanzada**: Los comandos del gamepad permiten un control intuitivo de la velocidad y dirección de los motores.
- **Visualización de datos**: Envía datos a través del monitor serial para monitorear el estado del gamepad y el robot en tiempo real.

## Instalación

### Requisitos previos

1. **Arduino IDE** (recomendado).
2. **ESP32** como microcontrolador.
3. Biblioteca **Bluepad32** para conexión Bluetooth.

### Pasos para la instalación

1. **Clonar el repositorio**:
    ```bash
    git clone https://github.com/NeftaliVenancio/Robofut-Robocoons.git
    cd Robofut-Robocoons
    ```
2. **Instalar la biblioteca Bluepad32**:
   - Dirígete a **Sketch** > **Incluir Biblioteca** > **Administrar Bibliotecas** en el Arduino IDE.
   - Busca e instala [**Bluepad32**](https://github.com/ricardoquesada/bluepad32) de Ricardo Quesada.

3. **Cargar el código en el ESP32**:
    - Conecta el ESP32 a tu computadora.
    - Abre el archivo en el Arduino IDE y carga el código en el ESP32.

## Uso

1. **Encender el robot**: Asegúrate de que el ESP32 y los motores estén alimentados.
2. **Emparejar el gamepad**: Conecta el gamepad mediante Bluetooth. El callback `onConnectedController` muestra en el monitor serial cuando un gamepad ha sido conectado exitosamente.
3. **Control del robot**:
   - Usa los botones del gamepad para controlar la dirección y velocidad.
   - Los valores de los joysticks izquierdo y derecho controlan la velocidad de cada motor.

## Configuración del Hardware

1. **Pines del controlador L298N**:
    - Motores derecho: `ena`, `in1`, `in2`
    - Motores izquierdo: `enb`, `in3`, `in4`

2. **Configuración de pines en el código**:
    ```cpp
    int enb = 25;  // Motor izquierdo
    int in3 = 26;
    int in4 = 27;

    int ena = 13;  // Motor derecho
    int in1 = 12;
    int in2 = 14;
    ```

3. **Umbral de joystick**:
    - El valor `umbral` (200 en este caso) define la zona muerta para el joystick, evitando movimiento involuntario cuando el joystick está en reposo.

## Biblioteca Bluepad32

El proyecto utiliza la biblioteca [**Bluepad32**](https://github.com/ricardoquesada/bluepad32), creada por Ricardo Quesada, para gestionar la conexión Bluetooth con gamepads compatibles. La biblioteca ofrece una interfaz fácil de usar que permite la conexión de múltiples controladores y proporciona acceso a datos de los botones, joysticks y sensores del gamepad.

## Licencia

Este proyecto está licenciado bajo la [Licencia MIT](LICENSE).

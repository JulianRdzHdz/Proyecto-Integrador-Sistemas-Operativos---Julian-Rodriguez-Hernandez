# Proyecto-Integrador-Sistemas-Operativos---Julian-Rodriguez-HernandezProducto Integrador Sistemas Operativos Grupo 6J

Simulador de Gestión de Memoria (RAM y Swap) Este proyecto consiste en un simulador de gestor de memoria para Sistemas Operativos, implementando técnicas de paginación, memoria virtual (Swapping) y traducción de direcciones.

Integrantes del Equipo:

-Argüelles Obregón René

-Rocha Coronado Carlos Julián

-Rodriguez Hernández Juan Julián

-Terán Ramírez Leonardo Alonso

Instrucciones de Compilación y Ejecución El simulador está desarrollado en Python 3, por lo que no requiere compilación previa, solo interpretación.

Requisitos previos Tener instalado Python 3.x. Asegúrese de que el archivo config.ini se encuentre en la misma carpeta que el código fuente. Pasos para ejecutar Abra una terminal o línea de comandos. Navegue hasta la carpeta src del repositorio: cd src Ejecute el script principal: python proyecto_memoria.py Explicacion del diseño y Estructura de Datos Para el desarrollo del simulador se eligieron estructuras nativas de Python por su eficiencia y facilidad de implementación: Tablas de Páginas: Se implementaron utilizando Diccionarios dentro de la estructura de cada proceso (PCB). Esto permite traducir el número de página lógica a su ubicación física (RAM o Swap) de manera directa.

Memoria RAM y Swap: Se modelaron mediante Listas (Arrays) de tamaño fijo. Cada posición de la lista representa un Marco (Frame) físico o un Slot de intercambio.

Colas de Gestión: Se utilizó la librería collections.deque (Cola doble) para manejar eficientemente las colas de procesos Listos/Bloqueados y la cola de historial de páginas para el algoritmo FIFO.

TLB (Translation Lookaside Buffer): Se simuló mediante un OrderedDict para manejar una memoria caché de traducción con capacidad limitada.

Algoritmo De Reemplazo El sistema implementa estrategias de reemplazo de páginas para gestionar el Swapping cuando la memoria RAM se llena:

Algoritmo Implementado: FIFO (First-In, First-Out).

El sistema mantiene una cola que registra el orden de llegada de los marcos a la memoria RAM.

Cuando ocurre un fallo de página y no hay marcos libres, se selecciona el marco que está al frente de la cola (el más antiguo) como "víctima".

Esta víctima se mueve al área de Swap para liberar espacio para la nueva página.

Flexibilidad: El diseño permite cambiar la configuración a algoritmos LRU o CLOCK editando el archivo config.ini.

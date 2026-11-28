# Programa Cafeteria - Control de inventario

Sistema por consola en C++ puro (solo biblioteca estandar) para registrar entradas,
salidas y mermas, calcular existencias, detectar stock minimo y generar reportes.

Proyecto de Fundamentos de Programacion - Universidad Politecnica de Pachuca (UPP) - Grupo 01_02.

## Estructura
```
(raiz del repositorio)
├── README.md
├── .gitignore
└── Cafeteria/
    ├── src/
    │   ├── main.cpp           menu y flujo del programa
    │   ├── insumo.h/.cpp      datos de insumo y movimiento, estado de stock
    │   ├── inventario.h/.cpp  entradas, salidas, mermas y validaciones
    │   ├── archivo.h/.cpp     guardar y cargar con fstream
    │   └── reportes.h/.cpp    existencias, alertas y reportes
    ├── data/
    │   ├── inventario.txt     id|nombre|unidad|existencia|minimo|proveedor
    │   └── movimientos.txt    fecha|id|tipo|cantidad|nota|proveedor
    └── docs/                  guia de desarrollo, entrevista, FODA, manual
```

## Compilar y ejecutar
Siempre desde la carpeta `Cafeteria`, para que el programa encuentre `data/`:
```
cd Cafeteria
g++ -std=c++17 -Wall -Wextra src/*.cpp -o cafeteria
.\cafeteria.exe      (Windows)
./cafeteria          (Linux / Mac)
```
No uses el boton "Run C/C++ File" de VS Code: compila un solo archivo y falla con
"undefined reference".

## Estados de stock
- Suficiente: existencia mas de 20 % arriba del minimo
- Por agotarse: existencia hasta 20 % arriba del minimo (preparar la compra)
- Agotado - Reabastecer: existencia en el minimo o por debajo (comprar de inmediato)

El margen de 20 % esta en `MARGEN_POR_AGOTARSE`, dentro de `src/insumo.h`.

## Menu
1. Ver existencias
2. Agregar insumo
3. Registrar entrada (compra, con proveedor)
4. Registrar salida (consumo)
5. Registrar merma (caducado / danado)
6. Ver alertas de stock
7. Reportes: consumo, compras, mermas, lista de compras sugerida, historial
8. Cambiar stock minimo
9. Eliminar insumo

Los datos se guardan automaticamente despues de cada cambio.

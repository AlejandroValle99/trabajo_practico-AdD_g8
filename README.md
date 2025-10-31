# Configuración del Proyecto

Este proyecto requiere Python 3.12 y utiliza `uv` como gestor de dependencias.

## Prerequisitos

1. Python 3.12
2. [uv](https://github.com/astral-sh/uv) - Un instalador de paquetes Python ultrarrápido

## Configuración del Entorno

1. Clonar el repositorio:

```sh
git clone <https://github.com/AlejandroValle99/trabajo_practico-AdD_g6.git>
cd trabajo_practico-AdD_g6
```

2. Instalar uv (si no está instalado):

Referirse a la documentacion de uv para instalacion [uv-instalacion](https://docs.astral.sh/uv/getting-started/installation/)

3. Instalar proyecto y dependencias. Esto ya instalara el virtual environment.

```sh
uv sync --all
```

4. Crear el kernel de Jupyter para el proyecto

```sh
uv run python -m ipykernel install --user --name=trabajo_practico-AdD_g6

```

## Estructura del Proyecto

```
trabajo_practico-AdD_g6/
├── lib/
│   └── Crimes_-_2024_20251030.csv    # Dataset de crímenes
├── main.ipynb                         # Notebook principal
├── test.ipynb                         # Notebook de pruebas
└── pyproject.toml                     # Configuración del proyecto
```

## Antes de trabajar

Exportar el dataset [Crimes-2024](https://data.cityofchicago.org/Public-Safety/Crimes-2024/dqcy-ctma/about_data) y colocarlo dentro de la carpeta "lib".

5. Trabajar con los Notebooks

El proyecto utiliza notebooks de Jupyter (`.ipynb`). Se asume que ya tienes configurado un entorno de desarrollo con soporte para Jupyter (como VS Code, PyCharm, etc.).

- Abre `main.ipynb` en tu IDE
- Asegúrate de seleccionar el kernel del entorno virtual (`.venv`) que creaste

## Comandos Útiles de UV

```sh
# Ver la versión de uv
uv --version

# Sincronizar dependencias (incluidas las de desarrollo)
uv sync --all

# Sincronizar solo dependencias principales (sin las de desarrollo)
uv sync

# Listar paquetes instalados
uv pip list

# Verificar el entorno
uv pip verify
```

## Solución de Problemas

- Si `uv` no responde, verifica que el entorno virtual esté activado:

  ```sh
  # Linux/macOS
  source .venv/bin/activate

  # Windows
  .venv\Scripts\activate
  ```

- Para problemas con los notebooks, asegúrate de que ipykernel esté instalado:
  ```sh
  uv pip install ipykernel
  ```

## 6) Archivos de datos

Los datos utilizados están en la carpeta `lib`:

- `lib/Crimes_-_2024_20251030.csv`

## 7) Archivos útiles del repositorio

- `.python-version`
- `.gitignore`
- `pyproject.toml`
- `README.md`
- `main.ipynb`

## Branching Strategy

Seguimos una estrategia de branching específica para análisis de datos:

### Convención de Nombres

- `data/*`: Para cambios relacionados con la preparación o limpieza de datos

  - Ejemplo: `data/clean-crime-dates`
  - Ejemplo: `data/handle-missing-values`

- `feature/*`: Para nuevas características o análisis

  - Ejemplo: `feature/crime-trends-analysis`
  - Ejemplo: `feature/location-clustering`

- `viz/*`: Para visualizaciones y gráficos

  - Ejemplo: `viz/crime-heatmap`
  - Ejemplo: `viz/temporal-patterns`

### Comandos Git Comunes

1. Crear y cambiar a una nueva rama:

```bash
# Para nuevos análisis
git checkout -b feature/crime-patterns-2024

# Para visualizaciones
git checkout -b viz/crime-distribution-map

# Para preparación de datos
git checkout -b data/clean-coordinates
```

2. Actualizar tu rama con main:

```bash
git checkout main
git pull
git checkout tu-rama
git merge main
```

O actualiza primero main con git pull origin main y creas tu branch a partir de main.

3. Subir cambios:

```bash
git add .
git commit -m "feat: análisis de patrones temporales"
git push origin tu-rama
```

### Convención de Commits

- `data:` para cambios en datos
- `feat:` para nuevos análisis o características
- `viz:` para visualizaciones
- `doc:` para documentación
- `fix:` para correcciones

Ejemplo:

```bash
git commit -m "viz: agregar heatmap de crímenes por zona"
git commit -m "data: limpiar valores nulos en coordenadas"
git commit -m "model: implementar clustering por ubicación"
```

---

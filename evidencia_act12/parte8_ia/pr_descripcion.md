# Título del PR
feat: morph dona -> taza (endpoint, figuras guardadas, relevo al visor)

# Descripción escrita por el autor
## Objetivo del Pull Request
Integrar la deformación topológica continua (**Morph Dona → Taza**) entre nuestros dos microservicios (`Calculadora de matrices` en el puerto `8000` y `Modelador3D_matrices` con interfaz *Glassmorphism* en el puerto `8001`).

## Cambios Implementados por Capa
1. **Motor Matemático (`Calculadora de matrices/app/services/matrix_service.py`):**
   - Implementación de las superficies paramétricas `vertice_dona(u, v)`, `vertice_taza(u, v)` e interpolación lineal `calcular_morph(t, resolucion)`.
2. **Routers Modulares (`Calculadora de matrices/app/api/routers/`):**
   - **`operations.py` (`POST /operaciones/morph-3d` y `/calc/morph`):** Devuelve la nube de puntos interpolada y genera una tabla `resumen_markdown` con la caja envolvente (*bounding box*) lista para el agente de **n8n**.
   - **`figuras.py` (`POST /figuras`, `GET /figuras`, `GET /figuras/{id}`, `DELETE /figuras/{id}`):** Nuevo router modular para guardar, consultar y eliminar figuras personalizadas del morph.
3. **Visor 3D *Glassmorphism* (`Modelador3D_matrices/index.html` y `main.py`):**
   - Nuevo botón **`☕ Dona→Taza`** en el selector de figuras con transición de color neón (`#00ffaa` → `#ff3399`), slider de porcentaje `0%..100%` y guardado por WebSocket (`/ws/transform`).
4. **Suite de Pruebas (`test_e2e/`):**
   - Nuevas pruebas en `test_morph.py`, `test_regresion_seguridad.py` y `test_vision.py` (13 pruebas en verde).

## Cómo inicializar y probar
```bash
docker compose up --build -d
# Calculadora (Estilo Excel): http://localhost:8000
# Documentación Swagger API:  http://localhost:8000/docs
# Visor 3D Glassmorphism:     http://localhost:8001/view (seleccionar botón "☕ Dona→Taza")
```

# Commits del PR (de más antiguo a más reciente)
- b088337 chore: agregar docker-compose.yaml y pyproject.toml en la raiz del pr…
- a7d799e feat(calculadora): agregar servicio y endpoints de morph dona->taza y…
- 080d24a feat(modelador3d): integrar relevo WebSocket de morph y controles Don…
- b32f6c1 test(morph): agregar pruebas de interpolacion dona->taza y guardado d…
- 7a234e0 feat(calculadora): router modular figuras.py con DELETE, resumen_mark…

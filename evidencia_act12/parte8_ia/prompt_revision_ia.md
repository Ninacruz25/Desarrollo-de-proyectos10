Actúa como revisor de código senior. Revisa el siguiente Pull Request de un proyecto con dos servicios FastAPI (una "Calculadora de matrices" en el puerto 8000 y un "Modelador 3D" con visor web y WebSocket en el puerto 8001), orquestados con Docker Compose. La IA generó parte del código.

Quiero una revisión completa del diff, como la haría un equipo profesional. Revisa estos puntos:
- Si el código hace lo que dice la descripción del PR, incluidos los casos límite.
- Matemática y funcionalidad.
- Arquitectura por capas (API -> servicios -> repositorio) y separación de responsabilidades entre los dos servicios.
- Validación de entradas (tipo, rango y tamaño máximo).
- Seguridad (OWASP: inyección, XSS, diseño inseguro y abuso de recursos, configuración, control de acceso, manejo de errores).
- Idempotencia de las operaciones.
- Calidad de las pruebas: si fallarían cuando el código esté mal, o si solo comprueban que "pasan".
- Documentación (OpenAPI) y si la descripción del PR es honesta.
- Alcance del PR y calidad de los commits.

Para cada hallazgo usa este formato:
- **[Severidad]** (Bloqueante / Mayor / Menor / Nit / Pregunta)
- **Dónde:** archivo y línea o función
- **Qué:** el problema, en una frase
- **Por qué importa:** el riesgo o la consecuencia
- **Evidencia:** el fragmento de código del diff que lo demuestra
- **Sugerencia:** qué cambiarías, sin escribir todo el código

Reglas:
1. Basa cada hallazgo en el código del diff. Si no puedes verificar algo solo con el diff, dilo explícitamente en lugar de afirmarlo.
2. No inventes líneas, funciones ni comportamientos que no aparezcan en el diff.
3. Al final da una decisión (Approve, Request changes o Comment) con un párrafo que la justifique, y una lista de lo que no pudiste verificar.

A continuación van la descripción del PR y el diff completo.

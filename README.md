# RODA API | Backend y Frontend Full-Stack
Este proyecto es la solución al reto técnico de RODA, implementando una arquitectura Full-Stack con FastAPI (Backend) y React/TypeScript con Vite (Frontend).

💡 Tecnologías Utilizadas
Componente	Tecnología	Motivación
Backend	Python (FastAPI)	Elegido por su rendimiento (asíncrono con async/await), tipificación automática con Pydantic, y facilidad para crear documentación de API (Swagger/OpenAPI).
Frontend	React & TypeScript	Garantiza la calidad y mantenibilidad del código (especialmente en el manejo de estructuras de datos complejas como el cronograma de pagos).
Diseño	Tailwind CSS	Permite construir una interfaz de usuario limpia y profesional, con un enfoque mobile-first (responsive design) y una paleta de colores corporativa.
Base de Datos	PostgreSQL (Asumido)	Utilizado para simular la persistencia y la consulta de datos estructurados complejos.

Exportar a Hojas de cálculo
🚀 Guía de Ejecución Local (WSL/Linux)
A continuación se detallan los pasos para levantar la aplicación completa. Se requiere tener Python, Node.js (npm) y Git instalados en el entorno (ej: WSL o Linux).

1. Clonar el Repositorio e Instalar Dependencias
Bash

# 1. Clonar
git clone [TU_URL_DE_GITHUB]
cd roda_techInterview

# 2. Instalar dependencias de Python (Asumiendo que ya tienes .venv)
source .venv/bin/activate
pip install -r requirements.txt # O ejecuta todas las dependencias con pip install fastapi uvicorn...

# 3. Instalar dependencias de Node/Frontend
cd web
npm install
cd .. # Volver a la raíz
2. Configurar Variables de Entorno (.env)
Asegúrate de tener un archivo .env dentro de la carpeta web/ con la URL base de la API, apuntando al puerto 8000 del backend:

Fragmento de código

# Archivo: web/.env
VITE_API_BASE_URL=http://127.0.0.1:8000
3. Iniciar el Backend (FastAPI)
Abrir la Terminal 1 y ejecutar:

Bash

# Asegúrate de estar en la raíz del proyecto y el entorno activado
uvicorn server.main:app --reload

# Verificación: El backend debe estar corriendo en http://127.0.0.1:8000
4. Iniciar el Frontend (React/Vite)
Abrir la Terminal 2 (dejando el backend corriendo) y ejecutar:

Bash

cd web
npm run dev

# Verificación: El frontend se abrirá en tu navegador (ej: http://localhost:5173)
⚙️ Estructura y Endpoints Clave
La aplicación se separa en dos directorios principales:

Backend (server/)
Archivo/Módulo	Función
main.py	Configuración principal de FastAPI y el Middleware CORS.
routers/clientes.py	Contiene el endpoint principal para la consulta del cronograma.
db/database.py	Lógica de consulta simulada a la base de datos (PostgreSQL).
schemas/models.py	Define las estructuras de datos (Pydantic) para el cliente y los créditos.

Exportar a Hojas de cálculo
Endpoint Único:

Método	Endpoint	Descripción
GET	/clientes/{cliente_id}/schedule	Devuelve la información de un cliente (nombre, doc) y el arreglo de sus créditos con el cronograma de pagos.

Exportar a Hojas de cálculo
Frontend (web/)
Archivo/Módulo	Función
src/App.tsx	Componente principal que maneja la lógica de consulta (fetch) y los estados (useState).
src/components/CreditSchedule.tsx	Componente que renderiza el cronograma de pagos como una tabla estilizada.
tailwind.config.js	Configuración de la paleta de colores RODA y las directivas de Tailwind.

Exportar a Hojas de cálculo
📌 Decisiones Técnicas Destacadas
Tipificación Estricta: Uso consistente de TypeScript y Pydantic para garantizar la integridad de los datos entre el backend y el frontend.

Manejo de CORS: Implementación del Middleware CORS en FastAPI para permitir la comunicación segura entre los diferentes puertos del frontend y backend.

Arquitectura Modular: Uso de Routers en FastAPI para mantener el código organizado y escalable.

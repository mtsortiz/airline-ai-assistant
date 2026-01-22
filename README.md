# 🛫 Flightly - Airline AI Assistant

Un asistente inteligente basado en IA para gestionar consultas de precios de vuelos y actualizar tarifas en tiempo real.

## 📋 Descripción

**Flightly** es un chatbot conversacional impulsado por [Gemini 2.5 Flash](https://ai.google.dev/) que permite a los clientes consultar precios de boletos y a los administradores actualizar tarifas dinámicamente. Utiliza herramientas automáticas (function calling) para acceder a una base de datos SQLite de precios y proporciona respuestas corteses y precisas.

## ✨ Características

- 🤖 **Conversación Natural**: Responde a consultas en lenguaje natural
- 💰 **Consulta de Precios**: Obtiene precios de boletos por ciudad destino
- 📊 **Actualización de Tarifas**: Permite establecer y actualizar precios de vuelos
- 💾 **Persistencia de Datos**: Almacena precios en base de datos SQLite
- 🎨 **Interfaz Intuitiva**: Interfaz web interactiva con Gradio
- ⚡ **Function Calling**: Utiliza herramientas automáticas del modelo de IA

## 🚀 Inicio Rápido

### Requisitos Previos

- Python 3.10+
- Clave API de Gemini

### Instalación

1. **Clonar el repositorio**
```bash
git clone <repository-url>
cd airline-ai-assistant
```

2. **Crear un entorno virtual**
```bash
python -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate
```

3. **Instalar dependencias**
```bash
pip install -r requirements.txt
```

4. **Configurar variables de entorno**
```bash
echo "GEMINI_API_KEY=your_api_key_here" > .env
```

### Ejecutar

```bash
jupyter notebook airline-ai-assistant.ipynb
```

## 🔧 Estructura del Proyecto

```
airline-ai-assistant/
├── airline-ai-assistant.ipynb  # Notebook principal
├── requirements.txt             # Dependencias
├── .env                         # Variables de entorno
└── prices.db                    # Base de datos SQLite
```

## 📚 Componentes Principales

### 1. **Sistema de Mensajes**
Define el comportamiento del asistente como representante profesional de la aerolínea Flightly.

### 2. **Herramientas (Tools)**

#### `get_ticket_price(destination_city)`
Obtiene el precio del boleto para una ciudad destino.
- **Parámetro**: `destination_city` (string)
- **Respuesta**: Precio del boleto de retorno

#### `set_ticket_price(destination_city, price)`
Establece o actualiza el precio del boleto para una ciudad destino.
- **Parámetros**: 
  - `destination_city` (string)
  - `price` (número)

### 3. **Base de Datos**
Tabla `prices` con dos columnas:
- `city` (PRIMARY KEY, TEXT)
- `price` (REAL)

## 💬 Ejemplos de Uso

```
Usuario: ¿Cuál es el precio de un boleto a París?
Asistente: The price of a ticket to Paris is $900

Usuario: Establece el precio para Londres en $750
Asistente: Price for London set to $750
```

## 🔐 Configuración

### Variables de Entorno
```env
GEMINI_API_KEY=your_gemini_api_key_here
```

### Modelo y Configuración
- **Modelo**: `gemini-2.5-flash`
- **Ciudades Disponibles**: London, Paris, Tokyo, Berlin (inicialmente)
- **Respuestas**: Máximo una oración, corteses y profesionales

## 📦 Dependencias

```
google-genai>=0.5.0
gradio>=4.0
python-dotenv>=1.0
sqlite3 (built-in)
```

## 🎯 Casos de Uso

✅ Asistencia al cliente 24/7 para consultas de precios  
✅ Actualización dinámica de tarifas  
✅ Gestión de precios por destino  
✅ Integración en sistemas de reservas  

## 🛠️ Desarrollo

### Agregar Nuevas Herramientas

1. Define la función en Python
2. Crea un `FunctionDeclaration` en el array `tools`
3. Agrega la lógica de manejo en `chat()`
4. Prueba con el chatbot

### Expandir Funcionalidades

- Agregar más ciudades a la base de datos
- Implementar validaciones de precios
- Agregar historial de cambios de precios
- Integrar autenticación para administradores

## 📝 Notas

- El asistente solo conoce sobre datos de aerolíneas
- Todos los vuelos son de un único origen (cada ciudad tiene un precio único)
- Las respuestas son breves (máximo una oración)
- Se mantiene un tono profesional y cortés en todo momento

## 📄 Licencia

Este proyecto está disponible bajo la licencia MIT.
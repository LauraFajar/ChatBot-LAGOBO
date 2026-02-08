# 🤖 ChatBot Almacén Oportunidades - Asistente de Ventas IA

**ChatBot Almacén Oportunidades** es un asistente virtual inteligente diseñado para automatizar las ventas y la atención al cliente de un almacén de electrodomésticos. A diferencia de los chatbots tradicionales, este sistema está enfocado en el **cierre de ventas** y la **gestión de inventario en tiempo real**.

Integrado con **WhatsApp Business API** y potencidado por **Google Gemini AI**, el bot ofrece una experiencia de compra fluida, desde la consulta de precios hasta la confirmación del pedido.

## 🚀 Características Principales

*   **🧠 IA Híbrida Inteligente**: Combina la potencia de **Google Gemini** para entender el lenguaje natural con reglas de negocio estrictas para asegurar la precisión en precios y stock.
*   **📊 Inventario en Tiempo Real**: Se conecta directamente a **Google Sheets** para leer el inventario. Si se acaba un producto en la hoja, el bot lo sabe al instante.
*   **💰 Cierre de Ventas Automatizado**: Detecta la intención de compra, solicita los datos de envío (Nombre, Dirección) y genera una orden de venta automáticamente en el sistema.
*   **📈 Registro de Intereses (Leads)**: Guarda en una base de datos qué es lo que buscan los clientes (ej: "Air Fryer"), permitiendo al negocio saber qué productos tienen alta demanda, incluso si no están en inventario.
*   **🛒 Carrito por Sesión**: Maneja múltiples conversaciones simultáneas sin mezclar los pedidos de los clientes.

---

## 🛠️ Tecnologías Utilizadas

*   **Python 3.x**: Lenguaje principal.
*   **Flask**: Servidor web para manejar los Webhooks de WhatsApp.
*   **Google Gemini (Generative AI)**: Motor de inteligencia artificial.
*   **Google Sheets API (gspread)**: Base de datos ligera para inventario y ventas.
*   **WhatsApp Cloud API**: Interfaz de mensajería.

---

## ⚙️ Configuración e Instalación

### 1. Prerrequisitos
*   Tener Python instalado.
*   Una cuenta de desarrollador en Meta (Facebook) para WhatsApp API.
*   Credenciales de servicio de Google Cloud Console (para acceder a Sheets).

### 2. Instalación de Dependencias
```bash
pip install -r requirements.txt
```

### 3. Configuración del Entorno (.env)
Crea un archivo `.env` en la raíz del proyecto con las siguientes variables:

```ini
# Google Gemini AI
GEMINI_API_KEY=tu_api_key_de_google

# WhatsApp Cloud API (Meta)
WHATSAPP_TOKEN=tu_token_permanente_o_temporal
PHONE_NUMBER_ID=tu_identificador_de_numero
VERIFY_TOKEN=tu_token_de_verificacion_personalizado
```

### 4. Configuración de Google Sheets
El sistema espera un archivo de Google Sheets con las siguientes hojas:

*   **Inventario**: Columnas `id`, `nombre`, `descripcion`, `precio`, `stock`.
*   **Ventas**: (Se llena automáticamente) `Fecha`, `Cliente`, `Telefono`, `Direccion`, `Producto`, `Total`, `Estado`.
*   **Intereses**: (Se llena automáticamente) `Fecha`, `Telefono`, `Busqueda`.

> **Nota**: Debes colocar tu archivo de credenciales de Google como `credenciales_sheets.json` en la carpeta raíz.

---

## ▶️ Ejecución

### Modo Simulador (Pruebas Locales)
Puedes probar la lógica del bot directamente en tu terminal sin conectar WhatsApp:

```bash
python main_simulador.py
```

### Modo Servidor (Producción)
Para recibir mensajes reales de WhatsApp (requiere HTTPS, puedes usar Ngrok para pruebas locales):

```bash
python app.py
```

---

## 📂 Estructura del Proyecto

```
ChatBot LAGOBO/
├── src/
│   ├── cerebro.py       # Lógica principal (IA + Reglas de flujo)
│   └── inventario.py    # Conexión con Google Sheets (Lectura/Escritura)
├── app.py               # Servidor Web (Flask endpoint para WhatsApp)
├── main_simulador.py    # Script para probar en consola
├── requirements.txt     # Librerías necesarias
└── .env                 # Variables de entorno (No subir a GitHub)
```

## 📝 Autor
Desarrollado para **Almacén Oportunidades**.

# ARQUTECTURA_MEDALLION

# 🏗️ Data Engineering Project: Capa Bronze (Arquitectura Medallion)

Este proyecto implementa la primera fase de una arquitectura **Medallion**, denominada **Capa Bronze**. El objetivo principal es establecer un flujo de ingesta de datos crudos (Raw Data) desde archivos locales hacia una base de datos **PostgreSQL** alojada en **Supabase**, garantizando la trazabilidad y la integridad inicial de la información.

---

## 📋 Descripción del Proceso ETL (Bronze)

El pipeline desarrollado en este repositorio realiza una extracción y carga directa sin transformaciones profundas, siguiendo el principio de "fidelidad al origen".

### 🔹 Funcionalidades Clave:

- **Gestión Segura de Credenciales:** Uso de archivos `secrets.toml` para desacoplar las llaves de acceso del código fuente.
- **Interfaz Dinámica:** Selección interactiva del archivo a procesar mediante un menú numerado en el Notebook.
- **Validación de Esquemas:** El script inspecciona las columnas reales de la base de datos antes de subir la información, permitiendo que solo las columnas válidas sean procesadas.
- **Estrategia de Carga (Truncate & Load):** Para este entorno de desarrollo, se implementó el vaciado de tablas (`TRUNCATE`) previo a la carga para asegurar que los datos actuales sean los únicos presentes, evitando duplicidad.
- **Metadatos de Trazabilidad:** Inserción automática de la columna `fuente_archivo` para identificar el origen de cada registro.

---

## 🧪 Generación de Datos

Para este proyecto se utilizan **datos sintéticos** generados mediante scripts de Python. Se crearon tres datasets principales con 100 registros cada uno:

1.  **Ventas:** Transacciones históricas con IDs de clientes y productos.
2.  **Clientes:** Maestro de clientes con datos demográficos y geográficos.
3.  **Productos:** Catálogo con categorías, precios y proveedores.

> **Nota:** Todos los datos numéricos y de fecha se cargan inicialmente como tipo `TEXT` en la capa Bronze para asegurar que la ingesta no falle por errores de formato, delegando la limpieza a la capa Silver.

---

## 💻 Configuración del Entorno de Desarrollo

Este proyecto está diseñado para ejecutarse en un **Entorno Virtual (venv)** para evitar conflictos de dependencias.

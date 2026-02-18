# RequerimientosFIS

### 1. Análisis General del Proyecto

**Objetivo del Negocio:** Crear un marketplace C2C (Consumer to Consumer) para que estudiantes de una universidad pública puedan vender y comprar productos entre sí (comida, artesanías, servicios, etc.).

**Actores Principales:**
1.  **Visitante (No Registrado):** No puede ver nada (según documento).
2.  **Estudiante (Usuario Base):** Persona con código, proyecto curricular, estado (activo/inactivo).
3.  **Comprador:** Estudiante que puede comprar. Si es menor de edad, requiere autorización.
4.  **Vendedor:** Estudiante que puede vender. Tiene cuenta bancaria, productos y credenciales.
5.  **Administrador:** Contratista que gestiona el sistema (catálogos, usuarios, estadísticas).

---

### 2. Síntesis de Requerimientos Funcionales (RF)

He organizado y sintetizado todos los requerimientos del documento en esta lista. Es lo que el sistema *debería* hacer idealmente.

#### Módulo de Usuarios y Autenticación
-   **RF1: Registro de Persona/Estudiante:** Permitir el registro con datos: tipo/número documento, nombres, apellidos, fecha nacimiento, teléfono, género.
-   **RF2: Registro con Roles:** Un estudiante puede registrarse y habilitarse como Comprador, Vendedor o ambos.
-   **RF3: Validación de Estado:** Verificar que un estudiante esté "activo" (matriculado) para permitirle cualquier acción. Si está inactivo, se bloquea.
-   **RF4: Gestión de Menores de Edad:** Si un estudiante es menor de edad, el sistema debe solicitar y almacenar (simular) la autorización del tutor y la cédula del tutor para poder ser vendedor/comprador.
-   **RF5: Inicio de Sesión (Login):** Implementar un mecanismo de autenticación (ej. usuario/contraseña + JWT).
-   **RF6: Recuperación de Contraseña:** Permitir a cualquier usuario recuperar su contraseña (ej. vía correo electrónico).
-   **RF7: CRUD de Administradores:** Crear, leer, actualizar y desactivar administradores (datos de persona + tipo de contrato, duración, cargo).

#### Módulo de Productos y Catálogo
-   **RF8: Gestión de Categorías (Admin):** El administrador puede crear categorías para clasificar productos.
-   **RF9: Publicación de Productos (Vendedor):** El vendedor puede publicar un producto con: nombre, descripción, categoría, precio unitario, condiciones de venta, imágenes.
-   **RF10: Gestión de Productos (Vendedor):** El vendedor puede editar, pausar o eliminar (dar de baja) sus publicaciones.
-   **RF11: Búsqueda y Filtros (Comprador):** Buscar productos por nombre, categoría o vendedor. Poder filtrar y comparar precios.
-   **RF12: Galería de Vendedores:** Listado de vendedores con opción de ver sus productos.

#### Módulo de Compras (Carrito y Pago)
-   **RF13: Carrito de Compras:** Añadir/quitar productos, modificar cantidades y recalcular el subtotal.
-   **RF14: Simulación de Pasarela de Pago:** Al finalizar, mostrar un formulario simulado de pago. Al "pagar", generar una factura/tirilla de compra.
-   **RF15: Cálculo de Factura:** Calcular total (subtotal + IVA - descuentos + envío).
-   **RF16: Gestión de Envío/Recogida:**
    -   Opción 1: Recoger en sitio (permite usar geolocalización para ver si está cerca del vendedor/un punto de entrega).
    -   Opción 2: Envío a domicilio
-   **RF17: Historial de Compras (Comprador):** Ver productos comprados y opción a "recomprar".
-   **RF18: Historial de Ventas (Vendedor):** Ver productos vendidos e ingresos.

#### Módulo de Interacción y Reputación
-   **RF19: Mensajería Interna:** Permitir comunicación asíncrona entre comprador y vendedor (preguntas, respuestas, negociación).
-   **RF20: Valoraciones y Reseñas Post-Compra:** Después de la compra, ambas partes pueden calificar (1-5 estrellas) y dejar un comentario (reseña) sobre la transacción.
-   **RF21: Cálculo de Puntaje Promedio:** Mostrar el promedio de estrellas de un producto o vendedor basado en las valoraciones.
-   **RF22: Sistema de Recompensas/Puntos:** El sistema puede otorgar puntos o descuentos por acciones (ej. 10 reseñas positivas = 20% dto en siguiente compra). El vendedor puede configurar sus propias recompensas.

#### Módulo de Fidelización y Notificaciones
-   **RF23: Sistema de Referidos:** Un usuario puede invitar a un amigo. Si el amigo se registra, ambos reciben un descuento (ej. para la próxima compra, con vigencia).
-   **RF24: Notificaciones Push (App) y Correos (Web):**
    -   Enviar correo de bienvenida.
    -   Enviar correos de fidelización (newsletters, ofertas).
    -   Enviar notificaciones de pago y credenciales.
    -   (Opcional) Recuperación de carrito abandonado.

#### Módulo de Administración
-   **RF25: Gestión de Catálogo (Admin):** CRUD de categorías de productos.
-   **RF26: Gestión de Usuarios (Admin):** Ver, bloquear/desbloquear estudiantes.
-   **RF27: Estadísticas y Monitoreo (Admin):** Ver número de transacciones, usuarios registrados, productos más vendidos en un periodo de tiempo.
-   **RF28: Mesa de Ayuda (Soporte):** Un formulario o chat para que los usuarios contacten al admin.

#### Requerimientos Técnicos y Transversales
-   **RFT1: Multiplataforma:** Front-end Web (responsivo) y App Móvil Nativa (Android APK).
-   **RFT2: Geolocalización:** Mostrar mapa y ubicación del comprador/vendedor (o puntos de entrega como las sedes de la universidad) para la opción "recoger en sitio".
-   **RFT3: Realidad Aumentada (AR):** Mostrar descripción del lugar de entrega (sede universitaria) de forma inmersiva. *Este es un punto muy complejo.*
-   **RFT4: Arquitectura de Microservicios:** Backend en Spring Boot (Java) y FastAPI (Python) comunicándose vía RestClient/WebClient.
-   **RFT5: Patrones de Diseño:** Implementar DAO y Singleton.
-   **RFT6: Seguridad:** Implementar autenticación robusta (se sugiere JWT + OAuth2 Social Login como "mecanismo seleccionado").
-   **RFT7: Documentación:** Código comentado (JavaDoc) y diagramas.

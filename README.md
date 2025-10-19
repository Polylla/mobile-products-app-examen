# Mobile Products App (Examen — Computación Móvil)

Aplicación de e-commerce móvil desarrollada en Flutter que utiliza Firebase como Backend-as-a-Service (BaaS).
Esta aplicación fue creada como entregable del examen del ramo de Computación Móvil. El README describe
las funcionalidades implementadas, cómo ejecutar el proyecto localmente, configuración requerida y
un mapeo entre las características del código y los requisitos típicos de un enunciado de examen.

## Resumen

- Tecnologías: Flutter, Firebase (Authentication, Cloud Firestore), Provider.
- Objetivo: permitir registro/login de usuarios, navegación entre pantallas, listar productos y categorías,
  gestionar proveedores (CRUD básico), mantener un carrito de compras y simular un flujo de pago con
  página de agradecimiento.

## Estado actual (implementado)

- Autenticación de usuarios: registro, inicio de sesión y recuperación de contraseña (Archivo: `lib/services/auth_service.dart`).
- Productos: listado, detalle y actualizaciones puntuales de stock/proveedor (Archivo: `lib/services/product_service.dart`, modelo en `lib/models/product.dart`).
- Categorías: listado (Archivo: `lib/services/category_service.dart`, modelo en `lib/models/category.dart`).
- Proveedores: listado, creación, actualización y eliminación (CRUD) (Archivo: `lib/services/supplier_service.dart`, modelo en `lib/models/supplier.dart`).
- Carrito de compras: agregar/remover ítems y conteo de cantidad total (Archivo: `lib/providers/cart_provider.dart`).
- Flujo de compra simulado: checkout que conduce a `ThankYouPage` (Archivo: `lib/pages/thank_you_page.dart`).
- Páginas principales y rutas declaradas en `lib/main.dart`:
  - `/dashboard` → `DashboardPage`
  - `/products` → `ProductsPage`
  - `/categories` → `CategoriesPage`
  - `/suppliers` → `SuppliersPage`
  - `/recover` → `RecoverPage`

## Mapeo al enunciado del examen

Basado en el código disponible, la aplicación cubre los requisitos habituales que se piden en un enunciado de examen de este tipo:

- Gestión de usuarios (registro/login/recuperación): implementado (`lib/services/auth_service.dart`).
- CRUD de entidades del negocio (proveedores implementan create/update/delete). Productos y categorías tienen operaciones de lectura y actualizaciones puntuales.
- Carrito y proceso de compra simulado: presente en `lib/providers/cart_provider.dart` y páginas de UI correspondientes (`lib/pages/`).
- Integración con Firebase (Firestore y Auth) y uso de `firebase_options.dart` para configuración por plataforma.

Nota: no pude leer directamente el PDF del enunciado desde la ruta original (fuera del workspace). Si quieres que ajuste el README exactamente a los criterios del enunciado del profesor, por favor pega aquí los requisitos o coloca el PDF dentro del directorio del proyecto y lo leo para adaptar el README al 100%.

## Requisitos y dependencias

- Flutter (versión compatible con SDK Dart especificado en `pubspec.yaml`, p. ej. Flutter 3.x / Dart SDK >=3.9).
- SDK de Firebase configurado para las plataformas que quieras ejecutar (Android/iOS/web/windows/macOS/linux).
- Variables de entorno y archivo `.env` (ya incluido como asset en `pubspec.yaml`).

Dependencias relevantes (ver `pubspec.yaml`):

- firebase_core
- firebase_auth
- cloud_firestore
- provider
- flutter_dotenv

## Variables de entorno

La aplicación carga variables desde un archivo `.env` en la raíz del proyecto (esto ya aparece en `pubspec.yaml` como asset). Usualmente contiene claves relacionadas a Firebase o configuraciones locales. Ejemplo mínimo (NO compartir secretos públicos):

```
FIREBASE_API_KEY=...
FIREBASE_APP_ID=...
FIREBASE_MESSAGING_SENDER_ID=...
FIREBASE_PROJECT_ID=...
```

Sin embargo, el proyecto también incluye `firebase_options.dart` (generado por FlutterFire). Si usas ese archivo y tus credenciales locales están correctamente configuradas, la app inicializa Firebase automáticamente.

## Cómo ejecutar (Windows — PowerShell)

1. Asegúrate de tener Flutter instalado y disponible en tu PATH.
2. Desde la raíz del proyecto (ej. `mobile-products-app`) instala dependencias:

```powershell
flutter pub get
```

3. Ejecuta la app en un emulador o dispositivo conectado:

```powershell
flutter run
```

4. Para ejecutar en Windows desktop (si tienes habilitado el soporte):

```powershell
flutter run -d windows
```

5. Para compilar un APK (Android):

```powershell
flutter build apk --release
```

## Comandos útiles para verificación (análisis y tests)

```powershell
flutter analyze
flutter test
```

Si alguno de estos comandos falla, comparte la salida y te ayudo a corregir los problemas.

## Estructura clave del proyecto

- `lib/main.dart` — punto de entrada, inicializa Firebase y providers.
- `lib/pages/` — pantallas de la app (login, productos, categorías, proveedores, carrito, checkout, etc.).
- `lib/services/` — servicios que encapsulan llamadas a Firestore y Auth.
- `lib/models/` — modelos de datos (`product.dart`, `category.dart`, `supplier.dart`).
- `lib/providers/` — providers para estado (carrito, proveedores, etc.).

## Qué verificar para la entrega (checklist sugerido)

- [ ] Confirmar que `firebase_options.dart` corresponde al proyecto Firebase que se evaluará.
- [ ] Añadir/confirmar el contenido del `.env` si el professor requiere variables específicas.
- [ ] Probar registro/login y recuperación de contraseña con cuentas de prueba.
- [ ] Probar CRUD de proveedores: crear, editar y eliminar un proveedor.
- [ ] Probar que al realizar checkout se muestra la página de agradecimiento.

## Limitaciones y mejoras sugeridas

- No hay integración de pagos reales — el flujo de compra es simulado; podrías integrar un gateway (Stripe, Flow, etc.) si el enunciado lo pide.
- Añadir validaciones y mensajes más robustos en la UI para manejo de errores de red o permisos.
- Agregar tests unitarios/widget para las principales pantallas y servicios. Actualmente existe la plantilla `test/widget_test.dart`.

## Cómo puedo ayudar a afinar el README

Si quieres que adapte el README exactamente al enunciado del profesor, por favor:

1. Coloca el PDF del enunciado dentro del workspace (p. ej. en la raíz del proyecto) o pega aquí los criterios clave.
2. Indica si hay criterios de evaluación extra (p. ej. entrega en GitHub Pages, video demostración, criterios de diseño).

Una vez tenga el enunciado, actualizaré el README para reflejar los puntos obligatorios y las evidencias requeridas.

---

Archivo original reemplazado. Si quieres que también añada una sección de evidencia (screenshots, video link) o tests automatizados, dime y lo implemento.

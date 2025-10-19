# Mobile Products App (Examen — Computación Móvil)

Aplicación de e-commerce móvil desarrollada en Flutter que utiliza Firebase como Backend-as-a-Service (BaaS).
Esta aplicación fue creada como entregable del examen del ramo de Computación Móvil. El README describe
las funcionalidades implementadas, cómo ejecutar el proyecto localmente, configuración requerida y
un mapeo entre las características del código.

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

La aplicación cubre los requisitos pedidos en el enunciado del examen:

- Gestión de usuarios (registro/login/recuperación): implementado (`lib/services/auth_service.dart`).
- CRUD de entidades del negocio (proveedores implementan create/update/delete). Productos y categorías tienen operaciones de lectura y actualizaciones puntuales.
- Carrito y proceso de compra simulado: presente en `lib/providers/cart_provider.dart` y páginas de UI correspondientes (`lib/pages/`).
- Integración con Firebase (Firestore y Auth) y uso de `firebase_options.dart` para configuración por plataforma.

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

El proyecto también incluye `firebase_options.dart` (generado por FlutterFire). Si usas ese archivo y tus credenciales locales están correctamente configuradas, la app inicializa Firebase automáticamente.

## Cómo ejecutar (Windows — PowerShell)

1. Asegúrate de tener Flutter instalado y disponible en tu PATH.
2. Desde la raíz del proyecto (ej. `mobile-products-app`) instala dependencias:

# Entrega — Examen Computación Móvil

Profesor,

Adjunto mi entregable del examen de Computación Móvil: una aplicación móvil de e-commerce desarrollada en Flutter que utiliza Firebase como backend. A continuación describo, de manera concisa lo que implementé, cómo probarlo y qué puntos revisar para la evaluación.

Resumen rápido

- Tecnologías: Flutter, Firebase (Authentication y Cloud Firestore), Provider.
- Funcionalidades principales: registro/login/recuperación de usuarios, listado y detalle de productos, listado de categorías, CRUD básico de proveedores, carrito de compras y flujo de finalización de compra (simulado) con página de agradecimiento.

Estado del proyecto (implementado)

- Autenticación: registro, inicio de sesión y recuperación de contraseña — `lib/services/auth_service.dart`.
- Productos: listado y detalle; actualizaciones puntuales desde servicios — `lib/services/product_service.dart` y `lib/models/product.dart`.
- Categorías: listado — `lib/services/category_service.dart` y `lib/models/category.dart`.
- Proveedores: CRUD completo (crear/editar/eliminar/leer) — `lib/services/supplier_service.dart` y `lib/models/supplier.dart`.
- Carrito: agregar/remover ítems y conteo de ítems — `lib/providers/cart_provider.dart`.
- Flujo de compra: proceso simulado que termina en `lib/pages/thank_you_page.dart`.
- Rutas principales definidas en `lib/main.dart` (dashboard, products, categories, suppliers, recover).

Requisitos y dependencias

- Flutter (usar la versión compatible con el SDK declarado en `pubspec.yaml`).
- Firebase configurado para la(s) plataforma(s) objetivo. El proyecto incluye `firebase_options.dart` generado por FlutterFire para inicializar la app.
- Variables desde `.env` (opcional si `firebase_options.dart` ya gestiona las credenciales). El proyecto usa `flutter_dotenv` como dependencia opcional.

Dependencias clave (ver `pubspec.yaml`):

- firebase_core
- firebase_auth
- cloud_firestore
- provider
- flutter_dotenv

Cómo ejecutar (Windows — PowerShell)

1. Desde la raíz del repo, instalar dependencias:

```powershell
flutter pub get
```

2. Ejecutar la app en un dispositivo o emulador:

```powershell
flutter run
```

3. Ejecutar en Windows desktop (si está habilitado):

```powershell
flutter run -d windows
```

4. Generar APK Android:

```powershell
flutter build apk --release
```

Comandos útiles para verificación

- flutter analyze
- flutter test

Archivos y rutas importantes (evidencia de implementación)

- `lib/main.dart` — inicialización de Firebase y providers.
- `lib/pages/` — pantallas: login, register, products, product detail, categories, suppliers, cart, checkout, thank you.
- `lib/services/` — servicios para Auth, Firestore (productos, categorías, proveedores).
- `lib/models/` — modelos de datos (product, category, supplier).
- `lib/providers/` — providers para estado (cart, suppliers, etc.).

Checklist sugerido para la evaluación

- [ ] Verificar que `firebase_options.dart` apunta al proyecto Firebase que use para evaluar.
- [ ] Registrar un usuario y comprobar login y recuperación de contraseña.
- [ ] Probar CRUD de proveedores (crear, editar, eliminar).
- [ ] Añadir productos al carrito y completar el flujo hasta la página de agradecimiento.

Limitaciones y observaciones

- El flujo de pagos es simulado; no se integró un gateway real (p. ej. Stripe). Si el enunciado exige pagos reales, puedo añadirlo.
- Faltan tests automatizados profundos; sólo existe la plantilla de `test/widget_test.dart`.

# 🔐 Locksy `v1.0.0`

> **Gestor de contraseñas zero-knowledge. Tu vault, tus reglas.**  
> Construido con React Native · .NET · AES-256-GCM

---

## ✦ ¿Qué es Locksy?

Locksy es un gestor de contraseñas personal construido sobre una arquitectura **zero-knowledge** — tu master password nunca sale de tu dispositivo. Cada credencial se cifra del lado del cliente con AES-256-GCM antes de llegar al servidor.

Nadie puede leer tus contraseñas. Ni nosotros.

---

## ✦ Qué incluye esta versión

### 🔒 Seguridad
- Cifrado de extremo a extremo con **AES-256-GCM**
- Derivación de clave con **PBKDF2** desde la master password
- Arquitectura **zero-knowledge** — el servidor solo almacena texto cifrado
- Protección contra capturas de pantalla en la vista de detalle
- **Desbloqueo biométrico** — Face ID / Huella dactilar
- **Bloqueo por PIN** — PIN de 4 dígitos con teclado aleatorio en la pantalla de desbloqueo
- Auto-bloqueo cuando la app pasa a segundo plano

### 🗄️ Bóveda
- Crear, editar y eliminar credenciales cifradas
- Campos: sitio/app, usuario, contraseña, categoría, notas
- **Indicador de fortaleza de contraseña** (barra de 5 niveles)
- **Generador de contraseñas** — longitud configurable, mayúsculas, números, símbolos
- Marcar credenciales como favoritas con filtro rápido
- Búsqueda por título y usuario
- Filtrar por categoría

### 🗂️ Categorías
- Crea categorías personalizadas con nombre, ícono (15 presets) y color (10 presets)
- Vista previa en tiempo real al crear
- Contador de credenciales por categoría
- Estado compartido — los cambios se reflejan instantáneamente en todas las pantallas

### 👤 Perfil
- Login con Google OAuth
- Configuración de master password en el primer acceso
- Resumen del estado de seguridad
- Detalles del cifrado y cómo funciona
- Versión de la app, stack tecnológico e información de licencia

### ⚙️ Configuración
- Activar/desactivar **bloqueo por PIN** (configura un PIN de 4 dígitos)
- Activar/desactivar **Face ID / Huella**
- PIN y biometría son mutuamente excluyentes
- Las configuraciones de seguridad se borran al cerrar sesión o desinstalar
- Eliminar cuenta permanentemente (zero-knowledge — los datos son irrecuperables)

---

## ✦ Stack tecnológico

| Capa | Tecnología |
|---|---|
| Mobile | React Native (Expo) |
| Backend | .NET 8 / C# |
| Base de datos | MySQL |
| Autenticación | Google OAuth 2.0 + JWT |
| Cifrado | AES-256-GCM · PBKDF2 |
| Almacenamiento | expo-secure-store · AsyncStorage |

---

## ✦ Modelo de seguridad

```
Master Password
      │
      ▼
  PBKDF2 (derivación de clave)
      │
      ▼
  Clave AES-256-GCM  ──►  Cifrar credencial
                                 │
                                 ▼
                          Texto cifrado + IV
                                 │
                                 ▼
                           Enviado al servidor
                        (ilegible sin la clave)
```

La master password se almacena únicamente en `expo-secure-store` en el dispositivo.  
El servidor guarda `encryptedPassword` + `iv` — nada más.  
Si pierdes tu master password, tus datos son **irrecuperables de forma permanente**.

---

## ✦ Roadmap

- [ ] Temporizador de auto-bloqueo (tiempo de inactividad configurable)
- [ ] Bloqueo tras intentos fallidos de PIN
- [ ] Detección de contraseñas duplicadas y débiles
- [ ] Swipe para copiar usuario/contraseña desde la lista
- [ ] Notas seguras independientes (sin usuario ni contraseña)
- [ ] Exportar backup cifrado de la bóveda (archivo `.locksy`)
- [ ] Importar desde CSV / Bitwarden

---

## ✦ Licencia

**Todos los derechos reservados © 2025 Locksy**  
Este software es propietario. Se prohíbe su distribución o reproducción no autorizada.

---

<div align="center">

**LOCKSY** · Zero-knowledge · AES-256 · Hecho con ♥

</div>

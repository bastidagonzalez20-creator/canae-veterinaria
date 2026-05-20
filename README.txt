================================================================================
CANAE - URGENCIAS VETERINARIAS
Aplicación Web para Emergencias Veterinarias
================================================================================

DESCRIPCIÓN
================================================================================

CANAE es una aplicación web que ayuda a los dueños de mascotas a evaluar el 
nivel de urgencia de situaciones médicas y proporciona recomendaciones 
inmediatas, además de conectarlos con veterinarios cercanos.

Características:
- Evaluación rápida de síntomas en 5 categorías
- Determinación automática del nivel de urgencia (ALTA, MEDIA, BAJA)
- Acciones recomendadas paso a paso
- Búsqueda de veterinarios cercanos
- Llamada directa a clínicas veterinarias
- Interfaz responsiva y fácil de usar


ESTRUCTURA DEL PROYECTO
================================================================================

pet-care-app/
├── login.html                   → Punto de entrada (autenticación)
├── app.html                     → Menú principal y navegación
├── questionnaire.html           → Selección de síntomas
├── resultado.html               → Resultado de urgencia y acciones
├── veterinarios.html            → Búsqueda de veterinarios
├── sos.html                     → Pantalla de llamada de emergencia
├── index.html                   → Página antigua (legado, no usar)
├── README.txt                   → Este archivo
│
├── css/
│   └── styles.css               → Todos los estilos de la aplicación
│
└── assets/                       → Recursos multimedia
    ├── logo.png
    ├── Home.png
    ├── settings.png
    ├── perfil.png
    ├── logout.png
    ├── search.png
    └── logo_small.png


CÓMO USAR LA APLICACIÓN
================================================================================

1. ABRIR LA APP:
   - Abre login.html en tu navegador
   - Es el punto de entrada de la aplicación

2. AUTENTICACIÓN:
   - Ingresa cualquier correo y contraseña
   - O regístrate si es la primera vez
   - (En esta versión, la autenticación es simulada con localStorage)

3. EVALUAR SÍNTOMAS:
   - En el menú principal, selecciona la categoría que mejor describe
     la situación de tu mascota
   - Se abrirá el cuestionario con síntomas específicos
   - Marca los síntomas que notas en tu mascota
   - Haz click en "Continuar"

4. VER RESULTADO:
   - Se muestra el nivel de urgencia (ALTA/MEDIA/BAJA) con color
   - Aparece el mensaje recomendado según la urgencia
   - Puedes ver las acciones recomendadas
   - Puedes buscar veterinarios cercanos

5. ACCIONES INMEDIATAS:
   - Se muestran pasos numerados a seguir
   - Recomendaciones personalizadas según el nivel de urgencia
   - Botón para buscar veterinario

6. BUSCAR VETERINARIO:
   - Lista de 3 clínicas veterinarias cercanas
   - Información de distancia y teléfono
   - Botones para ver ruta o llamar directamente


ARCHIVOS HTML FUNCIONALES
================================================================================

login.html
├─ Punto de entrada de la aplicación
├─ Pantalla de autenticación y registro
├─ Gestiona localStorage para sesión de usuario
└─ Redirige a app.html después de login

app.html
├─ Menú principal de la aplicación
├─ Muestra 5 categorías de emergencias
├─ Botón SOS para emergencia directa
├─ Menú lateral con opciones de usuario
├─ Modal de confirmación de salida
└─ Redirige a questionnaire.html al seleccionar categoría

questionnaire.html
├─ Pantalla de cuestionario dinámico
├─ Carga síntomas según categoría seleccionada
├─ Permite seleccionar múltiples síntomas
├─ Evalúa urgencia usando algoritmo
└─ Redirige a resultado.html con nivel de urgencia

resultado.html
├─ Muestra nivel de urgencia (ALTA/MEDIA/BAJA) con color
├─ Muestra síntomas seleccionados
├─ Acciones recomendadas paso a paso
├─ Permite ver acciones o buscar veterinario
└─ Redirige a veterinarios.html si es necesario

veterinarios.html
├─ Lista de veterinarios cercanos
├─ Información: nombre, distancia, teléfono
├─ Estado: abierto/cerrado
├─ Botones para ver ruta o llamar
└─ Vuelve atrás

sos.html
├─ Pantalla de llamada de emergencia
├─ Interfaz tipo llamada telefónica
├─ Botones de control (silencio, altavoz, etc)
├─ Número de veterinario principal
└─ Botón para terminar llamada


CATEGORÍAS DE EVALUACIÓN
================================================================================

La aplicación evalúa 5 categorías de emergencias:

1. GOLPE / CAÍDA
   Síntomas: Cojera, llanto, inmobilidad, inflamación, respiración agitada
   Acciones: Reposo, evitar movimiento, veterinario urgente

2. DESHIDRATACIÓN
   Síntomas: Ojos hundidos, no bebe, orina poco, encías secas, cansancio
   Acciones: Ofrecer agua, lugar fresco, veterinario si es severa

3. INTOXICACIÓN
   Síntomas: Babeo excesivo, temblores, desorientación, vómito
   Acciones: Retirar sustancia, no provocar vómito, veterinario inmediato

4. HERIDA
   Síntomas: Dolor al tocar, herida abierta, inflamación, sangrado
   Acciones: Presión si sangra, limpiar, vendaje si es necesario

5. NO ESTOY SEGURO
   Síntomas: Decaimiento, inapetencia, cambio de comportamiento, llanto
   Acciones: Observación, vigilancia, consultar si dura más de 24h


NIVELES DE URGENCIA
================================================================================

ALTA (Rojo - #E8574B)
├─ Síntomas graves que requieren atención inmediata
├─ Recomendación: Acude al veterinario de inmediato
└─ Pasos: Estabiliza, tranquiliza, acude al veterinario

MEDIA (Naranja - #FFB800)
├─ Síntomas que requieren cuidado y observación
├─ Recomendación: Cuida en casa, vigila evolución
└─ Pasos: Acciones de cuidado, consulta si no mejora

BAJA (Verde - #4CAF50)
├─ Síntomas leves que probablemente mejorarán
├─ Recomendación: Observa y cuida en casa
└─ Pasos: Cuidado general, vigila evolución


ALGORITMO DE EVALUACIÓN
================================================================================

El algoritmo de urgencia funciona así:

1. Se cuentan síntomas de ALTA importancia seleccionados
2. Se cuentan síntomas de MEDIA importancia seleccionados
3. Se aplica la siguiente lógica:

   - URGENCIA ALTA si:
     * 2 o más síntomas de ALTA importancia, O
     * 1 síntoma de ALTA importancia + 3 o más síntomas totales

   - URGENCIA MEDIA si:
     * 1 síntoma de ALTA importancia, O
     * 2 o más síntomas de MEDIA importancia

   - URGENCIA BAJA si:
     * No cumple ninguno de los criterios anteriores

Ejemplo:
├─ Seleccionas: "Cojera" (ALTA) + "Inflamación" (MEDIA)
├─ highCount = 1, mediumCount = 1
├─ Resultado: URGENCIA MEDIA (tiene 1 síntoma ALTA)


FLUJO DE NAVEGACIÓN
================================================================================

                    ┌──────────────┐
                    │   LOGIN.HTML │ (Punto de entrada)
                    └──────┬───────┘
                           │
                    ┌──────▼──────┐
                    │  APP.HTML   │ (Menú principal)
                    └──────┬──────┘
                           │
      ┌────────────────────┼──────────────────┐
      │                    │                  │
   ┌──▼─────────┐    ┌────▼────┐      ┌──────▼───┐
   │QUESTIONNAIRE│   │SOS.HTML │      │VET.HTML  │
   │.HTML        │   │(Llamada)│      │(Clinicas)│
   └──┬──────────┘   └─────────┘      └──────────┘
      │
   ┌──▼────────────┐
   │RESULTADO.HTML │
   │(Urgencia +    │
   │Acciones)      │
   └───────────────┘


ALMACENAMIENTO LOCAL (localStorage)
================================================================================

La aplicación usa localStorage para guardar estado entre pantallas:

userLogged
├─ Tipo: Boolean (true/false)
├─ Uso: Verificar si usuario está autenticado
└─ Borrado al: Hacer logout

currentQuestionnaire
├─ Tipo: String (golpe, deshidratacion, intoxicacion, herida, noSeguro)
├─ Uso: Saber qué categoría está siendo evaluada
└─ Borrado al: Volver a menú principal

selectedSymptoms
├─ Tipo: JSON Array de strings
├─ Uso: Guardar síntomas seleccionados en cuestionario
└─ Borrado al: Seleccionar nueva categoría

urgencyLevel
├─ Tipo: String (high, medium, low)
├─ Uso: Guardar resultado de evaluación
└─ Borrado al: Iniciar nueva evaluación

comingFrom
├─ Tipo: String (URL)
├─ Uso: Saber de dónde vino el usuario para volver correctamente
└─ Borrado al: Cada navegación


TECNOLOGÍA
================================================================================

Frontend:
- HTML5: Estructura semántica
- CSS3: Estilos responsivos y variables
- JavaScript Vanilla: Lógica inline en cada archivo
- localStorage: Almacenamiento de sesión

Características:
- No requiere servidor
- No requiere base de datos
- Funciona completamente en el navegador
- Multi-página (MPA): Cada pantalla es un archivo HTML
- Compatible con dispositivos móviles
- Responsivo (400px a pantalla completa)


USUARIOS DE PRUEBA
================================================================================

Puedes usar cualquier correo y contraseña para la autenticación:

Ejemplos:
├─ Email: user@example.com | Contraseña: 123456
├─ Email: test@test.com | Contraseña: password
└─ Email: tu.email@mail.com | Contraseña: cualquiera

(La autenticación es simulada, no hay validación real)


VETERINARIOS DISPONIBLES
================================================================================

1. CLÍNICA PATITAS
   📍 Distancia: 1.2 km
   📞 Teléfono: 555-123-4567
   ⏰ Horario: Consultar
   
2. VETCARE 24H
   📍 Distancia: 2.0 km
   📞 Teléfono: 555-987-6543
   ⏰ Horario: Abierto 24 horas
   
3. ANIMAL HEALTH
   📍 Distancia: 3.5 km
   📞 Teléfono: 555-222-1111
   ⏰ Horario: Cerrado (consultar horarios)


INSTALACIÓN
================================================================================

1. Descarga todos los archivos en una carpeta
2. Estructura requerida:
   pet-care-app/
   ├── login.html
   ├── app.html
   ├── questionnaire.html
   ├── resultado.html
   ├── veterinarios.html
   ├── sos.html
   ├── css/
   │   └── styles.css
   └── assets/
       └── [todas las imágenes]

3. Abre login.html en tu navegador
4. ¡La app está lista para usar!

No se requiere instalación adicional, compilación o servidor.


REQUISITOS TÉCNICOS
================================================================================

Navegador:
- Chrome, Firefox, Safari, Edge (versión moderna)
- Soporte para localStorage
- JavaScript habilitado
- Soporte para CSS3 variables

Dispositivo:
- Computadora de escritorio
- Tablet
- Smartphone (responsivo)

Conexión:
- No requiere internet después de cargar la app
- Las imágenes necesitan estar en la carpeta assets/


RESOLUCIÓN DE PROBLEMAS
================================================================================

Problema: "Página no encontrada" o "404"
Solución: Asegúrate de que todos los archivos .html estén en la misma carpeta

Problema: Las imágenes no cargan
Solución: Verifica que la carpeta assets/ exista y tenga las imágenes

Problema: Los estilos no funcionan
Solución: Verifica que css/styles.css esté en la ruta correcta

Problema: No puedo navegar entre pantallas
Solución: Asegúrate de que JavaScript está habilitado en el navegador

Problema: Los datos no se guardan
Solución: Verifica que localStorage está habilitado (no uses modo incógnito)

Problema: El cuestionario no carga síntomas
Solución: Verifica que hayas seleccionado una categoría desde app.html


COLOR PALETTE
================================================================================

Colores principales:
├─ Rosa primario (#F4D4C1) - Fondos cálidos
├─ Coral (#E8907B) - Acentos
├─ Rosa claro (#FFF5F0) - Fondos secundarios
└─ Coral oscuro (#D4605C) - Bordes

Colores de urgencia:
├─ ALTA: Rojo (#E8574B)
├─ MEDIA: Naranja (#FFB800)
└─ BAJA: Verde (#4CAF50)

Colores de texto:
├─ Texto oscuro (#2C3E50)
└─ Texto gris (#95A5A6)

Otros:
├─ Blanco (#FFFFFF)
├─ Azul claro (#E8F3F8)
└─ Sombra: rgba(0,0,0,0.1)


CARACTERÍSTICAS FUTURAS
================================================================================

Posibles mejoras:
- Integración con API de veterinarios reales
- Autenticación con usuario y contraseña reales
- Guardado de historial de consultas
- Notificaciones de seguimiento
- Chat con veterinarios
- Ubicación GPS real
- Base de datos de emergencias por región
- Recomendaciones personalizadas por raza
- Recordatorios de citas


VERSIÓN
================================================================================

Versión: 2.0 (Multi-archivo funcional)
Última actualización: Mayo 2026
Licencia: Libre uso para propósitos educativos y personales

Cambios en v2.0:
- División en 6 archivos HTML funcionales
- Cada archivo es independiente pero conectado
- Mejor mantenibilidad y escalabilidad
- Navegación clara entre pantallas
- Almacenamiento de estado en localStorage


================================================================================
¡Gracias por usar CANAE - Urgencias Veterinarias!
================================================================================

# PulseTime ⏱️

**PulseTime** es una aplicación de gestión de tareas y productividad basada en la técnica Pomodoro. Permite a los usuarios organizar tareas, asignar prioridades, estimar pomodoros y realizar seguimiento del tiempo de enfoque.

## 🚀 Características

- ✅ **Gestión de Tareas**: Crea, visualiza y organiza tus tareas
- 🎯 **Sistema de Prioridades**: Clasifica tareas por prioridad (alta, media, baja)
- 🍅 **Estimación de Pomodoros**: Planifica el tiempo necesario para cada tarea
- 📊 **Vista de Tareas**: Visualiza todas tus tareas organizadas por proyecto
- 🎨 **Interfaz Moderna**: Diseño limpio y responsive con Tailwind CSS 4
- ⚡ **Reactivo**: Desarrollado con Vue 3 Composition API

## 🛠️ Tecnologías

- **Vue 3.5.24** - Framework JavaScript progresivo
- **Vite 7.2.4** - Build tool y dev server ultrarrápido
- **Tailwind CSS 4.1.17** - Framework de CSS utility-first
- **Script Setup** - Sintaxis simplificada de Vue 3

## 📁 Estructura del Proyecto

```
pulseTime/
├── public/              # Archivos estáticos
├── src/
│   ├── assets/          # Recursos (imágenes, fuentes, etc.)
│   ├── components/      # Componentes de Vue
│   │   ├── ui/          # Componentes de UI reutilizables
│   │   │   └── LogoBrand.vue
│   │   ├── FormTask.vue       # Formulario para agregar tareas
│   │   ├── Header.vue         # Encabezado de la aplicación
│   │   ├── Hero.vue           # Sección hero
│   │   ├── Navigation.vue     # Navegación principal
│   │   ├── TaskCard.vue       # Tarjeta individual de tarea
│   │   └── TaskView.vue       # Vista de lista de tareas
│   ├── data/
│   │   └── tasks.js           # Datos de tareas (temporal)
│   ├── App.vue          # Componente raíz
│   ├── main.js          # Punto de entrada
│   └── style.css        # Estilos globales
├── index.html
├── package.json
├── vite.config.js       # Configuración de Vite
└── README.md
```

## 🎯 Componentes Principales

### FormTask
Formulario para crear nuevas tareas con los siguientes campos:
- Título de la tarea
- Prioridad (alta, media, baja)
- Pomodoros estimados
- Estado de completado

Utiliza `v-model` bidireccional y emite eventos al componente padre.

### TaskView
Muestra la lista de tareas recibidas como props. Renderiza cada tarea usando el componente `TaskCard`.

### TaskCard
Componente de tarjeta individual que muestra la información de una tarea específica.

### Header & Hero
Componentes de presentación para la interfaz de usuario.

## 📦 Instalación

```bash
# Clonar el repositorio
git clone <repository-url>

# Navegar al directorio
cd pulseTime

# Instalar dependencias
npm install
```

## 🚀 Desarrollo

```bash
# Iniciar servidor de desarrollo
npm run dev
```

El servidor estará disponible en `http://localhost:5173`

## 🏗️ Build

```bash
# Compilar para producción
npm run build

# Previsualizar build de producción
npm run preview
```

## 💡 Características Técnicas

### Composition API
El proyecto utiliza la Composition API de Vue 3 con `<script setup>` para una sintaxis más concisa y mejor organización del código.

### Reactividad
- Variables reactivas con `ref()`
- Lifecycle hooks con `onMounted()`
- Props y Emits para comunicación entre componentes

### Comunicación de Componentes
- **Props**: Para pasar datos de padre a hijo
- **Emits**: Para enviar eventos de hijo a padre
- **v-model**: Para binding bidireccional de datos del formulario

### Gestión de Estado
Actualmente utiliza refs locales en `App.vue`. Estructura preparada para integrar Pinia o Vuex en el futuro.

## 🔄 Estado Actual del Proyecto

### ✅ Implementado
- Estructura base del proyecto
- Componentes principales (Header, Hero, FormTask, TaskView, TaskCard)
- Sistema de formularios con v-model bidireccional
- Visualización de tareas
- Datos de prueba simulados
- Estilos con Tailwind CSS

### 🚧 En Desarrollo
- Sistema de rutas con Vue Router
- Persistencia de datos (localStorage o backend)
- Temporizador Pomodoro
- Filtros y búsqueda de tareas
- Estadísticas y reportes

### 📋 Próximas Funcionalidades
- Backend con API REST
- Autenticación de usuarios
- Base de datos
- Gestión de proyectos
- Notificaciones
- Temas claro/oscuro

## 📝 Modelo de Datos

```javascript
{
  id: String,                    // ID único
  title: String,                 // Título de la tarea
  description: String,           // Descripción detallada
  project_id: Number,            // ID del proyecto asociado
  user_id: Number,               // ID del usuario
  completed: Boolean,            // Estado de completado
  priority: String,              // "high", "medium", "low"
  status: String,                // "pending", "in_progress", "done"
  created_at: String,            // Fecha de creación
  updated_at: String,            // Fecha de actualización
  due_date: String,              // Fecha límite
  pomodoro_count: Number,        // Pomodoros completados
  estimated_pomodoros: Number,   // Pomodoros estimados
  total_focus_time: Number,      // Tiempo total en minutos
  last_pomodoro_at: String       // Último pomodoro realizado
}
```

## 👨‍💻 Autor

Manuel - Proyecto PulseTime

## 📄 Licencia

Proyecto privado en desarrollo

---

**Última actualización**: 25 de noviembre de 2025

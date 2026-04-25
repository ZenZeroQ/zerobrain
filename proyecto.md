# Sistema de Gestión con IA para Sociedad

> Un sistema de gestión documental, financiera, de proyectos y presencia digital potenciado con inteligencia artificial, diseñado para sociedades pequeñas que buscan orden, transparencia y eficiencia.

---

## 📋 Tabla de Contenidos

- [Descripción](#descripción)
- [Arquitectura](#arquitectura)
- [Estructura de Carpetas](#estructura-de-carpetas)
- [Inicio Rápido](#inicio-rápido)
- [Los 4 Pilares](#los-4-pilares)
- [Configuración de Herramientas](#configuración-de-herramientas)
- [Guía de Uso](#guía-de-uso)
- [Contribuir](#contribuir)
- [Licencia](#licencia)

---

## 📖 Descripción

Este proyecto implementa un **sistema de gestión integral con IA** para una sociedad de 4 socios. El sistema está diseñado para:

- **Gestionar conocimiento** — Documentos, decisiones, metodología
- **Administrar finanzas** — Ingresos, gastos, distribución de ganancias
- **Coordinar proyectos** — Tareas, responsabilidades, seguimiento
- **Gestionar presencia digital** — Web, redes sociales, comunicaciones
- **Potenciar con IA** — Un asistente que conoce el contexto y ayuda a decidir

### Principios de Diseño

1. **Separación datos/procesos** — Los datos son independientes de las herramientas
2. **Open source como preferencia** — Priorizamos soluciones de código abierto
3. **Escalabilidad** — Empezamos simple, crecemos según necesidad real
4. **Transparencia** — Todos los socios tienen acceso
5. **Privacidad** — La información sensible queda local

---

## 🏗️ Arquitectura

```
┌─────────────────────────────────────────────────────────────────┐
│                    REPOSITORIO GITHUB                           │
│                   (metodología pública)                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  📁 proyecto-sociedad/                                          │
│  ├── 📄 README.md                  ← Este archivo               │
│  ├── 📄 LICENSE.md                ← Licencia MIT               │
│  ├── 📄 .gitignore               ← Archivos excluidos          │
│  │                                                               │
│  ├── 📁 docs/                    ← Documentación               │
│  │   ├── genesis_proceso.md                                  │
│  │   ├── propuesta_sistema.md                                │
│  │   └── estructura_pilares.md                               │
│  │                                                               │
│  ├── 📁 templates/               ← Plantillas reutilizables     │
│  │   ├── genesis_socio.md                                   │
│  │   ├── bitacora_entrada.md                                 │
│  │   ├── objetivos.md                                       │
│  │   └── contexto_pilar.md                                   │
│  │                                                               │
│  ├── 📁 programs/                ← Configuraciones de software   │
│  │   ├── 📁 zettlr/                                         │
│  │   ├── 📁 obsidian/                                       │
│  │   ├── 📁 ollama/                                         │
│  │   ├── 📁 docker/                                         │
│  │   └── 📁 scripts/                                         │
│  │                                                               │
│  └── 📁 config/                  ← Configuraciones compartidas   │
│      ├── git_settings.md                                     │
│      └── notas_estructura.md                                 │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│                    DATOS LOCALES (PRIVADOS)                     │
│                    (cada socio tiene lo suyo)                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  📁 datos/                      ← NUNCA se sube a GitHub        │
│  ├── 📁 sociedad/                                            │
│  │   ├── bitacora_privada.md                                  │
│  │   ├── reglas_finanzas.md                                   │
│  │   └── actas_firmadas/                                      │
│  │                                                               │
│  ├── 📁 personal/                                              │
│  │   └── mi_contexto.md                                        │
│  │                                                               │
│  └── 📁 ia/                                                   │
│      └── modelo_configurado/                                   │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📂 Estructura de Carpetas

```
proyecto-sociedad/
│
├── docs/                          # Documentación general
│   ├── README.md                   # Este archivo
│   ├── genesis_proceso.md          # El origen del proceso
│   ├── propuesta_sistema.md        # La propuesta completa
│   ├── estructura_pilares.md       # Detalle de los 4 pilares
│   └── guia_rapida.md              # Para nuevos miembros
│
├── templates/                      # Plantillas para usar
│   ├── genesis_socio.md            # Para crear genesis individual
│   ├── bitacora_entrada.md          # Formato para entradas
│   ├── objetivos_template.md        # Para definir objetivos
│   ├── contexto_pilar.md           # Para documentar cada pilar
│   └──decision_template.md         # Para decisiones importantes
│
├── programs/                       # Configuraciones de software
│   ├── zettlr/                     # Gestor documental Zettlr
│   │   ├── config.json
│   │   └── preferencia.css
│   ├── obsidian/                   # Gestor de notas Obsidian
│   │   ├── vault-settings.json
│   │   └── plugins-config.css
│   ├── ollama/                     # IA local
│   │   ├── models.txt              # Modelos a usar
│   │   └── system-prompt.md        # Prompt base del sistema
│   ├── docker/                     # Contenedores
│   │   ├── docker-compose.yml
│   │   └── services/
│   │       ├── gestordocs/
│   │       ├── finances/
│   │       └── ia-assistant/
│   └── scripts/                    # Automatizaciones
│       ├── setup.sh                # Script de instalación
│       ├── update.sh               # Actualizar proyecto
│       └── backup.sh               # Backup de datos
│
├── config/                         # Configuraciones compartidas
│   ├── git_settings.md             # Settings de git
│   ├── estructura_notas.md         # Cómo organizar notas
│   └── convenciones.md             # Convenciones del equipo
│
├── .gitignore                      # Archivos excluidos de git
└── LICENSE                         # Licencia MIT
```

---

## 🚀 Inicio Rápido

### 1. Clonar el Repositorio

```bash
git clone https://github.com/tu-usuario/proyecto-sociedad.git
cd proyecto-sociedad
```

### 2. Configurar tu Entorno Local

```bash
# Ejecutar script de setup
chmod +x programs/scripts/setup.sh
./programs/scripts/setup.sh
```

### 3. Crear tu Carpeta de Datos Locales

```bash
mkdir -p datos/sociedad datos/personal datos/ia
```

### 4. Copiar Plantillas a tu Carpeta Local

```bash
# Para tu contexto personal
cp templates/genesis_socio.md datos/personal/mi_genesis.md

# Para la sociedad
cp templates/bitacora_entrada.md datos/sociedad/
```

### 5. Configurar Herramientas

Ver la sección [Configuración de Herramientas](#configuración-de-herramientas) para instrucciones de cada herramienta.

---

## 🏛️ Los 4 Pilares

### Pilar 1: Gestión Documental

**Objetivo:** Todo lo que sabemos, documentado y accesible.

**Componentes:**
- Sistema de conocimiento centralizado
- Gestor documental (Zettlr u Obsidian)
- Proceso de firma de documentos
- Control de versiones de documentos

**Flujo:**
```
Documento → Se redacta → Se guarda → Se comparte → Se firma → Se archiva
```

**Herramientas sugeridas:**
- Zettlr (open source, Markdown, funciona offline)
- Obsidian (alternativa con más features)
- Git (control de versiones)

---

### Pilar 2: Gestión de Finanzas

**Objetivo:** Clarity sobre ingresos, gastos y distribución de ganancias.

**Componentes:**
- Registro de ingresos y gastos
- Facturación
- Distribución de ganancias (reglas claras)
- Dashboard por socio

**Reglas mínimas requeridas:**
1. ¿Cómo se valora el trabajo de cada socio?
2. ¿Cómo se distribuyen las ganancias?
3. ¿Hay remuneración por trabajo antes de ganancias?
4. ¿Qué pasa si alguien quiere retirarse?

**Herramientas sugeridas:**
- Planilla de cálculo (Google Sheets, Excel)
- Gnucash o Ledger (open source, contabilidad)
- Scripts personalizados para reportes

---

### Pilar 3: Gestión de Proyectos

**Objetivo:** Saber en todo momento qué hacemos y quién hace qué.

**Componentes:**
- Tablero de proyectos
- Registro de decisiones por proyecto
- Asignación de responsabilidades
- Timeline de hitos

**Flujo:**
```
Proyecto → Estado → Responsables → Próximo paso → Decisión pendiente
```

**Herramientas sugeridas:**
- Wekan (open source, tipo Trello)
- Taskwarrior (línea de comandos)
- Notion (si prefieren interfaz visual)

---

### Pilar 4: Gestión Social / Presencia Digital

**Objetivo:** Tener identidad digital profesional.

**Componentes:**
- Sitio web de la sociedad
- Gestión de comunicaciones
- Redes sociales (si aplica)
- Publicación de casos de éxito

**Nota:** Este pilar se activa cuando los otros tres estén funcionando.

**Herramientas sugeridas:**
- GitHub Pages (alojamiento web, gratis)
- HTML/CSS/JS simple (sin frameworks complejos)
- Formspree (formularios sin backend)

---

## 🔧 Configuración de Herramientas

### Zettlr (Gestor Documental)

**Instalación:**
```bash
# Descargar desde https://www.zettlr.com/
# O en Linux:
sudo snap install zettlr
```

**Configuración del proyecto:**

1. Abrir Zettlr
2. Ir a `Archivo` → `Abrir espacio de trabajo`
3. Seleccionar la carpeta `proyecto-sociedad/`
4. Zettlr cargará la estructura y estará listo

**Configuraciones recomendadas:**

- Formato: Markdown
- Exportar: PDF, DOCX
- Zettelkasten: Activado
- Mostrar línea de números: Sí

---

### Obsidian (Gestor de Notas Alternativo)

**Instalación:**
```bash
# Descargar desde https://obsidian.md/
# O en Linux:
sudo snap install obsidian
```

**Configuración:**

1. Abrir Obsidian
2. `Abrir otra bóveda` → `Crear nueva`
3. Nombre: `SociedadAssistant`
4. Ubicación: `proyecto-sociedad/`
5. En Configuración → Plugins:
   - Activar "Local REST API"
   - Activar "Templates"

**Plugins recomendados:**
- Local REST API (para integración con IA)
- Templater (para crear documentos desde plantillas)
- Git (backup automático a GitHub)

---

### Ollama (IA Local)

**Instalación:**
```bash
# En Mac/Linux:
curl -fsSL https://ollama.com/install.sh | sh

# En Windows (PowerShell):
winget install Ollama.Ollama
```

**Configuración:**

```bash
# Descargar modelo base (requiere ~4GB RAM mínimo)
ollama pull llama3:8b

# Ver modelos disponibles
ollama list

# Crear archivo de configuración del sistema
# Ver programs/ollama/system-prompt.md
```

**Uso con el proyecto:**

```bash
# Iniciar servidor local
ollama serve

# En tu navegador:
# http://localhost:11434
```

---

### Docker (Contenedores)

**Instalación:**
```bash
# En Ubuntu/Debian:
sudo apt update
sudo apt install docker.io docker-compose

# En Mac/Windows:
# Descargar Docker Desktop desde docker.com
```

**Usar los contenedores del proyecto:**

```bash
# Ir a la carpeta de docker
cd programs/docker

# Levantar todos los servicios
docker-compose up -d

# Ver servicios activos
docker-compose ps

# Detener servicios
docker-compose down
```

**Servicios incluidos:**
- `gestordocs`: Sistema de gestión documental
- `finances`: Panel de finanzas
- `ia-assistant`: API de IA para el asistente

---

## 📚 Guía de Uso

### Para Nuevos Socios

1. **Lee la documentación**
   - Lee `docs/genesis_proceso.md`
   - Lee `docs/propuesta_sistema.md`
   - Familiarízate con la estructura

2. **Configura tu entorno**
   - Sigue las instrucciones en [Inicio Rápido](#inicio-rápido)
   - Instala las herramientas que prefieras

3. **Completa tu Génesis**
   - Copia `templates/genesis_socio.md` a tu carpeta local
   - Llena con tu información
   - No subas nada personal a GitHub

4. **Participa en la bitácora**
   - Agrega entradas cuando haya decisiones
   - Usa el formato en `templates/bitacora_entrada.md`

### Para Mantener el Sistema

**Semanalmente:**
- Revisar bitácora de la sociedad
- Actualizar estado de proyectos
- Agregar entradas de decisiones nuevas

**Mensualmente:**
- Revisar métricas de finanzas
- Actualizar objetivos si es necesario
- Hacer backup de datos locales

**Por decisión:**
- Documentar en bitácora con formato
- Archivar documento en carpeta correspondiente
- Actualizar estado de pilares si cambió

---

## 🤝 Contribuir

Este proyecto es para uso interno de la sociedad, pero si quieres contribuir o adaptarlo:

1. Haz fork del repositorio
2. Crea una rama para tu feature (`git checkout -b feature/nueva-funcion`)
3. Haz commit (`git commit -m 'Agrega nueva función'`)
4. Push a la rama (`git push origin feature/nueva-funcion`)
5. Abre un Pull Request

---

## 📄 Licencia

Este proyecto usa licencia MIT. Ver archivo `LICENSE` para más detalles.

---

## 📞 Contacto

Para preguntas sobre el proyecto, contacta a los socios directamente.

---

## 🗺️ Roadmap

- [ ] Fase 1: Gestión Documental (en proceso)
- [ ] Fase 2: Gestión de Finanzas (pendiente)
- [ ] Fase 3: Gestión de Proyectos (pendiente)
- [ ] Fase 4: Gestión Social (pendiente)
- [ ] Integración con IA (en diseño)

---

*Este proyecto fue diseñado siguiendo principios de open source, separación de datos/procesos, y eficiencia operativa.*
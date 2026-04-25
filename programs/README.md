# Configuraciones de Programas

Esta carpeta contiene las configuraciones para todas las herramientas que usa el sistema.

```
programs/
├── zettlr/         # Gestor documental Zettlr
├── obsidian/       # Gestor de notas Obsidian
├── ollama/          # Motor de IA local
├── docker/          # Contenedores Docker
└── scripts/         # Scripts de automatización
```

---

## Zettlr (Gestor Documental)

Zettlr es un editor de Markdown open source, diseñado para gestión de conocimiento y escritura académica. Soporta Zettelkasten, exportación a múltiples formatos, y funciona completamente offline.

### Instalación

**Linux:**
```bash
# Opción 1: Snap
sudo snap install zettlr

# Opción 2: AppImage
wget https://github.com/Zettlr/Zettlr/releases/download/v2.x.x/Zettlr-linux-x64.AppImage
chmod +x Zettlr-linux-x64.AppImage
./Zettlr-linux-x64.AppImage
```

**Mac:**
```bash
brew install --cask zettlr
```

**Windows:**
Descargar desde https://www.zettlr.com/download

### Configuración Recomendada

1. Abrir Zettlr
2. Ir a `Archivo` → `Preferencias`
3. Configurar:

```json
{
  "editor": {
    "spellcheck": true,
    "showLineNumbers": true,
    "mode": "source",
    "writeMode": "vim",
    "fontSize": 14
  },
  "export": {
    "pdf": {
      "defaultFont": "Fira Code",
      "fontSize": 11
    }
  },
  "zettelkasten": {
    "autoComplete": true,
    "-IDlength": 6
  },
  "fileManager": {
    "workspace": "/ruta/a/proyecto-sociedad"
  }
}
```

### Atajos Útiles

| Atajo | Acción |
|-------|--------|
| `Ctrl+Shift+L` | Abrir archivo rápido |
| `Ctrl+E` | Exportar |
| `Ctrl+T` | Nueva pestaña |
| `Ctrl+P` | Búsqueda de proyecto |

---

## Obsidian (Gestor de Notas)

Obsidian es un editor de notas conocimiento. Permite crear una red de notas interconectadas con enlaces bidireccionales. Muy flexible y extensible con plugins.

### Instalación

**Linux:**
```bash
# Opción 1: Snap
sudo snap install obsidian --classic

# Opción 2: AppImage
wget https://github.com/obsidianmd/obsidian-releases/releases/download/v1.x.x/obsidian_x.x.x_amd64.AppImage
chmod +x obsidian_x.x.x_amd64.AppImage
./obsidian_x.x.x_amd64.AppImage
```

**Mac:**
```bash
brew install --cask obsidian
```

**Windows:**
Descargar desde https://obsidian.md/download

### Plugins Recomendados

| Plugin | Función |
|--------|---------|
| **Local REST API** | Permite que scripts y外部 herramientas interactúen con Obsidian |
| **Templater** | Crea documentos desde plantillas con variables |
| **Git** | Hace backup automático a GitHub |
| **Quick Add** |快速 agregar notas y contenido |
| **Dataview** | Consulta y filtra notas como base de datos |

### Configuración del Vault

Crear archivo `obsidian/vault-config.json`:

```json
{
  "vaultName": "SociedadAssistant",
  "plugins": {
    "local-rest-api": {
      "enabled": true,
      "port": 47384
    },
    "git": {
      "enabled": true,
      "autoCommitInterval": 300
    },
    "templater": {
      "templateFolder": "templates"
    }
  },
  "appearance": {
    "showLineNumber": true,
    "showInlineTitle": true,
    "showTabTitle": true
  }
}
```

### Integración con IA

Para conectar Obsidian con Ollama:

1. Instalar plugin "Local REST API"
2. En terminal, ejecutar:
```bash
curl -X POST http://localhost:47384/v1/query \
  -H "Content-Type: application/json" \
  -d '{"query": "tu pregunta aquí", "context": "ruta/al/contexto.md"}'
```

---

## Ollama (IA Local)

Ollama permite correr modelos de lenguaje grandes (LLMs) en tu computador local. No requiere GPU potente — puede funcionar con CPU, aunque es más lento.

### Instalación

**Linux/Mac:**
```bash
curl -fsSL https://ollama.com/install.sh | sh
```

**Windows:**
```powershell
winget install Ollama.Ollama
```

### Modelos Recomendados

| Modelo | Tamaño | RAM Necesaria | Uso |
|--------|--------|---------------|-----|
| `llama3:8b` | 4.7 GB | 8 GB+ | Bueno para todo, balance general |
| `mistral:7b` | 4.1 GB | 6 GB+ | Más eficiente, buena comprensión |
| `mixtral:8x7b` | 26 GB | 32 GB+ | Más capaz, requiere más recursos |
| `codellama:7b` | 3.8 GB | 6 GB+ | Especializado en código |

### Descargar Modelos

```bash
# Modelo base para empezar
ollama pull llama3:8b

# Modelo eficiente
ollama pull mistral:7b

# Si tienes hardware capaz
ollama pull mixtral:8x7b
```

### Archivo de Configuración del Sistema

Crear `ollama/system-prompt.md`:

```markdown
# Sistema Prompt para Asistente de Sociedad

Eres un asistente de IA configurado para conocer el contexto de una sociedad de 4 socios en Chile.

## Tu Rol
- Ayudar a tomar decisiones informadas
- Analizar situaciones y proponer opciones
- Mantener consistencia con decisiones previas
- Recordar el contexto de la sociedad

## Cómo Funcionas
1. Conoces la información de los documentos cargados
2. Respondes basándote en ese contexto
3. Siempre indicas cuando falta información
4. No inventas información — dices "no sé" si no tienes datos

## Limitaciones
- No tienes acceso a internet
- No puedes tomar decisiones por otros
- Solo puedes acceder a documentos que se te proporcionen

## Formato de Respuestas
- Claro y directo
- Con puntos si hay varios items
- Indicas cuando algo es sugerencia vs. hecho
- Siempre preguntás si necesitas más contexto

## Contexto Actual de la Sociedad
[Sera actualizado con la información real cuando esté disponible]
```

### Uso con el Proyecto

```bash
# Iniciar servidor
ollama serve

# Probar en terminal
ollama run llama3

# O usar API
curl http://localhost:11434/api/generate -d '{
  "model": "llama3:8b",
  "prompt": "tu pregunta aquí",
  "system": "lee el archivo context.md primero"
}'
```

---

## Docker (Contenedores)

Docker permite ejecutar aplicaciones en contenedores aislados, asegurando que todo funcione igual en todos los computadores.

### Instalación

**Linux:**
```bash
sudo apt update
sudo apt install docker.io docker-compose
sudo usermod -aG docker $USER
# Cerrar sesión y volver a entrar para aplicar
```

**Mac/Windows:**
Descargar Docker Desktop desde https://docker.com/products/docker-desktop

### Servicios Incluidos

El proyecto incluye configuraciones para estos servicios:

#### Gestor Documental como Servicio

`docker/services/gestordocs/Dockerfile`:

```dockerfile
FROM nginx:alpine
COPY docs/ /usr/share/nginx/html
EXPOSE 80
```

#### Panel de Finanzas

`docker/services/finances/Dockerfile`:

```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
EXPOSE 3000
CMD ["npm", "start"]
```

#### API de IA

`docker/services/ia-assistant/Dockerfile`:

```dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
EXPOSE 8000
CMD ["uvicorn", "main:app", "--host", "0.0.0.0"]
```

### docker-compose.yml

Crear `docker/docker-compose.yml`:

```yaml
version: '3.8'

services:
  gestordocs:
    build: ./services/gestordocs
    ports:
      - "8080:80"
    volumes:
      - ./docs:/usr/share/nginx/html:ro

  finances:
    build: ./services/finances
    ports:
      - "8081:3000"
    environment:
      - DATABASE_URL=sqlite:/data/finances.db
    volumes:
      - ./data/finances:/data

  ia-assistant:
    build: ./services/ia-assistant
    ports:
      - "8082:8000"
    volumes:
      - ./data/ia:/data
    depends_on:
      - ollama

  ollama:
    image: ollama/ollama:latest
    ports:
      - "11434:11434"
    volumes:
      - ollama_data:/root/.ollama
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              count: all
              capabilities: [gpu]

volumes:
  ollama_data:
```

### Comandos Útiles

```bash
# Levantar todos los servicios
docker-compose up -d

# Ver servicios activos
docker-compose ps

# Ver logs de un servicio
docker-compose logs -f gestordocs

# Detener servicios
docker-compose down

# Rebuild si hiciste cambios
docker-compose up -d --build

# Ver uso de recursos
docker stats
```

---

## Scripts de Automatización

### setup.sh — Instalación Inicial

```bash
#!/bin/bash
# Script de setup para nuevo miembro

echo "Configurando entorno del proyecto..."

# Crear carpetas locales
mkdir -p datos/sociedad datos/personal datos/ia

# Copiar plantillas
cp templates/genesis_socio.md datos/personal/mi_genesis_ejemplo.md
cp templates/bitacora_entrada.md datos/sociedad/

# Crear .gitkeep en carpetas vacías
touch datos/sociedad/.gitkeep
touch datos/personal/.gitkeep
touch datos/ia/.gitkeep

echo "Setup completado!"
echo "Ahora:"
echo "1. Instala las herramientas que prefieras (Zettlr, Obsidian, Ollama)"
echo "2. Configura tu carpeta local en la herramienta elegida"
echo "3. Llena tu documento de genesis personal"
```

### update.sh — Actualizar Proyecto

```bash
#!/bin/bash
# Script para actualizar el proyecto

echo "Actualizando proyecto..."

# Ir a directorio del proyecto
cd "$(dirname "$0")/../.."

# Pull cambios de GitHub
git pull origin main

# Mostrar cambios
git status

echo "Actualización completada."
```

### backup.sh — Backup de Datos

```bash
#!/bin/bash
# Script para hacer backup de datos locales

BACKUP_DIR="$HOME/backups-proyecto"
TIMESTAMP=$(date +%Y%m%d_%H%M%S)

echo "Creando backup..."

# Crear directorio de backup
mkdir -p "$BACKUP_DIR"

# Comprimir datos locales
tar -czf "$BACKUP_DIR/datos_$TIMESTAMP.tar.gz" datos/

# Mostrar backup
ls -la "$BACKUP_DIR"

echo "Backup guardado en: $BACKUP_DIR/datos_$TIMESTAMP.tar.gz"
```

---

## Instalación Completa Paso a Paso

### Opción 1: Manual (Recomendada para empezar)

1. **Clonar repositorio**
```bash
git clone https://github.com/tu-usuario/proyecto-sociedad.git
cd proyecto-sociedad
```

2. **Instalar herramientas básicas**
```bash
# Zettlr
sudo snap install zettlr

# Obsidian (alternativa)
sudo snap install obsidian

# Ollama
curl -fsSL https://ollama.com/install.sh | sh

# Docker (opcional)
sudo apt install docker.io docker-compose
```

3. **Configurar carpeta local**
```bash
mkdir -p datos/sociedad datos/personal datos/ia
./programs/scripts/setup.sh
```

4. **Elegir gestor documental**
   - Zettlr: Abrir proyecto directamente
   - Obsidian: Crear vault apuntando a carpeta del proyecto

5. **Probar IA local**
```bash
ollama pull llama3:8b
ollama run llama3 "¿Funciona?"
```

### Opción 2: Con Docker (Para usuarios avançados)

```bash
# Clonar proyecto
git clone https://github.com/tu-usuario/proyecto-sociedad.git
cd proyecto-sociedad

# Levantar servicios
cd docker
docker-compose up -d

# Acceder a servicios
# - Gestor documental: http://localhost:8080
# - Panel finanzas: http://localhost:8081
# - API IA: http://localhost:8082
```

---

## Solución de Problemas

### Zettlr no abre

```bash
# En Linux, puede faltar dependencias
sudo apt install libwebkitgtk-3.0-0
```

### Ollama muy lento

```bash
# Usar modelo más pequeño
ollama pull mistral:7b
ollama run mistral "¿Funciona?"
```

### Docker no tiene permisos

```bash
# Agregar usuario al grupo docker
sudo usermod -aG docker $USER
# Cerrar sesión y volver a entrar
```

### No puedo hacer git push

```bash
# Verificar que tienes acceso
git remote -v
# Si no funciona, regenerar token de GitHub
```

---

*Documentación de configuraciones de software*
*Versión: 1.0*
*Para más detalles, ver README.md en la raíz del proyecto*
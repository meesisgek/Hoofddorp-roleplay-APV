#!/bin/bash

# Eenvoudig script om de Amersfoort RolePlay homepage na te maken met MkDocs

echo "🏗️  Amersfoort RolePlay MkDocs setup..."

# Maak project directory
PROJECT_NAME="amersfoort-roleplay"
mkdir -p "$PROJECT_NAME"
cd "$PROJECT_NAME"

# Installeer MkDocs
pip3 install mkdocs mkdocs-material

# Initialiseer MkDocs
mkdocs new . --force

# Maak eenvoudige mkdocs.yml
cat > mkdocs.yml << 'EOF'
site_name: Amersfoort RolePlay
theme:
  name: material
  language: nl
  palette:
    primary: indigo
EOF

# Creëer de exacte pagina content
cat > docs/index.md << 'EOF'
# Wet- en Regelgeving Amersfoort RolePlay

Welkom op de pagina voor de Wet- en Regelgeving van Amersfoort! Zorg ervoor, dat je voor je deelneemt aan Amersfoort, kennis hebt genomen van deze wetten.

De Algemene Plaatselijke Verordening (APV) bevat alle regels die niet te maken hebben met de Roleplay (dit zijn zogenaamd de 'server regels').

- Het Algemeen Wetboek Amersfoort bevat alle wetten voor de burgers.
- Alle overige documenten zijn specifiek bedoeld voor bepaalde zaken.

## Officiële Discord Servers

Amersfoort heeft verschillende discord servers die goed gekeurd zijn door de Hoge Raad hier kan je belangrijke informatie vinden:

| Server | Beschrijving | Discord Invite link |
|--------|--------------|-------------------|
| Amersfoort RolePlay | Main discord server van Amersfoort | Uitnodiging |
| Amersfoort Support | Support discord server van Amersfoort | Uitnodiging |
| Amersfoort Onderwereld | Onderwereld discord server van Amersfoort | Uitnodiging |
| Amersfoort Overheid | Overheids discord server van Amersfoort | Uitnodiging |

---

*De Hoofd Pagina is opgesteld uit naam van de Hoge Raad, bedoeld voor het eiland, de gemeente en de stad "Amersfoort", opgetekend door Portak te Amersfoort.*

*3 maanden geleden*
EOF

echo "✅ Setup voltooid!"
echo "📁 Ga naar de $PROJECT_NAME directory"
echo "🚀 Start de server met: mkdocs serve"
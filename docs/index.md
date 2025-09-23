#!/usr/bin/env python3
"""
Python script om de Amersfoort RolePlay homepage na te maken met MkDocs
"""

import os
import subprocess
import sys

def install_mkdocs():
    """Installeer MkDocs en Material theme"""
    print("📦 Installeren van MkDocs...")
    try:
        subprocess.check_call([sys.executable, "-m", "pip", "install", "mkdocs", "mkdocs-material"])
        print("✅ MkDocs geïnstalleerd!")
    except subprocess.CalledProcessError:
        print("❌ Fout bij installeren van MkDocs")
        return False
    return True

def create_project():
    """Maak project directory en bestanden"""
    project_name = "amersfoort-roleplay"
    
    # Maak directory
    os.makedirs(project_name, exist_ok=True)
    os.chdir(project_name)
    
    # Maak docs directory
    os.makedirs("docs", exist_ok=True)
    
    print(f"📁 Project directory '{project_name}' aangemaakt")
    return True

def create_mkdocs_config():
    """Creëer mkdocs.yml configuratie"""
    config_content = """site_name: Amersfoort RolePlay
theme:
  name: material
  language: nl
  palette:
    primary: indigo
"""
    
    with open("mkdocs.yml", "w", encoding="utf-8") as f:
        f.write(config_content)
    
    print("⚙️ mkdocs.yml aangemaakt")

def create_homepage():
    """Creëer de homepage met exacte content"""
    homepage_content = """# Wet- en Regelgeving Amersfoort RolePlay

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
"""
    
    with open("docs/index.md", "w", encoding="utf-8") as f:
        f.write(homepage_content)
    
    print("📄 Homepage (index.md) aangemaakt")

def main():
    """Hoofdfunctie"""
    print("🏗️  Amersfoort RolePlay MkDocs setup...")
    
    # Installeer MkDocs
    if not install_mkdocs():
        return
    
    # Maak project
    if not create_project():
        return
    
    # Creëer configuratie
    create_mkdocs_config()
    
    # Creëer homepage
    create_homepage()
    
    print("\n✅ Setup voltooid!")
    print("📁 Ga naar de amersfoort-roleplay directory")
    print("🚀 Start de server met: mkdocs serve")
    print("🌐 Bekijk de site op: http://127.0.0.1:8000")

if __name__ == "__main__":
    main()
# Mise à jour du serveur MCP TopSolid

Ce dépôt est un **fork** de `Julien38300/topsolid-automation-mcp` avec tes 7 recettes locales.

## Recettes locales (à ne jamais perdre)

| Recette | Description |
|---------|-------------|
| `creer_assemblage` | Crée un assemblage .TopAsm depuis le modèle "Assemblage panneau" |
| `creer_projet` | Crée un projet depuis le template "Modèle AnP" |
| `ouvrir_projet` | Ouvre un projet existant par nom |
| `texture_creation_from_image` | Crée une texture .TopTex depuis une image |
| `coating_creation_from_texture` | Crée un revêtement .TopCoa depuis une texture |
| `list_licenses` | Liste les licences TopSolid |
| `creer_esquisse_rectangle` | Esquisse rectangle avec nommage unique (version améliorée) |

## Procédure de mise à jour

Quand une nouvelle version sort sur `Julien38300/topsolid-automation-mcp` :

```bash
cd ~/Desktop/IA/topsolid-mcp-src-v1.8.3

# 1. Récupérer les nouveautés upstream
git fetch upstream

# 2. Merger dans ta branche locale
git merge upstream/main

# 3. Si conflit dans RecipeTool.cs : garder NOS recettes
#    (les recettes locales + la version améliorée de creer_esquisse_rectangle)
git checkout --ours server/src/Tools/RecipeTool.cs
git add server/src/Tools/RecipeTool.cs

# 4. Finaliser le merge
git commit -m "Merge upstream vX.Y.Z"

# 5. Pusher sur ton fork
git push origin main
```

## Compilation

```bash
cd server/src
dotnet build TopSolidMcpServer.csproj -c Release
```

## Déploiement

Copier `bin/Release/net48/TopSolidMcpServer.exe` dans :
`C:\Users\antoine.pinet\Downloads\TopSolidMcpServer-v1.8.1\`

Puis redémarrer le serveur MCP.

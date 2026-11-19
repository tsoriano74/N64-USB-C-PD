# N64 USB-C Power Delivery — N64-PSU

Projet de PCB d’alimentation USB-C pour une Nintendo 64 modifiée. Ce dépôt rassemble les sources KiCad et les fichiers de fabrication transmis par son créateur.

**État : projet réalisé par l’auteur ; documentation reconstituée à partir des fichiers. Les performances et la fabrication ne sont pas qualifiées par cette préparation.** Voir [les vérifications et points ouverts](docs/VALIDATION.md).

## Architecture

- Entrée USB-C J1, contrôleur CH224K (U3).
- U1 AP62301Z6-7, L1 3,3 µH et pont R1/R2 : sortie repérée 3,3 V, TP3.
- U2 AP62301Z6-7, L2 3,3 µH et pont R3/R4 : sortie repérée 5 V, TP5.
- TP4 et TP6 : masse.
- Rail d’entrée VBUS destiné au 12 V selon les échanges de conception retrouvés. La tension effectivement négociée reste à mesurer.

Le rôle du 5 V dans l’installation personnalisée et le câblage exact vers la console restent à documenter. Ne pas déduire le brochage de raccordement à la console à partir de la seule position des pads.

## Fichiers

| Dossier | Contenu |
|---|---|
| `hardware/` | Projet, schéma et PCB KiCad, fichiers originaux |
| `production/JLCPCBv2.zip` | Gerbers et perçages fournis |
| `production/JLCPCBv2_bom.csv` | Nomenclature d’assemblage, références LCSC non renseignées |
| `production/JLCPCBv2_positions.csv` | Positions et rotations de placement |
| `docs/images/N64-PSU.svg` | Schéma exporté pour consultation |
| `docs/PCB-INVENTORY.md` | Composants et connexions extraits du PCB |
| `docs/VALIDATION.md` | Contrôles et informations à confirmer |
| `SOURCE-SHA256.txt` | Empreintes de contrôle des six fichiers originaux |

[Consulter le schéma](docs/images/N64-PSU.svg).

## Ouvrir et modifier

Ouvrir `hardware/N64-PSU.kicad_pro` avec KiCad 10 : les sources indiquent le générateur 10.0. Les symboles et empreintes déjà placés sont inclus dans les documents KiCad ; certaines bibliothèques personnalisées et certains modèles 3D externes ne sont pas livrés. Voir les points ouverts avant de remplacer ou mettre à jour des empreintes.

## Fabrication et assemblage

L’archive de production comprend deux couches cuivre, masques, sérigraphies, pâtes à braser, contour et perçages PTH/NPTH. Le PCB déclare une épaisseur de 1,6 mm.

La BOM comporte 23 composants ; le fichier de placement comporte aussi TP3 à TP6. Vérifier dans l’outil d’assemblage que ces points de test ne deviennent pas des composants à acheter. Les références LCSC sont toutes vides : compléter et contrôler les pièces choisies avant commande. Les positions et rotations doivent être contrôlées dans l’aperçu du fabricant.

Avant de connecter la console, contrôler le câblage et mesurer les rails à vide puis en charge. Les limites de courant, le choix du chargeur et les résultats thermiques ne sont pas établis dans les fichiers transmis.

## Crédits et licence

La sérigraphie du PCB mentionne : « Based on CrazyGadget’s PSU-PLUS And Xenii 2026 ». Cette attribution est conservée ; les liens vers les projets d’origine et leurs licences restent à identifier avant de choisir une licence de redistribution.

Aucune licence supplémentaire n’est appliquée dans cette préparation. Le nom Nintendo 64 désigne la console cible et n’implique aucune affiliation avec Nintendo.

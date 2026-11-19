# N64 USB-C Power Delivery 🔌

Salut les bidouilleurs et les makers !

J’ai travaillé sur ce petit PCB à la base pour mon projet de Nintendo 64 custom : l’idée était de pouvoir alimenter la console en USB-C, avec du **12 V, du 5 V et du 3,3 V** disponibles sur la carte. Je partage ici les fichiers KiCad et les fichiers de fabrication pour que vous puissiez regarder comment c’est fait et vous en inspirer pour vos propres bidouilles.

Le PCB a été retravaillé à partir des travaux de **Xenii2026** et de **CrazyGadget**, notamment le **PSU-PLUS**. Merci à eux pour les bases du projet !

## Comment ça fonctionne ?

Le principe : utiliser un chargeur **USB-C Power Delivery compatible avec un profil 12 V**. Le contrôleur **CH224K** s’occupe de la négociation avec le chargeur, puis deux convertisseurs **AP62301Z6-7** abaissent cette tension pour obtenir le 5 V et le 3,3 V.

```text
Chargeur USB-C PD compatible 12 V
              │
       CH224K : négociation
              │
             12 V ───────────────► sortie 12 V
              ├── AP62301 ───────► sortie 5 V
              └── AP62301 ───────► sortie 3,3 V
```

Le 12 V vient donc du chargeur après négociation ; le 5 V et le 3,3 V sont générés sur le PCB. Un chargeur USB-C ne propose pas forcément le profil 12 V : pensez à vérifier le vôtre.

La N64 a été le point de départ, mais ces trois tensions peuvent aussi donner des idées pour d’autres projets de makers. À vous de vérifier que les besoins de votre montage correspondent aux capacités de la carte.

## Ce que vous trouverez ici

| Fichier ou dossier | À quoi ça sert |
|---|---|
| `hardware/` | Le projet KiCad, le schéma et le PCB pour explorer ou modifier la carte |
| `production/JLCPCBv2.zip` | Les Gerbers et les fichiers de perçage |
| `production/JLCPCBv2_bom.csv` | La liste des composants pour l’assemblage |
| `production/JLCPCBv2_positions.csv` | Les positions et rotations des composants |
| `docs/images/N64-PSU.svg` | Le schéma consultable directement |
| `docs/PCB-INVENTORY.md` | Les composants et les connexions du PCB |
| `docs/VALIDATION.md` | Les vérifications et les points à compléter |
| `SOURCE-SHA256.txt` | Les empreintes de contrôle des six fichiers originaux |

[Voir le schéma](docs/images/N64-PSU.svg) · [Voir les points à vérifier](docs/VALIDATION.md)

## Envie de mettre les mains dedans ?

Ouvrez `hardware/N64-PSU.kicad_pro` avec **KiCad 10**. Le PCB est en deux couches, avec une épaisseur déclarée de **1,6 mm**. Certaines bibliothèques personnelles et certains modèles 3D externes ne sont pas inclus ; les détails sont dans la documentation.

Quelques repères pour vous y retrouver :

- **J1** : entrée USB-C.
- **U3** : contrôleur CH224K.
- **U1 + L1** : conversion vers le 3,3 V, accessible sur **TP3**.
- **U2 + L2** : conversion vers le 5 V, accessible sur **TP5**.
- **TP4 et TP6** : masse.

## Avant de commander ou de brancher

La BOM contient **23 composants**, mais les références **LCSC sont encore à renseigner**. Le fichier de placement inclut aussi les points de test TP3 à TP6 : vérifiez leur traitement dans l’aperçu d’assemblage du fabricant.

Prenez le temps de contrôler les pièces choisies, les rotations et la cohérence des fichiers de fabrication avec votre version du PCB. Avant de brancher une console, mesurez les tensions et vérifiez le câblage. Les courants disponibles et les résultats thermiques ne sont pas encore documentés ici.

Les remarques techniques et les contrôles du projet sont regroupés dans [VALIDATION.md](docs/VALIDATION.md).

## Crédits et partage

Ce projet s’appuie sur le travail de **Xenii2026** et de **CrazyGadget / PSU-PLUS**. La sérigraphie conserve la mention « Based on CrazyGadget’s PSU-PLUS And Xenii 2026 ».

Si vous repérez une amélioration, adaptez la carte à un autre montage ou avez des retours de fabrication, venez les partager dans les issues ! C’est aussi comme ça qu’on fait avancer les projets entre makers.

Aucune licence de redistribution n’est définie pour le moment ; les licences des projets d’origine restent à vérifier avant d’en choisir une. Projet indépendant, sans affiliation avec Nintendo.

# État des vérifications

Examen du 19 novembre 2026, KiCad 10.0.1. Les six fichiers fournis sont conservés à l’identique. Les exports JLCPCB n’ont pas été régénérés : leur correspondance exacte avec les sources reste à vérifier.

## Contrôle électrique du schéma

28 signalements dans cet environnement :

- 24 × warning : `lib_symbol_mismatch`
- 2 × warning : `lib_symbol_issues`
- 2 × warning : `footprint_link_issues`

Les différences de bibliothèques peuvent dépendre de l’installation locale. Le rapport ne constitue pas une qualification électrique du circuit.

## Contrôle du PCB

Le contrôle DRC de KiCad s’est interrompu sans rapport exploitable. Aucun résultat favorable de routage n’est donc revendiqué.

## Points à compléter

- Renseigner les références LCSC, tensions de service des condensateurs, tolérances, puissances et caractéristiques des inductances.
- Confirmer le profil 12 V négocié avec le chargeur utilisé et documenter le comportement en absence de ce profil.
- Confirmer les courants disponibles par rail, la température et l’ondulation en charge.
- Vérifier les connexions EN de U1/U2, nommées « unconnected » dans le PCB, et le signal PG de U3 également non raccordé.
- Confirmer les points de raccordement 12 V et masse : TP1/TP2 du schéma ne figurent pas dans les positions de placement transmises.
- Vérifier la cohérence schéma/PCB et la correspondance des Gerbers avant toute nouvelle commande.
- Restaurer les bibliothèques personnelles : le schéma référence notamment `Matterhorn 64:PowerPad`. Le PCB contient ses empreintes intégrées mais les bibliothèques complètes ne font pas partie des six fichiers.
- Les modèles 3D mélangent les variables `KICAD9_3DMODEL_DIR` et `KICAD10_3DMODEL_DIR` ; adapter l’environnement pour la vue 3D.

Aucun essai sur matériel n’a été réalisé dans le cadre de cette préparation.

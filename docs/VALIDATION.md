# État des vérifications

Examen du 19 novembre 2026, KiCad 10.0.1. Les fichiers KiCad, Gerbers et positions d’origine sont conservés à l’identique. La BOM CSV a été enrichie le 23 novembre 2026 avec les références LCSC du fichier `production/bom.xls` fourni par l’auteur. Les exports JLCPCB n’ont pas été régénérés : leur correspondance exacte avec les sources reste à vérifier.

## Contrôle électrique du schéma

28 signalements dans cet environnement :

- 24 × warning : `lib_symbol_mismatch`
- 2 × warning : `lib_symbol_issues`
- 2 × warning : `footprint_link_issues`

Les différences de bibliothèques peuvent dépendre de l’installation locale. Le rapport ne constitue pas une qualification électrique du circuit.

## Contrôle du PCB

Le contrôle DRC de KiCad s’est interrompu sans rapport exploitable. Aucun résultat favorable de routage n’est donc revendiqué.

## Points à compléter

- Les 12 groupes de la BOM disposent désormais de leur référence LCSC. Les quantités du CSV restent celles d’une seule carte (23 composants). Vérifier les tensions de service des condensateurs, tolérances, puissances et caractéristiques des inductances pour l’usage prévu.
- Confirmer le profil 12 V négocié avec le chargeur utilisé et documenter le comportement en absence de ce profil.
- Confirmer les courants disponibles par rail, la température et l’ondulation en charge.
- Vérifier les connexions EN de U1/U2, nommées « unconnected » dans le PCB, et le signal PG de U3 également non raccordé.
- Confirmer les points de raccordement 12 V et masse : TP1/TP2 du schéma ne figurent pas dans les positions de placement transmises.
- Vérifier la cohérence schéma/PCB et la correspondance des Gerbers avant toute nouvelle commande.
- Restaurer les bibliothèques personnelles : le schéma référence notamment `Matterhorn 64:PowerPad`. Le PCB contient ses empreintes intégrées mais les bibliothèques complètes ne font pas partie des six fichiers.
- Les modèles 3D mélangent les variables `KICAD9_3DMODEL_DIR` et `KICAD10_3DMODEL_DIR` ; adapter l’environnement pour la vue 3D.

Aucun essai sur matériel n’a été réalisé dans le cadre de cette préparation.

## Retours d’assemblage du 23 novembre 2026

L’auteur a fourni des photos de la carte assemblée, une capture du message JLCPCB concernant TP3 à TP6 et une capture de référence du placement. Les points de test/soudure TP3 à TP6 n’ont pas de composant à monter et sont volontairement absents de la BOM. Le message est attendu uniquement pour ces repères.

L’auteur signale avoir corrigé la rotation de U1 et U2 dans l’aperçu d’assemblage. Vérifier la concordance du repère violet de broche 1 avec la sérigraphie. La capture est une référence visuelle ; aucun angle précis n’est déduit et le fichier de positions n’a pas été modifié.

La présence de photos de la carte assemblée ne fournit pas de mesures de courant, de température ou d’ondulation. Voir le README pour les images et les consignes de commande.


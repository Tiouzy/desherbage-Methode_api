# desherbage-Methode_api

# Outil de désherbage — méthode API · Bib'INSA Toulouse

Outil d'aide au désherbage des collections de bibliothèque, développé pour le fonds **Architecture** de Bib'INSA Toulouse. Accessible directement dans le navigateur, sans installation.

🔗 **[Accéder à l'outil](https://tiouzy.github.io/desherbage-Methode_api)**

---

## À quoi ça sert

L'outil applique la **méthode API** (Abîmé · Périmé · Inadéquat) pour aider à évaluer titre à titre si un ouvrage est candidat au désherbage. Pour chaque document, il produit :

- un **score P** (Périmé) calibré selon la discipline Dewey
- un **score I** (Inadéquat) basé sur l'historique de prêts Alma
- des **signaux de valeur patrimoniale** (lien INSA Toulouse, éditeur confidentiel, rareté estimée dans Archires)
- une **recommandation** tenant compte du SUDOC si l'information est renseignée

Le critère **A** (Abîmé) reste à évaluer manuellement en main — l'outil ne peut pas voir l'état physique du document.

---

## Utilisation

**Option 1 — Copier-coller depuis le tableur**

Copier une ligne depuis le tableau de bord Alma (export Excel) et la coller directement dans le champ de saisie. L'outil détecte automatiquement les colonnes : localisation, titre, auteur, éditeur, code-barre, année, cote, tranches, prêts avant/depuis Alma.

**Option 2 — Saisie manuelle**

Renseigner les champs un à un. Seuls le titre et quelques données de base suffisent pour obtenir une première analyse.

**Renseigner le SUDOC**

Après avoir interrogé le catalogue collectif, entrer le nombre d'exemplaires trouvés. Ce chiffre affine la recommandation finale : un document bien diffusé (> 30 exemplaires) sera orienté vers le désherbage même si les autres critères sont modérés ; un document rare (< 15 exemplaires) incitera à vérifier dans Archires avant de décider.

---

## Seuils de péremption par discipline

Les seuils du score P varient selon la cote Dewey, reflétant la vitesse à laquelle chaque domaine évolue.

| Discipline | Cote | Seuil modéré | Seuil fort | Seuil très fort |
|---|---|---|---|---|
| Architecture durable / énergie | 720.47 | 7 ans | 12 ans | 18 ans |
| Construction / matériaux | 721 | 10 ans | 15 ans | 22 ans |
| Équipements spécialisés | 725 | 10 ans | 15 ans | 22 ans |
| Urbanisme / ville | 711 | 10 ans | 18 ans | 25 ans |
| Paysage | 712 | 12 ans | 20 ans | 28 ans |
| Architecture générale / théorie | 720 | 12 ans | 20 ans | 28 ans |
| Architecture contemporaine | 724 | 15 ans | 25 ans | 35 ans |
| Habitat / logement | 728 | 12 ans | 20 ans | 28 ans |
| Histoire / patrimoine | 722, 726 | 20 ans | 35 ans | 50 ans |
| Biographie d'architecte | 720.9, 720.92 | 20 ans | 35 ans | 50 ans |

---

## Limites et précautions

L'outil produit une **aide à la décision**, pas un verdict automatique. Plusieurs points méritent attention :

- La **valeur patrimoniale** est estimée par proxy (type d'éditeur, mentions dans les métadonnées). Elle ne remplace pas une vérification dans le SUDOC et dans [Archires](https://archires.fr).
- Le **lien INSA Toulouse** n'est détecté que s'il est explicitement mentionné dans les métadonnées (champ auteur ou éditeur). Les enseignants-chercheurs INSA dont le nom seul figure dans le champ auteur ne sont pas identifiés automatiquement.
- Les **ouvrages du magasin** sans cote Dewey (cotes de type `F XXXX`) ne bénéficient pas du score P discipliné — seul le score I (usage) et les signaux patrimoniaux s'appliquent.
- Un ouvrage avec un **score élevé mais un seul exemplaire dans le SUDOC** mérite toujours un regard humain avant décision.

---

## Contexte

Développé dans le cadre du projet de désherbage du fonds Architecture de Bib'INSA Toulouse (2025-2026), couvrant la salle de lecture (cotes Dewey 700-730) et le magasin (cotes F). Le fonds comprend des ouvrages en salle et des collections conservées au magasin pour leur valeur patrimoniale potentielle.

---

## Mise à jour

Pour modifier les seuils ou ajouter une discipline : éditer le fichier `index.html`, section `const DISCIPLINES`, et le redéposer dans ce dépôt.

---

*Bib'INSA Toulouse — bibliothèque de l'Institut National des Sciences Appliquées de Toulouse*

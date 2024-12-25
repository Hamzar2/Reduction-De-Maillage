Rapport de Projet : Simplification et Analyse de Modèles 3D en Format OBJ
=========================================================================

Description du Projet
---------------------

Ce projet vise à fournir un outil performant pour le traitement de fichiers OBJ, un format standard pour les modèles 3D. Les fonctionnalités incluent le chargement, l'analyse, et la simplification de maillages 3D via des algorithmes de clustering des sommets et d'extraction d'arêtes.

### Objectifs Principaux

*   **Chargement des modèles 3D** : Lire et analyser des fichiers OBJ pour extraire les informations de sommets, textures, normales, et faces.
    
*   **Simplification des maillages** : Réduire la complexité des modèles en regroupant les sommets proches à l’aide d’un clustering basé sur une grille 3D.
    
*   **Extraction des arêtes** : Identifier les arêtes uniques des faces pour des analyses ou transformations supplémentaires.
    

Fonctionnalités Implémentées
----------------------------

### 1\. **Fonction load\_obj**

*   **Objectif** : Charger un modèle 3D à partir d’un fichier OBJ et extraire ses composants (sommets, textures, normales, faces, groupes, etc.).
    
*   **Entrée** : Chemin vers un fichier OBJ.
    
*   **Sortie** :
    
    *   Liste des sommets, coordonnées de textures, normales, et faces.
        
    *   Groupes de faces associés à des noms.
        
    *   Fichier de bibliothèque de matériaux (MTL) si présent.
        

#### Méthodologie :

*   Lecture ligne par ligne du fichier pour interpréter les mots-clés (v, vt, vn, f, g, mtllib).
    
*   Gestion des index négatifs et des faces complexes (e.g., v/vt/vn).
    

### 2\. **Fonction vertex\_clustering**

*   **Objectif** : Simplifier le maillage en regroupant les sommets dans une grille 3D.
    
*   **Entrées** :
    
    *   Sommets, textures, normales, faces.
        
    *   Résolution de la grille (int ou liste \[x, y, z\]).
        
*   **Sortie** :
    
    *   Nouvelles listes de sommets, textures, normales, et faces mises à jour.
        

#### Méthodologie :

1.  Création d’une grille 3D basée sur les dimensions du modèle.
    
2.  Attribution des sommets aux cellules de la grille.
    
3.  Calcul du barycentre (moyenne des sommets) pour chaque cellule.
    
4.  Mise à jour des indices des faces pour référencer les nouveaux sommets.
    

### 3\. **Fonction get\_edges\_from\_faces**

*   **Objectif** : Extraire les arêtes uniques à partir des faces du modèle.
    
*   **Entrée** : Liste des faces.
    
*   **Sortie** : Ensemble d’arêtes uniques.
    

#### Méthodologie :

*   Parcours des faces pour extraire les paires de sommets formant des arêtes.
    
*   Tri des indices des sommets pour garantir l’unicité des arêtes.
    

Avantages et Cas d'Utilisation
------------------------------

*   **Réduction de la complexité** : Simplifie les modèles pour des rendus ou analyses plus rapides.
    
*   **Préparation des données** : Extraction d’arêtes pour la génération de graphes ou le traitement géométrique.
    
*   **Gestion flexible des données** : Compatible avec des fichiers OBJ complexes incluant des groupes, matériaux, et index variés.
    

Technologies et Bibliothèques Utilisées
---------------------------------------

*   **Python** : Langage principal pour la manipulation des données 3D.
    
*   **NumPy** : Calcul des barycentres et opérations matricielles.
    
*   **Collections (defaultdict)** : Gestion efficace des structures de données.
    

Perspectives d'Amélioration
---------------------------

*   **Support des fichiers MTL** : Implémenter un parseur pour extraire et appliquer les matériaux associés.
    
*   **Optimisation** : Réduire les temps de calcul pour les modèles complexes.
    
*   **Visualisation** : Ajouter une interface pour prévisualiser les modèles et la simplification.
    

### Auteur

*   **Nom** : \[Idrissi Hamza\]
    

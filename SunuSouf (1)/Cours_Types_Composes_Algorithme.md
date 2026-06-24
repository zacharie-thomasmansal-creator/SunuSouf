# 📚 COURS COMPLET - LES TYPES COMPOSÉS EN ALGORITHME

---

## TABLE DES MATIÈRES
1. [Les Tableaux / Listes](#tableaux)
2. [Les Dictionnaires / Tableaux Associatifs](#dictionnaires)
3. [Les Structures / Objets](#structures)
4. [Exercices Pratiques](#exercices)

---

# <a name="tableaux"></a>
# 📦 PARTIE 1 : LES TABLEAUX / LISTES

## 1.1 Concept Théorique

**Qu'est-ce qu'un tableau?**
- Un **tableau** (ou **liste**) est une collection ordonnée d'éléments du **même type**.
- Chaque élément a une **position** appelée **indice** (index).
- Les indices commencent à **0** (premier élément) et vont jusqu'à **n-1** (n = nombre d'éléments).

**Avantages:**
- Accès rapide à n'importe quel élément par son indice
- Parcours facile avec une boucle
- Modification simple des éléments

---

## 1.2 Syntaxe Générale

```
ALGORITHME Tableau

VAR
    tableau : Tableau[1..n] d'Entier
    i : Entier

DEBUT

    { Déclaration d'un tableau }
    TABLEAU nombres[1..5] d'Entier
    
    { Affectation d'éléments }
    nombres[1] ← 10
    nombres[2] ← 20
    nombres[3] ← 30
    nombres[4] ← 40
    nombres[5] ← 50
    
    { Accès à un élément }
    Afficher(nombres[2])  { Affiche 20 }
    
    { Modification d'un élément }
    nombres[3] ← 99
    
    { Parcours du tableau }
    Pour i ← 1 à 5 Faire
        Afficher(nombres[i])
    FinPour

FIN
```

---

## 1.3 Exemple Concret - Gérer des Notes d'Élèves

```
ALGORITHME GererNotes

VAR
    { Déclaration du tableau }
    notes : Tableau[1..4] d'Entier
    i : Entier
    somme : Entier

DEBUT
    
    { === ÉTAPE 1 : DÉCLARATION ===
       On crée un tableau qui peut contenir 4 notes }
    Afficher("Déclaration d'un tableau de 4 notes")
    
    { === ÉTAPE 2 : AFFECTATION DES ÉLÉMENTS ===
       Nous ajoutons les notes dans le tableau }
    notes[1] ← 15    { 1ère note : 15 }
    notes[2] ← 18    { 2ème note : 18 }
    notes[3] ← 12    { 3ème note : 12 }
    notes[4] ← 19    { 4ème note : 19 }
    
    Afficher("Notes rentrées : 15, 18, 12, 19")
    
    { === ÉTAPE 3 : ACCÈS À UN ÉLÉMENT ===
       On récupère une note spécifique }
    Afficher("La 2ème note est : ", notes[2])  { Affiche 18 }
    
    { === ÉTAPE 4 : MODIFICATION D'UN ÉLÉMENT ===
       On change une note }
    Afficher("Modification de la 3ème note : 12 → 14")
    notes[3] ← 14
    
    { === ÉTAPE 5 : PARCOURS AVEC BOUCLE ===
       On affiche toutes les notes une par une }
    Afficher("Toutes les notes après modification :")
    Pour i ← 1 à 4 Faire
        Afficher("Note", i, " = ", notes[i])
    FinPour
    
    { === ÉTAPE 6 : TRAITEMENT DES ÉLÉMENTS ===
       Calcul de la somme et de la moyenne }
    somme ← 0
    Pour i ← 1 à 4 Faire
        somme ← somme + notes[i]
    FinPour
    
    Afficher("Somme des notes : ", somme)
    Afficher("Moyenne des notes : ", somme / 4)

FIN
```

**Résultat attendu:**
```
Déclaration d'un tableau de 4 notes
Notes rentrées : 15, 18, 12, 19
La 2ème note est : 18
Modification de la 3ème note : 12 → 14
Toutes les notes après modification :
Note 1 = 15
Note 2 = 18
Note 3 = 14
Note 4 = 19
Somme des notes : 66
Moyenne des notes : 16.5
```

---

## 1.4 Opérations Courantes sur les Tableaux

### Accès à un élément
```
valeur ← tableau[indice]
```

### Modification d'un élément
```
tableau[indice] ← nouvelle_valeur
```

### Parcours du tableau
```
Pour i ← 1 à n Faire
    Traiter(tableau[i])
FinPour
```

### Recherche d'un élément
```
ALGORITHME RechercherElement

VAR
    tableau : Tableau[1..5] d'Entier
    cherche : Entier
    i : Entier
    trouve : Booleen

DEBUT
    { Remplir le tableau }
    tableau[1] ← 5
    tableau[2] ← 12
    tableau[3] ← 8
    tableau[4] ← 15
    tableau[5] ← 3
    
    { On cherche le nombre 12 }
    cherche ← 12
    trouve ← Faux
    
    { Parcourir et chercher }
    Pour i ← 1 à 5 Faire
        Si tableau[i] = cherche Alors
            trouve ← Vrai
            Afficher("Élément trouvé à la position ", i)
        FinSi
    FinPour
    
    Si Non trouve Alors
        Afficher("Élément non trouvé")
    FinSi

FIN
```

---

# <a name="dictionnaires"></a>
# 🗝️ PARTIE 2 : LES DICTIONNAIRES / TABLEAUX ASSOCIATIFS

## 2.1 Concept Théorique

**Qu'est-ce qu'un dictionnaire?**
- Un **dictionnaire** est une collection de **paires clé-valeur**.
- Contrairement aux tableaux, on accède aux éléments par une **clé** (texte/identifiant) et pas par un indice numérique.
- Chaque **clé est unique** dans un dictionnaire.

**Différence tableau vs dictionnaire:**

| Tableau | Dictionnaire |
|---------|--------------|
| Indice numérique (1, 2, 3...) | Clé texte ou identifiant |
| `tableau[1]` = valeur | `dico["nom"]` = "Alice" |
| Ordre préservé | Pas d'ordre garanti |

**Avantages:**
- Clés explicites et lisibles
- Accès par sens plutôt que par position
- Flexible pour stocker des données hétérogènes

---

## 2.2 Syntaxe Générale

```
ALGORITHME Dictionnaire

VAR
    { Déclaration d'un dictionnaire }
    personne : Dictionnaire(Texte, Texte)
    age_dico : Dictionnaire(Texte, Entier)

DEBUT
    
    { === AJOUT D'ÉLÉMENTS ===
       Syntaxe : dico[clé] ← valeur }
    personne["nom"] ← "Alice"
    personne["prenom"] ← "Bob"
    personne["ville"] ← "Paris"
    
    { === ACCÈS À UN ÉLÉMENT ===
       Syntaxe : valeur ← dico[clé] }
    Afficher(personne["nom"])  { Affiche "Alice" }
    
    { === MODIFICATION D'UN ÉLÉMENT ===
       Syntaxe : dico[clé] ← nouvelle_valeur }
    personne["ville"] ← "Lyon"
    
    { === VÉRIFIER SI UNE CLÉ EXISTE ===
       Syntaxe : Si clé ∈ dico Alors ... }
    Si "age" ∈ personne Alors
        Afficher("La clé age existe")
    Sinon
        Afficher("La clé age n'existe pas")
    FinSi

FIN
```

---

## 2.3 Exemple Concret - Profil d'Étudiant

```
ALGORITHME ProfilEtudiant

VAR
    { Déclaration d'un dictionnaire pour stocker les infos }
    etudiant : Dictionnaire(Texte, Texte)
    notes_etudiant : Dictionnaire(Texte, Entier)
    cle : Texte

DEBUT
    
    { === ÉTAPE 1 : CRÉATION ET REMPLISSAGE ===
       Construire le profil d'un étudiant }
    Afficher("=== PROFIL D'ÉTUDIANT ===")
    
    etudiant["nom"] ← "Dupont"
    etudiant["prenom"] ← "Marie"
    etudiant["classe"] ← "Terminale S"
    etudiant["etablissement"] ← "Lycée Louis-le-Grand"
    
    Afficher("Étudiant créée : ", etudiant["prenom"], " ", etudiant["nom"])
    
    { === ÉTAPE 2 : AFFICHAGE DES INFORMATIONS ===
       Afficher l'ensemble du profil }
    Afficher("Classe : ", etudiant["classe"])
    Afficher("Établissement : ", etudiant["etablissement"])
    
    { === ÉTAPE 3 : MODIFICATION D'UN ÉLÉMENT ===
       On met à jour la classe }
    Afficher("Passage en : Terminale L")
    etudiant["classe"] ← "Terminale L"
    
    { === ÉTAPE 4 : AJOUTER UN NOUVEL ÉLÉMENT ===
       Ajouter une information }
    Afficher("Ajout du numéro de matricule : 2024001")
    etudiant["matricule"] ← "2024001"
    
    { === ÉTAPE 5 : RECHERCHE D'UN ÉLÉMENT ===
       Vérifier si une clé existe }
    Si "email" ∈ etudiant Alors
        Afficher("Email : ", etudiant["email"])
    Sinon
        Afficher("Email non renseigné")
    FinSi
    
    { === ÉTAPE 6 : DICTIONNAIRE DE NOTES ===
       Créer un second dictionnaire avec les notes }
    Afficher("")
    Afficher("=== RÉSULTATS D'EXAMENS ===")
    
    notes_etudiant["mathematiques"] ← 18
    notes_etudiant["francais"] ← 16
    notes_etudiant["anglais"] ← 17
    notes_etudiant["histoire"] ← 14
    
    { === ÉTAPE 7 : PARCOURS DU DICTIONNAIRE ===
       Afficher matière par matière }
    Afficher("Détail des notes :")
    Afficher("Mathématiques : ", notes_etudiant["mathematiques"])
    Afficher("Français : ", notes_etudiant["francais"])
    Afficher("Anglais : ", notes_etudiant["anglais"])
    Afficher("Histoire : ", notes_etudiant["histoire"])
    
    { === ÉTAPE 8 : CALCUL À PARTIR DES VALEURS ===
       Moyenne des notes }
    VAR somme_notes : Entier
    somme_notes ← notes_etudiant["mathematiques"] + 
                  notes_etudiant["francais"] + 
                  notes_etudiant["anglais"] + 
                  notes_etudiant["histoire"]
    
    Afficher("Somme des notes : ", somme_notes)
    Afficher("Moyenne : ", somme_notes / 4)

FIN
```

**Résultat attendu:**
```
=== PROFIL D'ÉTUDIANT ===
Étudiant créée : Marie Dupont
Classe : Terminale L
Établissement : Lycée Louis-le-Grand
Ajout du numéro de matricule : 2024001
Email non renseigné

=== RÉSULTATS D'EXAMENS ===
Détail des notes :
Mathématiques : 18
Français : 16
Anglais : 17
Histoire : 14
Somme des notes : 65
Moyenne : 16.25
```

---

## 2.4 Opérations Courantes sur les Dictionnaires

### Ajouter une clé-valeur
```
dico[clé] ← valeur
```

### Accéder à une valeur
```
valeur ← dico[clé]
```

### Vérifier l'existence d'une clé
```
Si clé ∈ dico Alors
    { la clé existe }
FinSi
```

### Supprimer une clé-valeur
```
Supprimer dico[clé]
```

### Parcours des clés
```
Pour chaque clé dans dico Faire
    valeur ← dico[clé]
    Traiter(clé, valeur)
FinPour
```

---

# <a name="structures"></a>
# 🏗️ PARTIE 3 : LES STRUCTURES / OBJETS

## 3.1 Concept Théorique

**Qu'est-ce qu'une structure?**
- Une **structure** (ou **enregistrement**, **record**) regroupe **plusieurs données de types différents** sous un même nom.
- Elle permet de créer un **type de donnée personnalisé** combinant plusieurs champs.
- Chaque champ a un **nom** et un **type**.

**Exemple:**
- Un étudiant ne se résume pas à un nombre ou du texte.
- Il faut regrouper : nom (texte), age (entier), moyenne (réel), classe (texte).
- La structure permet cela!

**Avantages:**
- Organise les données liées ensemble
- Rend le code plus lisible et maintenable
- Permet de passer plusieurs données comme un seul paramètre

---

## 3.2 Syntaxe Générale

```
ALGORITHME Structure

{ === DÉFINITION D'UNE STRUCTURE ===
   On crée un nouveau type }
STRUCTURE Etudiant
    nom : Texte
    age : Entier
    moyenne : Reel
    classe : Texte
FIN STRUCTURE

VAR
    { === DÉCLARATION D'UNE VARIABLE DE TYPE STRUCTURE ===
       Créer une instance de la structure }
    eleve : Etudiant

DEBUT
    
    { === AFFECTATION DES CHAMPS ===
       Syntaxe : variable.champ ← valeur }
    eleve.nom ← "Alice"
    eleve.age ← 18
    eleve.moyenne ← 16.5
    eleve.classe ← "Terminale S"
    
    { === ACCÈS AUX CHAMPS ===
       Syntaxe : valeur ← variable.champ }
    Afficher(eleve.nom)     { Affiche "Alice" }
    Afficher(eleve.moyenne) { Affiche 16.5 }
    
    { === MODIFICATION D'UN CHAMP ===
       Syntaxe : variable.champ ← nouvelle_valeur }
    eleve.moyenne ← 17.0
    
    { === AFFICHAGE COMPLET ===
       Afficher tous les champs }
    Afficher(eleve.nom, " a une moyenne de ", eleve.moyenne)

FIN
```

---

## 3.3 Exemple Concret - Système de Gestion d'Étudiants

```
ALGORITHME SystemeGestionEtudiants

{ === DÉFINITION DE LA STRUCTURE ÉTUDIANT ===
   Regroupe toutes les informations d'un étudiant }
STRUCTURE Etudiant
    id : Entier           { Identifiant unique }
    nom : Texte           { Nom de famille }
    prenom : Texte        { Prénom }
    age : Entier          { Âge en années }
    classe : Texte        { Classe (ex: "Terminale S") }
    moyenne : Reel        { Moyenne générale }
    ville : Texte         { Ville de résidence }
FIN STRUCTURE

VAR
    { === DÉCLARATION DE DEUX ÉTUDIANTS ===
       Créer deux instances de la structure }
    etudiant1 : Etudiant
    etudiant2 : Etudiant

DEBUT
    
    { === CRÉATION DU PREMIER ÉTUDIANT ===
       Remplir tous les champs de etudiant1 }
    Afficher("=== CRÉATION D'ÉTUDIANT 1 ===")
    etudiant1.id ← 1
    etudiant1.nom ← "Dupont"
    etudiant1.prenom ← "Marie"
    etudiant1.age ← 18
    etudiant1.classe ← "Terminale S"
    etudiant1.moyenne ← 16.5
    etudiant1.ville ← "Paris"
    
    { === CRÉATION DU DEUXIÈME ÉTUDIANT ===
       Remplir tous les champs de etudiant2 }
    Afficher("=== CRÉATION D'ÉTUDIANT 2 ===")
    etudiant2.id ← 2
    etudiant2.nom ← "Martin"
    etudiant2.prenom ← "Jean"
    etudiant2.age ← 17
    etudiant2.classe ← "Terminale L"
    etudiant2.moyenne ← 14.2
    etudiant2.ville ← "Lyon"
    
    { === AFFICHAGE DES INFORMATIONS ===
       Accéder et afficher les champs }
    Afficher("")
    Afficher("=== PROFIL DE L'ÉTUDIANT 1 ===")
    Afficher("ID : ", etudiant1.id)
    Afficher("Nom : ", etudiant1.prenom, " ", etudiant1.nom)
    Afficher("Âge : ", etudiant1.age, " ans")
    Afficher("Classe : ", etudiant1.classe)
    Afficher("Moyenne : ", etudiant1.moyenne)
    Afficher("Ville : ", etudiant1.ville)
    
    Afficher("")
    Afficher("=== PROFIL DE L'ÉTUDIANT 2 ===")
    Afficher("ID : ", etudiant2.id)
    Afficher("Nom : ", etudiant2.prenom, " ", etudiant2.nom)
    Afficher("Âge : ", etudiant2.age, " ans")
    Afficher("Classe : ", etudiant2.classe)
    Afficher("Moyenne : ", etudiant2.moyenne)
    Afficher("Ville : ", etudiant2.ville)
    
    { === COMPARAISON ET TRAITEMENT ===
       Comparer les moyennes }
    Afficher("")
    Afficher("=== COMPARAISON ===")
    Si etudiant1.moyenne > etudiant2.moyenne Alors
        Afficher(etudiant1.prenom, " a une meilleure moyenne")
    Sinon
        Afficher(etudiant2.prenom, " a une meilleure moyenne")
    FinSi
    
    { === MODIFICATION D'UN CHAMP ===
       Mettre à jour la moyenne d'étudiant1 }
    Afficher("")
    Afficher("=== MISE À JOUR ===")
    Afficher("Modification de la moyenne de ", etudiant1.prenom)
    etudiant1.moyenne ← 17.5
    Afficher("Nouvelle moyenne : ", etudiant1.moyenne)
    
    { === CALCUL AVEC LES CHAMPS ===
       Moyenne générale des deux étudiants }
    Afficher("")
    Afficher("=== STATISTIQUES ===")
    VAR moyenne_globale : Reel
    moyenne_globale ← (etudiant1.moyenne + etudiant2.moyenne) / 2
    Afficher("Moyenne globale du groupe : ", moyenne_globale)

FIN
```

**Résultat attendu:**
```
=== CRÉATION D'ÉTUDIANT 1 ===
=== CRÉATION D'ÉTUDIANT 2 ===

=== PROFIL DE L'ÉTUDIANT 1 ===
ID : 1
Nom : Marie Dupont
Âge : 18 ans
Classe : Terminale S
Moyenne : 16.5
Ville : Paris

=== PROFIL DE L'ÉTUDIANT 2 ===
ID : 2
Nom : Jean Martin
Âge : 17 ans
Classe : Terminale L
Moyenne : 14.2
Ville : Lyon

=== COMPARAISON ===
Marie a une meilleure moyenne

=== MISE À JOUR ===
Modification de la moyenne de Marie
Nouvelle moyenne : 17.5

=== STATISTIQUES ===
Moyenne globale du groupe : 15.85
```

---

## 3.4 Opérations Courantes sur les Structures

### Accès à un champ
```
valeur ← variable.champ
```

### Modification d'un champ
```
variable.champ ← nouvelle_valeur
```

### Comparaison de champs
```
Si variable1.champ = variable2.champ Alors
    { les champs sont égaux }
FinSi
```

### Tableau de structures
```
VAR
    etudiants : Tableau[1..100] d'Etudiant
    i : Entier

DEBUT
    { Remplir le tableau }
    etudiants[1].nom ← "Dupont"
    etudiants[1].age ← 18
    
    { Parcourir le tableau }
    Pour i ← 1 à 100 Faire
        Afficher(etudiants[i].nom)
    FinPour
FIN
```

---

# <a name="exercices"></a>
# 💪 PARTIE 4 : EXERCICES PRATIQUES

## ⚠️ CONSIGNES IMPORTANTES

**Pour chaque exercice:**
1. **Lisez l'énoncé** attentivement
2. **Planifiez** votre algorithme avant de l'écrire
3. **Écrivez le pseudo-code** avec indentation
4. **Testez** votre algorithme mentalement ou sur papier
5. **Demandez l'aide** si vous bloquez (je donnerai les indices)

**Les solutions sont à la fin du fichier** - ne les regardez PAS avant d'essayer! 🚫

---

## EXERCICE 1 : Niveau DÉBUTANT ⭐

### Énoncé

Vous devez créer un **programme de gestion de liste de courses**.

**Objectif:**
1. Créer un tableau contenant **5 articles** (texte)
2. Afficher tous les articles
3. Modifier le **3e article**
4. Afficher la **liste mise à jour**

**Exemple attendu:**
```
=== LISTE DE COURSES INITIALE ===
Article 1 : Pain
Article 2 : Lait
Article 3 : Œufs
Article 4 : Fromage
Article 5 : Tomates

=== MODIFICATION ===
Changement : Œufs → Poulet

=== LISTE DE COURSES MISE À JOUR ===
Article 1 : Pain
Article 2 : Lait
Article 3 : Poulet
Article 4 : Fromage
Article 5 : Tomates
```

**À vous de jouer!** 👇

---

## EXERCICE 2 : Niveau INTERMÉDIAIRE ⭐⭐

### Énoncé

Vous devez créer un **annuaire téléphonique avec un dictionnaire**.

**Objectif:**
1. Créer un dictionnaire contenant **au moins 4 contacts** (clé = nom, valeur = numéro de téléphone)
2. Afficher **tous les contacts**
3. **Rechercher** un contact spécifique par son nom
4. **Ajouter un nouveau contact**
5. Afficher si un contact existe ou non

**Exemple attendu:**
```
=== ANNUAIRE INITIAL ===
Alice : 06 12 34 56 78
Bob : 06 98 76 54 32
Charlie : 07 11 22 33 44
Diana : 06 45 67 89 01

=== RECHERCHE ===
Cherche "Bob" : 06 98 76 54 32

=== AJOUT ===
Ajout d'Ève : 07 55 66 77 88

=== VÉRIFICATION ===
Contact "Frank" existe-t-il ? Non
Contact "Ève" existe-t-il ? Oui
```

**À vous de jouer!** 👇

---

## EXERCICE 3 : Niveau AVANCÉ ⭐⭐⭐

### Énoncé

Vous devez créer un **système de gestion de bibliothèque** combinant structures, tableaux et dictionnaires.

**Objectif:**
1. **Définir une structure `Livre`** avec : titre (texte), auteur (texte), année (entier), note (réel de 0 à 10)
2. Créer un **tableau de 3 livres**
3. **Afficher tous les livres** avec leurs informations
4. Créer un **dictionnaire** pour stocker les critiques : clé = titre, valeur = critique (texte)
5. **Afficher les critiques** des livres
6. **Calculer la note moyenne** de tous les livres
7. **Trouver le meilleur livre** (plus haute note)

**Exemple attendu:**
```
=== CATALOGUE DE LIVRES ===
Livre 1 : "Les Misérables" (Victor Hugo, 1862) - Note : 9.5/10
Livre 2 : "1984" (George Orwell, 1949) - Note : 9.0/10
Livre 3 : "Le Seigneur des Anneaux" (J.R.R. Tolkien, 1954) - Note : 9.8/10

=== CRITIQUES ===
"Les Misérables" : Un chef-d'œuvre de la littérature française
"1984" : Un roman de science-fiction dystopique remarquable
"Le Seigneur des Anneaux" : L'épopée fantastique par excellence

=== STATISTIQUES ===
Note moyenne : 9.43/10
Meilleur livre : "Le Seigneur des Anneaux" avec 9.8/10
```

**À vous de jouer!** 👇

---

## 📝 CONSEILS POUR RÉSOUDRE LES EXERCICES

1. **Tableaux**: Utilisez des boucles `Pour` pour parcourir
2. **Dictionnaires**: Accédez par clé, utilisez `∈` pour vérifier l'existence
3. **Structures**: Accédez aux champs avec la notation `variable.champ`
4. **Combinaison**: Mélangez les trois pour l'exercice 3

---

## 🎯 RÉSUMÉ DES TYPES COMPOSÉS

| Type | Accès | Usage |
|------|-------|-------|
| **Tableau** | Par indice (1, 2, 3...) | Collection de même type, ordre important |
| **Dictionnaire** | Par clé (texte) | Paires clé-valeur, accès rapide |
| **Structure** | Par champ (variable.champ) | Regrouper données hétérogènes |

---

## 🚀 PROCHAIN ÉTAPE

Une fois les 3 exercices résolus, vous pouvez:
1. Créer un **projet complet** combinant tous les types
2. Ajouter des **fonctions** pour modulariser le code
3. Gérer les **erreurs** (ex: clé inexistante dans dictionnaire)

**Bonne chance! 💪**


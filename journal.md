# Le language de programation Rust

### Questions sur Rust

- Quel est son secret pour être économe en mémoire s'il n'a pas de Garbage Collector?
- 


# Avant-propos

- Le point fort de Rust est sa puissance qui s'étends dans divers domaines.
**Q: Comment fait Rust pour garantir cette puissance?**
- Rust remédie aux contraintes et éventuelles erreurs du domaines bas niveau. Ceci à travers d'outils qui permettent d'éviter les risques, erreurs et de ne pas avoir à se casser la tête.
**Q: En quoi consiste les contraintes de la programmation système bas niveau?** 
- En plus du domaine bas niveau, Rust peut être facilement appliqué dans les serveurs web, résaux...
**Q:**


# Introduction

- Rust est un language de programmation qui mélange l'ergonomie du haut niveau et la puissance du bas niveau.
- Rust est destiné à plein de profils de développeurs ou chercheurs et qui leurs offre la productivité, fiabilité, sécurité et facilité pédagogique.
**Q:**


# 1. Prise en main

### 1.1. Installation

- En suivant la [documentation](https://www.rust-lang.org/fr/learn/get-started), on procéde à l'installation de Rust et ses dépendances.
- Avec l'installation de Rust, on aura aussi l'outil Cargo d'installé.
- Cargo est un outil de build et gestion de paquets. Il permet donc de construire, exécuter et tester les projets Rust avce toute facilité.
**Q: A quoi sert l'outil Cargo?**

### 1.2. Premier programme

###### Initialisation

- Avant de créer notre premier programme, on doit tout d'abord créer un dossier de projet pour le contenir et y accéder.
`
$ mkdir hello_world
$ cd hello_world
`
- Une fois, dans notre projet, on crée un fichier avec l'extention *rs* par exemple *main.rs*.

###### Exécution du programme

# Le language de programation Rust

### Questions sur Rust

- Quel est son secret pour être économe en mémoire s'il n'a pas de Garbage Collector?
- Sur quels critères Rust est plus performant que les autres?


# Avant-propos

- Le point fort de Rust est sa puissance qui s'étends dans divers domaines.  
**Q: Comment fait Rust pour garantir cette puissance?**
- Rust remédie aux contraintes et éventuelles erreurs du domaines bas niveau. Ceci à travers d'outils qui permettent d'éviter les risques, erreurs et de ne pas avoir à se casser la tête.  
**Q: En quoi consiste les contraintes de la programmation système bas niveau?** 
- En plus du domaine bas niveau, Rust peut être facilement appliqué dans les serveurs web, résaux...  
**Q: Quels sont les différents domaines applicables pour Rust?**


# Introduction

- Rust est un language de programmation qui mélange l'ergonomie du haut niveau et la puissance du bas niveau.  
**Q: En quoi consiste l'ergonomie et la puissance de Rust?**  
- Il est destiné à plein de profils de développeurs ou chercheurs et qui leurs offre la productivité, fiabilité, sécurité et facilité pédagogique.   
**Q: Qu'offre Rust comme bénéfices pour améliorer la qualité de travail des équipes de développeurs?**


# 1. Prise en main

### 1.1. Installation

- En suivant la [documentation](https://www.rust-lang.org/fr/learn/get-started), on procéde à l'installation de Rust et ses dépendances.
- Avec l'installation de Rust, on aura aussi l'outil Cargo d'installé.
- Cargo est un outil de build et gestion de paquets. Il permet donc de construire, exécuter et tester les projets Rust avce toute facilité.  
**Q: A quoi sert l'outil Cargo?**

### 1.2. Premier programme

###### Initialisation

- Avant de créer notre premier programme, on doit tout d'abord créer un dossier de projet pour le contenir et y accéder.  
```
$ mkdir hello_world
$ cd hello_world
```
- Une fois, dans notre projet, on crée un fichier avec l'extention *'.rs'* par exemple *'main.rs'* et on peut l'ouvrrir.  
**Q: Quelle est l'extension d'un fichier Rust?**

###### Exécution du programme

- On peut maintenant écrire du code Rust, pour par exemple : un programme qui affiche `"Hello, world!"`.  
```
fn main() {  
    println!("Hello, world!");  
}
```
- Avant d'éxécuter le programme, il faut d'abord le compiler en utilisant l'outil *'rustsc'* qui est le compilateur du language Rust. Puis, on peut lancer l'éxécutable generé.  
```
$ rustc main.rs
$ ./main
$ Hello, world!
```
**Q: Quel est le compilateur du language Rust?**

###### Structure d'un programme Rust

- Comme tout language de programmation, Rust a sa propre syntaxe et ses annotations, pour bien les comprendre on peut décomposer le code écrit précédemment.  
```
fn main() { }
```
- Ces lignes définissent la fonction *'main'*, qui est la fonction principale qui s'éxécute lors du lancement du programme.  
**Q: Qu'exécute le programme Rust quand on le lance?**
- A l'interieur de cette fonction on trouve l'instruction à exécuter.  
```
println!("Hello, world!");
```
- On peut remarquer un appel de la fonction `println!()` qui est un Macro Rust (fonction propre à Rust) et qui permet donc d'afficher le contenu qui est en argument.
- On peut aussi noter l'ajout de `!` qui signifie que la fonction est propre à Rust. Si on écrivait `println()` sans le `!`, cela signifie qu'on apelle un fonction et non une macro.  
**Q: Comment reconnait-on une Macro Rust?**

### 1.3. Premier projet avec Cargo

- Cargo est le système de compilation et de gestion de paquet et dépendances Rust. Il prends en charge plusieurs tâches comme la création, compilation, exécution de projets Rust.
**Q: Pourquoi Cargo est nécessaire pour les projets Rust complexes?**

###### Création d'un projet Cargo

- Cargo contient une commande qui permet de génerer directement un projet, qu'on va nommer *hello_cargo*, et en suite on va y accéder.  
```
$ cargo new hello_cargo 
$ cd hello_cargo
```
- Dans le projet géneré on trouve un dossiser */src* avec le fichier *main.rs* et un fichier de configuration *Cargo.toml* qui contient des informations sur le projet et ses dépendences. 
```
[package]
name = "hello_cargo"
version = "0.1.0"
edition = "2021"

[dependencies]
```   
**Q: A quoi sert me fichier Cargo.toml?**

###### Exécution d'un projet Cargo

- Comme dans l'exécution sans Cargo, on doit d'abord compiler notre programme Rust pour génerer un éxecutable.  
```
$ cargo build
```
- La première fois qu'on build, le programme va se lancer automatiquement et afficher le résultat qui est `"Hello, world!`. Comme on peut aussi le lancer avec la commande :  
```
$ cargo run
```
- On peut aussi vérifier l'éxecution du code rapidement sans passer par l'étape de compilation avec la commande :  
```
$ cargo check
```
**Q: Dans quel cas utilisent-on cargo check?**

###### Diffuser un projet Cargo

- Lorsqu'on est prêts à diffuser le projet ayant passé les étapes de test et de déboggage, on peut utiliser la commande:  
```
$ cargo build --release
```
- Cette commande crée un exécutable final optimisé et plus rapide pour l'utilisation. Cependant, il nécessite plus de temps de compilation à être prêt.  
**Q: Quelle est la différence entre la compilation sur target/release et target/debug**

###### Cargo comme convention

- Pour des projets simples, on ne peux pas distinguer la vraie utilité de Cargo. C'est quand on travail sur des projets à grande échelle plus complexes qu'on remarque la force de Cargo à gérer les dépendances et coordoner la compilation.  
**Q: Pourquoi Cargo n'est pas si nécessaire pour des programmes simples?**



# 2. Programmer un jeu en Rust

- Pour mieux comprendre le fonctionnement et la syntaxe du language Rust tels que `let`, `match` et les crates, on va coder un petit jeu dit *Le jeu du plus ou du moins*. Le principe est que : le programme choisi un nombre entre 1-100, l'utilisateur devera donc le deviner par saisie, le programme félicite le joueur en cas de bonne réponse sinon il lui indiquera si le nombre est plus grand ou plus petit que celui qui a été saisi.  
**Q: Qu'est ce que les crates en Rust?**  

### Mise en place

- Pour ce programme, on utilise Cargo pour créer le projet *jeu_du_plus_ou_du_moins* et ensuite y accéder.
```
$ cargo new jeu_du_plus_ou_du_moins
$ cd jeu_du_plus_ou_du_moins
```  
- La commande `cargo new` crée un programme de base */src/main.rs* qui a comme fonction d'afficher `Hello,  world!`. On aura donc besoin de modifier le code selon notre cahier de charges.  
**Q: Quels fichiers sont crées lors de l'utilisation de la commande cargo new?**

### Traitement de saisi

- Pour pouvoir donner accès à l'utillisateur pour saisir sa réponse, on droit d'abord importer la bibliothèque `io` qui provient de la bibliothèque standard `std` comme suit:  
```
use std::io
```
**Q: Quel bibliothèque Rust permet l'utilisation de l'entrée/sortie?**
- Afin d'indiquer à l'utilisateur que c'est à lui de taper, on utilise la Macro Rust `println!()` vu précedemment pour lui afficher un message.  
```
println!("Devinez le nombre !");
println!("Veuillez entrer un nombre.");
```  
**Q: Pourquoi met-on ! devant la fonction println!()?**

### Enregistrer les données

- Pour créer d'abord une variable, on utilise `let` suivi du nom de la variable. Par défaut, les variables déclarés dans Rust sont immuables, pour les rendre modifiables on doit ajouter `mut` devant le nom de la variable.  
**Q: Comment fait-on pour déclarer une variable qui peut changer de valeur?**
- Pour notre exemple, on déclare donc une variable mutable qu'on nommera `supposition`, comme suit :  
```
let mut supposition = String::new();
```
**Q: Quel est la valeur de retour de l'instruction String::new()?**
- On note l'utilisation de la fonction `new()` qui fait partie du type chaine de charactères `String` fourni par la bibliothèque standarde. Ceci en utilisant l'opérateur `::`. Cette opération affecte une instance `String` à la variable `supposition`.  
**Q: Que permet de faire l'opérateur ::?**

### Receuillir la saisie utilisateur

- Pour pouvoir récuperer l'entrée de l'untilisateur, on aura besoin d'appeler la fonction `stdin` de la bibliothèque `io` qu'on a importé.  
```
io::stdin().read_line(&mut supposition);
```
**Q: Quelle fonction permet la récuperation de données en entrée?**
- On appelle la méthode `read_line()` de l'entrée standard, avec comme argument `&mut supposition` pour lui indiquer où stocker la saisie. On note que qu'on passe cette argument comme mutable afin que la méthode puisse modifier sa valeur.  
**Q: De quelle type doivent être les variables passées comme argument de la fonction read_line()?**
- On note l'utilisation de `&` qui indique une réference, permettant d'accéder à la donnée sans avoir à la recopier en mémoire. Comme les variables, les réferences sont par défaut immuables, c'est pour cela qu'on doit mettre `&mut`.  
**Q: Quel est le but d'utiliser des réferences?**

### Gérer les erreurs avec le type Result

- On ajoute une nouvelle partie de code à celui de la lecture de la saisie :
```
.expect("Échec de la lecture de l'entrée utilisateur");
```  
**Q: Quel est le but de l'ajout de la fonction .expect()?**
- La fonction `read_line()` stocke l'entrée utilisateur dans la variable fournie et retourne une énumération de type `io::Result`. En Rust, les énumérations ont plusieurs variantes prédéfinies et sont souvent utilisées avec `match` pour gérer les différentes variantes lors de l'exécution du code.  
**Q: Quele le type de retour de la fonction read_line()?**
- Les variantes de `Result` sont `Ok` qui indique que l'opération a réussi et contient la valeur résultante, et `Err` qui signifie un échec et contient des informations sur l'échec.  
**Q: Quelles valeurs peut prendre la variante Result?**
- Les valeurs du type `Result` disposent de méthodes associées. Par exemple : la méthode `expect()` sur une instance de `io::Result` fait planter le programme avec un message spécifié si la valeur est `Err`. Si la valeur est `Ok`, `expect` retourne le contenu de `Ok`, qui est le résultat de l'opération, comme le nombre d'octets de la saisie utilisateur dans le cas de `read_line()`. 
**Q: Qu'est ce qui se passe en cas de valeur Err dans l'instance Result?**

### Affichage des valeurs

- Pour afficher afficher ce que l'utilisateur a saisi on utilise des espaces réservés `{}` suivi de la variable qu'on souhaite afficher. Chaque paire d'accolades affiche une valeur différente, et plusieurs valeurs peuvent être affichées avec une seule instruction `println!()`.  
```
println!("Votre nombre : {}", supposition);
```

### Test de la première partie

- Pour tester le code qu'on a écrit, on peut le lancer avec la commande `cargo run` :
```
$ cargo run
   Compiling jeu_du_plus_ou_du_moins v0.1.0 (file:///projects/jeu_du_plus_ou_du_moins)
    Finished dev [unoptimized + debuginfo] target(s) in 6.44s
     Running `target/debug/jeu_du_plus_ou_du_moins`
Devinez le nombre !
Veuillez entrer un nombre.
6
Votre nombre : 6
```

### Générer un nombre aléatoire

-
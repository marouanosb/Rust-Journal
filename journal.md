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
**Q: Quelle commande permet de créer un dossier à travers un terminal?**  
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
**Q: Quel est le compilateur du language Rust?**  
```
$ rustc main.rs
$ ./main
$ Hello, world!
```

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
**Q: Quelle commande permet de créer un projet Rust?**  
```
$ cargo new hello_cargo 
$ cd hello_cargo
```
- Dans le projet géneré on trouve un dossiser */src* avec le fichier *main.rs* et un fichier de configuration *Cargo.toml* qui contient des informations sur le projet et ses dépendences.  
**Q: A quoi sert me fichier Cargo.toml?**   
```
[package]
name = "hello_cargo"
version = "0.1.0"
edition = "2021"

[dependencies]
```   

###### Exécution d'un projet Cargo

- Comme dans l'exécution sans Cargo, on doit d'abord compiler notre programme Rust pour génerer un éxecutable.  
**Q: Quel commande compile le projet Rust?**  
```
$ cargo build
```
- La première fois qu'on build, le programme va se lancer automatiquement et afficher le résultat qui est `"Hello, world!`. Comme on peut aussi le lancer avec la commande :  
```
$ cargo run
```
- On peut aussi vérifier l'éxecution du code rapidement sans passer par l'étape de compilation avec la commande :  
**Q: Dans quel cas utilisent-on cargo check?**  
```
$ cargo check
```

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
**Q: Quelle commande permet de créer un nouveau projet Rust?**  
```
$ cargo new jeu_du_plus_ou_du_moins
$ cd jeu_du_plus_ou_du_moins
```  
- La commande `cargo new` crée un programme de base */src/main.rs* qui a comme fonction d'afficher `Hello,  world!`. On aura donc besoin de modifier le code selon notre cahier de charges.  
**Q: Quels fichiers sont crées lors de l'utilisation de la commande cargo new?**

### Traitement de saisi

- Pour pouvoir donner accès à l'utillisateur pour saisir sa réponse, on droit d'abord importer la bibliothèque `io` qui provient de la bibliothèque standard `std` comme suit:  
**Q: Quel bibliothèque Rust permet l'utilisation de l'entrée/sortie?**  
```
use std::io
```
- Afin d'indiquer à l'utilisateur que c'est à lui de taper, on utilise la Macro Rust `println!()` vu précedemment pour lui afficher un message.  
**Q: Pourquoi met-on ! devant la fonction println!()?**  
```
println!("Devinez le nombre !");
println!("Veuillez entrer un nombre.");
```  

### Enregistrer les données

- Pour créer d'abord une variable, on utilise `let` suivi du nom de la variable. Par défaut, les variables déclarés dans Rust sont immuables, pour les rendre modifiables on doit ajouter `mut` devant le nom de la variable.  
**Q: Comment fait-on pour déclarer une variable qui peut changer de valeur?**
- Pour notre exemple, on déclare donc une variable mutable qu'on nommera `supposition`, comme suit :  
**Q: Quel est la valeur de retour de l'instruction String::new()?**  
```
let mut supposition = String::new();
```
- On note l'utilisation de la fonction `new()` qui fait partie du type chaine de charactères `String` fourni par la bibliothèque standarde. Ceci en utilisant l'opérateur `::`. Cette opération affecte une instance `String` à la variable `supposition`.  
**Q: Que permet de faire l'opérateur ::?**

### Receuillir la saisie utilisateur

- Pour pouvoir récuperer l'entrée de l'untilisateur, on aura besoin d'appeler la fonction `stdin` de la bibliothèque `io` qu'on a importé.  
**Q: Quelle fonction permet la récuperation de données en entrée?**  
```
io::stdin().read_line(&mut supposition);
```
- On appelle la méthode `read_line()` de l'entrée standard, avec comme argument `&mut supposition` pour lui indiquer où stocker la saisie. On note que qu'on passe cette argument comme mutable afin que la méthode puisse modifier sa valeur.  
**Q: De quelle type doivent être les variables passées comme argument de la fonction read_line()?**
- On note l'utilisation de `&` qui indique une réference, permettant d'accéder à la donnée sans avoir à la recopier en mémoire. Comme les variables, les réferences sont par défaut immuables, c'est pour cela qu'on doit mettre `&mut`.  
**Q: Quel est le but d'utiliser des réferences?**

### Gérer les erreurs avec le type Result

- On ajoute une nouvelle partie de code à celui de la lecture de la saisie.  
**Q: Quel est le but de l'ajout de la fonction .expect()?**
```
.expect("Échec de la lecture de l'entrée utilisateur");
```  
- La fonction `read_line()` stocke l'entrée utilisateur dans la variable fournie et retourne une énumération de type `io::Result`. En Rust, les énumérations ont plusieurs variantes prédéfinies et sont souvent utilisées avec `match` pour gérer les différentes variantes lors de l'exécution du code.  
**Q: Quele le type de retour de la fonction read_line()?**
- Les variantes de `Result` sont `Ok` qui indique que l'opération a réussi et contient la valeur résultante, et `Err` qui signifie un échec et contient des informations sur l'échec.  
**Q: Quelles valeurs peut prendre la variante Result?**
- Les valeurs du type `Result` disposent de méthodes associées. Par exemple : la méthode `expect()` sur une instance de `io::Result` fait planter le programme avec un message spécifié si la valeur est `Err`. Si la valeur est `Ok`, `expect` retourne le contenu de `Ok`, qui est le résultat de l'opération, comme le nombre d'octets de la saisie utilisateur dans le cas de `read_line()`. 
**Q: Qu'est ce qui se passe en cas de valeur Err dans l'instance Result?**

### Affichage des valeurs

- Pour afficher afficher ce que l'utilisateur a saisi on utilise des espaces réservés `{}` suivi de la variable qu'on souhaite afficher. Chaque paire d'accolades affiche une valeur différente, et plusieurs valeurs peuvent être affichées avec une seule instruction `println!()`.  
**Q: Quelle syntaxe permet d'afficher le contenu des variables?**  
```
println!("Votre nombre : {}", supposition);
```

### Test de la première partie

- Pour tester le code qu'on a écrit, on peut le lancer avec la commande `cargo run`.  
**Q: Quel commande permet d'éxecuter notre projet?**  
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

- Pour permettre au joueur de deviner un nombre secret différent à chaque partie, nous devons générer un nombre aléatoire entre 1 et 100. Comme Rust ne possède pas de fonction intégrée pour cela, il faut utiliser la crate `rand` fournie par l'équipe de Rust.  
**Q: Donner un exemple de crates fournies par Rust.**

###### Les crates Rust

- Une crate est un ensemble de fichiers de code source Rust. Notre projet est une crate binaire (un programme exécutable), tandis que la crate `rand` est une crate de bibliothèque, utilisée dans d'autres programmes mais non exécutable seule.  
**Q: Qu'est ce qu'une crate Rust?**
- Cargo excelle dans la gestion des crates externes. Avant d'utiliser `rand`, il faut éditer le fichier *Cargo.toml* pour l’ajouter en tant que dépendance. Ajoutez la ligne sous `[dependencies]` avec le numéro de version exact indiqué, afin que les exemples du tutoriel fonctionnent correctement.  
**Q: Où doit-on indiquer l'utilisation des crates en Rust?**  
```
rand = "0.8.3"
```  
- Dans Cargo.toml, l'en-tête `[dependencies]` liste les crates externes et leurs versions nécessaires. Ici, on ajoute `rand` avec la version sémantique 0.8.3. Cela équivaut à ^0.8.3, ce qui signifie  que toute version ≥ 0.8.3 et < 0.9.0 est compatible.  
**Q: Qu'indique ^ devant la version d'une crate?**
- En compilant le projet, Cargo va automatiquement récuperer toutes les dépendances externes indiquées dans le fichier *Cargo.toml* depuis le registre, qui est une copie de [Crates.io](https://crates.io/) contenant l'ensemble des projets open sources publiés par les développeurs Rust.   
**Q: Comment fait-on pour avoir le code des crates externes utilisées?**  
```
$ cargo build
    Updating crates.io index
  Downloaded rand v0.8.3
  Downloaded libc v0.2.86
  Downloaded getrandom v0.2.2
  Downloaded cfg-if v1.0.0
  Downloaded ppv-lite86 v0.2.10
  Downloaded rand_chacha v0.3.0
  Downloaded rand_core v0.6.2
   Compiling rand_core v0.6.2
   Compiling libc v0.2.86
   Compiling getrandom v0.2.2
   Compiling cfg-if v1.0.0
   Compiling ppv-lite86 v0.2.10
   Compiling rand_chacha v0.3.0
   Compiling rand v0.8.3
   Compiling jeu_du_plus_ou_du_moins v0.1.0 (file:///projects/jeu_du_plus_ou_du_moins)
    Finished dev [unoptimized + debuginfo] target(s) in 2.53s
```
- Après la mise à jour du registre, Cargo lit `[dependencies]`, télécharge les crates listées et celles dont elles dépendent. Ici, en ajoutant seulement `rand`, Cargo télécharge aussi ses dépendances, les compile, puis compile notre projet avec ces crates. Les dépendances n'ayant pas changées, Cargo sait qu'il peut simplement réutiliser ce qu'il a déjà téléchargé et compilé précédemment.  
**Q: Que fait Cargo qu'on il ne trouve pas les versions des crates utilisées dans le registre?**

###### Reproductibilité des compilations avec Cargo.lock

- Cargo garantit la recompilation identique d'un projet en verrouillant les versions des dépendances. Il utilise les mêmes versions jusqu'à ce que vous en décidiez autrement. Par exemple, si  une nouvelle version `rand` sort et provoque une régression, Cargo empêche cela grâce au fichier *Cargo.lock*, créé lors du premier cargo build.  
**Q: Qu'est ce qui assure la compilation inaltérable du projet Rust?**
- Lors de la première compilation, Cargo choisit les versions des dépendances et les enregistre dans *Cargo.lock*. Lors des recompilations, il utilise ces versions pour garantir des compilations reproductibles. Ainsi, le projet reste sur la version 0.8.3 de `rand` jusqu'à une mise à jour explicite.  
**Q: Comment Cargo assure la reproductabilité des compilation?**

###### Mise à jors des Crates

- Pour mettre à jour une crate, utilisez la commande `cargo update`. Elle ignore *Cargo.lock* et cherche les versions correspondant aux critères de *Cargo.toml*, puis met à jour *Cargo.lock*. Par défaut, Cargo ne recherche que les versions entre 0.8.3 et avant 0.9.0. Si `rand` publie les versions 0.8.4 et 0.9.0, `cargo update` affichera ces mises à jour.  
**Q: Que fait-on pour utiliser une nouvelle version des crates?**  
```
$ cargo update
    Updating crates.io index
    Updating rand v0.8.3 -> v0.8.4
```
 
- Cargo facilite la réutilisation des bibliothèques, permettant aux développeurs Rust d'écrire des projets en assemblant divers paquets.  
**Q: Quel bénéfice apporte l'écosystème de Crates de Rust?**

###### Génération d'un nombre aléatoire

- D'abord, nous avons ajouté `use rand::Rng` pour accéder aux méthodes définies par le trait `Rng` du crate `rand`, nécessaire pour utiliser les générateurs de nombres aléatoires.  
**Q: Comment fait-on pour accéder aux fonctions des crates implementées?**  
- Nous utilisons `rand::thread_rng` pour obtenir un générateur de nombres aléatoires propre au fil d'exécution. Ensuite, la méthode `gen_range()`, définie par le trait `Rng`, génère un nombre aléatoire dans l'intervalle spécifié. L'intervalle est de la forme *début..fin*, incluant la borne inférieure et excluant la supérieure, ou utiliser l'intervalle fermé 1..=100. On voudrait ensuite enregistrer le résultat dans une variable *nombre_secret* et qui ne changera pas le long du jeu.  
**Q: pourquoi avoir appelé la fonction gen_range() à travers thread_rng au lieu de le faire directement?**
```
let nombre_secret = rand::thread_rng().gen_range(1..101);
```
- Pour s'assurer que notre code marche et voir le nombre aléatoire choisi, on peut l'afficher en utilisant la Macro `println!()`. Notre nouveau code sera comme suit :  
**Q: Quel utilitée peut avoir la Macro println!() lors du débogage?**
```
use std::io;
use rand::Rng;

fn main() {
    println!("Devinez le nombre !");

    let nombre_secret = rand::thread_rng().gen_range(1..101);

    println!("Le nombre secret est : {}", nombre_secret);

    println!("Veuillez entrer un nombre.");

    let mut supposition = String::new();

    io::stdin()
        .read_line(&mut supposition)
        .expect("Échec de la lecture de l'entrée utilisateur");

        println!("Votre nombre : {}", supposition);
}
```

### Comparaison de nombres

- Nous ajoutons use `std::cmp::Ordering` pour importer le type `Ordering` de la bibliothèque standard. `Ordering` est une énumération avec les variantes `Less`, ``Greater`` et ``Equal``, représentant les résultats possibles d'une comparaison entre deux valeurs.  
**Q: De quel type est Ordering?**
- La méthode ``cmp()`` compare supposition et nombre_secret, retournant une variante de ``Ordering``. Une expression `match` est ensuite utilisée pour déterminer l'action à prendre selon la variante retournée par ``cmp()``.  
**Q: Quel est le type de retour de la fonction cmp()??**
```
match supposition.cmp(&nombre_secret) {
        Ordering::Less => println!("C'est plus !"),
        Ordering::Greater => println!("C'est moins !"),
        Ordering::Equal => println!("Vous avez gagné !"),
```
- Une expression ``match`` comprend des branches avec des motifs et du code associé. Rust compare la valeur donnée au motif de chaque branche. ``match`` et les motifs permettent de gérer divers scénarios de manière exhaustive.  
**Q: A quoi sert l'expression match?**
- Dans notre exemple, si l'utilisateur saisit 50 et que le nombre secret est 38, ``cmp()`` retourne ``Ordering::Greater`` car 50 est plus grand que 38. L'expression ``match`` compare ``Ordering::Greater`` avec les motifs des branches pour trouver son équivalent, dont le code est exécuté pour afficher *"C'est moins !"*. ``match`` se termine après avoir trouvé une correspondance.  
**Q: Que fait match s'il ne trouve pas la branche correspondante?**
- Lors de la compilation de notre nouveau code, on aura un message d'erreur indique un problème de types non compatibles. Rust, avec son système de types fort et statique, infère les types automatiquement, comme avec ``let mut supposition = String::new()`` où Rust déduit que supposition est de type ``String``. Cependant, ``nombre_secret`` est un nombre. L'erreur survient parce que Rust ne peut pas comparer une chaîne de caractères avec un nombre.  
**Q: Que ce passe-t-il quand on compare deux types différents?**
- Au bout du compte, nous voulons convertir le ``String`` que le programme récupère de la saisie utilisateur en un nombre, afin de comparer numériquement au nombre secret. Nous allons faire ceci en ajoutant cette ligne supplémentaire dans le corps de la fonction ``main`` :  
**Q: Que doit-on faire à la saisie pour s'assurer qu'elle est du bon type?**
```
let supposition: u32 = supposition.trim().parse().expect("Veuillez entrer un nombre !");
```
- Nous créons une nouvelle variable ``supposition``, masquant l'ancienne. Rust permet le masquage de variables, ce qui permet de réutiliser le même nom sans créer de variables distinctes. Cette fonctionnalité est souvent utilisée pour convertir des valeurs d'un type à un autre.  
**Q: Que ce pass-t-il lorsqu'on déclare une nouvelle variable avec le nom d'une déja existante?**
- Nous associons la nouvelle variable ``supposition`` à l'expression ``supposition.trim().parse()``. Ici, ``supposition`` fait référence à la chaîne de caractères initiale saisie par l'utilisateur. La méthode ``trim()`` enlève les espaces et caractères de fin de lignepour nettoyer la chaîne avant la conversion en u32.  
**Q: Quel est le rôle de la fonction trim()?**
- La méthode ``parse()`` convertit une chaîne en un nombre, mais nous devons spécifier le type exact avec ``let supposition: u32``. Les deux-points indiquent le type de la variable. Ici, u32 est un entier non signé sur 32 bits. En spécifiant u32 pour supposition, Rust infère également que ``nombre_secret`` doit être un u32, permettant ainsi une comparaison entre deux valeurs du même type.  
**Q: Comment convertir une chaine de caractères en numbre?**
- La méthode ``parse()`` peut échouer si la chaîne ne peut pas être convertie en nombre, retournant un type ``Result`` de valeur ``Err``, ``expect`` fait planter le programme avec un message d'erreur. Sinon, elle retourne la valeur ``Ok``.  
**Q: Pourquoi la fonction parse() peut-elle échouer?**
- On peut maintenant tester notre programme et voir le résultats de son éxecution. Cependant, pour l'instant on ne peux faire qu'une seule supposition à la fois. On doit ajouter donc un moyen pour permettre plusieurs tentatives : les boucles.  
**Q: Que doit-on utiliser pour répeter une ou plusieurs instruction?**

### Les boucles en Rust

- Pour introduire une boucle, on utilise le mot-clé `loop { }`, créant ainsi une boucle infini. Il faudra ajouter une condition pour sortir de la boucle.  
**Q: Pourquoi loop{} boucle indéfiniment par défaut?**
```
loop {
        println!("Veuillez entrer un nombre.");

        // -- partie masquée ici --

        match supposition.cmp(&nombre_secret) {
            Ordering::Less => println!("C'est plus !"),
            Ordering::Greater => println!("C'est moins !"),
            Ordering::Equal => println!("Vous avez gagné !"),
        }
```
- L'utilisateur peut interrompre le programme à tout moment avec *ctrl+c*. Dans notre cas, nous alons vérifier si l'utilisateur saisit quelque chose qui n'est pas un nombre, par conséquent le programme va planter.  
**Q: Comment l'utilisateur peut interompre l'exécution du programme de façon brusque?**
- Le jeu se termine si l'utilisateur tape une saisie non numérique, mais nous souhaitons également que le jeu se termine lorsque le bon nombre est deviné.  
**Q: Que se passe-t'il si le type de la saisie est différente du type attendu?**

### Arrêt du programme sur demande

- L'ajout de l'expression ``break`` après le message de succès permet de sortir de la boucle lorsque le joueur devine le nombre secret. Cela termine également le programme, car la boucle est la dernière partie de ``main``.  
**Q: Quelle expréssion permet de sortir de la boucle sans planter le programme?**
```
Ordering::Equal => {
                println!("Vous avez gagné !");
                break;
            }
```

### Gestion de saisies invalides

- Pour améliorer le jeu, on modifie le code pour ignorer les entrées non numériques au lieu de faire planter le programme, permettant ainsi à l'utilisateur de continuer à essayer de deviner.  
**Q: **
```
let supposition: u32 = match supposition.trim().parse() {
            Ok(nombre) => nombre,
            Err(_) => continue,
};
```  
- On remplace ``expect`` par une expression ``match`` pour gérer proprement les erreurs, ``parse()`` retourne un ``Result`` avec les variantes ``Ok`` et ``Err``. De cette façon on peut traiter les erreurs sans faire planter le programme.  
**Q: Quelle est l'alternative de "expect" pour traiter la valeur d'une variable?**
- Si ``parse()`` réussit, elle retourne ``Ok`` contenant le nombre converti. L'expression ``match`` correspondra à ce motif et assignera le nombre à supposition, où nous en avons besoin.  
**Q: Quelle est la valeur d'argument de "Ok"?**
- Si ``parse()`` échoue, elle retourne ``Err`` avec des informations sur l'erreur. Le motif ``Err(_)`` dans l'expression ``match`` correspond à toutes les variantes ``Err``, peu importe leur contenu. Le programme exécutera alors le code de la branche ``continue``, qui passe à l'itération suivante de la boucle et demande un nouveau nombre, ignorant ainsi les erreurs de ``parse()``.  
**Q: Quel est le rôle de l'expression "continue"?**
- Finalement, on peux supprimer l'instruction qui affiche le nombre secret qui était utile pour le test. Le jeu est maintenant fini, on peut le lancer et y jouer.
```rust
use rand::Rng;
use std::cmp::Ordering;
use std::io;

fn main() {
    println!("Devinez le nombre !");

    let nombre_secret = rand::thread_rng().gen_range(1..101);

    loop {
        println!("Veuillez entrer un nombre.");

        let mut supposition = String::new();

        io::stdin()
            .read_line(&mut supposition)
            .expect("Échec de la lecture de l'entrée utilisateur");

        let supposition: u32 = match supposition.trim().parse() {
            Ok(nombre) => nombre,
            Err(_) => continue,
        };

        println!("Votre nombre : {}", supposition);

        match supposition.cmp(&nombre_secret) {
            Ordering::Less => println!("C'est plus !"),
            Ordering::Greater => println!("C'est moins !"),
            Ordering::Equal => {
                println!("Vous avez gagné !");
                break;
            }
        }
    }
}
```


# 3. Les concepts courants de programmation

- Ce chapitre présente des concepts communs des langages de programmation, et la façon dont ils sont représentés en Rust, comme les variables, types de base, fonctions, commentaires et structures de contrôle...  
**Q: Donnez des exemples de concepts qu'on trouve dans les différents languages de programmation?**

- Rust réserve certains mots-clés pour un usage exclusif, similaires à d'autres langages. Ces mots-clés ne peuvent pas être utilisés pour nommer des variables ou des fonctions. La plupart sont utilisés pour des tâches spécifiques, tandis que certains sont réservés pour de futures fonctionnalités.  
**Q: Dunnez des exemples de mot-clés non assosciés à des fonctionnalités.**


### 3.1. Les variables et la mutabilité

- En Rust, les variables sont immuables par défaut, ce qui aide à assurer la sécurité et la concurrence. Cependant, il est possible de rendre les variables modifiables avec le mot-clé ``mut``. Rust favorise l'immuabilité pour encourager des pratiques sûres, mais permet la mutabilité quand nécessaire, offrant ainsi un équilibre entre sécurité et flexibilité.  
**Q: Quelle est l'état par défaut des variables dans Rust?**
- Le compilateur aide à détecter les erreurs dans les programmes. Bien que frustrantes, les erreurs de compilation montrent que le programme n'est pas encore sécurisé. Il est crucial d'obtenir des erreurs de compilation lorsque nous essayons de modifier une valeur immuable, car cela peut entraîner des bugs difficiles à identifier. Si une partie de du code suppose qu'une valeur ne changera jamais alors qu'une autre partie la modifie, cela peut compromettre le fonctionnement de la première. Le compilateur Rust assure que les valeurs déclarées comme immuables ne changeront pas.  
**Q: Quelle est l'importance d'obtenir des erreurs de compilation lorsque l'on essaie de modifier une valeur immuable dans un programme Rust ?**
- La mutabilité est utile et facilite la rédaction du code. Les variables sont immuables par défaut, mais on peut les rendre mutables en ajoutant ``mut`` devant leur nom. Cela indique également aux lecteurs futurs que la valeur de cette variable sera modifiée par d'autres parties du code.  
**Q: Que doit-on ajouter devant le nom d'une variable pour la rendre mutable en Rust ?**
- L'utilisation de ``mut`` permet de modifier la valeur d'une variable. Il existe des compromis à considérer, comme la rapidité de la mutation d'une grande structure de données par rapport à la création d'une nouvelle instance. Pour les petites structures de données, une approche fonctionnelle peut améliorer la clarté du code, même si cela entraîne une légère perte de performance.  
**Q: Pourquoi muter une instance existante d'une grande structure de données peut-il être plus rapide que de créer une nouvelle instance ?**

###### Les constantes

- Les constantes en Rust, tout comme les variables immuables, sont des valeurs attachées à un nom qui ne peuvent pas être modifiées. Toutefois, il existe des différences notables entre les deux.  
**Q: Les constantes et les variables immuables peuvent-elles être modifiées ?**
- Les constantes en Rust sont toujours immuables et ne peuvent pas être déclarées avec le mot-clé ``mut``. Elles se déclarent avec const au lieu de ``let``, et il est nécessaire de spécifier le type de la valeur. Les détails concernant les types seront abordés dans une section ultérieure.  
**Q: Peut-on utiliser mut avec les constantes en Rust ?**
- Les constantes en Rust peuvent être déclarées à n'importe quel endroit du code, y compris dans la portée globale, ce qui les rend particulièrement utiles pour des valeurs accessibles à de nombreuses parties du code.  
**Q: Où peut-on déclarer des constantes en Rust ?**
- Les constantes en Rust doivent être définies par une expression constante, et ne peuvent pas être le résultat d'une valeur qui nécessite un calcul à l'exécution.  
**Q: Par quoi les constantes doivent-elles être définies par des expressions constantes en Rust ?**
- Les constantes en Rust sont valables pendant toute la durée d'exécution du programme dans la portée où elles sont déclarées, ce qui les rend utiles pour partager des valeurs entre différentes parties du code.  
**Q: Quelle est la durée de validité des constantes dans un programme Rust ?**
- Utiliser des constantes pour déclarer des valeurs codées en dur dans votre programme aide à clarifier leur signification et facilite les modifications futures en centralisant leur gestion.  
**Q: Quels sont les avantages d'utiliser des constantes pour les valeurs codées en dur dans un programme ?**

###### Le masquage

- En Rust, il est possible de déclarer une nouvelle variable avec le même nom qu'une variable précédente, masquant ainsi la première. Cela signifie que le programme utilisera la valeur de la seconde variable. Ce masquage s'effectue en réutilisant le mot-clé ``let``.  
**Q: Que signifie le masquage d'une variable en Rust ?**
- Créer un masque de variable est différent de marquer une variable comme mut, car une réassignation accidentelle d'une variable immuable entraîne une erreur de compilation. En utilisant ``let``, on peut transformer une valeur tout en rendant la variable immuable après ces transformations.  
**Q: Quelle est la différence entre créer un masque de variable et marquer une variable comme mut en Rust ?**
- En utilisant ``let``, on peut créer un masque de variable qui permet de changer le type de la valeur tout en réutilisant le même nom. Cela est utile dans des situations comme demander à l'utilisateur le nombre d'espaces souhaités entre deux portions de texte, où la saisie initiale pourrait être une chaîne de caractères, mais on veut la stocker ensuite sous forme de nombre.  
**Q: Quelle est une situation où l'utilisation de let permet de changer le type d'une valeur tout en réutilisant le même nom de variable ?**

### 3.2. Les types de données

- En Rust, chaque valeur a un type spécifique qui guide le langage dans le traitement des données. Les types de données se classifient en deux catégories principales : les types scalaires, qui représentent des valeurs uniques, et les types composés, qui regroupent plusieurs valeurs.  
**Q: Quelles sont les deux catégories de types de données en Rust ?**
- Rust est un langage statiquement typé, nécessitant la connaissance des types de toutes les variables lors de la compilation. Souvent, le compilateur déduit le type en fonction de la valeur et de son utilisation. Cependant, dans des cas ambigus, comme lors de la conversion d'une chaîne en un type numérique avec parse, il est nécessaire d'ajouter une annotation de type.  
**Q: Qu'est-ce que signifie qu'un langage est statiquement typé, et comment Rust gère-t-il les types des variables ?**

#### Types scalaires

- Un type scalaire en Rust représente une seule valeur et comprend quatre types principaux : les entiers, les nombres à virgule flottante, les booléens et les caractères, similaires à d'autres langages de programmation.  
**Q: Quels sont les quatre types principaux de scalaires en Rust ?**

###### Types de nombres entiers

- Les entiers en Rust sont des nombres sans partie décimale, et le type u32 indique qu'une valeur est un entier non signé de 32 bits. Les entiers négatifs sont indiqués par un type commençant par "i". Il existe plusieurs types d'entiers intégrés au langage, permettant de déclarer des valeurs entières de différentes manières.  
**Q: Quel type d'entier indique une valeur non signée de 32 bits en Rust ?**
- Les entiers en Rust peuvent être signés (acceptent les valeurs négatives) ou non signés (toujours positifs), chaque variante ayant une taille explicite. Les nombres signés utilisent le complément à deux pour leur stockage.  
**Q: Quelle méthode de stockage est utilisée pour les nombres signés en Rust ?**
- Les variantes signées en Rust peuvent stocker des nombres dans l'intervalle de -2^(n-1) à 2^(n-1) - 1, tandis que les variantes non signées peuvent stocker des nombres de 0 à 2^n - 1.  
**Q: Quel est l'intervalle de valeurs qu'un i8 peut stocker ?**
- Les types ``isize`` et ``usize`` en Rust varient en fonction de l'architecture de l'ordinateur, utilisant 64 bits sur une architecture 64 bits et 32 bits sur une architecture 32 bits.  
**Q: Quelles sont les tailles des types isize et usize selon l'architecture de l'ordinateur ?**
- Les littéraux d'entiers en Rust peuvent être écrits dans différentes formes et permettre l'utilisation de suffixes pour spécifier le type, comme 57u8. Ils peuvent également inclure des underscores (_) comme séparateurs pour améliorer la lisibilité.  
**Q: Comment pouvez-vous spécifier le type d'un littéral numérique en Rust ?**
- Pour déterminer le type d'entier à utiliser en Rust, vous pouvez vous référer aux choix par défaut, qui sont généralement appropriés. Par exemple, le type d'entier par défaut est ``i32``. Les types ``isize`` et ``usize`` sont principalement utilisés lors de l'indexation de collections.  
**Q: Quel est le type d'entier par défaut en Rust ?**

###### Dépassement d'entier

- Un type ``u8`` peut stocker des valeurs entre 0 et 255. Si vous essayez d'assigner une valeur comme 256 à cette variable, vous rencontrerez un dépassement d'entier (integer overflow). En mode débogage, Rust inclut des vérifications pour détecter ces dépassements, et si cela se produit, le programme va paniquer et se terminer avec une erreur.  
**Q: Que se passe-t-il si vous essayez d'assigner une valeur supérieure à 255 à une variable de type u8 ?**
- En mode publication avec le drapeau --release, Rust ne vérifie pas les dépassements d'entiers, ce qui entraîne un comportement de rebouclage du complément à deux. Par exemple, une valeur de 256 pour un u8 deviendra 0, et 257 deviendra 1. Bien que le programme ne panique pas, cela peut conduire à des valeurs inattendues, et se fier à ce rebouclage est une mauvaise pratique.  
**Q: Que se passe-t-il en mode publication si un dépassement d'entier se produit dans un programme Rust ?**
- Rust propose plusieurs méthodes pour gérer explicitement les dépassements d'entiers via sa bibliothèque standard :

1. ``wrapping_*`` : Enveloppez les opérations pour qu'elles retournent des valeurs en bouclant (ex. wrapping_add).
1. ``checked_*`` : Retourne None en cas de dépassement (ex. checked_add).
1. ``overflowing_*`` : Retourne la valeur et un booléen indiquant s'il y a eu un dépassement (ex. overflowing_add).
1. ``saturating_*`` : Saturation à la valeur minimale ou maximale (ex. saturating_add).  
**Q: Quelles méthodes peuvent être utilisées en Rust pour gérer les dépassements d'entiers ?**

###### Types de nombres à virgule flottante
- Rust offre deux types primitifs pour les nombres à virgule flottante : f32 et f64, correspondant à des tailles de 32 bits et 64 bits respectivement. Le type par défaut est f64 en raison de sa précision supérieure, étant donné qu'il est presque aussi rapide que f32 sur les processeurs modernes. Tous les flottants ont un signe.  
**Q: Quels sont les deux types primitifs pour les nombres à virgule flottante en Rust ?**
- Les nombres à virgule flottante en Rust sont conformes à la norme IEEE-754, où f32 représente un flottant à simple précision et f64 un flottant à double précision.  
**Q: Quelle norme est utilisée pour représenter les nombres à virgule flottante en Rust ?**

###### Les opérations numériques

- Rust propose des opérations mathématiques fondamentales pour tous les types de nombres, y compris l'addition, la soustraction, la multiplication, la division et le modulo. Les divisions entre entiers arrondissent le résultat à l'entier le plus proche.  
**Q: Quelles opérations mathématiques Rust offre-t-il pour les types de nombres ?**
- Chaque instruction utilise un opérateur mathématique pour calculer une valeur unique, qui est ensuite assignée à une variable.  
**Q: Où peut-on trouver la liste de tous les opérateurs fournis par Rust ?**

###### Types booléen

- En Rust, le type booléen a deux valeurs possibles : true et false. Il occupe un octet en mémoire et est désigné par le mot-clé bool.  
**Q: Quelles sont les deux valeurs possibles pour le type booléen en Rust ?**
- Les valeurs booléennes, qui prennent les valeurs true et false, sont principalement utilisées dans les structures conditionnelles, comme l'instruction if. Leur utilisation permet de contrôler le flux du programme en fonction de conditions spécifiques.  
**Q: Dans quel type de structures les valeurs booléennes sont-elles principalement utilisées en Rust ?**

###### Le type caractère

- Le type char en Rust représente le type de caractère le plus élémentaire. Chaque valeur char représente un caractère unique, y compris des caractères Unicode.  
**Q: Que représente le type char en Rust ?**
- En Rust, un littéral char est défini par des guillemets simples, tandis que les chaînes de caractères utilisent des doubles guillemets. Le type char occupe quatre octets en mémoire et représente une valeur scalaire Unicode, englobant un large éventail de caractères, y compris les lettres accentuées, les caractères asiatiques, les emojis et d'autres symboles. Toutefois, la définition de ce qu'est un "caractère" peut varier, et cette notion peut ne pas correspondre à celle de char en Rust.  
**Q: Quelle est la taille en mémoire du type char en Rust ?**

#### Les types composés

- Les types composés en Rust permettent de regrouper plusieurs valeurs en un seul type. Les deux principaux types composés de Rust sont les tuples et les tableaux.  
**Q: Quels sont les deux types composés de base en Rust ?**

###### Tuples

- Un tuple permet de regrouper plusieurs valeurs de types différents en un type composé. Sa taille est fixe, ce qui signifie qu'une fois déclaré, on ne peut ni ajouter ni enlever de valeurs.  
**Q: Quelle caractéristique détermine la taille d'un tuple en Rust ?**
- Pour créer un tuple en Rust, on écrit une liste de valeurs séparées par des virgules entre parenthèses. Chaque valeur dans le tuple peut avoir un type différent, et bien que les annotations de type soient possibles, elles ne sont pas obligatoires.  
**Q: Comment crée-t-on un tuple en Rust ?**
- Dans Rust, une variable peut être liée à un tuple entier, car celui-ci est considéré comme un seul élément. Pour accéder à un élément spécifique de ce tuple, on peut utiliser le filtrage par motif pour le déstructurer.  
**Q: Comment peut-on accéder à un élément spécifique d'un tuple en Rust ?**
- En Rust, il est également possible d'accéder directement à chaque élément d'un tuple en utilisant un point (.) suivi de l'indice de l'élément souhaité.  
**Q: Comment peut-on accéder directement à un élément d'un tuple en Rust ?**
- Le type unité, représenté par le tuple vide (), a une seule valeur, également (). Il est utilisé pour indiquer qu'une expression ne retourne pas de valeur significative, retournant plutôt la valeur unité par défaut.  
**Q: Quel est le nom du type représenté par le tuple vide () en Rust ?**

###### Tableaux

- Les tableaux en Rust permettent de regrouper plusieurs valeurs du même type dans une collection de taille fixe, définie au moment de la déclaration. Ils sont déclarés en écrivant une liste de valeurs entre crochets, séparées par des virgules.  
**Q: Quelle est la principale différence entre un tableau et un tuple en Rust concernant les types d'éléments ?**
- Les tableaux en Rust sont utilisés pour stocker des données de taille fixe sur la pile, tandis que les vecteurs sont des collections plus flexibles qui peuvent changer de taille. Si la taille des éléments n'est pas connue à l'avance, il est recommandé d'opter pour un vecteur. Les tableaux en Rust sont plus adaptés lorsque le nombre d'éléments est fixe.  
**Q: Dans quel cas est-il préférable d'utiliser un vecteur plutôt qu'un tableau en Rust ?**
- Le type d'un tableau en Rust est défini en utilisant des crochets, suivi du type des éléments, d'un point-virgule et du nombre d'éléments, comme ``[i32; 5]`` pour un tableau d'entiers de 32 bits contenant 5 éléments.  
**Q: Comment déclare-t-on le type d'un tableau en Rust ?**
- Pour initialiser un tableau avec la même valeur pour chaque élément, vous indiquez la valeur initiale, un point-virgule, puis la taille du tableau, le tout entre crochets.comme ``[0; 5]`` crée un tableau de 5 éléments, tous initialisés à 0.  
**Q: Comment initialise-t-on un tableau avec la même valeur pour chaque élément en Rust ?**

###### Accéder aux éléments d'un tableau

- Un tableau en Rust est un bloc de mémoire de taille fixe alloué sur la pile. On peut accéder aux éléments d'un tableau via l'indexation ``tableau[i]``.  
**Q: Comment accède-t-on aux éléments d'un tableau en Rust ?** 

###### Accès incorrect à un élément d'un tableau

- Lorsque vous accédez à un élément d'un tableau en Rust, le langage effectue une vérification à l'exécution pour s'assurer que l'indice fourni est valide. Si l'indice est inférieur à la taille du tableau, l'accès est autorisé. En revanche, si l'indice est supérieur ou égal à la taille du tableau, Rust déclenche une panique, arrêtant ainsi le programme pour éviter des erreurs d'accès mémoire.  
**Q: Que fait Rust si l'indice d'un tableau est supérieur ou égal à sa taille ?**
- Rust applique des principes de sécurité de la mémoire en vérifiant les indices d'accès aux tableaux. Contrairement à de nombreux langages de bas niveau, Rust effectue des vérifications à l'exécution pour éviter d'accéder à des emplacements mémoire invalides. Si un indice incorrect est utilisé, Rust arrête immédiatement l'exécution au lieu de permettre l'accès à une mémoire potentiellement dangereuse, contribuant ainsi à la sécurité du programme.  
**Q: Quelle est la principale différence entre Rust et de nombreux langages de bas niveau concernant la vérification des indices d'accès aux tableaux ?**

### 3.3. Les fonctions

- Les fonctions sont essentielles en Rust, avec la fonction ``main`` servant de point d'entrée pour de nombreux programmes. Les nouvelles fonctions sont déclarées avec le mot-clé ``fn``.  
**Q: Quelle est la fonction principale dans un programme Rust et comment déclare-t-on de nouvelles fonctions ?**
- Rust utilise la convention de nommage snake_case pour les fonctions et les variables. On définit une fonction en utilisant fn, suivie d'un nom et d'accolades pour indiquer son corps.  
**Q: Quelle convention de nommage Rust utilise-t-il pour les fonctions et comment définit-on une fonction ?**
- Le code s'exécute dans l'ordre où les instructions apparaissent, et une fonction peut être définie après son appel sans problème, tant qu'elle est définie quelque part dans le code.  
**Q: Est-il possible de définir une fonction après son appel dans le code Rust ?**
- Les fonctions peuvent avoir des paramètres, qui sont des variables dans la signature de la fonction. Les valeurs passées à ces paramètres lors de l'appel sont appelées arguments.  
**Q: Quelle est la différence entre un paramètre et un argument dans le contexte des fonctions en Rust ?**
- Lorsqu'on ajoute un paramètre à une fonction, on doit spécifier son type. Cela aide le compilateur à comprendre avec quel type il travaille, et plusieurs paramètres peuvent être déclarés en les séparant par des virgules.  
**Q: Pourquoi est-il important de spécifier le type des paramètres dans les fonctions Rust ?**
- Le corps des fonctions contient des instructions et éventuellement une expression finale. Les instructions ne retournent pas de valeur, tandis que les expressions sont évaluées pour retourner une valeur.  
**Q: Quelle est la différence entre une instruction et une expression dans une fonction en Rust ?**
- Les corps de fonction en Rust peuvent contenir des instructions et des expressions, avec un exemple montrant comment un bloc peut évaluer une valeur sans point-virgule.  
**Q: Que se passe-t-il si on ajoute un point-virgule à la fin d'une expression dans le corps d'une fonction ?**
- Les fonctions peuvent retourner des valeurs. On déclare le type de retour après une flèche (->), et la valeur retournée est généralement la dernière expression dans le corps de la fonction.  
**Q: Comment déclare-t-on le type de retour d'une fonction en Rust ?**
Le dernier élément d'une fonction est souvent la valeur retournée, et une fonction peut également utiliser le mot-clé return pour sortir précocement avec une valeur.  
**Q: Que se passe-t-il si une fonction Rust ne termine pas par une expression retournée ?**
- Un exemple montre comment une fonction retourne un nombre. Si une instruction est utilisée à la place d'une expression, cela peut provoquer une erreur due à un type de retour inadéquat.  
**Q: Pourquoi une fonction peut-elle générer une erreur de type si une instruction est utilisée à la place d'une expression pour la valeur retournée ?**
- Il est important de ne pas mettre de point-virgule à la fin d'une expression que l'on veut retourner, car cela la transforme en instruction, ce qui empêche le retour de valeur attendu.  
**Q: Quel effet a l'ajout d'un point-virgule à la fin d'une expression qui devrait être retournée dans une fonction ?**

### 3.4. Les commentaires

- Les développeurs utilisent des commentaires dans leur code pour fournir des explications utiles aux lecteurs, même si le compilateur les ignore. Cela aide à rendre le code plus compréhensible.  
**Q: Pourquoi les développeurs ajoutent-ils des commentaires dans leur code ?**

- Dans Rust, les commentaires simples commencent par deux barres obliques (//) et s'étendent jusqu'à la fin de la ligne. Pour les commentaires plus longs, il faut placer les barres obliques sur chaque ligne.  
**Q: Comment sont formatés les commentaires simples dans Rust ?**

- Les commentaires peuvent être ajoutés à la fin des lignes de code pour fournir des explications. Parfois, ils sont placés au-dessus du code pour clarifier la fonction du code qu'ils annotent.  
**Q: Comment peut-on utiliser les commentaires dans le code Rust par rapport aux lignes de code ?**

- Rust propose également des commentaires de documentation, qui sont une forme spéciale de commentaire, à traiter dans un chapitre futur.  
**Q: Quel type de commentaire Rust propose-t-il en plus des commentaires classiques ?**

### 3.5. Structures de controle

- Les structures de contrôle, comme les expressions if et les boucles, permettent de contrôler l'exécution du code en fonction de conditions.  
**Q: Quels sont les types de structures de contrôle en Rust ?**

#### Les expressions if

- Une expression if permet d'exécuter un bloc de code si une condition est remplie. Si la condition n'est pas remplie, le bloc de code ne s'exécute pas.  
**Q: Quel est le rôle d'une expression if dans Rust ?**

- Dans le code donné, la condition vérifie si la variable `nombre` est inférieure à 5, et le bloc de code s'exécute en fonction de cette vérification.  
**Q: Que vérifie la condition dans l'exemple donné avec l'expression if ?**

- On peut ajouter une expression else pour définir un bloc de code alternatif qui s'exécute si la condition est fausse. Si aucun else n'est fourni, le code passe simplement au suivant.  
**Q: Quelle est la fonction d'une expression else dans une structure if ?**

- Le code illustre le résultat de l'exécution avec une valeur vérifiée et une valeur non vérifiée pour `nombre`.  
**Q: Que se passe-t-il lorsque la condition n'est pas vérifiée dans l'exemple donné ?**

- Il est essentiel que la condition dans un if soit de type bool. Si ce n'est pas le cas, une erreur est générée. Rust ne convertit pas automatiquement les types.  
**Q: Que se passe-t-il si la condition dans une expression if n'est pas un booléen ?**

###### Gérer plusieurs conditions avec else if

- On peut combiner plusieurs conditions avec else if pour gérer différents cas dans une expression. Le code montre comment cela fonctionne avec un exemple de divisibilité.  
**Q: Comment peut-on gérer plusieurs conditions dans Rust ?**

- Rust n'exécute que le premier bloc dont la condition est vérifiée. Cela peut entraîner des comportements inattendus si plusieurs conditions sont vraies.  
**Q: Que se passe-t-il si plusieurs conditions sont vraies dans une expression else if ?**

- L'utilisation excessive d'expressions else if peut encombrer le code ; d'autres constructions, comme match, peuvent être envisagées.  
**Q: Pourquoi est-il conseillé d'éviter trop d'expressions else if dans un code Rust ?**

###### Utiliser if dans une instruction let

- Une expression if peut être utilisée pour assigner des valeurs à une variable. Le résultat de l'expression dépend de la condition.  
**Q: Comment peut-on assigner le résultat d'une expression if à une variable dans Rust ?**

- Les valeurs des branches if et else doivent être du même type pour éviter des erreurs de type.  
**Q: Quels types de valeurs doivent être compatibles dans une expression if ?**

#### Les répétitions avec les boucles

- Les boucles permettent d'exécuter un bloc de code plusieurs fois. Rust propose trois types de boucles : loop, while, et for.  
**Q: Quels types de boucles propose Rust pour répéter du code ?**

###### Répéter du code avec `loop`
- Le mot-clé `loop` en Rust demande au programme d'exécuter un bloc de code en continu. Cela crée une boucle infinie qui ne se termine que si une instruction explicite est donnée pour l'arrêter.  
**Q: Quel est le rôle de la boucle `loop` en Rust ?**

###### Exécution d'une boucle infinie
- Lorsque vous exécutez un programme utilisant `loop`, comme dans l'exemple donné, le texte "À nouveau !" s'affiche sans interruption dans le terminal. Cette boucle continuera à s'exécuter jusqu'à ce qu'une interruption manuelle soit effectuée, généralement en utilisant `Ctrl+C`, ce qui provoque l'arrêt du programme. Le texte peut être affiché plusieurs fois avant que l'arrêt ne soit effectué, en fonction du moment où l'utilisateur interrompt le programme.  
**Q: Que se passe-t-il lorsque l'on exécute une boucle infinie ?**

###### Utilisation de `break` et `continue`
- Rust fournit des moyens pour contrôler la sortie des boucles grâce aux mots-clés `break` et `continue`. Le mot `break` permet de quitter immédiatement la boucle courante, tandis que `continue` permet de sauter à l'itération suivante de la boucle. Lorsqu'il y a des boucles imbriquées, ces mots-clés affectent uniquement la boucle la plus interne, sauf si une étiquette de boucle est spécifiée, permettant ainsi une plus grande flexibilité dans le contrôle de la logique des boucles.  
**Q: Comment `break` et `continue` fonctionnent-ils dans des boucles imbriquées ?**

###### Retourner des valeurs d'une boucle
- Les boucles `loop` peuvent également être utilisées pour exécuter des opérations qui pourraient échouer et nécessiter des réessais. Lorsqu'une certaine condition est atteinte, on peut utiliser `break` pour quitter la boucle tout en retournant une valeur. Cette valeur, que l'on peut stocker dans une variable, est ensuite accessible à l'extérieur de la boucle, permettant ainsi de l'utiliser dans d'autres parties du programme.  
**Q: Comment peut-on retourner une valeur d'une boucle `loop` ?**

###### Boucles conditionnelles avec `while`
- Rust propose également la boucle `while`, qui exécute son bloc de code tant qu'une condition spécifiée est vraie. Cela évite la complexité que l'on pourrait avoir à gérer avec `loop`, `if`, et `break`. Par exemple, une boucle `while` peut être utilisée pour effectuer des répétitions jusqu'à ce qu'un compteur atteigne zéro. Ce type de boucle est souvent plus clair et plus concis pour des scénarios simples où une condition d'arrêt est nécessaire.  
**Q: Pourquoi utiliser `while` est-il plus simple que d'utiliser `loop` avec des conditions ?**

###### Boucler dans une collection avec `for`
- La boucle `for` en Rust est conçue pour itérer facilement sur les éléments d'une collection, comme un tableau. Contrairement à `while`, elle gère automatiquement l'indexation et la condition d'arrêt, ce qui réduit le risque d'erreurs d'indexation. Par exemple, lors de l'itération sur un tableau, il n'est pas nécessaire de se soucier de dépasser les limites, car la boucle s'arrête automatiquement après avoir traité tous les éléments.  
**Q: Quels avantages la boucle `for` offre-t-elle par rapport à `while` pour l'itération sur un tableau ?**

###### Utilisation d'un intervalle avec `for`
- Avec la boucle `for`, Rust permet également d'utiliser des intervalles pour exécuter du code sur une plage de nombres. Par exemple, l'utilisation de `(1..4).rev()` dans une boucle `for` permet de parcourir les nombres dans l'ordre inverse, rendant le code plus flexible et facile à comprendre. Cela simplifie également l'écriture de code pour des tâches récurrentes comme le décompte, car les utilisateurs n'ont pas à se préoccuper de gérer manuellement les indices ou les limites.  
**Q: Qu'est-ce que la méthode `rev` apporte à l'utilisation des intervalles dans une boucle `for` ?**


# 4. Comprendre la posession

- La possession est un concept clé en Rust, permettant de gérer la mémoire sans garbage collector. Chaque valeur a un propriétaire unique, et quand ce propriétaire cesse d'exister, la mémoire est libérée. Ce chapitre explore la possession, l'emprunt, les slices, et la gestion de la mémoire.  
**Q: Quel est l'objectif principal de la possession en Rust ?**

### 4.1. Qu'est ce que la possession

- La possession en Rust est un ensemble de règles permettant de gérer la mémoire sans ralentir l'exécution. Contrairement aux langages avec ramasse-miettes ou allocation manuelle, Rust gère la mémoire via la possession, en s'assurant que les règles sont respectées à la compilation. Si une règle est enfreinte, le programme ne compile pas.  
**Q: Comment Rust gère-t-il la mémoire différemment des autres langages ?**
- Comme la possession est un concept nouveau pour beaucoup, il faut un peu de temps pour s'y habituer. Mais avec de l'expérience, écrire du code sûr et efficace en respectant les règles de possession devient de plus en plus naturel.  
**Q: Quel est l'avantage d'acquérir de l'expérience avec les règles de possession en Rust ?**
- Lorsque vous maîtriserez la possession, vous disposerez des bases nécessaires pour comprendre les fonctionnalités uniques de Rust. Ce chapitre vous apprendra la possession à travers des exemples pratiques, principalement avec les chaînes de caractères.  
**Q: Quelle structure de données est utilisée pour illustrer la possession dans ce chapitre ?**

#### La pile et le tas

- De nombreux langages de programmation ne nécessitent pas que l'on se préoccupe de la gestion de la mémoire. Cependant, dans un langage comme Rust, il est important de comprendre la différence entre pile et tas, car cela influence la manière dont les données sont gérées.

**Q: Pourquoi est-il important de comprendre la différence entre pile et tas dans un langage comme Rust ?**

- La pile est organisée selon un principe de dernier entré, premier sorti, et les données qu'elle contient doivent avoir une taille connue et fixe au moment de la compilation.

**Q: Quel est le principe de gestion des données dans la pile, et pourquoi les données doivent-elles avoir une taille connue à la compilation ?**

- Le tas est moins organisé : il demande de l'espace mémoire et retourne un pointeur vers cet espace. Ce processus est appelé allocation, et c'est généralement plus lent que l'empilement sur la pile.

**Q: Pourquoi l'allocation sur le tas est-elle plus lente que l'empilement sur la pile ?**

- L'analogie avec un restaurant permet d'expliquer le fonctionnement de la gestion de mémoire sur le tas : le gestionnaire de mémoire trouve un espace assez grand pour les données, et retourne un pointeur comme un serveur qui assigne une table.

**Q: Comment l'analogie avec le restaurant aide-t-elle à comprendre le fonctionnement du tas en mémoire ?**

- Accéder à des données sur la pile est plus rapide que sur le tas, car il n'est pas nécessaire de suivre un pointeur. Les processeurs modernes sont plus efficaces lorsque les données sont proches en mémoire.

**Q: Pourquoi l'accès aux données sur la pile est-il plus rapide que sur le tas ?**

- Lorsque des fonctions sont utilisées, les valeurs passées à la fonction et les variables locales sont stockées sur la pile, et libérées une fois la fonction terminée.

**Q: Que devient les valeurs passées à une fonction et les variables locales après l'exécution de la fonction ?**

- Le système de possession dans Rust permet de gérer les données sur le tas sans que le développeur ait à s'en préoccuper directement. Comprendre la possession aide à comprendre comment Rust gère efficacement la mémoire.

**Q: Quel est le rôle du système de possession dans la gestion de la mémoire en Rust ?**

#### Le type String

- Les types de données simples ont une taille connue et peuvent être stockés sur la pile, mais Rust introduit des types plus complexes, comme `String`, qui stockent leurs données sur le tas, nécessitant une gestion particulière pour nettoyer la mémoire.

**Q: Pourquoi les types de données complexes comme `String` nécessitent-ils une gestion différente de la mémoire par rapport aux types simples ?**

- Le type `String` est utilisé pour gérer des données textuelles dont la taille n'est pas connue à la compilation. Contrairement aux littéraux de chaînes de caractères, qui sont immuables, `String` permet de manipuler des chaînes dynamiques et mutables.

**Q: Quelle est la principale différence entre les littéraux de chaînes et le type `String` en Rust ?**

- On peut créer une `String` à partir d'un littéral de chaîne de caractères avec `String::from()`. Cette méthode permet d'initialiser une chaîne de caractères dynamique.

**Q: Comment peut-on créer une `String` à partir d'un littéral de chaîne en Rust ?**

- Le type `String` permet d'ajouter du texte supplémentaire à une chaîne mutable, contrairement aux littéraux de chaînes qui sont immuables. Cela rend `String` plus flexible pour manipuler du texte dynamique.

**Q: Comment peut-on rendre une `String` mutable et ajouter du contenu supplémentaire ?**

- La différence fondamentale entre `String` et les littéraux de chaînes réside dans leur gestion de la mémoire. Les littéraux de chaînes sont immuables et stockés sur la pile, tandis que `String` gère ses données sur le tas, ce qui permet la mutabilité.

**Q: Pourquoi `String` peut-il être mutable alors que les littéraux de chaînes ne le sont pas ?**

#### Mémorie et allocation

- Les littéraux de chaînes de caractères sont immuables et leur contenu est connu à la compilation, ce qui les rend performants. Leur taille est fixe et intégrée dans l'exécutable final.

**Q: Pourquoi les littéraux de chaînes de caractères sont-ils plus rapides que les types `String` en Rust ?**

- Le type `String` permet de créer des chaînes de caractères mutables, mais nécessite une allocation dynamique sur le tas, ce qui implique une gestion manuelle de la mémoire pendant l'exécution.

**Q: Pourquoi le type `String` nécessite-t-il une allocation de mémoire sur le tas ?**

- Dans la majorité des langages, la mémoire est demandée lors de l'exécution, mais Rust se distingue par le fait qu'il libère automatiquement la mémoire lorsque la variable sort de la portée, sans nécessiter de ramasse-miettes.

**Q: Comment Rust gère-t-il la libération automatique de la mémoire sans avoir recours à un ramasse-miettes ?**

- En Rust, la mémoire allouée pour une `String` est automatiquement libérée lorsque la variable qui la possède sort de la portée. Cela est possible grâce à l'appel automatique de la fonction `drop`.

**Q: Quelle fonction Rust appelle-t-il pour libérer la mémoire lorsque la variable sort de la portée ?**

- Rust utilise le modèle RAII (acquisition d'une ressource est une initialisation) pour gérer la mémoire, similaire au C++, où les ressources sont libérées lorsque leur durée de vie prend fin.

**Q: Quel concept de gestion des ressources en C++ est similaire à la fonction `drop` de Rust ?**

###### Le déplacement

- L'assignation d'un entier simple dans Rust copie la valeur directement sur la pile, créant ainsi deux variables distinctes avec la même valeur.

**Q: Que se passe-t-il lors de l'assignation d'un entier en Rust ?**

- Contrairement aux entiers, l'assignation d'une `String` ne copie que le pointeur, la taille et la capacité sur la pile, sans dupliquer les données sur le tas.

**Q: Quelle est la différence entre l'assignation d'une `String` et celle d'un entier en Rust ?**

- Si Rust copiait aussi les données sur le tas, l'assignation pourrait être très coûteuse en performance, surtout avec des données volumineuses.

**Q: Pourquoi Rust ne copie-t-il pas les données du tas lors de l'assignation d'une `String` ?**

- Si deux pointeurs pointent vers les mêmes données sur le tas, cela créerait un problème de double libération de la mémoire, ce qui pourrait causer des corruptions de mémoire.

**Q: Quel problème se poserait si deux variables tentaient de libérer la même mémoire sur le tas en Rust ?**

- Rust résout le problème de la double libération en neutralisant la première variable après le déplacement de ses données dans la seconde. Ainsi, la première variable n'est plus utilisable.

**Q: Comment Rust empêche-t-il la double libération lors de l'assignation d'une `String` ?**

- Si vous essayez d'utiliser une variable déplacée après l'assignation, Rust génère une erreur, car cette variable n'est plus valide.

**Q: Que se passe-t-il si vous essayez d'utiliser une variable après qu'elle a été déplacée en Rust ?**

- Ce processus de neutralisation de la variable originale après l'assignation est appelé un "déplacement" en Rust, et non une copie superficielle.

**Q: Comment Rust appelle-t-il l'opération où une variable est désactivée après l'assignation ?**

- Rust ne crée jamais de copies profondes automatiques des données pour garantir des performances optimales. Toute copie automatique est donc peu coûteuse.

**Q: Pourquoi Rust évite-t-il de créer automatiquement des copies profondes des données ?**

###### Le clonage

- Pour faire une copie profonde des données sur le tas d'une `String`, il est possible d'utiliser la méthode `clone`. Cette méthode effectue une copie complète, y compris des données sur le tas, contrairement à une simple copie superficielle.

**Q: Quelle méthode permet de faire une copie profonde des données d'une `String` en Rust ?**

- L'utilisation de `clone` indique visuellement qu'un code coûteux est exécuté pour copier les données du tas.

**Q: Quel est l'indicateur visuel qu'une copie profonde est en cours dans le code Rust ?**

- Les entiers, et d'autres types de données simples, ne nécessitent pas l'utilisation de `clone` car ils sont entièrement stockés sur la pile. Leur copie est rapide et ne demande pas de désactiver la première variable après l'assignation.

**Q: Pourquoi les entiers en Rust ne nécessitent-ils pas l'utilisation de `clone` ?**

- Les types comme les entiers qui ont une taille fixe au moment de la compilation implémentent le trait `Copy`. Ce trait permet de copier ces types sans déplacer la valeur initiale.

**Q: Quel trait en Rust permet de copier un type sans le déplacer ?**

- Le trait `Copy` ne peut pas être implémenté pour un type si ce type implémente également le trait `Drop`, car cela entraînerait des conflits lors de la libération de la mémoire.

**Q: Pourquoi ne peut-on pas utiliser le trait `Copy` sur un type qui implémente `Drop` ?**

- Les types qui implémentent `Copy` incluent les entiers, les booléens, les flottants, les caractères, et certains tuples si tous leurs éléments implémentent aussi `Copy`.

**Q: Quels types en Rust implémentent généralement le trait `Copy` ?**

#### La possession et les fonctions

- En Rust, la syntaxe pour passer une valeur à une fonction fonctionne de manière similaire à l'assignation de cette valeur à une variable. Lorsque vous passez une variable à une fonction, cela déplace ou copie la valeur, selon son type.

**Q: Comment la syntaxe de Rust gère-t-elle les variables passées à une fonction par rapport à l'assignation ?**

- Lorsqu'une variable est passée à une fonction, cela peut déplacer la valeur si elle n'implémente pas le trait `Copy`, ce qui la rendra inutilisable après l'appel de la fonction.

**Q: Que se passe-t-il lorsqu'une variable est déplacée dans une fonction en Rust ?**

- Si une variable implémente le trait `Copy` (comme pour les types scalaires simples comme `i32`), elle

#### Les valeurs de retour et les portées

- En Rust, retourner des valeurs peut également transférer leur **possession**. Quand une fonction retourne une valeur, cette valeur est déplacée dans la variable de l'appelant. Cela suit la même logique que l'assignation.

**Q: Qu'est-ce que cela signifie quand on dit qu'une valeur retourne une fonction en Rust ?**

- L'exemple de l'encart 4-4 montre que les valeurs de type `String`, qui ont des données sur le tas, sont déplacées entre les fonctions. Par exemple, la fonction `donne_possession` retourne une `String`, et la variable qui l'appelle prend possession de cette chaîne.

**Q: Que se passe-t-il lorsque la fonction `donne_possession` retourne une valeur ?**

- Le retour d'une fonction peut aussi déplacer la possession d'une variable qui est passée en paramètre. La fonction `prend_et_rend` montre ce mécanisme : la valeur `s2` est déplacée dans la fonction, mais elle est aussi retournée, donc une nouvelle variable peut la reprendre.

**Q: Comment fonctionne la fonction `prend_et_rend` dans cet exemple ?**

- Lorsqu'une variable sort de la portée, elle est supprimée à moins que sa **possession** soit transférée à une autre variable. C'est pourquoi il est important de transférer explicitement la possession si on veut réutiliser une variable après l'avoir passée à une fonction.

**Q: Pourquoi la variable `s2` est-elle supprimée alors que `s3` ne l'est pas à la fin de la fonction `main` ?**

- Le processus de transférer et de retourner constamment la possession peut être fastidieux, surtout si l'on veut que la fonction utilise une valeur sans la prendre. Pour résoudre cela, Rust permet de retourner plusieurs valeurs avec un tuple, comme dans l'encart 4-5, où la taille de la chaîne est retournée en même temps que la chaîne elle-même.

**Q: Comment Rust permet-il de retourner plusieurs valeurs sans devoir gérer manuellement la possession de chaque élément ?**

- Rust a une fonctionnalité appelée **références** qui permet d'utiliser une valeur sans en prendre la possession. Cela simplifie le code et évite de devoir constamment transférer ou retourner la possession.

**Q: Quelle est l'alternative à la gestion manuelle des possessions en Rust pour utiliser une valeur sans la transférer ?**

### 4.2. Les références et l'emprunt

- Le code du tuple vu précédemment est un peu fastidieux car nous devons retourner la `String` pour pouvoir la réutiliser. En Rust, nous pouvons utiliser une **référence** pour éviter ce transfert de possession. Une référence agit comme un pointeur vers une donnée sans en prendre la possession.

**Q: Qu'est-ce qu'une référence en Rust et comment fonctionne-t-elle ?**

- Une référence permet de manipuler une valeur sans transférer sa possession, garantissant que la donnée à laquelle elle pointe est toujours valide. Par exemple, en passant `&s1` à la fonction `calculer_taille`, nous passons une référence plutôt que la valeur, ce qui permet à `s1` d'être toujours en vigueur après l'appel à la fonction.

**Q: Quelle est la différence entre passer une valeur et passer une référence dans une fonction en Rust ?**

- L'utilisation d'une référence permet de garder la variable originale après l'appel à la fonction tout en accédant à sa valeur. Cela évite la nécessité de retourner manuellement des valeurs.

**Q: Pourquoi est-il préférable d'utiliser des références plutôt que de retourner manuellement la possession en Rust ?**

- Une référence garantit qu'on pointe vers une valeur valide. Cela diffère des pointeurs classiques qui peuvent pointer vers des valeurs invalides. Le déréférencement est l'opération opposée à la création de références, et cela se fait avec un opérateur spécifique.

**Q: Qu'est-ce que le déréférencement en Rust, et pourquoi est-il important de l'utiliser avec précaution ?**

- Lorsqu'une référence est utilisée, elle ne prend pas possession de la valeur qu'elle pointe. La mémoire n'est donc pas libérée quand la référence sort de la portée, ce qui est très pratique pour éviter de devoir retourner manuellement des valeurs.

**Q: Quelle est l'importance de la portée d'une référence en Rust ?**

- Le concept d'**emprunt** décrit l'action de passer une référence sans transfert de possession. Cela est similaire à emprunter un objet dans la vie réelle : vous pouvez l'utiliser, mais vous devez le rendre à la fin.

**Q: Comment Rust gère-t-il l'emprunt et quelles sont ses implications ?**

#### Les références mutables

- Pour modifier une valeur empruntée, on peut utiliser une **référence mutable**. Cela nécessite de déclarer la variable comme mutable avec `mut` et de spécifier que la fonction accepte une référence mutable.

**Q: Comment modifier une valeur empruntée en Rust ?**

- Une contrainte des références mutables est qu'il ne peut y avoir qu'une seule référence mutable à une donnée à la fois. Tenter de créer plusieurs références mutables à la même donnée entraînera une erreur de compilation.

**Q: Quelle est la contrainte associée aux références mutables en Rust ?**

- Si une donnée a déjà une référence mutable, vous ne pouvez pas en créer une autre tant que la première est encore en vigueur. Cette limitation permet d'éviter les accès concurrents, ce qui peut entraîner des comportements indéfinis.

**Q: Pourquoi Rust interdit-il plusieurs références mutables à la même donnée ?**

- L'accès concurrent à des données partagées peut causer des problèmes de synchronisation. Rust empêche cela en s'assurant qu'aucun code avec des références concurrentes ne se compile, garantissant ainsi la sécurité des données.

**Q: Comment Rust gère-t-il les accès concurrents aux données partagées ?**

- On peut créer de nouvelles portées pour permettre l'utilisation de références mutables. En utilisant des accolades, vous pouvez sortir une référence mutable d'une portée avant d'en créer une nouvelle.

**Q: Quelle est l'importance des portées dans la gestion des références mutables en Rust ?**

- Rust impose également des règles lorsque des références immuables et mutables coexistent. Si une donnée a des références immuables, vous ne pouvez pas créer de référence mutable vers cette même donnée tant que ces références immuables sont en vigueur.

**Q: Quelles sont les règles concernant les références immuables et mutables en Rust ?**

- Les portées des références commencent dès leur création et se poursuivent jusqu'à leur dernière utilisation. Les **Non-Lexical Lifetimes (NLL)** permettent au compilateur de déterminer si une référence est encore utilisée avant la fin de sa portée.

**Q: Que signifie le terme Non-Lexical Lifetimes (NLL) en Rust ?**

- Bien que les erreurs liées aux emprunts puissent être frustrantes, elles servent à signaler les bogues potentiels lors de la compilation, ce qui facilite la détection et la correction des problèmes avant l'exécution.

**Q: Quel est l'avantage des erreurs de compilation liées aux emprunts en Rust ?**

#### Les références pendouillantes

- Dans les langages utilisant des pointeurs, il est possible de créer des **pointeurs pendouillants**, qui pointent vers un emplacement mémoire libéré. En revanche, Rust garantit que les références ne seront jamais pendouillantes, car le compilateur s'assure qu'une donnée ne sort pas de sa portée tant qu'il existe une référence vers elle.

**Q: Quel est le risque associé aux pointeurs dans d'autres langages par rapport à Rust ?**

- Lorsque l'on tente de créer une référence pendouillante dans Rust, le compilateur génère une erreur de compilation. Cela se produit lorsque l'on essaie de retourner une référence vers une variable qui sera désallouée après la sortie de la fonction.

**Q: Que se passe-t-il lorsque l'on essaie de créer une référence pendouillante en Rust ?**

- Le message d'erreur indique que la fonction retourne une valeur empruntée, mais il n'y a plus de valeur à emprunter, ce qui est dû à la désallocation de la variable lorsque la fonction se termine.

**Q: Que signifie le message d'erreur lié à une référence pendouillante en Rust ?**

- Dans l'exemple, lorsque la variable `s` est créée dans la fonction `pendouille`, elle sort de la portée lorsque la fonction se termine. Essayer de retourner une référence vers `s` devient donc problématique, car `s` sera libérée, rendant la référence invalide.

**Q: Pourquoi retourner une référence à `s` dans `pendouille` pose-t-il problème ?**

- La solution consiste à retourner directement la `String` au lieu de sa référence. Cela transfère la possession de la valeur de retour, évitant ainsi tout problème de désallocation.

**Q: Quelle est la solution pour éviter une référence pendouillante en Rust ?**

#### Les règles de référencement

Ce que nous avons vu à propos des références en Rust

1. **Types de références** :
   - À un instant donné, vous pouvez avoir :
     - **Une référence mutable**.
     - **Un nombre quelconque de références immuables**.

2. **Durée de vie des références** :
   - Les références doivent toujours être **en vigueur**.

**Q: Quelle est la différence entre une référence mutable et une référence immuable en Rust ?**

### 4.3. Le type slice

#### Les Slices en Rust

- Une slice permet d'obtenir une référence à une séquence d'éléments d'une collection sans en prendre possession. Pour illustrer ce concept, nous devons écrire une fonction qui retourne le premier mot d'une chaîne de caractères. La fonction `premier_mot` prend une référence à une `String` comme paramètre. Cependant, sans les slices, nous ne pouvons pas directement retourner une partie de la chaîne.  
  **Q: Pourquoi est-il difficile de retourner une partie d'une chaîne de caractères sans utiliser de slices ?**

- La fonction `premier_mot` utilise la méthode `as_bytes` pour convertir la `String` en un tableau d'octets afin de trouver l'indice du premier espace. Nous parcourons ce tableau d'octets pour identifier la position de l'espace et retournons cet indice. Si aucun espace n'est trouvé, nous retournons la longueur de la chaîne.  
  **Q: Comment la fonction `premier_mot` détermine-t-elle l'indice de l'espace dans la chaîne ?**

- Bien que nous puissions trouver l'indice de la fin du premier mot, cela pose un problème car cet indice n'est valide que tant que la chaîne d'origine n'est pas modifiée. Dans un exemple, après avoir appelé `premier_mot`, nous vidons la chaîne, ce qui rend l'indice retourné invalide.  
  **Q: Quel est le problème de retourner un indice au lieu d'une référence à une slice de la chaîne ?**

- Gérer les indices devient encore plus complexe si nous tentons de récupérer le deuxième mot. Cela implique de garder une trace de plusieurs indices, ce qui augmente les risques d'erreurs.  
  **Q: Pourquoi la gestion de plusieurs indices peut-elle être problématique dans des fonctions comme `second_mot` ?**

- Rust résout ces problèmes grâce aux slices de chaînes de caractères, qui permettent de faire référence directement à une partie de la chaîne tout en garantissant la validité de cette référence.  
  **Q: Comment les slices de chaînes de caractères aident-elles à résoudre les problèmes liés à la gestion des indices ?**

#### Les slices de chaînes de caractères

- Une slice de chaîne est une référence à une partie d'une String, permettant d'accéder à une portion spécifique sans en prendre possession. On crée des slices en spécifiant des indices de début et de fin.  
  **Q: Qu'est-ce qu'une slice de chaîne et comment est-elle créée ?**

- La syntaxe d'intervalle de Rust permet de créer des slices de différentes manières, y compris en omettant les indices de début ou de fin. Les indices doivent respecter les limites des caractères encodés en UTF-8 pour éviter des erreurs.  
  **Q: Quelles sont les différentes manières de créer une slice de chaîne en Rust et quelles précautions faut-il prendre ?**

- La fonction premier_mot a été réécrite pour retourner une slice de chaîne, simplifiant ainsi la gestion des références. En retournant une slice, la fonction garantit que la valeur est liée à la donnée de base.  
  **Q: Comment la fonction premier_mot a-t-elle été modifiée pour utiliser des slices, et quels avantages cela apporte-t-il ?**

- Le compilateur s'assure que les références restent valides, évitant ainsi les problèmes de synchronisation des indices, comme ceux rencontrés précédemment. Cela améliore la sécurité du code en éliminant les erreurs au moment de la compilation.  
  **Q: Quel est l'avantage principal des slices par rapport à l'utilisation d'indices séparés dans la gestion des chaînes de caractères ?**

- Le programme de démonstration montre que l'utilisation de slices entraîne une erreur de compilation si une référence mutable est utilisée en même temps qu'une référence immuable, garantissant ainsi la sécurité des références.  
  **Q: Quelle erreur se produit lors de l'utilisation simultanée de références immuables et mutables dans l'exemple de code donné ?**

###### Les littéraux de chaîne de caractères sont aussi des slices

- Les littéraux de chaîne de caractères sont stockés dans le binaire du programme. En utilisant des slices, nous pouvons comprendre comment ces littéraux fonctionnent. Un exemple est donné avec une variable s qui est de type &str, ce qui signifie qu'elle pointe vers un emplacement spécifique dans le binaire.  
  **Q: Que signifie le fait que les littéraux de chaîne soient stockés dans le binaire et quel type de données représentent-ils ?**

- Le type &str est une référence immuable, ce qui explique pourquoi les littéraux de chaîne sont immuables.  
  **Q: Pourquoi les littéraux de chaîne sont-ils immuables dans Rust ?**

###### Les slices de chaînes de caractères en paramètres

- L'utilisation de slices de littéraux et de String permet d'améliorer la fonction premier_mot. Au lieu d'utiliser une référence à une String, une signature plus générale serait d'utiliser une slice de chaîne de caractères comme paramètre. Cela permet d'utiliser la même fonction pour les références de String et pour les slices de littéraux.  
  **Q: Quelle est l'amélioration apportée à la fonction premier_mot concernant son paramètre ?**

- En définissant la fonction avec un paramètre de type slice de chaîne (&str), on obtient plus de flexibilité : on peut passer directement une slice de chaîne ou une référence à une String. Cela rend l'API plus générique et utile tout en maintenant la même fonctionnalité.  
  **Q: Quels avantages offre l'utilisation d'un paramètre de type slice de chaîne pour la fonction premier_mot ?**

#### Les autres slices

- Les slices de chaînes de caractères sont spécifiques aux chaînes, mais il existe aussi des slices plus génériques pour d'autres types de données, comme les tableaux. Par exemple, il est possible de référencer une partie d'un tableau en utilisant un intervalle pour créer une slice.  
  **Q: Qu'est-ce qui rend les slices de tableaux différentes des slices de chaînes de caractères ?**

- Une slice de tableau, comme celle créée à partir d'un tableau d'entiers, fonctionne de la même manière que les slices de chaînes en stockant une référence vers le premier élément et une longueur. Ce type de slice, noté &[i32], sera utilisé pour d'autres types de collections qui seront abordées plus tard.  
  **Q: Comment une slice de tableau est-elle représentée et comment fonctionne-t-elle ?**

#### Resumé

- Les concepts de possession, d'emprunt et de slices assurent la sécurité de la mémoire en Rust à la compilation. Rust permet de contrôler l'utilisation de la mémoire tout en nettoyant automatiquement les données lorsqu'elles sortent de la portée, ce qui évite d'avoir à gérer manuellement la mémoire.  
  **Q: Comment Rust garantit la sécurité de la mémoire à la compilation ?**

- La possession a un impact sur de nombreuses autres fonctionnalités de Rust, ce qui justifie des discussions supplémentaires sur ces concepts dans le livre. Le chapitre 5 traitera de la manière de regrouper des données dans une structure (struct).  
  **Q: Pourquoi est-il important de continuer à explorer le concept de possession dans le reste du livre ?**

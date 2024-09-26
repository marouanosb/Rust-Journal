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
```
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
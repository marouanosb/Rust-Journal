<!-- CHAPITRE 13 -->
- Quelles sont les fonctionnalités implementés dans Rust qui sont inspirées de la programmation fonctionnelle?
- Définissez ce qu'est une fermeture dans Rust et donnez un exemple basique de syntaxe.
- Expliquez les trois façons dont une fermeture peut capturer des variables de son environnement. Donnez un exemple pour chacune.
- Pourquoi les fermetures sont-elles utiles dans le contexte de la programmation fonctionnelle ?
- Quelle est la différence principale entre une fermeture et une fonction classique dans Rust ?
- Quelles sont les implications des traits `Fn`, `FnMut` et `FnOnce` dans la conception des fermetures ? Donnez un exemple où chacun de ces traits est pertinent.
- Que se passe-t-il lorsqu’une fermeture est utilisée dans un contexte nécessitant une capture mutable d’une variable ? Comment cela est-il géré par Rust ?
- Expliquez comment Rust infère le type des arguments et du retour d'une fermeture. Pourquoi cette fonctionnalité est-elle importante ?
- Dans quels scénarios les fermetures sont-elles souvent utilisées avec les itérateurs en Rust ? Donnez un exemple simple où une fermeture est passée à une méthode comme `filter` ou `map`.
- Décrivez les avantages de l’utilisation des fermetures en termes de performance et d’ergonomie du code dans Rust.
- Comment une fermeture peut-elle être explicitement transformée en fonction, si nécessaire ? Pourquoi cela pourrait-il être utile ?

- Décrivez le rôle des itérateurs dans Rust et leur fonctionnement général.
- Expliquez comment la méthode `next` est utilisée pour parcourir un itérateur.
- Pourquoi les itérateurs sont-ils considérés comme des abstractions "à coût zéro" en Rust ?
- Quelles sont les trois étapes principales nécessaires pour créer votre propre type implémentant le trait `Iterator` ?
- Donnez un exemple de scénario où l'utilisation des méthodes comme `map` ou `filter` sur les itérateurs améliore la lisibilité et la concision du code.
- Expliquez la différence entre les méthodes de consommation des itérateurs et celles qui produisent de nouveaux itérateurs.
- Comment Rust gère-t-il la sécurité et la performance lors de l'utilisation d'itérateurs dans des boucles complexes ?
- Pourquoi l’utilisation d’itérateurs peut-elle améliorer les performances comparées aux boucles explicites ?
- Décrivez une situation où vous pourriez vouloir utiliser un itérateur personnalisé au lieu des itérateurs standard.
- Que signifie "chainer" des itérateurs en Rust ? Donnez un exemple simple illustrant ce concept.

- Quels sont les quatre principaux problèmes identifiés dans la structure initiale de notre programme ?
- Pourquoi est-il important de séparer les responsabilités entre `main.rs` et `lib.rs` ?
- Quels sont les trois rôles que la fonction `main` conserve après la restructuration ?
- Expliquez pourquoi regrouper les variables de configuration dans une structure est bénéfique.
- Pourquoi éviter l’utilisation répétée de `expect` pour gérer les erreurs dans le programme ?
- Décrivez le processus de division des responsabilités entre `main.rs` et `lib.rs`.
- Comment la séparation des responsabilités entre `main.rs` et `lib.rs` améliore-t-elle les tests du programme ?
- Pourquoi est-il préférable d’afficher des messages d’erreur spécifiques plutôt qu’un message générique comme "Quelque chose s'est mal passé lors de la lecture du fichier" ?
- Quels sont les avantages d’avoir tout le code de gestion des erreurs regroupé en un seul endroit ?
- Comment la communauté Rust recommande-t-elle d’organiser les projets binaires complexes ?

- Pourquoi est-il préférable d'utiliser un itérateur plutôt que de collecter les arguments avec `env::args()` dans le projet de gestion des entrées/sorties ?
- Qu'est-ce que le "coût zéro" en ce qui concerne l'utilisation des itérateurs dans Rust ?
- Quelle est l'importance de ne pas avoir de clonage inutile lors de l'utilisation des itérateurs ?
- Expliquez comment l'utilisation des itérateurs améliore la performance du programme par rapport à une boucle classique.
- Pourquoi les fermetures et les itérateurs sont-ils considérés comme une combinaison performante dans Rust ?
- Comment Rust optimise-t-il le code des closures utilisées dans les méthodes d'itérateur ?
- Qu'est-ce que la technique de "mouvement" des valeurs dans un itérateur et pourquoi est-elle plus efficace que la copie ?
- Décrivez un exemple d'optimisation de performance dans le programme `Config::new` en remplaçant les clones par des itérateurs.
- Quels sont les avantages d’utiliser des itérateurs pour transformer ou filtrer des données au lieu d’utiliser des boucles explicites ?
- Expliquez en quoi la gestion des erreurs de manière centralisée contribue à une meilleure performance dans un programme Rust.

<!-- CHAPITRE 15 -->
- Quelles sont les principales différences entre les pointeurs intelligents et les références classiques en Rust ?
- Expliquez le rôle du trait `Deref` en Rust et comment il permet de traiter les pointeurs intelligents comme des références. Donnez un exemple pour illustrer son utilisation.
- Pourquoi utiliser des pointeurs intelligents comme `Box<T>` ou `Rc<T>` en Rust ? Quels problèmes résolvent-ils par rapport aux références classiques ?
- Comparez et contrastez les types de pointeurs intelligents `Box<T>` et `Rc<T>`. Quand utiliseriez-vous l'un plutôt que l'autre ?
- Comment fonctionnent les pointeurs intelligents en Rust lorsqu'une valeur est déplacée (moved) d'un pointeur à un autre ? Expliquez comment Rust gère cette situation.
- Qu'est-ce que le trait `DerefMut` et comment est-il utilisé en combinaison avec des pointeurs intelligents ?
- Examinez comment les pointeurs intelligents en Rust, comme `RefCell` ou `Mutex`, permettent une gestion mutable de la mémoire tout en conservant la sécurité du programme.
- Quels sont les avantages de l'utilisation de pointeurs intelligents en termes de sécurité de mémoire et d'ergonomie du code dans Rust ?
- Donnez un exemple où une `Box<T>` est utilisée pour allouer dynamiquement de la mémoire sur le tas et expliquer pourquoi cela est utile.
- Comment les pointeurs intelligents comme `Box<T>` et `Rc<T>` peuvent-ils améliorer la lisibilité et la clarté du code Rust ?

- Qu'est-ce qu'un pointeur Box<T> dans Rust, et à quoi sert-il ?
- Quel est l'avantage principal de l'utilisation de Box<T> pour allouer des données sur le tas ?
- Expliquez pourquoi il est nécessaire de déplacer la propriété d'une valeur lorsque vous l'affectez à une variable de type Box<T>.
- Quelles sont les limitations de l'utilisation de Box<T> pour partager la propriété entre plusieurs variables ?
- Quel type de valeur peut être contenu dans un Box<T> ?
- Comment Box<T> se compare-t-il à d'autres pointeurs intelligents comme Rc<T> et RefCell<T> ?
- Donnez un exemple de code où Box<T> est utilisé pour allouer une structure sur le tas.
- Quelle est la différence entre Box<T> et une référence classique dans Rust ?
- Pourquoi Box<T> ne permet-il pas d'avoir plusieurs propriétaires d'une même valeur ?
- Quel est l'impact de l'utilisation de Box<T> sur la gestion de la mémoire dans le programme ?

- Quelle est la principale fonction du trait `Deref` en Rust ?
- Expliquez comment l'implémentation de `Deref` peut permettre de surcharger l'opérateur `*` pour un type personnalisé.
- Qu'est-ce que l'auto-déréférencement, et comment fonctionne-t-il en Rust avec le trait `Deref` ?
- Donnez un exemple simple de l'utilisation de `Deref` pour transformer un type personnalisé en un type auquel l'on peut appliquer des opérations de déréférencement.
- Quelle est la différence entre les comportements de `Deref` et `DerefMut` ?
- Comment Rust choisit-il quand appliquer `Deref` ou `DerefMut` dans les situations de types imbriqués ?
- Quelle est la relation entre le trait `Deref` et le mot-clé `Box` ?
- Comment le trait `Deref` permet-il la compatibilité avec les types sous-jacents d'objets trait (trait objects) ?
- Pourquoi le trait `Deref` est-il essentiel pour l'ergonomie dans l'écriture de bibliothèques Rust ?
- Que se passe-t-il si `Deref` est implémenté sur un type qui ne possède pas la fonctionnalité attendue par l'utilisateur ?

- Qu'est-ce que le trait `Drop` en Rust et pourquoi est-il important pour la gestion de la mémoire ?
- Expliquez le rôle de la méthode `drop` et donnez un exemple de son utilisation.
- Quand est-ce que Rust appelle la méthode `drop` d'un type ?
- Quelle est la différence entre `Drop` et la gestion automatique de la mémoire dans Rust ?
- Quels types de ressources doivent souvent implémenter `Drop` et pourquoi ?
- Pourquoi la méthode `drop` ne peut-elle pas être appelée explicitement à l'intérieur de la méthode `drop` elle-même ?
- Quelle est la conséquence de la tentative d'implémentation du trait `Drop` sur des types avec des ressources partagées ?
- Décrivez l'effet de l'appel explicite à `std::mem::drop` dans un programme Rust.
- Quel est l'impact de la gestion automatique de la mémoire (via `Drop`) sur la performance d'un programme ?
- Expliquez la différence entre `Drop` et d'autres mécanismes de gestion de la mémoire dans des langages comme C++ ou Python.

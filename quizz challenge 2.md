<!-- CHAPITRE 15 suite -->
- Que permet de faire le type `Rc<T>` dans Rust, et pourquoi est-il utile ?
- Quelle est la différence entre les compteurs `strong_count` et `weak_count` dans `Rc<T>` ?
- Expliquez pourquoi les références faibles (`Weak<T>`) sont nécessaires pour éviter les boucles de références.
- Donnez un exemple d'utilisation de `Rc::downgrade` et expliquez son fonctionnement.
- Pourquoi une boucle de références avec des `Rc<T>` peut-elle entraîner une fuite de mémoire ? Donnez un exemple.
- Quels sont les avantages de combiner `Rc<T>` avec `RefCell<T>` dans certaines situations ?
- Décrivez une situation où l’utilisation de `Rc<T>` serait appropriée dans un programme Rust.
- Comment pouvez-vous transformer une référence forte en une référence faible avec `Rc<T>` ?
- Expliquez les implications de la propriété partagée offerte par `Rc<T>` dans un contexte multi-thread.
- Quels sont les points à surveiller pour éviter des problèmes liés au cycle de vie des données avec `Rc<T>` ?

- Qu'est-ce que le concept de mutabilité interne en Rust et pourquoi est-il utile dans certains scénarios ?
- Décrivez le rôle de `RefCell<T>` dans la mutabilité interne et comment il diffère de `Rc<T>` ou `Box<T>`.
- Comment le type `RefCell<T>` garantit-il la sécurité à l'exécution en Rust ? Quels types d'erreurs peut-il détecter ?
- Qu'est-ce que l'empreinte `UnsafeCell<T>` et comment est-elle utilisée comme base pour la mutabilité interne en Rust ?
- Expliquez la différence entre les vérifications de sécurité faites à la compilation et à l'exécution. Donnez un exemple impliquant `RefCell<T>`.
- Dans quel contexte l'utilisation combinée de `RefCell<T>` et `Rc<T>` est-elle utile ? Donnez un exemple pratique.
- Quelles sont les implications de la mutabilité interne sur la conception et la performance des programmes Rust ?
- Comment Rust prévient-il les conflits d'accès mutable avec `RefCell<T>` ? Quelles sont les conséquences si une violation est détectée ?
- Décrivez un cas où la mutabilité interne serait préférable à une structure de données classique mutables.
- Quels sont les compromis liés à l'utilisation de la mutabilité interne, en termes de performances et de clarté du code ?

- Qu'est-ce qu'un cycle de références en Rust et pourquoi pose-t-il problème avec le type `Rc<T>` ?
- Comment le type `Weak<T>` aide-t-il à prévenir les cycles de références ?
- Quelle est la différence principale entre une référence forte (`Rc<T>`) et une référence faible (`Weak<T>`) ?
- Expliquez comment convertir une référence forte en une référence faible à l'aide de `Rc::downgrade`.
- Donnez un exemple pratique où l'utilisation de `Weak<T>` est nécessaire pour éviter des fuites de mémoire.
- Que se passe-t-il lorsqu'une référence faible (`Weak<T>`) tente d'accéder à une valeur qui a été nettoyée ?
- Quels outils ou techniques Rust fournit-il pour diagnostiquer ou éviter les cycles de références ?
- Pourquoi les cycles de références sont-ils plus probables dans des structures de données comme les graphes ou les arbres ?
- Expliquez la relation entre le compteur de références fortes et le compteur de références faibles dans `Rc<T>`.
- Quels sont les avantages et inconvénients de l’utilisation de `Weak<T>` dans la conception de structures de données partagées ?

<!-- CHAPITRE 16 -->
- Qu'est-ce que la concurrence en Rust et comment le langage assure-t-il la sécurité lors de l'exécution simultanée de tâches ?
- Comment les tâches (`tasks`) sont-elles utilisées pour exécuter simultanément du code en Rust ?
- Quelles sont les principales différences entre la gestion de la concurrence en Rust et celle dans d'autres langages comme Python ou JavaScript ?
- Expliquez le concept de "passing messages" pour transférer des données entre différentes tâches en Rust. Pourquoi ce mécanisme est-il sûr ?
- Qu'est-ce que le partage d'état en concurrence dans le contexte de Rust, et comment des mécanismes comme `Mutex` ou `RwLock` sont-ils utilisés ?
- Quelle est la différence entre les traits `Sync` et `Send` en Rust et pourquoi sont-ils essentiels pour la concurrence ?
- Dans quel cas une donnée serait-elle marquée `Send` et non `Sync` ? Donnez un exemple concret.
- Comment Rust empêche-t-il les courses de données (data races) lors de l'utilisation de la concurrence ?
- Pourquoi l'usage des références et de l'ownership est crucial pour la sécurité en concurrence en Rust ?
- Comment l'architecture de Rust facilite-t-elle la création de systèmes hautement concurrentiels et performants ?

- Qu'est-ce qu'un thread en Rust et comment peut-on en créer un ?
- Expliquez comment le mécanisme de gestion de la mémoire de Rust (propriété et emprunt) assure la sécurité des threads.
- Quelle est la différence entre un thread et un processus dans le contexte de Rust ?
- Quel rôle joue la fonction `thread::spawn` dans l'exécution concurrente de code en Rust ?
- Comment les closures `move` sont-elles utilisées pour déplacer des données dans un thread ?
- Qu'est-ce qui se passe si un thread se termine prématurément avant que son travail soit effectué ?
- Comment garantir qu’un thread a bien terminé son travail avant que le programme principal ne se termine ?
- Pourquoi est-il important de gérer les erreurs dans les threads en Rust et comment le faire ?
- Donnez un exemple d'utilisation d'un thread pour exécuter une tâche longue de manière concurrente.
- Quel est l'impact de l’utilisation de threads sur la performance d’un programme en Rust ?

- Qu'est-ce que l'envoi de messages entre threads en Rust et pourquoi est-ce important pour la concurrence ?
- Expliquez ce qu'est un canal (`channel`) en Rust et comment il est utilisé pour la communication entre threads.
- Quelle est la différence entre un canal avec un producteur unique et un consommateur unique (`mpsc`) et un canal avec plusieurs producteurs et consommateurs (`mpmc`) ?
- Comment Rust garantit-il la sécurité lors du passage de données entre threads via des canaux ?
- Quel type de données peut-on envoyer par un canal en Rust et comment la propriété de ces données est-elle transférée ?
- Comment gérer les erreurs potentielles lorsqu'un thread échoue à envoyer ou recevoir un message ?
- Qu'est-ce que le `Receiver` et le `Sender` dans le contexte d'un canal en Rust ? Expliquez leur rôle respectif.
- Donnez un exemple d'utilisation d'un canal pour envoyer des messages d'un thread principal à un thread secondaire.
- Pourquoi l'utilisation de canaux en Rust est-elle plus sûre que d'autres formes de communication entre threads, comme le partage de mémoire ?
- Dans quel cas l'utilisation de canaux est-elle plus appropriée que l'utilisation de mécanismes de verrouillage comme `Mutex` ?

- Qu'est-ce qu'un `Mutex` en Rust et comment permet-il de gérer l'accès à des données partagées entre plusieurs threads ?
- Quelle est la différence entre un `Mutex` et un `RwLock` en termes de gestion de l'accès à un état partagé ?
- Comment le système de type de Rust assure-t-il la sécurité de la mémoire lors de l'utilisation de ces mécanismes de synchronisation ?
- Expliquez le rôle de la méthode `lock` dans un `Mutex` et comment elle permet de synchroniser l'accès aux données.
- Dans quel cas devrait-on utiliser un `RwLock` au lieu d'un `Mutex` ?
- Quels sont les dangers potentiels associés à l'utilisation de `Mutex` et `RwLock` dans des programmes concurrentiels ?
- Quelle est la fonction de l'attribut `Sync` et comment est-il lié à la sécurité en concurrence dans Rust ?
- Donnez un exemple d'utilisation de `Mutex` pour protéger une donnée partagée dans un programme multithread.
- Pourquoi est-il important de minimiser la durée pendant laquelle un thread détient un verrou (`lock`) ?
- Comment gérer les erreurs qui peuvent survenir lors du verrouillage d'un `Mutex` ?

- Quel est le rôle des traits `Send` et `Sync` dans la concurrence en Rust ?
- Quelle condition un type doit-il remplir pour implémenter le trait `Send` ?
- En quoi `Send` et `Sync` diffèrent-ils ?
- Pourquoi `Rc<T>` ne peut-il pas implémenter `Send` ni `Sync` ?
- Quel trait doit implémenter un type pour pouvoir être utilisé en toute sécurité avec un `Mutex` dans un environnement concurrent ?
- Que se passe-t-il si un type non synchronisé est accédé de manière concurrente ?
- Quels sont les avantages d'utiliser un `Mutex` pour partager des données entre threads ?
- Peut-on partager un type comme `i32` entre threads avec un `Mutex` ?

<!-- CHAPITRE 17 -->
- Quel rôle joue l'encapsulation dans la programmation orientée objet en Rust ?
- Qu'est-ce que l'héritage et comment Rust gère-t-il l'héritage entre types ?
- Quelle est la différence entre le polymorphisme statique et dynamique dans le contexte de Rust ?
- Comment les traits sont-ils utilisés en Rust pour implémenter des comportements similaires à l'héritage ?
- Quelles sont les différences clés entre Rust et les langages orientés objet classiques comme Java ou C++ en termes de gestion de la mémoire et des objets ?

- Quels sont les principaux concepts de la programmation orientée objet ?
- Comment Rust permet-il d'implémenter l'encapsulation à travers ses structures ?
- Quelle est la différence entre l'héritage en Rust et dans les langages orientés objet traditionnels ?
- Comment Rust permet-il le polymorphisme, et quel rôle jouent les traits dans ce mécanisme ?
- Pourquoi Rust n'est-il pas considéré comme un langage purement orienté objet ?

- Qu'est-ce qu'un objet de trait en Rust et pourquoi est-il utile ?
- Quelle est la différence entre un objet de trait et un type concret dans Rust ?
- Comment utiliser un objet de trait pour permettre le polymorphisme en Rust ?
- Quels sont les avantages et les inconvénients d'utiliser des objets de trait par rapport à des types génériques ?
- Quelles sont les règles de compatibilité des objets de trait avec les types dynamiques ?

- Qu'est-ce qu'un patron de conception *Composite* et comment peut-on l'implémenter en Rust ?
- Expliquez le patron de conception *Observer* et comment il peut être utilisé en Rust.
- Quel est le rôle du patron *Strategy* et comment peut-on le modéliser avec des traits en Rust ?
- Quels sont les avantages de l'utilisation de ces modèles de conception dans Rust ?
- Comment les modèles de conception orientée objet peuvent-ils améliorer la flexibilité et l'extensibilité du code en Rust ?

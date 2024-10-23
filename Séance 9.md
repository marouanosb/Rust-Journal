# Chapitre 8

- Les collections étudiés dans ce chapitre sont-elles stockées sur la pile ou sur le tas ?  
Elles sont stockées sur le tas.
- La quantité de données stockées doit-elle être connu à la compilation ?  
Non, elle n'est pas connue.
- Vrai ou faux ? "L'instruction `let mut v = Vec::new();` est invalide.".  
Vrai, il faut préciser le type des valeur qu'on va stocker dans le vecteur.
- Le programme `let v = vec![1,2]; v.push(3);` ne compile pas. Pourquoi ?  
Il ne compile pas parceque la `push()` modifie le vecteur qui n'est pas mutable dans cet exemple.
- Le programme `let mut v = vec!['a','b']; v.push(3);` ne compile pas. Pourquoi ?  
Il ne compile pas parceque le type des données stockées dans le vecteur est différent de celui qu'on essaye d'ajouter.
- Si on déclare `let v = vec![1,2];`, quel est le type de `v.get(0)` ?  
Le type est `Option<i32>`.
- Si on déclare `let v = vec!['a','b'];`, quel est le type de `v[0]` ?  
Le type est de type `char`.
- On souhaite accéder à l'indice `i` d'un vecteur, alors que `i` est une valeur fournie par l'utilisateur. Vaut-il mieux utiliser `v[i]` ou `v.get(i)` ?  
Vaut mieux utilisier `v.get(i)` pour pouvoir indiquer à l'utilisateur qu'il a tapé un indexe très grande si le programme reàoit `None`, ce qui est mieux que planter le programme sans que l'utilisateur sache quel était le problème.
- Quel règle du vérificateur d'emprunt est violé lorsque si l'on écrit `let mut v = vec![1,2]; let x = v.get(0); v.push(3); let y = x;` ?  
On peut pas avoir une réference mutable `v.push(3)` et immuable `v.get(0)` en même temps.
- Réécrire la boucle sur collection suivante de façon plus idiomatique
  ```rust
	let v = vec!['h','e','l','l','o'];
	for i in &v {
		println!("{}",i);
	}
	```
- Réécrire la boucle sur collection suivante de façon plus idiomatique
  ```rust
	let mut v = vec!['h','e','l','l','o'];
	for i in &mut v {
		*i = '_';
	}
	```
- Vrai ou faux ? "Un vecteur a tous ses éléments du même type."  
Vrai.
- Est-il possible d'avoir un unique type qui correspond parfois à la donnée d'un `i32`, parfois à la donnée d'un `String`  ?  
Vrai, c'est possible d'avoir un vecteur d'un même type Enum qui peut avoir plusieurs sous-types différents.
- Vrai ou faux ? "Il existe deux types pour les chaînes de caractères en Rust".  
Faux, Rust a un seul type de chaine de charactère qui est `str`.
- Donner une expression équivalente à `String::from("hello")`.
	```rust
		let text = "hello".to_string();
	```
- Quelle est la différence entre les méthodes `push` et `push_str` sur une chaîne de caractère ?  
La méthode ``push()`` permet d'ajouter un seul caractère à la chaine, tandis que ``push_str()`` permet d'ajouter une slice de chaine de caractère (str).
- En utilisant l'opérateur `+`, donner l'expression retournant la concaténation de deux variables `x` et `y` toutes deux de type `String`. Peut-on encore utiliser `x` après ? Peux-on encore utiliser `y` après ?  
Non, on ne peut pas parceque `x` sera deplacé dans `y` et donc ne sera plus en vigeur.
	```rust
		let s = x + &y;
	```
- Donner un exemple simple d'_extrapolation de déréférencement_ ?  
SSur l'exemple précedent, l'opérateur `+` fait appel à la fonction standard `add()` qui extrapole en paramètre `&y` pour qu'il n'en prend pas possession.
- À quelle méthode correspond l'opérateur `+` ?  
Il correspond à la méthode `add(self, s: &str) -> String`.
- Transformer la fonction suivante pour quelle retourne une chaîne de caractère au lieu de provoquer un affichage:
  ```rust
	fn f(nom: String, age: i32) -> String {
		nom + " " + &(age.to_string())
	}
	```
- Vrai ou faux ? "Le code `let s = String::from("hello"); v[0]` retourne le caractère `'h'`."  
Faux, Rust n'utilise pas les index pour accéder aux élements de `String` parceque chaque élement n'est pas forcément un seul caractère et peut aussi donc être representé par un vecteur. C'est donc difficile d'accéder à chacun d'eux.
- Vrai ou faux ? "Le type `String` est une surcouche de `Vec<char>`."  
Faux, c'es une surcouche de `Vec<u8>`.
- La méthode `len` d'un `String` retourne le nombre de caractère graphique ou le nombre d'octet permettant de le stocker ?  
Elle retourne le nombre d'oct stockés.
- Étant donnée une chaîne de caractère, combien de façon différentes y a-t-il de le décomposer ?  
Une seule, on peut les décomposer par slice (prendre une petite partie de l'ensemble de la chaine de caractère).
- Vrai ou faux ? "Comme un `char` occupe 4 octets, le 10ième caractère d'un `String` se trouve toujours à l'octet (10-1)×4=36 en mémoire de l'espace alloué."  
Faux, un ``String`` peut contenir des caractères supérieurs à 4 octets.
- Vrai ou faux ? "Si `s` est un `String` et que l'expression `s[10..12]` fait paniquer le programme, c'est nécessairement que `s` est de taille inférieur à 12".  
Faux, ça peut aussi dire que `s` est de taille inférieure à 10 aussi.
- Comment s'appelle les deux méthodes permettant de parcourir un `String` ?  
La méthode `String::chars()` et ``String::bytes()``.
- Quelle fonction associé permet de créer une table de hachage ?
	```rust
		HashMap::new();
	```
- Quelle méthode permet d'ajouter une entrée dans la table de hachage ?
	```rust
		HashMap::insert(k,v);
	```
- Quelle méthode permet de récupérer une valeur associée à une clé d'une table de hachage ? Quel est le type du résultat de cette méthode si les clés sont des `i32` et les valeurs de `String` ?  
Le résultat sera de type `String`.
	```rust
		HashMap::get(k);
	```	
- Qu'est-ce qui ne va pas dans le code suivant ? (sans le compilateur idéalement)
  ```rust
	let ok = String::from("autorisé");
	let ko = String::from("interdit");
	let mut h = HashMap::new();
	h.insert(10,ko);
	h.insert(15,ko);
	h.insert(20,ok);
	h.insert(25,ok);
	```
- Modifier le code suivant pour le rendre plus idiomatique (en une seule ligne)
  	```rust
	let o = h.entry(key).or_insert(val);
	```
- Quel type retourne la méthode `or_insert` du type `Entry` d'une table de hachage ayant pour clé des `String` et pour valeur des `i32` ?  
Le type de retour est `i32`.

# Chapitre 9

- Quelles sont les deux comportements possible lorsque le programme panique ? Comment choisir entre les deux ?  
Soit le programme déroule la mémoire puis se ferme, ou il abandonne la mémoire tel qu'elle est et se ferme immédiatement.
- Quel est le type de retour de la fonction `std::fs::File::open` ?  
Le type de retour est `Result<T,E>`.
- Que fait la méthode `unwrap` de ce type de retour ?  
Elle vérifie si `Result` est `Ok`, elle affecte sa valeur à la variable, sinon si c'est la variable ``Err`` elle déclenche un ``panic!``.
- Que fait la méthode `expect` de ce type de retour ?  
Elle vérifie si `Result` est `Ok`, elle affecte sa valeur à la variable, sinon si c'est la variable ``Err`` elle fait paniquer le programme tout en affichant un message d'erreur qu'on définit dans l'argument de `expect()`.
- Écrire une fonction minimale utilisant l'opérateur `?` de propagation d'erreur, et une seconde version de ce code sans le propagateur.  
	```rust
		let f = File::open("hello.txt")?;
	```
	```rust
		let f = File::open("hello.txt");
		let mut f = match f {
        	Ok(fichier) => fichier,
        	Err(e) => return Err(e),
    };
	```
- Quelle fonction est automatique appelée par l'opérateur `?` en cas d'erreur à gérer et que fait cette fonction ?  
C'est la fonction `std::From::from()`.
- Quel doit être le type de retour de la fonction englobante pour pouvoir utiliser l'opérateur `?` ?  
Le type doit être `Result<T,E>`.
- Réduire le corps de la fonction suivante à une seule expression !
    ```rust
	fn somme_match(x: Option<i32>, y: Option<i32>) -> Option<i32> {
		x+y?
	}
	```
- Quel type `Result` peut-être mis à la fonction `main` pour qu'il puisse retourner n'importe quelle  erreur ?  
Le type `Box<dyn Error>>`.
- Lorsque l'on code un prototype, comment gérer les erreurs rapidement sans contrainte ?  
On utiliste `expect()` avec un message d'erreur indiquant là où on est pour bien comprendre ensuite d'où peuvent provenir les bugs.
- Utilise-t-on `unwrap()` uniquement lorsque l'on souhaite paniquer en cas de problème ?  
Vrai.
- Faites le rapport entre ce qui est discuté dans la section 9.3 à propos du type `Supposition` et ce que nous avons discuté à la précédente séance sur l'encapsulation du type `Carte` (et plus précisément du type `Valeur` en réalité) (partie non faite avec le master Cybersécurité, à faire à la prochaine séance).
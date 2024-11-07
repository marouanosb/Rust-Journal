# Chapitre 10

- Donner des exemples de type génériques vu dans les chapitres précédents.  
i32, f64, bool.
- Vrai ou faux: "Quand une fonction est générique, elle s'instancier nécessairement sur n'importe quel type, c'est ça que ça veut dire être générique".  
Vrai.
- Vrai ou faux: "les durées de vie sont des genre de générique".  
Vrai.
- Vrai ou faux: "La généricité sert à éviter de la duplication de code".  
Vrai.
- Vrai ou faux: "La convention de nommage des types en Rust est en snake_case comme les noms de variable ou de fonctions."  
Faux.
- Écrire une fonction générique qui reçoit trois données de même type et retourne un booléen indiquant si elle sont égales les unes aux autres. Utiliser les messages d'erreurs du compilateur pour savoir quel trait doit implémenter votre type générique
	```rust
		fn tous_egaux<T: std::cmp::PartialEq>(x: T, y: T, z: T) -> bool {
			if x == y && y == z {true}
			else {false}
		}
	```
- Quels sont les deux erreurs syntaxiques dans le code suivant ?
  ```rust
	enum Option(T) {	// <T>
		Some<T>,	// (T)
		None
	}
	```
- Maintenant que vous avez vu la généricité, vous avez vu une des raisons pour laquelle Rust autorise plusieurs bloc `impl`  pour une même déclaration de type. Quel est l'exemple du chapitre ?  
Utiliser les traits liés pour conditionner l'implémentation des méthodes : `impl<T> Paire<T> {}` et `impl<T: Display + PartialOrd> Paire<T> {}`.
- Qu'est-ce que la monomorphisation ? Quel est la différence entre le code avant monomorphisation et après monomorphisation ?  
????
- Définir un trait `Parallelogramme` avec trois méthodes `largeur`, `longueur`, `angle` (en degrée). Définir ensuite trois structures `Carre`, `Rectangle` et `ParallelogrammeGeneral` ayant respectivement un champ, deux champs et trois champs. Définir ensuite une implémentation du trait `Parallelogramme` pour chacune des trois structures. Toutes les nombres seront des `i32`.  
	```rust 
		pub trait Parallelogramme {
			fn largeur(&self) -> i32;
			fn hauteur(&self) -> i32;
			fn angle(&self) -> i32;
		}

		pub struct Carre {
			pub largeur: i32,
		}
		impl Parallelogramme for Carre {
			fn largeur(&self) -> i32 {
				self.largeur
			}
			fn hauteur(&self) -> i32 {
				self.largeur
			}
			fn angle(&self) -> i32 {
				90
			}
		}

		pub struct Rectangle {
			pub largeur: i32,
			pub hauteur: i32,
		}
		impl Parallelogramme for Rectangle {
			fn largeur(&self) -> i32 {
				self.largeur
			}
			fn hauteur(&self) -> i32 {
				self.hauteur
			}
			fn angle(&self) -> i32 {
				90
			}
		}

		pub struct ParallelogrammeGeneral {
			pub largeur: i32,
			pub hauteur: i32,
			pub angle: i32,
		}
		impl Parallelogramme for ParallelogrammeGeneral {
			fn largeur(&self) -> i32 {
				self.largeur
			}
			fn hauteur(&self) -> i32 {
				self.hauteur
			}
			fn angle(&self) -> i32 {
				self.angle
			}
		}
	```
- Vrai ou faux: "Nous ne pouvons implémenter un trait sur un type qu'à condition qu'au moins le trait ou le type soit défini localement dans notre module."  
Vrai.
- Supposons que l'on soit en train de programmer un projet dans un unique fichier `main.rs`. On sait que la bibliothèque standard définie le trait `std::cmp::PartialOrd` et le type `std::collections::HashMap`. Dans le fichier `main.rs`, nous avons défini un trait `MyPersonalTrait` et une structure `MyPersonalType`. Lesquelles de ces phrases sont vraies:
	- On peut implémenter le trait `std::cmp::PartialOrd` pour `HashMap`  
	Faux.
	- On peut implémenter le trait `std::cmp::PartialOrd` pour `MyPersonalType`  
	Vrai.
	- On peut implémenter le trait `MyPersonalTrait` pour `HashMap`  
	Vrai.
	- On peut implémenter le trait `MyPersonalTrait` pour `MyPersonalType`  
	Vrai.
- Vrai ou faux: "Si un trait contient 3 méthodes, alors une implémentation de ce trait doit toujours définir les 3 méthodes."  
Faux.
- Vrai ou faux: "La syntaxe `impl I` dans un type de paramètre de fonction n'est qu'un sucre syntaxique; on peut toujours réécrire un programme utilisant cette syntaxe en un autre ne l'utilisant pas."  
Vrai : on peut mettre `<I: Trait>` et utiliser le type I directement pour le type du paramètre.
- Vrai ou faux: "La syntaxe `impl I` dans le type de retour d'une fonction n'est qu'un sucre syntaxique; on peut toujours réécrire un programme utilisant cette syntaxe en un autre ne l'utilisant pas."  
Vrai : on peut mettre `<I: Trait>` et utiliser le type I directement pour le type de retour.
- Vrai ou faux: "Les signatures `fn f<T: I>(x: &T, y: &T);` et `fn f(x: &impl I, y: &impl I);` sont équivalentes."  
Vrai.
- Écrire la signature `fn f<T: I>(x: &T, y: &T);` en utilisant le mot clé `where`.  
	```rust
		fn f<T>(x: &T, y: &T)
		where
			T: I,
		{}
	```
- Écrire un code minimal, sans signification particulière, contenant une _implémentation générale_ d'un trait pour tout type présent et futur.
	```rust
		impl<T: Display> ToString for T {} // Tout type qui implémente Display, implémente aussi ToString
	```
- Est-il possible de déclarer une variable sans l'initialisée en Rust ?  
Oui, sauf pour les variables constantes qui doivents être ocnnu avant la compilation.
- Vrai ou faux: "Le vérificateur d'emprunt vérifie que les références vers une donnée durent toujours plus longtemps que la donnée elle-même."  
Vrai.
- Écrire une fonction de signature `fn correct_str<'a,'b>(x: &'a str, y: &'b str) -> Option<&'a str>` qui, en abusant un peu du langage, "ne retourne `x` que s'il est égale à `y`".
	```rust
		fn correct_str<'a,'b>(x: &'a str, y: &'b str) -> Option<&'a str> {
			if x == y {Some(x)}
			else {None}
		}
	```
- Quelles sont les trois règles d'élision de durée de vie indiquant quand est-ce que nous pouvons omettre des durées de vie et savoir que le compilateur les déduira automatiquement ?  
	1. Chaque paramètre est une référence a sa propre durée de vie.
	2. Si il y a exactement un seul paramètre de durée de vie d'entrée, cette durée de vie est assignée à tous les paramètres de durée de vie des sorties.
	3. Lorsque nous avons plusieurs paramètres de durée de vie, mais qu'un d'entre eux est &self ou &mut self parce que c'est une méthode, la durée de vie de self sera associée à tous les paramètres de durée de vie des sorties.
- Créer un trait générique `Correct` avec une méthode `correct` similaire à la fonction précédente et l'implémenter pour tout les types implémentant `PartialEq`. Utiliser au maximum l'élision de durée de vie.
	```rust
		pub trait Correct {
			fn correct<'a,'b>(x: &'a str, y: &'b str) -> Option<&'a str>;
		}
		impl<T: PartialEq> Correct for T{
			fn correct<'a,'b>(x: &'a str, y: &'b str) -> Option<&'a str>{
				if x == y {Some(x)}
				else {None}
			}
		}
	```
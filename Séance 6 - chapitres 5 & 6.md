# Chapitre 5

- Les structures sont similaires à une famille de types vue au chapitre 3, laquelle ?  
		Les tuples.
- Quelle est la différence entre cette famille de types du chapitre 3 et les structures ?  
		Les structures sont plus pertinentes pour grouper des données (chaque élement possède un nom) et peuvents avoirs des méthodes associées.
- Comment appelle-t-on les différentes parties qui composent une structure ?  
		On les appelle les élements de la struct.

- Deviner si le code suivant compile ou non (en ignorant les warnings):
  ```rust
	struct A { n: i32, m: f64 }
	fn f (x: A) { println!("{} {}", x.n, x.m); }
	
	struct B { n: i32, m: f64 }
	fn main() {
	  let x = B { n: 0, m: 0.0 };
	  println!("{} {}", x.n, x.m);
	  f(x);
	}
	```
	Non, il ne compile pas car la fonction f prend un parametre de type A, alors que x est défini de type B.
- Vrai, faux ou autre ? "Lorsqu'on instancie une structure, il faut donner les champs dans le même ordre que lors de la déclaration de la structure."  
		Autre, dans les struct classique, l'ordre n'est pas important. Cependant dans les structure tuple où on n'indique pas le nom, il est nécessaire de respecter l'ordre.
- Vrai, faux ou autre ? "Il est possible de ne pas donner de nom au champs des structures Rust."  
		Autre, il faut donner le nom classique, mais ce n'est pas nécessaire dans les structure tuple.
- Vrai, faux ou autre ? "Dans le code suivant, les deux instances `x` et `y` des structures unités `X` et `Y` sont égales, car les instances de structures unités sont toutes égales."
  	```rust
	struct X;
	struct Y;
	fn main() {
		let x = X;
		let y = Y;
	}
	``` 
	Vrai.
- Déclarer une structure décrivant un livre par son titre, sa description et son nombre de chapitre.
		```rust
		struct livre{
    		titre: String,
    		description: String,
    		nbr_page: i32,
		}
		```
- Donner l'*expression* (et uniquement elle sans rien autour) créant une instance de votre structure pour le Rust Book.
	```rust
	let rust_book = livre{
        titre: String::from("Rust Book"),
        description: String::from("par Steve Klabnik et Carol Nichols, avec la participation de la Communauté Rust."),
        nbr_page: 675,
    };
	```
- Comment indiquer que le champ description de votre structure est mutable mais pas le titre ni le nombre de chapitre ?  
		Pour qu'une élement d'une structure soit mutable en Rust, toute la structure doit être mutable donc : ``let mut rust_book = livre{...};``
- Donner le code d'une fonction `creer_livre` qui créer un livre avec un titre et un nombre de chapitre reçu en paramètre et retourne ce livre avec une description vide. Donner deux versions de votre code: l'une sans raccourci d'initialisation de champ et l'autre avec.
	```rust
		fn creer_livre(titre: String, nbr_page: i32) -> livre {
   			livre{
       			titre: titre,
        		description: String::from(""),
        		nbr_page: nbr_page,
    		}
		}
	```
	```rust
		fn creer_livre(titre: String, nbr_page: i32) -> livre {
   			livre{
       			titre,
        		description: String::from(""),
        		nbr_page,
    		}
		}
	```
- En combinant la syntaxe de mise à jour de structure et un raccourci d'initialisation de champ, créer une fonction `nouvelle_description` qui reçoit un livre et une description et retourne un livre identique à celui en premier paramètre hormis pour sa description est celle reçue en second paramètre. **⚠ Ne pas utiliser de référence ! ⚠** 
	```rust
		fn nouvelle_description(l: livre, description: String) -> livre {
			livre{
				description,
				..l
			}
		}
	```
- Écrire une fonction `main` qui instance un livre `l1` via la fonction `creer_livre`, demande à l'utilisateur une description que l'on va stocker dans une variable `description_utilisateur` et instancie un autre livre `l2` via la fonction `nouvelle_description` appelée avec `l1` et `description_utilisateur`. Votre fonction `main` doit afficher le contenu de toutes les variables **encore en vigueur** juste avant de se terminer, en utilisant la macro `dbg!`.
	```rust
		fn main() {
			let l1 = creer_livre(String::from("Rust Book"), 675);
			let mut description_utilisateur = String::new();
			println!("Tapez une description :");
			io::stdin()
				.read_line(&mut description_utilisateur)
				.expect("Erreur lors de la lecture de la description.");
			let description_utilisateur = description_utilisateur.trim().to_string();
			let l2 = nouvelle_description(l1, description_utilisateur);
			dbg!(l2.titre, l2.description, l2.nbr_page);
		}
	```
- En utilisant la méthode clone vue au chapitre 3, écrire une fonction `dupliquer_livre` qui reçoit une référence vers un livre et retourne un nouveau livre avec le même titre, la même description et le même nombre de chapitre.
	```rust
		fn dupliquer_livre(l: &livre) -> livre {
			livre{
				titre: l.titre.clone(),
				description: l.description.clone(),
				nbr_page: l.nbr_page.clone(),
			}
		}
	```
- Écrire une nouvelle version de `nouvelle_description` appelée `changer_description` qui reçoit en paramètre une *référence mutable* vers un livre ainsi qu'une description et modifie le champ description du livre pour y mettre la nouvelle description.
	```rust
	fn changer_description(l: &mut livre, d: String){
		l.description = d;
	}
	```
- On souhaiterait éviter de cloner inutilement des chaînes de caractères qui vont en réalité rester identiques. Le type `&str` permet justement à plusieurs variable de pointé vers la même zone mémoire de chaîne de caractère, mais pas le type `String`. Quelle fonctionnalité de Rust faudrait-il utiliser pour remplacer les `String` de votre structure livre par des `&str` ?  
		On utilise les réferences.
- Remanier votre code de sorte à ce que `creer_livre`, `nouvelle_description` et `changer_description` soient des fonctions associées à votre structure. Mettre à jour votre fonction `main` en conséquence et utiliser la syntaxe d'appel de méthode lorsque c'est possible.
	```rust 
		struct livre{
			titre: String,
			description: String,
			nbr_page: i32,
		}
		impl livre{
			fn creer_livre(titre: String, nbr_page: i32) -> livre {
				livre{
					titre,
					description: String::from(""),
					nbr_page,
				}
			}
			fn nouvelle_description(self, description: String) -> livre {
				livre{
					description,
					..self
				}
			}
			fn changer_description(&mut self, d: String){
				self.description = d;
			}
		}
	```
- Donner un exemple de votre nouveau `main` où _référencement et déréférencement automatiques_ de Rust lors rend l'appel de méthodes plus simple.
	```rust
		fn main() {
			let mut l1 = livre::creer_livre(String::from("Rust Book"), 675);
			let mut description_utilisateur = String::new();
			println!("Tapez une description :");
			io::stdin()
				.read_line(&mut description_utilisateur)
				.expect("Erreur lors de la lecture de la description.");
			let description_utilisateur = description_utilisateur.trim().to_string();
			l1.changer_description(description_utilisateur);
			dbg!(l1.titre, l1.description, l1.nbr_page);
		}
	```
- Qu'est-ce qu'un bloc `impl` ? Est-il possible d'en avoir plusieurs pour une seule structure ?  
		Un bloc `impl` contient toutes les fonctions liées à la structure. Oui, c'est possible d'avoir plusieurs bloc pour une seule structure mais c'est inutile.
- La notation `&self` en premier paramètre d'un déclaration de méthode est un raccourci. Quelle est la forme complète ?  
		Sa forme complète est `struc: &Struct`.
- Vrai ou faux ? "Comme les méthodes et les champs d'une structure s'invoquent tous les deux avec la notation pointé `x.nom`, une méthode ne peut pas porter le même nom d'un champ."  
		Faux, c'est possible.
- Donner un exemple d'attribut externe.  
		``fn fonction(&self, autre: &Struct)``

# Chapitre 6

- Définir une énumération permettant de décrire une couleur qui peut soit être en RGB ou en CMYK, et faire une fonction `main` de teste qui les instancie et affiche une instance de chaque variante en utilisant `dbg!`.  
	```rust
	enum Couleur {
		RGB,
		CMYK,
	}
	fn main() {
		let couleur_rgb = Couleur::RGB;
		let couleur_cmyk = Couleur::CMYK;
		dbg!(&couleur_rgb);
		dbg!(&couleur_cmyk);
	}
	```
- Définir une structure permettant de décrire un carte par sa "couleur" (qui est une énumération dont les variantes sont cœur, trèfle, carreau et pique) et sa "valeur" (qui est une énumération dans la première variante est muni d'un `u8` précisant la valeur en 1 et 10 et trois variantes supplémentaires correspondent à valet, dame et roi).  
	```rust
	enum Couleur {
		Coeur,
		Trefle,
		Carreau,
		Pique,
	}
	enum Valeur {
		Numero(u8),
		Valet,
		Dame,
		Roi,
	}
	struct Carte {
		couleur: Couleur,
		valeur: Valeur,
	}
	fn main() {
		let carte1 = Carte {
			couleur: Couleur::Coeur,
			valeur: Valeur::Numero(10),
		};
		let carte2 = Carte {
			couleur: Couleur::Pique,
			valeur: Valeur::Dame,
		};
		dbg!(&carte1);
		dbg!(&carte2);
	}
	```
- Faire un programme qui instancie toutes les cartes possibles et les affiche avec `dbg!`.
	```rust
	fn main() {
		let mut cartes: Vec<Carte> = Vec::new();
		for couleur in &[Couleur::Coeur, Couleur::Trefle, Couleur::Carreau, Couleur::Pique] {
			for valeur in 1..=10 {
				cartes.push(Carte {
					couleur: couleur.clone(),
					valeur: Valeur::Numero(valeur),
				});
			}
		}
		for couleur in &[Couleur::Coeur, Couleur::Trefle, Couleur::Carreau, Couleur::Pique] {
			cartes.push(Carte {
				couleur: couleur.clone(),
				valeur: Valeur::Valet,
			});
			cartes.push(Carte {
				couleur: couleur.clone(),
				valeur: Valeur::Dame,
			});
			cartes.push(Carte {
				couleur: couleur.clone(),
				valeur: Valeur::Roi,
			});
		}
	}

	```
- Vrai ou faux ? "Dans un langage utilisé le concept de valeur nulle, n'importe quelle variable peut potentiellement contenir null et c'est au programmeur de savoir si cette possibilité est effectivement ou non, ce qui pose un problème si le programmeur pense que ce n'est pas possible alors qu'en fait la valeur nulle est possible".  
		Vrai.
- Vrai ou faux ? "En Rust, une valeur pouvant être invalide ou non-disponible à pour type `Option<T>` alors qu'une valeur qui est toujours valide a pour type `T` directement, donc le programmeur ne peut pas se tromper et doit travailler différent dans un cas et dans l'autre."  
		Vrai.
- Donner le code d'une fonction `seulement_positif` qui reçoit une valeur `i32` et retourne un `Option<i32>` qui est `None` si la valeur est strictement négative, et `Some(v)` sinon.
	```rust
	fn seulement_positif(valeur: i32) -> Option<i32> {
		if valeur < 0 {
			None
		} else {
			Some(valeur)
		}
	}
	```
- En utilisant `match`, faire une fonction `valeur_non_atout` qui reçoit une carte (voir question précédente) et retourne sa valeur à la belote (https://fr.wikipedia.org/wiki/Belote#Valeur_des_cartes) en supposant que les cartes de couleur cœur sont atout et les autres couleurs non.
	```rust
	fn valeur_non_atout(carte: &Carte) -> Option<u8> {
		match &carte.valeur {
			Valeur::Numero(v) => Some(v),
			Valeu::As => Some(11),
			Valeur::Valet => Some(2),
			Valeur::Dame => Some(3),
			Valeur::Roi => Some(4),
		}
	}
	```
- Faire une version avec `match` et une version avec `if let` d'une fonction recevant deux `Option<i32>` et retournant leur somme quand c'est possible et `None` sinon.
	```rust
	fn somme_match(a: Option<i32>, b: Option<i32>) -> Option<i32> {
		match (a, b) {
			(Some(val1), Some(val2)) => Some(val1 + val2),
			_ => None,
		}
	}
	```
	```rust
	fn somme_if_let(a: Option<i32>, b: Option<i32>) -> Option<i32> {
		if let (Some(val1), Some(val2)) = (a, b) {
			Some(val1 + val2)
		} else {
			None
		}
	}

	```
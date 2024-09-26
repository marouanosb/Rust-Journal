- Voici une question pour vous montrer le format d'une réponse:
		Voici une réponse correctement indentée pour être replier avec la question.
		Merci d'ajouter vos réponses aux questions ci-dessous en respectant ce format.
		Répondez avec concision, mais avec le niveau de détail que vous donneriez à l'oral.
- Selon la page d'introduction du chapitre, combien de concepts y sont abordés ?
		Il aborde 5 concepts : variables, les types de base, les fonctions, les commentaires et les structures de contrôle.
- Qu'est-ce qu'un _mot clé_ ?
		C'est un mot (chaine de caractères) réservé par le langage pour usage exlusif, pouvant avoir une fonctionnalité précise.
- Tous les mots clés sont-ils associés à des fonctionnalités ?
		Non, quelques mots clé n'ont pas de fonctionnalités pour le moment.
- Où peut-on trouver la liste de tous les mots clés ?
		Dans l'[Annexe A](https://jimskapt.github.io/rust-book-fr/appendix-01-keywords.html) du Rust Book.
- Vrai, faux, ou autres ? "Une variable correspond à toujours une "mémoire" pouvant prendre différentes valeurs durant une seule et même exécution."
		Autres, une variable en Rust est par défaut immuable et donc ne peux pas changer, cependant on peut ajouter le mot-clié ``mut`` pour qu'elle puisse prendre d'autres valeurs.
- Comment déclarer une variable correspond à une "mémoire" pouvant prendre différentes valeurs durant une seule et même exécution ?
		``let mut nom_variable;``.
- Vrai, faux, ou autres ? "Si un variable ne prends qu'une seule valeur au cours de l'exécution d'un programme, alors il est toujours possible de la déclarer comme une constante."
		Vrai.
- Vrai, faux, ou autres ? "Comme en Java, deux variables Rust différentes ont forcément des noms différents au sein d'un seul et même bloc de portée."
		Faux, on peut avoir deux variables du même nom dans un même bloc, et la dernière masquera la précedente valeur.
- Vrai, faux, ou autres ? "Au sein d'un bloc de portée, un _nom_ de variable correspond à un unique et même type tout au long du bloc de portée."
		Faux, car si on le masque en déclarant un nouvelle variable avec le meme _nom_ on peut le déclarer avec un type différent. C'est quand on utilise ``mut`` qu'on ne peux pas changer son type.
- Donner la liste des principaux types scalaires de Rust.
		Les entiers, les floats, les booléens et les caractères.
- Combien y a-t-il de types de nombres entiers en Rust ?
		Il y a 6 types d'entiers : sur 8, 16, 32, 64 et 128 bits, et archi (selon l'architecture utilisée).
- Combien de types de nombres entiers ont un nombre de bit indépendant de l'architecture vers laquelle le programme est compilé ?
		Il y a 5 types : sur 8, 16, 32, 64 et 128bits, qui sont assigné à leurs nombre de bits associés indépendamment de l'architecture utilisée.
- Quelle est le type de nombres entiers par défaut ?
		Par défaut, Rust choisir le type d'entier sur 32bits.
- Quelles types de nombres entiers utilise-t-on pour indexer un tableau en Rust ?
		Pour les tableaux, Rust utilise le type d'entiers archi.
- Quelle est la représentation binaire machine de la valeur -3 de type i16 ?
		La valeur -3 en binaire i16 s'écrit : ``1111 1111 1111 1101``.
- Donner le littéral correspond à -3 de type i16.
		``let x: i16 = -3;``
- Comment écrire le littéral correspond à "cent millions" en Rust de sorte à rendre facilement lisible que le nombre de zéro est le bon ?
		``let cent_millions = 100_000_000;``
- Vrai, faux, ou autres ? "En Rust, si on incrémente une variable de type u8 dans une boucle infini, alors toutes les valeurs de 0 à 255 s'affiche en boucle et le programme ne s'arrête jamais."
		Faux, en mode debug, Rust vérifie les cas de dépassement d'entier et panique le programme en le terminant. Et en mode release, seulement les valeur qui dépasse la taille de l'entier vont reboucler depuis la valeur 0, ce qui change le résultat attendu.
- Donner la liste des types à virgule flottante.
		Les types à virgule flottante : f32 et f64.
- Vrai, faux, ou autres ? "Rust est un langage bas niveau, donc une variable à virgule flottante a une représentation différente en fonction de l'architecture vers laquelle on compile notre programme."
		Faux, les nombres float en Rust sont représentés selon la norme IEEE-754.
- Vrai, faux, ou autres ? "Le type flottant par défaut a une taille de 32 bits."
		Faux, en Rust le type par défaut des float est f64 (de taille 64bits).
- Où peut-on consulter la liste de tous les opérateurs numériques ?
		Dans l'[Annexe B](https://jimskapt.github.io/rust-book-fr/appendix-02-operators.html) du Rust Book.
- Vrai, faux, ou autres ? "Rust profite d'une panoplie de près de 200 opérateurs numériques."
		Faux.
- Vrai, faux, ou autres ? "En Rust, un test qui échoue (comme 10 > 30) renvoie 0 alors qu'un test qui réussi comme (10 < 30) renvoie 1."
		Faux, une opération booléen en Rust renvoit ``true``(vrai) ou ``false``(faux). 
- Vrai, faux, ou autres ? "Le type char représente 8 octets et représente un caractère ASCII."
		Faux, le type char prend 4octets en mémoire et représent une valeur Unicode.
- Vrai, faux, ou autres ? "Il est possible d'ajouter des éléments dans un tableau Rust, modifiant ainsi sa taille, au cours de l'exécution d'un programme."
		Faux, on ne peux pas modifier la taille d'un tableau, mais celle d'une vecteur.
- Si on a écrit un programme avec une variable x de type `(i32, i32, i32)`, décrire informellement comment le réécrire pour que son type soit maintenant `[i32; 3]` ? Le programme résultat est-il globalement plus court ? plus long ? de même longueur ?
		``let x: [i32; 3] = [1, 2, 3];``
		Le programe est un peu plus court vu qu'on repète pas le type.
- Si on a écrit un programme avec une variable x de type `[i32; 3]`, décrire informellement comment le réécrire pour que son type soit maintenant  `(i32, i32, i32)` ? Le programme résultat est-il globalement plus court ? plus long ? de même longueur ?
		``let x: (i32, i32, i32) = (1, 2, 3);``
		Le programme est legèrement plus long vu qu'on répéte le type de tout les élementsdu tuple.
- Que se passe-t-il en Rust si on tente d'accéder à la case 10 d'un tableau de taille 5 ? En quoi cela diffère de ce qui se passe en C ?
		On aura une erreur 'index out of bound'. Contrairement en C, où il peux accéder à une mémoire non alloué pouvant avoir un comportement non securisé sur les zones mémoires.
- Existe-t-il d'autres types Rust fonctionnant comme les tableaux ?
		Oui, les vecteurs qui sont fourni par la bibliothèque standard et qui est plus flexible que les tableaux.
- Vrai, faux, ou autres ? "Comme en Java, Rust a besoin d'allouer de la mémoire et d'utiliser des pointeurs en interne pour faire fonctionner ces types composés."
		Vrai.
- Proposer une expression à mettre à la place des points d'intérrogation afin que le programme suivant compile et affiche "Yes" à l'exécution.
  ```rust
	fn main() {
	    let x = (1, 0, [(true,), (false,)]);
		if x.2[x.1].0 {
			println!("Yes");
		} else {
			println!("No");
		}
	}
	```
- Transformer le code précédent en une fonction recevant en paramètre la valeur de x.
  ```rust
	fn yes_no(x: (i32, usize, [(bool,); 2])){
		if x.2[x.1].0 {
			println!("Yes");
		} else {
			println!("No");
		}
	}
	```
- Modifier la fonction pour qu'elle prenne un paramètre la valeur de x et retourne un booléen au lieu d'afficher un message. Faites le bien "à la Rust", en suivant le style indiqué dans le chapitre.
    ```rust
	fn yes_no(x: (i32, usize, [(bool,); 2])) -> bool {
		x.2[x.1].0
	}
	```
- Quelle convention utilise-t-on en Rust pour nommer les variables et les fonctions ?
		Rust utilise la convention snake case : toutes les lettres en minuscule et on utilise des tirets bas pour séparer les mots.
- Quel est normalement la différence technique entre "paramètre" et "argument" ?
		Le parametre est utilisé dans la fonction, tandis que l'argument est indique la valeur passée dans l'appel de la fonction.
- Le bout de code `let x = 10` est une expression ou une instruction ?
		C'est une insctruction.
- Le bout de code `let x = 10` contient il une expression ?
		Non.
- Vrai, faux, ou autres ? "Lorsqu'on déclare une variable, il est optionnel d'indiquer le type."
		Vrai, dans la plus part des cas Rust peut déduire son type selon les operations effectués avec cette variable. Mais des fois où le résultat attendu d'une expression n'est pas de type fixe, on doit l'indiquer.
- Vrai, faux, ou autres ? "Lorsqu'on déclare un paramètre, il est optionnel d'indiquer le type."
		Faux, c'est exigé par Rust de définir le type des paramètres.
- Vrai, faux, ou autres ? "En Rust, il n'existe qu'une seule façon de faire des commentaires."
		Vrai, en utilisant //.
- Dans le code suivant, que faut-il mettre à la place des parenthèses pour que le code de la fonction compile (on ignorera les warnings):
	```rust
	fn blabla(x: i32) -> i32 {
		x + x;
	}
	```
- Les `if/else` sont ils des instructions ou des expressions ?
		Ce sont des expressions.
- Les `if` sans `else` sont ils des instructions ou des expressions ?
		Ce sont des expressions.
- Remanier le code suivant afin de n'avoir qu'un seul appel à `println!` et aucune variable supplémentaire.
    ```rust
	fn main() {
	    let x = (1, 0, [(true,), (false,)]);
    	println!("{}", if x.2[x.1].0 { "Yes "} else {"No"});
	}
	```
- A quoi servent les étiquettes de boucle ?
		Ils servent d'abord à préciser sur quelle boucle on applique les mot-cliés ``break`` et ``continue`` en cas de boucles imbriquées.
- Une boucle `loop` est une expression. Quels types peuvent être retournés par un loop ?
		On peut retourner n'importe quel types.
- Une boucle `while` est une expression. Quels types peuvent être retournés par un while ?
		Contrairement à la boucle 'loop', la boucle 'while' n'est pas conçue pour retourner des valeurs.
- Les boucles `for` de Rust ressemble au boucle `for` de quels languages que vous connaissez ?
		Elles ressembles aux boucles 'for' de Python qui ont une syntaxe similaire horsmi les '{ }'.
- Comme suggéré à la fin du chapitre, réaliser les programmes suivants:
	- Convertir des températures entre les degrés Fahrenheit et Celsius.
		```rust
		use std::io;

		fn convert_celsius_fahrenheit(x: f64) -> f64{
			(9.0/5.0)*x+32.0
		}
		fn convert_fahrenheit_celsius(x: f64) -> f64{
			(5.0/9.0)*(x-32.0)
		}

		fn main() {
			loop {
				println!("1: Celsius -> Fahrenheit.");
				println!("2: Fahrenheit -> Celsius.");
				println!("3: Quitter.");
				let mut choice = String::new();
				io::stdin()
					.read_line(&mut choice)
					.expect("Échec de la lecture de l'entrée utilisateur");
				let choice : u32 = match choice.trim().parse() {
					Ok(nombre) => nombre,
					Err(_) => continue,
				};
				if choice == 1 {
					println!("Tapez la temperature:");
					let mut degree = String::new();
					io::stdin()
						.read_line(&mut degree)
						.expect("Échec de la lecture de l'entrée utilisateur");
					let degree: f64 = match degree.trim().parse() {
						Ok(nombre) => nombre,
						Err(_) => continue,
					};
					println!("{}°C -> {}°F", degree, convert_celsius_fahrenheit(degree));
				} else if choice == 2 {
					println!("Tapez la temperature:");
					let mut degree = String::new();
					io::stdin()
						.read_line(&mut degree)
						.expect("Échec de la lecture de l'entrée utilisateur");
					let degree: f64 = match degree.trim().parse() {
						Ok(nombre) => nombre,
						Err(_) => continue,
					};
					println!("{}°F -> {}°C", degree, convert_fahrenheit_celsius(degree));
				}
			}
		
		}

		```
	- Générer le _n_-ième nombre de Fibonacci.
		```rust
		use std::io;

		fn fibonacci(n: u32) -> u32 {
			if n == 0 {
				return 0;
			} else if n == 1 {
				return 1;
			}

			let mut a = 0;
			let mut b = 1;
			let mut fib = 0;
			let mut count = 2;

			while count <= n {
				fib = a + b;
				a = b;
				b = fib;
				count += 1;
			}

			fib
		}

		fn main() {
			println!("Entrez un nombre pour calculer le n-ième nombre de Fibonacci :");

			let mut input = String::new();
			io::stdin()
				.read_line(&mut input)
				.expect("Erreur lors de la lecture");

			let n: u32 = match input.trim().parse() {
				Ok(num) => num,
				Err(_) => {
					println!("Veuillez entrer un nombre valide.");
					return;
				}
			};

			let result = fibonacci(n);
			println!("Le {}-ième nombre de Fibonacci est : {}", n, result);
		}

		```
	- Afficher les paroles de la chanson de Noël _The Twelve Days of Christmas_ en profitant de l'aspect répétitif de la chanson (https://www.lyricsforchristmas.com/christmas-carols/the-twelve-days-of-christmas/).
		```rust
		fn main() {
			let gifts = [
				"a Partridge in a Pear Tree",
				"two Turtle Doves",
				"three French Hens",
				"four Calling Birds",
				"five Golden Rings",
				"six Geese a-Laying",
				"seven Swans a-Swimming",
				"eight Maids a-Milking",
				"nine Ladies Dancing",
				"ten Lords a-Leaping",
				"eleven Pipers Piping",
				"twelve Drummers Drumming",
			];

			let days = [
				"first", "second", "third", "fourth", "fifth", "sixth",
				"seventh", "eighth", "ninth", "tenth", "eleventh", "twelfth",
			];

			let mut day = 0;
			while day < 12 {
				println!(
					"On the {} day of Christmas, my true love sent to me:",
					days[day]
				);
				let mut gift = day;
				while gift >= 0 {
					if day != 0 && gift == 0 {
						print!("and ");
					}
					println!("{}", gifts[gift]);

					if gift == 0 {
						break;
					}
					gift -= 1;
				}
				day += 1;
			}
		}

		```
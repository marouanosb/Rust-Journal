- Quels sont les 4 thèmes abordés dans ce chapitre ?  
		La possession, l'emprunt, les slices et l'agence des données en mémoire.
- Quelles sont les deux approches traditionnelles de gestion de la mémoire ?  
		La pile et le tas.
- Est-il a priori rapide de se familiariser avec le concept de possession ?  
		Non, ca prend un peu de temps.
- Quelle structure de donnée est utilisé dans le chapitre pour exemplifier la possession ?  
		Le type String.
- Connaîssez-vous un autre langage qui demande la maitrise de la différence pile/tas ?  
		C++.
- (Hors Livre) En gros, quelles instructions assembleurs permettent de manipuler la pile, et comment la pile est-elle gérée ? et par quoi ? processeur/système d'exploitation/bibliothèque ?  
		Les instruction PUSH et POP permette d'empiler et dépiler. Le processeur gère donc cette pile en mettant à jour les registes contenant les pointeurs de la pile. Le système d'exploitation permet d'allouer les espaces mémoire. Les bibliothèques permettent la gestion de la manière dont la pile est utilisé dans le code.
- (Hors Livre) En gros, quelles instructions assembleurs permettent de manipuler le tas, et comment le tas est-il géré ? et par quoi ? processeur/système d'exploitation/bibliothèque ?  
		Il n'existe pas d'instructions assembley permettant de manipuler le tas, cepandant les langages de programmation propose des bibliothèques qui fournissent des fonctions permettant sa manipulation comme ``malloc`` et ``free`` en C. Le système d'exploitation gère donc l'allocation de ces espaces mémoires et de leur libération.
- (Hors Livre) Pourquoi il est mieux de consulter des données qui sont proches les unes des autres pour un processeur moderne ?  
		Les CPU modernes utilisent la mémoire cache le minimisant le temps d'accès à la mémoire. Si les données ne se trouve pas proche dans le cache, cela engendre un accès lent à la mémoire qui va générer un délai lors de l'exécution.
- Quel genre de données sont stockées sur la pile ?  
		Les données de taille connue et fixe.
- Quel est le but principale de la possession ?  
		Le but principale aide à minimiser les données en double sur le tas et leur libération, ainsi minimiser les temps d'accès à la mémoire.
- Quand est-ce qu'une valeur est supprimée ?  
		Elle est supprimé quand son propriétaire sort de la portée.
- Vrai, faux ou autre ? "Une variable est "en vigueur" de sa déclaration jusqu'à la fin de l'exécution de programme."  
		Faux, une variable est en vigeur jusqu'à la fin de sa portée.
- En terme de pile et de tas, quelle est la différence entre les types du chapitre 3 et le type String ? Pourquoi cette différence est-elle nécessaire ?  
		Les types précédents ont une taille représentable en nombre de bits connue et peuvent donc être stockées dans la pile. Le type String sont immuables et donc peuvent avoir une taille aléatoire.
- Donner une expression de type String.  
		``"String::from("Hello world!")``
- Les littéraux comme ", world" sont-ils de type String ?  
		Non, de type char.
- Vrai, faux ou autre ? "Les chaînes de caractères littérales et celles saisies par l'utilisateur sont stockés dans la même zone mémoire."  
		Non, les litéraux sont stockés dans la pile, et ceux par l'utilisateur dans le tas.
- Quelle fonction est automatiquement appelée lorsque qu'un String sort de sa portée ?  
		La fonction drop.
- Une valeur de type String nécessite de la mémoire: uniquement dans le tas, uniquement sur la pile, ou sur les deux ?  
		Le type String nécessite de la mémoire de pile pour les données internes (pointeur, capacité, taille) et sa valeur est mise dans le tas.
- Qu'est-ce qu'une "double libérations" (ou "double free")  et son rapport avec la sécurité informatique ?  
		C'est quand on libère deux fois la mémoire sur le tas, ce qui peut emmener à une perte de données non accessibles engendrant un mauvais résultat ou une erreur d'éxecution.
- Étant donnée la façon dont Rust gère la mémoire, pourquoi serait-il un problème que deux pointeurs possèdent la même mémoire dans la tas en même temps ?  
		Parceque dans le cas de la sortie de la portée, il se peut que les deux pointeurs se libèrent en même temps et on aura donc une double libèration, pouvant corrompre la mémoire. 
- Vrai, faux ou autre ? "Une instruction telle que `let y = x;` peut parfois représentée une copie profonde couteuse."  
		Autre, dans le cas où Rust fait un déplacement, déplacant x dans y. Il considère que l'ancienne valeur n'est plus en vigeur et l'affect à la nouvelle variable, ce qui n'est pas couteux. Mais lorsqu'il fait une copie profonde cela handicap la performance.
- Quelle est la différence entre un déplacement et une copie superficielle ?  
		Une copie superficielle consiste à copier le pointeur, tandis que le déplacement considère que l'ancienne valeur n'est plus en vigeur et déplace cette valeur dans la nouvelle variable.
- Vrai, faux ou autre ? "Si on souhaite qu'un type fasse une copie il *suffit simplement* d'annoter ce type avec le trait Copy."  
		Faux, le trait Copy concerne les types alloués dans la pile de valeur connue, et pour les types sur le tas comme les String, il faut utiliser le trait Clone pour avoir une copie profonde.
- Vrai, faux ou autre ? "Tout ce qui est alloué durant l'exécution d'une fonction est désallouée à la fin de l'exécution de la fonction."  
		Autre, à moins que la possession de la donnée à été accordée à une autre variable en retour.
---
- Vrai, faux ou autre ? "Pour des raisons de sécurité et de cohérence, une fonction ne peut désallouer que ce qu'elle a alloué."  
		Vrai.
- Vrai, faux ou autre ? "Les fonctions n'introduisent aucunes subtilités sur la gestion de la possession: pour comprendre la possession il suffit comprendre ce qui se passe avec des variables."  
		Faux, elles proposent un moyen transférer la possession avec des références.
- Dans le même style que l'encart 4-5, écrire une fonction `meme_longueur` qui reçoit deux String, et retourne un booléen indiquant s'ils ont la même taille, ainsi que les deux String pour rendre leur propriété. Écrire une fonction main similaire à celle de l'encart pour tester votre fonction.
  ```rust
	fn main() {
		let s1 = String::from("hello");
		let s2 = String::from("world");

		let (a, b, c) = comparer_taille(s1,s2);

		if c {
			println!("Les tailles sont égales.");
		} else {
			println!("Les tailles sont différentes.")
		}
	}
	fn comparer_taille(s1: String, s2: String) -> (String, String, bool) {
		let taille1 = s1.len();
		let taille2 = s2.len();

		(s1, s2, (taille1 == taille2))
	}
	```
- Réécrire votre code précédent afin de profiter des références Rust.
  ```rust
	fn main() {
		let s1 = String::from("hello");
		let s2 = String::from("world");

		let (a, b, c) = comparer_taille(&s1,&s2);

		if c {
			println!("Les tailles sont égales.");
		} else {
			println!("Les tailles sont différentes.")
		}
	}
	
	fn comparer_taille(s1: &String, s2: &String) -> (&String, &String, bool) {
		let taille1 = s1.len();
		let taille2 = s2.len();

		(s1, s2, (taille1 == taille2))
	}
	```

	Cependant, on a une erreur  
	``expected named lifetime parameter``  
	qu'on a pas vu pour l'instant.
- Vrai, faux ou autre ? "Lorsque d'une fonction à une référence vers un String, cette fonction *possède* ce String, et par les règles de la possession, cette String est désalloué à la fin de la fonction."  
		Faux, elle ne possède pas ce string, mais plutot elle référe à ce string. Il n'est donc pas désalloué.
- Vrai, faux ou autre ? "Lorsque d'une fonction à une référence vers un String peut également modifier le String".  
		Faux, elle ne peut pas le modifier car le passage par réference est immuable par défaut.
- Votre fonction `meme_longueur` précédente (version avec référence) peut-elle être appelé avec deux références identique, i.e. `meme_longueur(&s, &s)` ?  
		Oui, c'est possible.
- Tentez d'écrire de mémoire les règles sur les emprunts.  
		On peut avoir soit une référence mutable ou immuable à la fois.  
		Les valeurs passées par référence sont restent en vigeur.
- (question volontairement flou) Donner différents exemples d'emprunts invalides et essayer d'imaginer, pour chacun d'eux, un contexte dans lequel cela provoquerait un bogue.  
		Si par exemple on emprunte immuablement une variable à une fonction, et qu'ensuite on l'emprunte mutablement, risque d'avoir un conflit.
- Quels soucis pourraient survenir si on choisi de faire une fonction `second_mot(&String) -> (usize,usize)` qui se contente de retourner la taille du premier et laisse le programmeur utiliser le String d'origine et cette taille lorsqu'il veut travailler avec le premier mot ?  
		La nouvelle taille peux dépasser la taille du String d'origine et donc ne coresspondera plus à la taille déja alloué dans le tas. Engendrant des erreurs d'execution.
- Y aurait-il une façon de résoudre ces soucis sans utiliser le concept de slice ? Quel compromis faut-il faire ?  
	Oui, en utilisant une nouvelle instance String qui va prendre la partie souhaitée. Cependant, donne une grande utilisation de la mémoire et baisse de performance.
- Si on a un variable `s` de type `String`, quel est le type de `&s` ? Vers quoi pointe le pointeur sous-jacent de `&s` ? quel est le type de `&s[..]` ?  Vers quoi pointe le pointeur sous-jacent de `&s[..]` ?  
		&s est de type &String, elle pointe vers l'emplacement mémoire de l'objet.  
		Le type &s[..] est &str, il pointe vers les données internes comme le premier élement, la taille du Sftring...
# CHAPITRE 7

- Quels sont les différentes fonctionnalités du système de module de Rust?
- Quelle est la différence entre une crate et un paquet?
- Quelle est la différence entre une crate de bibliothèque et une crate binaire?
- Dans quel répertoire peut-on ajouter d'autre crates binaires?
- Vrai ou Faux? On ne peux pas utiliser un nom dans notre crate qui est identique au nom d'un trait d'une crate externe.
- Qu'apporte les modules en Rust comme bénéfices?
- Vrai ou Faux? On ne peux pas définir un module imbriqué dans un autre.
- Vrai ou Faux? On peux définir des variables dans le crops d'un module.
- Donnez un exemple de module d'une université qui est composée de : Un amphi, qui a comme fonctionnalités d'assister à des cours ou à des conférences. Un salle, qui permet de exercer des td ou passer des examens. Salle des prof où il y a organisation de réunion.
- Quelle différence entre le chemin absolu et courant pour l'utilisation des crates?
- Ajoutez au code précedent une fonction `faire_cours()`publique qui permet d'avoir accès à la fonction pour assister au cours, en utilisant l'annotation de chemin absolu puis relatif.
- Modifiez le code afin de permettre à la fonction `faire_cours()` d'accéder à la fonction d'assister au cours dans Amphi.
- Créez un module `Cours`, qui a comme élement son titre qui sera publique et une durée de cours qui sera privé, ajoutez une fonction associé qui permet de créer un cours avec un titre donné et une durée de 3heures par défaut. Une autre fonction pour modifier la durée. (Faites attention à la portée)
- Dans le même module, ajoutez une énumeration `titre_cours` qui peut avoir comme valeur les differents intitulées des cours. Mettez à jour le code précedent pour prendre en charge le titre du cours selon cette énumeration. Puis donnez un exemple de fonction qui utilise ces modules.
- Modifiez la syntaxe de chemin de façon à utiliser le mot-clé `use` pour l'appel des fonctions du module.
- Divisez vos différents modules en différents fichiers.
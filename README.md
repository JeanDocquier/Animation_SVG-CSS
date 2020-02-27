# Animation_SVG-CSS
## Comment ça s'utilise ?
### 1. A propos des fichiers SVG 
Un fichier SVG (Scalable Vector Graphics) est un fichier vectoriel utilisé pour le web. 
### 2. Comment récupérer un fichier SVG sous forme de code HTML ?? 
Pour récupérer un fichier SVG au format HTML, il suffit d'exporter votre code sous format ".svg" avec Illustrator et de cliquer sur "Code SVG...". Vous aurez ainsi accès dans fichier texte, au code SVG de votre objet vectoriel.
### 3. Compisition du code SVG
Le code SVG se compose de plusieurs balises : 
1. <?xml> : Cette balise reprend des informations d'encodage, etc. 
2. <svg> :  Balise reprenant les informations générales de votre vecteur (nom du calque, position,...) ainsi que des attributs xmls faisant renvoyant à des pages w3c. 
3. <style> : Permet d'incorporer vos couleurs dans vos illustrations avec la propriété "fill". Propre aux svg. Les classes définies permettant de coloriser vos illustrations s'intitulent "st". Vous les retrouverez dans les balises dessinant vos formes. 
4. <g> : Balise regroupant les éléments que vous avez groupé dans votre fichier Illustrator
5. <polygon> : Balise indiquant que votre forme est un polygone (forme créé avec l'outil polygone d'Illustrator).
6. <path> : Balise indiquant que votre forme est un tracé que vous avez dessiné "vous-meme".

Vous remarquerez que vos balises <polygon> et <path> sont respectivement composés d'attributs "points" et "d". Ces attributs ont en valeur une longue série de chiffres. Il s'agit en fait des coordonnées vectorielles qui permettent à HTML de retracer vos formes. Il vaut donc mieux laisser ces valeurs tranquilles sous peine de voir votre illustation déformée. 
  
  
    

# Animation_SVG-CSS
## Comment ça s'utilise ?
### 1. A propos des fichiers SVG 
Un fichier SVG (Scalable Vector Graphics) est un fichier vectoriel utilisé pour le web. 
### 2. Comment récupérer un fichier SVG sous forme de code HTML ?? 
Pour récupérer un fichier SVG au format HTML, il suffit d'exporter votre code sous format ".svg" avec Illustrator et de cliquer sur "Code SVG...". Vous aurez ainsi accès dans fichier texte, au code SVG de votre objet vectoriel.
### 3. Compisition du code SVG
Le code SVG se compose de plusieurs balises : 
1. **<?xml>** : Cette balise reprend des informations d'encodage, etc. 
2. **<svg>** :  Balise reprenant les informations générales de votre vecteur (nom du calque, position,...) ainsi que des attributs xmls faisant renvoyant à des pages w3c. 
3. **<style>** : Permet d'incorporer vos couleurs dans vos illustrations avec la propriété "fill". Propre aux svg. Les classes définies permettant de coloriser vos illustrations s'intitulent "st". Vous les retrouverez dans les balises dessinant vos formes. 
4. **<g>** : Balise regroupant les éléments que vous avez groupé dans votre fichier Illustrator
5. **<polygon>** : Balise indiquant que votre forme est un polygone (forme créé avec l'outil polygone d'Illustrator).
6. **<path>** : Balise indiquant que votre forme est un tracé que vous avez dessiné "vous-meme".

Vous remarquerez que vos balises <polygon> et <path> sont respectivement composés d'attributs "points" et "d". Ces attributs ont en valeur une longue série de chiffres. Il s'agit en fait des coordonnées vectorielles qui permettent à HTML de retracer vos formes. Il vaut donc mieux laisser ces valeurs tranquilles sous peine de voir votre illustation déformée. 

### 4. Sélecteurs CSS du code SVG
Pour pouvoir animer un fichier SVG, le plus intéressant sera donc d'animer les balises composant le SVG. Il faudra ainsi cibler les balises <polygon> ou <path> en CSS. Pour repérer plus facilement les composants de votre SVG, il est recommandé de les nommer dans votre fichier Illustrator. Ainsi, vous pourrez les reconnaitre via les valeurs de leur attributs "id" respectifs. 
  
Vous pourrez dès lors cibler vos tracés et formes via les sélecteur CSS. Si, via un même sélecteur vous voulez cibler plusieurs éléments, il est également possible de rajouter des classes à vos tracés.

### 5. Animation du SVG avec @KeyFrames et :hover
Une fois vos sélecteurs couchés sur votre CSS, il vous suffit de les animer comme n'importe quel autre élément HTML ! 
Vous pouvez réaliser des animations lors d'un survol avec :hover, etc. 
Pour une animation "automatique", utilisez la baliser @KeyFrames. 

Vous pouvez réaliser des animations différentes pour chaque tracé de votre fichier vectoriel. 

Attention, si vous voulez changer la couleur de fond, il faut bien utiliser la propriété "fill" et non "background". 

### 6. Exemple (En SASS)
On réalise l'animation de changement de couleur de fond

        @keyframes changecolor {
           0%   {
             fill : #fcacac;
           }
           25%  {
             fill : #ac9ded;
           }
          75%  {
            fill : #befab9;
          }
         100% {
          fill : #fcacac;
          }
        }

On réalise l'animation de mouvement

        @keyframes movesvg { 
           0%   {
            transform: translateY(0);
            }
          50%  {
            transform: translateY(30px);
          }
          100% {
            transform: translateY(0);
          }
        }

On cible le fichier vectoriel et les tracés. ON applique ensuite les animations

        #jean_logo{ // On cible l'élément SVG et on lui applique l'annimation de mouvement avec 'animation: movesvg 2s infinite;' 
            width: 500px; // On défini la largeur du SVG à 500px
            animation: movesvg 2s infinite; 
             // On cible les tracés/polygon et on leur applique l'annimation de changement de couleurs avec des timings différents avec 'animation: changecolor 3s infinite; 
            polygon{
                fill : white;
                animation: changecolor 2s infinite; 
            }
           ' 
            path:nth-of-type(1){
                animation: changecolor 3s infinite; 
                fill : white;
            }
            path:nth-of-type(2){
                fill : white;
                animation: changecolor 4s infinite; 
        }

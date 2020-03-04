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

Code HTML 

    <div class="svg-wrapper">
           <h1>Animation SVG ::CSS</h1>

        <?xml version="1.0" encoding="utf-8"?>
        <!-- Generator: Adobe Illustrator 24.0.2, SVG Export Plug-In . SVG Version: 6.00 Build 0)  -->
        <svg version="1.1" id="jean_logo" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 1000 1000" style="enable-background:new 0 0 1000 1000;" xml:space="preserve">
            <style type="text/css">
                .st0 {
                    fill: #E73335;
                }

            </style>
            <g>
                <polygon class="st0" points="415.38,349.76 415.38,628.88 657.11,489.32 518.64,409.38 	" />
                <path class="st0" d="M48.57,696.72c65.28,148.73,201.96,259.18,366.45,287.84L48.57,696.72z" />
                <path class="st0" d="M499.75,6.9c-28.78,0-56.93,2.62-84.37,7.38v217.87c-25.6-14.75-51.19-29.52-76.94-44
		c-2.92-1.63-5.83-3.27-8.75-4.9V37.18C141.65,106.58,7.21,287.6,7.21,499.45c0,25.14,1.91,49.83,5.57,73.97l316.92,248.93v-26.47
		c0.59-0.33,1.22-0.59,1.8-0.94c9.5-5.15,18.94-10.41,28.32-15.77c18.59-10.47,37.06-21.16,55.57-31.78v237.22
		c27.44,4.76,55.59,7.38,84.37,7.38c271.59,0,492.55-220.96,492.55-492.55C992.31,227.86,771.35,6.9,499.75,6.9z M358.71,759.45
		c-7.02,4.18-14.05,8.35-21.07,12.53c-2.89,1.62-5.59,3.52-8.39,5.27l-0.45-572.21c0.3,0.18,0.6,0.36,0.9,0.54v-0.48
		c2.55,1.51,5.08,3.07,7.64,4.57c25.92,15.33,145.82,85.28,173.34,100.76c3.36,1.88,6.72,3.77,10.09,5.65L824.98,492
		C824.98,492,390.49,740.61,358.71,759.45z" />
            </g>
        </svg>


    </div>


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

        #jean_logo{ /* On cible l'élément SVG et on lui applique l'annimation de mouvement avec 'animation: movesvg 2s infinite;' */
            width: 500px; /* On défini la largeur du SVG à 500px */
            animation: movesvg 2s infinite; 
             /* On cible les tracés/polygon et on leur applique l'annimation de changement de couleurs avec des timings différents avec 'animation: changecolor 3s infinite; */
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


Exemple ici : https://jeandocquier.github.io/Animation_SVG-CSS/?fbclid=IwAR3aOx9xPlQXI_K9HAJLo9mTJ8zVJ1JiQC6AGzIB8FCW5dL3rHQhmX2gwwI

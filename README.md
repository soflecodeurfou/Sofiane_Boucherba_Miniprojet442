# Sofiane_Boucherba_Miniprojet442
Mini projet de 442, rapport et code


Mon mini-projet de 442 est un jeu de dames fonctionnant grâce à l'écran tactile sur la carte de ST. 
Il fonctionne grâce à FreeRTOS et utilise 2 tâches :

-il y a une tâche d'affichage, qui utilise une variable globale "damier" (qui est un tableau 11*11). Elle affiche la position des pièces (un nombre -1 correspond à une case blanche non utilisé, 0 à une case noire vide, et les nombres 1 à 4 aux pions et dames jaunes et bleus). Elle se lance en continue et modifie tout le temps le damier à partir de la variable globale mais on ne s'en rend pas compte : il n'y a pas donc pas besoin d'introduire d'Event. Elle permet aussi d'afficher la victoire des 2 joueurs si un camp ne comporte plus de pions et dames. On utilise pour cela un drapeau qui est baissé à chaque fois que la tache détecte un pion ou une dame : quand le drapeau n'est pas baissé, cela signifie alors que un des camps n'a plus de pièces et que l'autre a gagné. 

-il y a aussi une tache coups, permettant de gérer l'état du damier à partir des pressions du joueur sur l'écran tactile. Elle vérifie à chaque tour si une prise est possible et contraint donc le joueur à prendre tant qu'il n'existe plus de prises (comme dans un jeu de dames classiques). Les prises peuvent être vers l'avant et vers l'arrière. Les dames peuvent se déplacer seulement d'une case vers l'arrière.  Il y a quelque petits imperfections comme le fait que si on touche une pièce qui ne peut pas jouer, on reste bloqué car il n'y a pas de changement d'état à chaque nouvelle touche. Aussi, les dames ne sont pas détectés dans les prises et elles ne peuvent donc pas l'être. Le reste du jeu fonctionne bien.

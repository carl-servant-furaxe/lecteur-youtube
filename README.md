# Lecteur Youtube avec suivi Google Analytics
La configuration du  lecteur se fait seulement dans la partie de code PHP en haut.

**Ne rien modifier en bas de la partie configuration**

## Code Google Analytics
Mettre le code de tracking Google Analytics sous cette variable "$ga".
```
$ga = 'UA-130445059-XX';
```

## Valeurs par default
Au debut du code, ces valeurs sont celles utilisees par defaut si le lecteur ne trouve pas la video desiree.

```
$cta_image = '';
$cta_title = '';
$cta_url = '';
```

### Code destinee au "call-to-action" a la fin de la video
Si vous ajoutez des valeurs a ces variables, une image de prise d'action sera affichee par dessus la video a la fin de la lecture.

| Variable      | Description |
| :------------ | :---------- |
| $cta_image    | URL de l'image cliquable |
| $cta_title    | Nom du CTA qui sera utilise pour identifier dans Google Analytics |
| $cta_url      | URL de destination lors du clique |


## Valeurs pour chacune des videos
Une video est definie via la valeur "v=" dans un url.

```
ex. https://ici.radio-canada.ca/nom-du-mandat/youtube.php?v=LUSfN64cjgg
```

La valeur "v=" doit etre identique a celle du url Youtube. Voir l'exemple suivant:

```
Youtube: https://www.youtube.com/watch?v=LUSfN64cjgg

Lecteur: https://ici.radio-canada.ca/nom-du-mandat/youtube.php?v=LUSfN64cjgg
```


C'est dans la partie PHP definie par la "switch" que le code determine quelle video afficher.
Ici, c'est "LUSfN64cjgg" qui serait trouvee par le systeme.

```
$video_id = array_key_exists('v', $_GET) ? $_GET['v'] : '';
switch($video_id){
	case 'LUSfN64cjgg':
		$cta_image = '';
		$cta_url = '';
		$cta_title = '';
	break;
}
```

Les variables definies entre "case 'LUSfN64cjgg'" et "break" vont ecraser les valeurs par defaut que nous avons vu plus tot.

Ajouter autant de video que vous voulez en  utilisant le code suivant a l'interieur de la "switch".

```
	case 'LUSfN64cjgg':
		$cta_image = '';
		$cta_url = '';
		$cta_title = '';
	break;
```


Il est tres important de ne pas avoir 2 valeurs identiques dans le "case".
Sinon, la 2e sera prise en compte.

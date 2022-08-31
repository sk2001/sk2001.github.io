---
layout: post
title:  "What if?"
tags: if
---
### `NULL` proxy
Débutons par une assignation toute simple. La méthode `detect` accepte de zéro à un argument.
```PHP
public function detect(?string $type = null)
{
    if ($type === null) {
        $type = 'default';
    }

    // reste de la méthode 
}
```

```PHP
public function detect(?string $type = null)
{
    $type = $type ?? 'default';

    // reste de la méthode
}
```
Est-ce que c'est plus clair? Pas nécessairement. Une question plus valide serait se demande si cette condition ne devrait pas se trouver à un niveau plus haut, à l'appel de la méthode!

```PHP
public function detect(string $type = 'default')
{
    // reste de la méthode
}
```
En modifiant la signature de la méthode ainsi, il nous est possible d'avoir le même effet en restant simple.

### What about some `else`?
Il arrive des fois que nous voyons des `if/else` qui ressemble quelque peu à ça :
```PHP
public function detect(string $type = 'default')
{
    if ($type === 'default') {
        $valeur = 0;
    } else {
        $valeur = 1;
    }
    // some code
}
```
Il est possible d'assigner une valeur par défaut au lieu de dépendre du `else` dans des situations semblables.
```PHP
public function detect(string $type = 'default')
{
    $valeur = 1;
    if ($type === 'default') {
        $valeur = 0;
    }
    // some code
}
```
Certains cas sont impossibles à changer par contre, mais plusieurs peuvent être modifiés pour retourner un élément.
```PHP
public function detect(string $type = 'default')
{
    if ($type === 'default') {
        // some code
        return 0;
    }

    // some code
    return 1;
}
```
Oui, nous doublons le nombre de retours, mais nous retirons une complexité visuelle.

### no `if`
Dans certain cas, il nous est possible de se demander si l'utilisation d'un `if` est vraiment nécessaire.
```PHP
const TYPES = [
    'default' => 0,
    'autre' => 1,
];

public function detect(string $type = 'default')
{
    return self::TYPES[$type];
}
```
Certes, de cette façon la méthode `detect` peut lancer des exceptions. Tout dépend du "use case", il pourrait être préférable d'avoir une exception ou encore d'avoir une valeur par défaut. Si nous voulons avoir un défaut, il est possible de modifier la ligne de retour pour quelque chose de similaire.
```PHP
const DEFAULT_TYPE = 'default';
const TYPES = [
    'default' => 0,
    'autre' => 1,
];

public function detect(?string $type = null)
{
    return self::TYPES[$type] ?? self::TYPES[self::DEFAULT_TYPE];
}
```
Il est à noter que j'utilise des constantes dans mes exemples. Elles servent à faciliter les changements de valeur sans aller les modifier dans la logique du traitement. Si nous voulons changer le type par défaut, nous le modifions qu'à un seul endroit.
Pour ceux qui ont remarqué, la signature de la méthode est revenue celle du départ. L'utilisation de la constante `DEFAULT_TYPE` signale le type par défaut désiré.


#### Note
Il se peut que l'application soit en transition et qu'il serait préférable d'utiliser un retour hâtif en début de méthode. Ces conditions permettent à l'application de bien fonctionner.

Tous les projets ayant un certain vécu sont différents. Certain favorise des retours hâtifs, ~~d'autre préfère lancer des exceptions~~ et d'autre ne font absolument rien.
---
layout: post
title:  "PHP self or static"
tags: php
---

En PHP, lorsque nous parlons de variable ou de méthode `static` tel que celle démontrée ci-dessous :
```php
class Parent
{
    public static $bar = 10;
}
```

Cette valeur peut être récupérée de plusieurs façons, afin de démontrer la différence entre `self` et `static`, nous allons ajouter une méthode à notre classe pour récupérer la valeur.

```php
class Parent
{
    protected static $bar = 10;

    public static getBar()
    {
        return self::$bar;
    }
}
```

Dans cet exemple, en ayant mis la propriété en `protected`, elle n'est plus accessible par aucun autre élément qui ne fait pas partie de sa hiérarchie. Nous pouvons seulement récupérer sa valeur en appelant `Parent::getBar()`, qui nous retournera la valeur `10`.

Si nous créions une nouvelle classe qui serait un enfant de `Parent`.

```php
class Enfant extends Parent
{
    protected static $bar = 20;
}
```

Si nous appelons `Enfant::getBar()`, nous allons avoir comme résultat `10`, car la méthode `getBar()` retourne `self::$bar`. Le `self` spécifie d'aller chercher dans la classe actuel l'élément recherché.

Si nous réalisons une modification dans la classe `Parent`.

```php
class Parent
{
    protected static $bar = 10;

    public static getBar()
    {
        return static::$bar;
    }
}
```

Et que nous appelons `Enfant::getBar()`, nous allons avoir un résultat différent, cette fois la réponse sera `20`. Le changement pour `static` prend en considération la classe qui appelle la méthode.
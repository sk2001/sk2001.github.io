---
layout: post
title:  "War again custom"
tags: custom
---

## Sur mesure
Je ne veux pas dire qu’il y a une guerre, ou que je désire entamer une croisade pour la libération de la roue (je vais y revenir plus tard, je le promets). C’est plus un point de vue sur la création de code qui peut être trop spécifique.

Vous êtes-vous déjà retrouvé face à face avec un site ou encore une application web qui déforme tout ce qui existe pour réussir à se frayer un chemin? Ça arrive lorsque plusieurs personnes s’unissent derrière un produit et désire le percevoir d’une façon différente de ce qu’il est réellement. C’est un peu comme un enfant, ces parents ne le trouveront jamais laid. Ce n’est pas essentiellement mauvais, mais d’un autre sens, c’est un allé simple vers une possible catastrophe.

Lorsque nous nous trouvons face à face avec un tel code source, nous ne pouvons rien faire d’autre que de le regarder, le fixer, s’interroger, se demander s’il n’est pas un de ces projets qui serait "[legacy](https://sk2001.similiar.ca/2022/10/04/legacy.html)". Indirectement, il a beaucoup de chance de s’en approcher, si nous ne gardons pas une main ferme et des lignes bien décrites, ce projet s’en va directement à la décrépitude.

Voici ma définition d’un produit "custom". Une application, qui essaye de recréer une solution complète qui répondrait mieux à ces besoins que l’implémentation actuelle, dont chaque modification ne sert qu’à se rapprocher d’un autre produit déjà existant. Vous voyez ou je veux m’en venir? Est-il encore nécessaire de réinventer la roue? Est-ce qu’il ne serait pas mieux de simplement l’améliorer au lieu de la réécrire au complet? La création d’un CMS est un beau défi, mais de le développer, de le maintenir, de le supporter et de l’apporter en production, c’est un gap qui n’est plus utile aujourd’hui. En quoi est-ce que ton produit sera meilleur que celui de la concurrence? Il t’appartiendra? C’est un couteau à deux tranchants.

J’entends déjà parler les gens d’entreprise dire que c’est ce qui les différencie de cette dernière. J’avoue, je ne veux pas me débattre là-dessus, mais je ne suis pas d’accord. Lorsque votre entreprise aura un boom de croissance, avez-vous planifié d’engager du personnel dont vous allez devoir former pour expliquer toutes les différences, les subtilités, de votre application? C’est probablement à ce moment que la concurrence, qui utilise un produit plus commun, va prendre le dessus en trouvant du personnel du jour au lendemain qui est capable d’être productif à partir de la première semaine. Contrairement à vous, dont la formation interne est d’au minimum deux mois avant d’écrire la première ligne de code.

Lorsqu’il est temps de choisir un [`framework`](https://www.google.com/search?q=laravel+vs+symfony+usage) ou encore une [dépendance](https://packagist.org/explore/popular), nous devons nous assurer de plusieurs détails. L’un d’eux est la connaissance de l’outil choisi. C’est plaisant d’être avant-gardiste et de trouver le logiciel parfait pour notre unique situation.

Je vais être franc, des produits taillés à votre réalité bâtis sur mesure et répondant à vos besoins spécifiques peuvent être créé. Cependant, c’est comme acheter un complet sur mesure, le processus sera long et le résultat reflètera la compétence du concepteur. Une chose est certaine, le coût sera élevé.

## Furthor
Pennons, par exemple, une entreprise __fictive__ du nom de ___Furthor___. Chez nous, nous imprimons des magazines. Tous nos articles sont écrits au format `markdown`. Pour interpréter ce format, nous avons notre propre interpréteur qui format le tout selon nos `specs`, et non ceux du [standard](https://commonmark.org/). Par exemple, notre interpréteur échange les `_` pour des espaces fines insécables pour répondre au besoin de notre correcteur d’avoir ce type d’espace devant certaine ponctuation (`!` et `?`), le problème que nous avons est que l’utilisation de `_` avant et après le texte ne donne pas le [résultat escompté](https://spec.commonmark.org/0.30/#emphasis-and-strong-emphasis).

Un problème survient lorsque quelqu’un décide de mettre de l’emphase dans son texte en utilisant la composition de glyph `_` dans son texte. À permière vu, dans son éditeur de texte de prédilection, tout se passe bien! Cependant, lorsque ce texte est compilé par l’interprétation maison, le texte a perdu son emphase et l’espacement n’est plus correct.

L’utilisateur décide de faire part de ce `bug` à ___Furthor___ pour qu’il soit corrigé et se fait répondre que c’est une [`feature`](https://www.wired.com/story/its-not-a-bug-its-a-feature/). Il y aura probablement une frustration qui va naitre. Le danger, un jour la concurrence sera probablement très attirante.

# WORKING THAT

Un problème qu’une nouvelle personne pourrait réaliser, c’est de croire qu’il pourra utiliser notre implémentation de la même façon que les autres. Malheureusement, ce n’est pas le cas, c’est plus l’équivalent d’apprendre quelque chose de nouveau avec une lutte pour pas retomber dans ce qui est connu. À la fin, de faire une demande pour que certaine fonctionnalité soit implémentée, des fonctionnalités qui existe et fonctionne déjà ailleurs, et se faire dire que ça va prendre du temps dans le cas ou il sera implémenté. Est-ce le temps de regarder la concurrence? Être un client, c’est probablement le meilleur moment pour le faire. Quoi que...

Est-ce qu’il est mieux d’avoir une application qui répond spécifiquement à ces besoins selon _ce que nous en comprenons_ ou d’avoir une application qui permet de grandir? Idéalement, les deux... Par contre, il existe toujours une solution que je vais appeler _générique_, qui est "presque" ce qui est demandé. Des fois la concession ne peut pas être fait, mais dans les cas qu’il est possible de réaliser un changement, il serait avantageux de regarder s’il est possible de le faire, cette solution sera toujours moins chère finalement.

## Au développement
Malheureusement, nous sommes les "spécialistes". Je veux dire, généralement, le client n’a aucune idée qu’il existe un produit _générique_ qui pourrait répondre à ces besoins. D’un autre côté, l’équipe qui propose une solution pourrait, eux aussi, être dans l’ignorance à ce sujet. Est-ce qu’il manque un niveau de recherche avant de donner une solution? Possible. Cependant, ce n’est pas une façon de faire courante.

Une autre option est que l’équipe juge qu’il est plus préférable de tout réécrire, histoire de `copyright`. J’aimerais rappeler qu’il n’est pas nécessaire d’avoir l’entièreté d’une application couverte par un `copyright`. Il est possible de seulement avoir quelques parties de couverte. Cependant, le principe du `blacklist` est utilisé au lieu de celui du `whitelist`. Pour mieux comprendre :
- [blacklist] J’applique un `copyright` sur toute l’application sauf les `dependencies`.
- [whitelist] J’applique un `copyright` sur ce `package` uniquement.

### Tourne `vice`
J’ai changé des prises électriques dernièrement, ils utilisent quelque chose de bien comme principe. La vis pour serrer le fils électrique peut être tourné à la fois avec un tournevis plat ou carré. J’ai appris dernièrement qu’il existait des tournevis qui sont parfaits pour ce type de fente ([square slot](https://www.amazon.ca/Klein-Tools-32378-Combo-Driver/dp/B00OJQWWFC)). Quels sont les autres utilisés? Je ne sais pas, je n’en vois pas vraiment. Je peux probablement me tromper, mais personnellement j’utilise soit un tournevis "carré" ([Robertson](https://fr.wikipedia.org/wiki/Carr%C3%A9_Robertson)) ou plat, type de tournevis que plusieurs personnes ont!

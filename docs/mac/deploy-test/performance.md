---
title: Performances de Xamarin.Mac
description: Ce document fournit des considérations relatives aux performances pour les applications Xamarin.Mac.
ms.prod: xamarin
ms.assetid: 54B07DED-FDF2-49B2-A5FB-3A9357E65922
ms.technology: xamarin-mac
author: bradumbaugh
ms.author: brumbaug
ms.date: 11/10/2017
ms.openlocfilehash: 273fb1980695a3dcd4a4fc2123b1ebafef1756a2
ms.sourcegitcommit: 945df041e2180cb20af08b83cc703ecd1aedc6b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2018
---
# <a name="xamarinmac-performance"></a>Performances de Xamarin.Mac

## <a name="overview"></a>Vue d'ensemble

Les applications Xamarin.Mac sont similaires aux applications Xamarin.iOS, et la plupart des mêmes suggestions relatives aux performances leur sont applicables :

- [Niveau de performance de Xamarin.iOS](~/ios/deploy-test/performance.md)
- [Niveau de performance multiplateforme](~/cross-platform/deploy-test/memory-perf-best-practices.md)

mais un certain nombre de suggestions spécifiques à macOS peuvent être utiles.

## <a name="prefer-modern-target-framework"></a>Préférer le framework cible moderne

Plusieurs [frameworks cibles](~/mac/platform/target-framework.md) avec des fonctionnalités et des caractéristiques de performances différentes sont disponibles pour une application Xamarin.Mac.

Dans la mesure du possible, préférez le framework Moderne et utilisez des bibliothèques dépendantes pour ajouter la prise en charge. Seul le framework cible Moderne permet la liaison, ce qui peut considérablement réduire la taille de l’assembly. Cela devient particulièrement important quand AOT est activé, car la compilation AOT d’assemblys complets peut produire des bundles finaux volumineux.

## <a name="enable-the-linker"></a>Activer l’éditeur de liens

Le temps de démarrage, à la fois lors du chargement et de JIT (« Just In Time »), évolue de façon plutôt linéaire avec la taille de vos fichiers binaires finaux. La façon la plus simple d’améliorer cela consiste à supprimer le code mort avec l’[éditeur de liens](~/mac/deploy-test/linker.md).

Même si cette suggestion s’applique principalement aux utilisateurs du framework cible Moderne, l’utilisation de la [liaison de plateforme](~/mac/deploy-test/linker.md) peut également fournir une amélioration limitée des performances.

## <a name="enable-aot-when-appropriate"></a>Activer AOT si nécessaire

La compilation JIT des assemblys en code machine constitue un autre aspect des performances du démarrage. La compilation Ahead of Time (AOT) peut réduire considérablement le temps de démarrage, mais elle s’accompagne d’un certain nombre de compromis traités dans la [documentation d’AOT](~/mac/internals/aot.md).

## <a name="ensure-performant-delegates"></a>Garantir les performances des délégués

De nombreuses applications Xamarin.Mac sont centrées sur les vues Cocoa comme `NSCollectionView`, `NSOutlineView` ou `NSTableView`. Souvent, ces vues sont optimisées par les classes `Delegate` et `DataSource` que vous fournissez à Cocoa, répondant à des questions sur les éléments à afficher.

Beaucoup de ces points d’entrée sont souvent appelés, parfois plusieurs fois par seconde lors du défilement.

Afin d’éviter le blocage de l’interface utilisateur, vérifiez que ces fonctions retournent des valeurs qui sont facilement calculées ou qui utilisent des informations déjà mises en cache.

## <a name="use-cocoa-provided-apis-for-reusing-views"></a>Utiliser les API fournies par Cocoa pour la réutilisation des vues

De nombreuses vues Cocoa contenant beaucoup de cellules ou de vues enfants (comme `NSCollectionView`, `NSOutlineView` et `NSTableView`) fournissent des API pour créer et réutiliser des vues. Ces API créent des pools d’éléments partagés et évitent les problèmes de performances lors du défilement rapide des vues.

## <a name="use-async-and-do-not-block-the-ui"></a>Utiliser async pour ne pas bloquer l’interface utilisateur

Les applications de bureau traitent souvent de grandes quantités de données, et il est très facile de bloquer le thread d’interface utilisateur en attente d’une opération synchrone.

Autant que possible, utilisez [async](~/cross-platform/platform/async.md) et des threads pour éviter le blocage de l’interface utilisateur.

Pour les opérations dont l’exécution est longue, utilisez [NSProgressIndicator](https://developer.xamarin.com/samples/mac/ProgressBarExample/) ou d’autres options signalées dans les recommandations [HIG (Human Interface Guidelines)](https://developer.apple.com/macos/human-interface-guidelines/indicators/progress-indicators/) d’Apple pour avertir les utilisateurs.


## <a name="related-links"></a>Liens associés

- [Niveau de performance multiplateforme](~/cross-platform/deploy-test/memory-perf-best-practices.md)
- [Niveau de performance de Xamarin.iOS](~/ios/deploy-test/performance.md)

---
title: Extensions de balisage XAML
description: Cet article explique comment utiliser des extensions de balisage XAML de Xamarin.Forms pour étendre la puissance et la flexibilité du code XAML en permettant aux attributs de l’élément à définir à partir de sources autres que des chaînes de texte littéral.
ms.prod: xamarin
ms.assetid: EB06C8B7-3FD5-47B7-A09C-A13063BD110F
ms.technology: xamarin-forms
author: charlespetzold
ms.author: chape
ms.date: 01/05/2018
ms.openlocfilehash: c6f1853c5864eed8484e7746755c6fa80a28a49b
ms.sourcegitcommit: 66682dd8e93c0e4f5dee69f32b5fc5a96443e307
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35245883"
---
# <a name="xaml-markup-extensions"></a>Extensions de balisage XAML

Extensions de balisage XAML prolonger la puissance et la flexibilité du code XAML en permettant aux attributs de l’élément à définir à partir de sources autres que des chaînes de texte littéral.

Par exemple, normalement vous définir la `Color` propriété du `BoxView` comme suit :

```xaml
<BoxView Color="Blue" />
```

Ou bien, vous pouvez définir une valeur de couleur RVB hexadécimale :

```xaml
<BoxView Color="#FF0080" />
```

Dans les deux cas, la chaîne de texte définie le `Color` attribut est converti en un `Color` valeur par la [ `ColorTypeConverter` ](https://developer.xamarin.com/api/type/Xamarin.Forms.ColorTypeConverter/) classe.

Vous préférerez peut-être à la place définir la `Color` attribut à partir d’une valeur stockée dans un dictionnaire de ressources, la valeur d’une propriété statique d’une classe que vous avez créée ou d’une propriété de type `Color` d’un autre élément dans la page, ou il est construit à partir de Séparez les valeurs de teinte, saturation et de luminosité.

Toutes ces options sont possibles à l’aide des extensions de balisage XAML. Mais ne vous laissez la phrase « extensions de balisage » vous font peur : sont des extensions de balisage XAML *pas* extensions XML. Même avec les extensions de balisage XAML, XAML est toujours conforme XML.

Une extension de balisage est simplement une manière différente pour exprimer un attribut d’un élément. Extensions de balisage XAML sont généralement identifiables par un paramètre d’attribut qui est placé entre accolades :

```xaml
<BoxView Color="{StaticResource themeColor}" />
```

N’importe quel paramètre d’attribut entre accolades est *toujours* une extension de balisage XAML. Toutefois, comme vous le verrez, les extensions de balisage XAML peuvent également être référencées sans l’utilisation d’accolades.

Cet article est divisé en deux parties :

## <a name="consuming-xaml-markup-extensionsconsumingmd"></a>[Consommation des extensions de balisage XAML](consuming.md)  

Utilisez les extensions de balisage XAML définies dans Xamarin.Forms.

## <a name="creating-xaml-markup-extensionscreatingmd"></a>[Création d’extensions de balisage XAML](creating.md)

Écrire vos propres extensions de balisage XAML personnalisées.



## <a name="related-links"></a>Liens associés

- [Extensions de balisage (exemple)](https://developer.xamarin.com/samples/xamarin-forms/XAML/MarkupExtensions/)
- [Chapitre d’extensions de balisage XAML à partir du carnet de Xamarin.Forms](~/xamarin-forms/creating-mobile-apps-xamarin-forms/summaries/chapter10.md)
- [Dictionnaires de ressources](~/xamarin-forms/xaml/resource-dictionaries.md)
- [Styles dynamiques](~/xamarin-forms/user-interface/styles/dynamic.md)
- [Liaison de données](~/xamarin-forms/app-fundamentals/data-binding/index.md)

---
title: Styles de texte de Xamarin.Forms
description: Cet article explique comment le texte de style dans les applications de Xamarin.Forms. Styles peuvent être définis qu’une seule fois et utilisés par de nombreuses vues, mais un style est utilisable uniquement avec les vues d’un type.
ms.prod: xamarin
ms.assetid: 57C0CFD6-A568-46B8-ADA1-BF25681893CF
ms.technology: xamarin-forms
author: davidbritch
ms.author: dabritch
ms.date: 05/22/2017
ms.openlocfilehash: b8cc6493c3574180e7938050075c5a70ecebeebf
ms.sourcegitcommit: 66682dd8e93c0e4f5dee69f32b5fc5a96443e307
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35245320"
---
# <a name="xamarinforms-text-styles"></a>Styles de texte de Xamarin.Forms

_Texte de style dans Xamarin.Forms_

Styles peuvent être utilisés pour ajuster l’apparence des étiquettes, des entrées et des éditeurs. Styles peuvent être définis qu’une seule fois et utilisés par de nombreuses vues, mais un style est utilisable uniquement avec les vues d’un type.
Styles peuvent être accordées à un `Key` et appliquées de manière sélective à l’aide d’un contrôle spécifique `Style` propriété.

<a name="Built-In_Styles" />

## <a name="built-in-styles"></a>Styles intégrés

Xamarin.Forms comprend plusieurs [intégrés](http://developer.xamarin.com/api/type/Xamarin.Forms.Device+Styles/) styles pour les scénarios courants :

- `BodyStyle`
- `CaptionStyle`
- `ListItemDetailTextStyle`
- `ListItemTextStyle`
- `SubtitleStyle`
- `TitleStyle`

Pour appliquer des styles intégrés, utilisez le `DynamicResource` extension de balisage pour spécifier le style :

```xaml
<Label Text="I'm a Title" Style="{DynamicResource TitleStyle}"/>
```

En c#, les styles intégrés sont sélectionnés à partir de `Device.Styles`:

```csharp
label.Style = Device.Styles.TitleStyle;
```

![](styles-images/builtinstyles.png "Exemple de Styles de périphérique")

<a name="Custom_Styles" />

## <a name="custom-styles"></a>Styles personnalisés

Styles se composent de méthodes setter et méthodes setter se comprendre des propriétés et les valeurs de propriétés seront fixés à.

Dans c#, un style personnalisé pour une étiquette avec le texte rouge de taille 30 serait défini comme suit :

```csharp
var LabelStyle = new Style (typeof(Label)) {
    Setters = {
        new Setter {Property = Label.TextColorProperty, Value = Color.Red},
        new Setter {Property = Label.FontSizeProperty, Value = 30}
    }
};

var label = new Label { Text = "Check out my style.", Style = LabelStyle };
```

En XAML :

```xaml
<ContentPage.Resources>
    <ResourceDictionary>
        <Style x:Key="LabelStyle" TargetType="Label">
            <Setter Property="TextColor" Value="Red"/>
            <Setter Property="FontSize" Value="30"/>
        </Style>
    </ResourceDictionary>
</ContentPage.Resources>

<ContentPage.Content>
    <StackLayout>
        <Label Text="Check out my style." Style="{StaticResource LabelStyle}" />
    </StackLayout>
</ContentPage.Content>
```

Notez que les ressources (y compris tous les styles) sont définies dans `ContentPage.Resources`, qui est un frère de plus familiers `ContentPage.Content` élément.

![](styles-images/customstyle.png "Exemple de Styles personnalisés")

<a name="Applying_Styles" />

## <a name="applying-styles"></a>Appliquer des Styles

Une fois un style a été créé, il peut être appliqué à toute correspondance de vue son `TargetType`.

En XAML, les styles personnalisés sont appliqués aux vues en fournissant leurs `Style` propriété avec un `StaticResource` extension de balisage en référençant le style souhaité :

```xaml
<Label Text="Check out my style." Style="{StaticResource LabelStyle}" />
```

En c#, styles peuvent soit être appliqués directement à une vue ou ajoutés à et récupérées à partir d’une page `ResourceDictionary`. Pour ajouter directement :

```csharp
var label = new Label { Text = "Check out my style.", Style = LabelStyle };
```

Pour ajouter et récupérer à partir de la page `ResourceDictionary`:

```csharp
this.Resources.Add ("LabelStyle", LabelStyle);
label.Style = (Style)Resources["LabelStyle"];
```

Styles intégrés sont appliquées différemment, car ils ont besoin répondre à des paramètres d’accessibilité. Pour appliquer des styles intégrés en XAML, le `DynamicResource` extension de balisage est utilisée :

```xaml
<Label Text="I'm a Title" Style="{DynamicResource TitleStyle}"/>
```

En c#, les styles intégrés sont sélectionnés à partir de `Device.Styles`:

```csharp
label.Style = Device.Styles.TitleStyle;
```

## <a name="accessibility"></a>Accessibilité

Les styles intégrés existent pour le rendre plus facile de respecter les préférences d’accessibilité. Lorsque vous utilisez un des styles intégrés, les tailles de police augmentera automatiquement si un utilisateur définit les préférences de leur accessibilité en conséquence.

Prenons l’exemple suivant de la même page de style avec les styles intégrés avec les paramètres d’accessibilité activé et désactivé des vues :

Désactivé :

![](styles-images/pre-access.png "Styles de périphérique avec accessibilité désactivé")

Activé :

![](styles-images/post-access.png "Styles de périphérique avec l’accessibilité activé")

Pour garantir l’accessibilité, assurez-vous que les styles intégrés sont utilisés comme base pour tous les styles de texte dans votre application, et que vous utilisez les styles de manière cohérente. Consultez [Styles](~/xamarin-forms/user-interface/styles/index.md) pour plus d’informations sur l’extension et travailler avec des styles en général.


## <a name="related-links"></a>Liens associés

- [Création d’applications mobiles avec Xamarin.Forms, chapitre 12](https://developer.xamarin.com/r/xamarin-forms/book/chapter12.pdf)
- [Styles](~/xamarin-forms/user-interface/styles/index.md)
- [Texte (exemple)](https://developer.xamarin.com/samples/xamarin-forms/UserInterface/Text)
- [Style](https://developer.xamarin.com/api/type/Xamarin.Forms.Style/)

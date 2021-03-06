---
title: 'Xamarin.Essentials : préférences'
description: Ce document décrit la classe Préférences dans Xamarin.Essentials, qui enregistre les préférences de l’application dans un magasin de clé/valeur. Elle explique comment utiliser la classe et les types de données qui peuvent être stockées.
ms.assetid: AA81BCBD-79BA-448F-942B-BA4415CA50FF
author: jamesmontemagno
ms.author: jamont
ms.date: 05/04/2018
ms.openlocfilehash: e453c04a953e60be2508670723d175bde3dc7c42
ms.sourcegitcommit: ea1dc12a3c2d7322f234997daacbfdb6ad542507
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34782841"
---
# <a name="xamarinessentials-preferences"></a>Xamarin.Essentials : préférences

![Version préliminaire de NuGet](~/media/shared/pre-release.png)

Le **préférences** classe permet de stocker les préférences de l’application dans un magasin de clé/valeur.

## <a name="using-secure-storage"></a>À l’aide du stockage sécurisé

Ajoutez une référence à Xamarin.Essentials dans votre classe :

```csharp
using Xamarin.Essentials;
```

Pour enregistrer une valeur pour une donnée _clé_ dans les préférences de :

```csharp
Preferences.Set("my_key", "my_value");
```

Pour récupérer une valeur de préférences ou une valeur par défaut s’il n’est pas définie :

```csharp
var myValue = Preferences.Get("my_key", "default_value");
```

Pour supprimer la _clé_ des préférences :

```csharp
Preferences.Remove("my_key");
```

Pour supprimer toutes les préférences :

```csharp
Preferences.Clear();
```

Outre ces méthodes acceptent chacun dans facultatif `sharedName` qui peut être utilisé pour créer des conteneurs supplémentaires de préférence. Lire les détails d’implémentation de plateforme ci-dessous.

## <a name="supported-data-types"></a>Types de données pris en charge

Types de données suivants sont pris en charge dans **préférences**:

- **bool**
- **double**
- **int**
- **float**
- **long**
- **string**

## <a name="platform-implementation-specifics"></a>Caractéristiques d’implémentation de plate-forme

# <a name="androidtabandroid"></a>[Android](#tab/android)

Toutes les données sont stockées dans [partagé des préférences](https://developer.android.com/training/data-storage/shared-preferences.html). Si aucun `sharedName` est spécifié pour les préférences partagée par défaut sont utilisées, sinon le nom est utilisé pour obtenir un **privé** partagé préférences avec le nom spécifié.

# <a name="iostabios"></a>[iOS](#tab/ios)

[NSUserDefaults](https://docs.microsoft.com/en-us/xamarin/ios/app-fundamentals/user-defaults) est utilisé pour stocker les valeurs sur les appareils iOS. Si aucun `sharedName` est spécifié le `StandardUserDefaults` sont utilisées, sinon le nom est utilisé pour créer un nouveau `NSUserDefaults` portant le nom spécifié est utilisé pour le `NSUserDefaultsType.SuiteName`.

# <a name="uwptabuwp"></a>[UWP](#tab/uwp)

[ApplicationDataContainer](https://docs.microsoft.com/en-us/uwp/api/windows.storage.applicationdatacontainer) est utilisé pour stocker les valeurs sur l’appareil. Si aucun `sharedName` est spécifiée la `LocalSettings` sont utilisées, sinon le nom est utilisé pour créer un nouveau conteneur à l’intérieur de `LocalSettings`.

--------------

## <a name="limitations"></a>Limitations

Lorsque vous stockez une chaîne, cette API est destinée à stocker de petites quantités de texte.  Performances peuvent être été si vous essayez d’utiliser pour stocker de grandes quantités de texte.

## <a name="api"></a>API

- [Préférences de code source](https://github.com/xamarin/Essentials/tree/master/Xamarin.Essentials/Preferences)
- [Documentation de préférences de l’API](xref:Xamarin.Essentials.Preferences)

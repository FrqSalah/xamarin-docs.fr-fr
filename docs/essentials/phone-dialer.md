---
title: Numéroteur Xamarin.Essentials
description: La classe PhoneDialer permet à une application ouvrir un lien web dans le navigateur par défaut système optimisé ou un navigateur externe.
ms.assetid: E7457942-4D7B-4195-A2FF-417919B9537F
ms.technology: xamarin-crossplatform
author: jamesmontemagno
ms.author: jamont
ms.date: 05/04/2018
ms.openlocfilehash: 70e43d58eab562f032b59edf7095ca2614af8082
ms.sourcegitcommit: 46d3c9daa45350bdd536d9e105517f3c1c753c5b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="xamarinessentials-phone-dialer"></a>Numéroteur Xamarin.Essentials

![Version préliminaire de NuGet](~/media/shared/pre-release.png)

Le **PhoneDialer** classe permet à une application ouvrir un lien web dans le navigateur par défaut système optimisé ou un navigateur externe.

## <a name="using-phone-dialer"></a>À l’aide de Numéroteur téléphonique

Ajoutez une référence à Xamarin.Essentials dans votre classe :

```csharp
using Xamarin.Essentials;
```

La fonctionnalité Numéroteur téléphonique fonctionne en appelant le `Open` méthode avec un numéro de téléphone pour ouvrir le numéroteur avec. Lorsque `Open` est demandé à l’API tente automatiquement de mettre en forme le nombre en fonction de l’indicatif du pays, s’il est spécifié.

```csharp
public class PhoneDialerTest
{
    public async Task PlacePhoneCall(string number)
    {
        try
        {
            PhoneDialer.Open(number);
        }
        catch (ArgumentNullException anEx)
        {
            // Number was null or white space
        }
        catch (FeatureNotSupportedException ex)
        {
            // Phone Dialer is not supported on this device.
        }
        catch (Exception ex)
        {
            // Other error has occurred.
        }
    }
}
```

## <a name="api"></a>API

- [Numéroteur téléphonique code source](https://github.com/xamarin/Essentials/tree/master/Essentials/PhoneDialer)
- [Documentation de l’API de Numéroteur téléphonique](xref:Xamarin.Essentials.PhoneDialer)
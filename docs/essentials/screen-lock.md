---
title: 'Xamarin.Essentials : Verrouillage d’écran'
description: Ce document décrit la classe ScreenLock dans Xamarin.Essentials, ce qui peut demander à conserver l’écran de tomber en mode veille lorsque l’application est en cours d’exécution.
ms.assetid: 6B67C114-315E-4199-AA72-3F90E85A4909
author: jamesmontemagno
ms.author: jamont
ms.date: 05/04/2018
ms.openlocfilehash: 3c8110b7abc86fe1d12485579f134997718540e6
ms.sourcegitcommit: ea1dc12a3c2d7322f234997daacbfdb6ad542507
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34782906"
---
# <a name="xamarinessentials-screen-lock"></a>Xamarin.Essentials : Verrouillage d’écran

![Version préliminaire de NuGet](~/media/shared/pre-release.png)

Le **ScreenLock** classe peut demander à conserver l’écran de tomber en mode veille lorsque l’application est en cours d’exécution.

## <a name="using-screenlock"></a>À l’aide de ScreenLock

Ajoutez une référence à Xamarin.Essentials dans votre classe :

```csharp
using Xamarin.Essentials;
```

La fonctionnalité de verrouillage d’écran fonctionne en appelant le `RequestActive` et `RequestRelease` méthodes pour demander de l’écran à partir de la mise hors tension.

```csharp
public class ScreenLockTest
{
    public void ToggleScreenLock()
    {
        if (!ScreenLock.IsActive)
            ScreenLock.RequestActive();
        else
            ScreenLock.RequestRelease();
    }
}
```

## <a name="api"></a>API

- [Écran de code source du verrou](https://github.com/xamarin/Essentials/tree/master/Xamarin.Essentials/ScreenLock)
- [Documentation de l’API de verrou écran](xref:Xamarin.Essentials.ScreenLock)

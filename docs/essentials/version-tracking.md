---
title: 'Xamarin.Essentials : Suivi de Version'
description: La classe VersionTracking dans Xamarin.Essentials vous permet de vérifier la version des applications et des numéros de build, ainsi que de voir des informations supplémentaires telles que si c’est la première fois que l’application lancée jamais ou pour la version actuelle, obtenez la build précédente plus d’informations et bien plus encore.
ms.assetid: 670C7E8A-E882-4AC0-97D2-A53D90ADD6A3
author: jamesmontemagno
ms.author: jamont
ms.date: 05/04/2018
ms.openlocfilehash: 2c092d6767045f0af956c5dab74801077dadb51f
ms.sourcegitcommit: ea1dc12a3c2d7322f234997daacbfdb6ad542507
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34783000"
---
# <a name="xamarinessentials-version-tracking"></a>Xamarin.Essentials : Suivi de Version

![Version préliminaire de NuGet](~/media/shared/pre-release.png)

Le **VersionTracking** classe vous permet de vérifier la version des applications et des numéros de build, ainsi que de voir des informations supplémentaires telles que si c’est la première fois l’application lancée jamais ou pour la version actuelle, obtenez le précédent informations de build et bien plus encore.

## <a name="using-version-tracking"></a>Utilisation du suivi de Version

Ajoutez une référence à Xamarin.Essentials dans votre classe :

```csharp
using Xamarin.Essentials;
```

La première fois que vous utilisez le **VersionTracking** classe démarre le suivi de la version actuelle. Vous devez appeler `Track` précoce que dans votre application chaque fois qu’il est chargé pour vérifier les informations de version en cours sont suivies :

```csharp
VersionTracking.Track();
```

Après le premier `Track` est appelée peuvent lire les informations de version :

```csharp

// First time ever launched application
var firstLaunch = VersionTracking.IsFirstLaunchEver;

// First time launching current version
var firstLaunchCurrent = VersionTracking.IsFirstLaunchForCurrentVersion;

// First time launching current build
var firstLaunchBuild = VersionTracking.IsFirstLaunchForCurrentBuild;

// Current app version (2.0.0)
var currentVersion = VersionTracking.CurrentVersion;

// Current build (2)
var currentBuild = VersionTracking.CurrentBuild;

// Previous app version (1.0.0)
var previousVersion = VersionTracking.PreviousVersion;

// Previous app build (1)
var previousBuild = VersionTracking.PreviousBuild;

// First version of app installed (1.0.0)
var firstVersion = VersionTracking.FirstInstalledVersion;

// First build of app installed (1)
var firstBuild = VersionTracking.FirstInstalledBuild;

// List of versions installed (1.0.0, 2.0.0)
var versionHistory = VersionTracking.VersionHistory;

// List of builds installed (1, 2)
var buildHistory = VersionTracking.BuildHistory;
```

## <a name="platform-implementation-specifics"></a>Caractéristiques d’implémentation de plate-forme

Toutes les informations de version sont stockées à l’aide de la [préférences](preferences.md) API dans Xamarin.Essentials et est stocké avec un nom de fichier de **[votre-APP-PACKAGE-ID] .xamarinessentials**.

Désinstallation de l’application entraîne le _LocalSettings_et tous les versions à supprimer les informations de suivi.

## <a name="api"></a>API

- [Code de source de suivi de version](https://github.com/xamarin/Essentials/tree/master/Xamarin.Essentials/VersionTracking)
- [Documentation sur les API de suivi de version](xref:Xamarin.Essentials.VersionTracking)

---
title: Fonctionnalités de la plateforme Android
description: Cet article explique comment ajouter des fonctionnalités Android propres aux applications de Xamarin.Forms et il se concentre sur les documents de conception.
ms.prod: xamarin
ms.assetid: E24168F3-0138-4814-86EA-B467F6B8A545
ms.technology: xamarin-forms
author: davidbritch
ms.author: dabritch
ms.date: 01/13/2016
ms.openlocfilehash: 2eada518586f222d200ec19aeddc65107d7603b3
ms.sourcegitcommit: 66682dd8e93c0e4f5dee69f32b5fc5a96443e307
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35242402"
---
# <a name="android-platform-features"></a>Fonctionnalités de la plateforme Android

## <a name="platform-support"></a>Prise en charge de plateforme

La valeur par défaut du projet de Xamarin.Forms Android utilise un ancien style de contrôle renderering qui était courant avant Android 5.0. Les applications générées à l’aide du modèle ont `FormsApplicationActivity` comme classe de base de leur activité principale.

## <a name="material-design-via-appcompat"></a>Conception de matériel via AppCompat

Xamarin.Forms a également une option `FormsAppCompatActivity` qui utilise **AppCompat** fonctionnalités fournies par Android pour implémenter des thèmes de matériel.

Pour ajouter des thèmes de matériau à votre projet Xamarin.Forms Android, suivez le [prend en charge les instructions d’installation de AppCompat](appcompat.md)

Voici le **Todo** exemple avec la valeur par défaut `FormsApplicationActivity`:

[![](images/before-appcompat-sml.png "Exemple de tâches d’Application sans AppCompat")](images/before-appcompat.png#lightbox "Application Todo exemple sans AppCompat")

C’est le même code après la mise à niveau le projet à utiliser `FormsAppCompatActivity` (et ajouter les informations de thème supplémentaires) :

[![](images/post-appcompat-sml.png "Exemple de tâches d’Application avec AppCompat et des thèmes")](images/post-appcompat.png#lightbox "Application Todo exemple avec AppCompat et thèmes")

> [!NOTE]
> Lorsque vous utilisez `FormsAppCompatActivity`, le [classes de base pour certains convertisseurs personnalisés Android](~/xamarin-forms/app-fundamentals/custom-renderer/renderers.md) sera différente.


## <a name="related-links"></a>Liens associés

- [Ajouter la prise en charge de la conception de matériel](appcompat.md)

---
title: Liaison iOS bibliothèques
description: Ce document décrit comment créer c# des liaisons avec code Objective-C, ce qui permet d’utiliser des bibliothèques natives et CocoaPods dans une application Xamarin.iOS.
ms.prod: xamarin
ms.assetid: EBDC50DC-B44B-4003-AB2B-1EEB868A5E01
ms.technology: xamarin-ios
ms.custom: xamu-video
author: bradumbaugh
ms.author: brumbaug
ms.date: 03/18/2017
ms.openlocfilehash: b054595568a34616a01f2c3f3c7d85f968c3f1fa
ms.sourcegitcommit: ea1dc12a3c2d7322f234997daacbfdb6ad542507
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34787165"
---
# <a name="binding-ios-libraries"></a>Liaison iOS bibliothèques

Suivez ces liens pour en savoir plus sur la liaison des bibliothèques de Objective-C et CocoaPods pour Xamarin.iOS et Xamarin.Mac :

- [**Vue d’ensemble** ](~/cross-platform/macios/binding/overview.md) -
  décrit le fonctionne de la liaison.
- [**Liaison Objective-C bibliothèques** ](~/cross-platform/macios/binding/objective-c-libraries.md) -
  obtenir des Instructions sur la façon de lier les bibliothèques Objective-C pour une utilisation dans les projets de Xamarin.
- [**Guide de référence de définition de type** ](~/cross-platform/macios/binding/binding-types-reference.md) -
  décrit tous les attributs disponibles pour les auteurs de la liaison pour piloter le processus de génération de liaison.

## <a name="objective-sharpiecross-platformmaciosbindingobjective-sharpieindexmd"></a>[Objective Sharpie](~/cross-platform/macios/binding/objective-sharpie/index.md)

Objectif Sharpie est un outil de ligne de commande permettant de démarrer le premier test d’une liaison.
Il fonctionne en analysant les fichiers d’en-tête d’une bibliothèque native pour mapper l’API publique dans le [définition de liaison](~/cross-platform/macios/binding/objective-c-libraries.md) (processus qui est sinon effectué manuellement). Objectif Sharpie ne crée pas d’une liaison par lui-même, mais il peut vous aider à commencer !

Objectif Sharpie 3.0 a introduit la possibilité de lier directement des Cocoapods !

## <a name="walkthrough---binding-an-ios-objective-c-librarywalkthroughmd"></a>[Procédure pas à pas : liaison d’une bibliothèque de Objective-C iOS](walkthrough.md)

Cette page fournit une procédure pas à pas détaillées de création d’un projet de liaison iOS à l’aide de la source ouverte [ **InfColorPicker** ](https://github.com/InfinitApps/InfColorPicker) projet Objective-C comme exemple. Le **InfColorPicker** bibliothèque fournit un contrôleur de vue réutilisables qui permettent à l’utilisateur de sélectionner une couleur en fonction de sa représentation sous forme de TSL, effectuer une sélection de couleur plus conviviaux.
Objectif Sharpie permet de faciliter le processus de liaison.

## <a name="xamarin-university-lightning-lecture"></a>Xamarin University éclair conférence

> [!VIDEO https://youtube.com/embed/ZUoPLcmnf1o]

**e/s en C/C++, les liaisons par [Xamarin University](https://university.xamarin.com/)**

## <a name="related-links"></a>Liens associés

- [Liaison Objective-C](~/cross-platform/macios/binding/index.md)
- [Liaison de Mac](~/mac/platform/binding.md)

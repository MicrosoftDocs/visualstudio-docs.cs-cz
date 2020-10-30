---
title: Speciální znaky nástroje MSBuild | Microsoft Docs
description: Přečtěte si o vyhrazených znacích MSBuild pro speciální použití v konkrétních kontextech a kdy a jak tyto znaky vyřídí.
ms.custom: SEO-VS-2020
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 67de0c2e5aa35fa3a1f54e26f425f4b0916cb428
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049118"
---
# <a name="msbuild-special-characters"></a>Speciální znaky nástroje MSBuild

Nástroj MSBuild rezervuje některé znaky pro speciální použití v konkrétních kontextech. Chcete-li je použít v kontextu, ve kterém jsou vyhrazené, stačí je pouze odsekvencit. Hvězdička má například zvláštní význam pouze v `Include` `Exclude` atributech a definice položky a v volání `CreateItem` . Pokud chcete, aby se hvězdička zobrazovala jako hvězdička v jednom z těchto kontextů, je nutné ji řídicím znakem. V každém jiném kontextu stačí zadat hvězdičku, kde se má objevit.

 Chcete-li zadat zvláštní znak, použijte syntaxi% \<xx> , kde \<xx> představuje šestnáctkovou hodnotu ASCII znaku. Další informace naleznete v tématu [How to: Escape Special Characters in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).

## <a name="special-characters"></a>Speciální znaky

 V následující tabulce jsou uvedeny speciální znaky nástroje MSBuild:

|**Znak**|**Abecední**|**Rezervované využití**|
|-------------------|---------------|------------------------|
|%|%25|Odkazování na metadata|
|$|%24|Odkazování na vlastnosti|
|@|%40|Odkazy na seznamy položek|
|'|%27|Podmínky a jiné výrazy|
|;|% 3B|Oddělovač seznamu|
|?|% 3F|Zástupný znak pro názvy souborů v `Include` a `Exclude` atributy|
|*|%2A|Zástupný znak pro použití v názvech souborů `Include` v `Exclude` atributech a|

## <a name="see-also"></a>Viz také

- [Pokročilé koncepty](../msbuild/msbuild-advanced-concepts.md)
- [Položky](../msbuild/msbuild-items.md)

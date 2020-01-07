---
title: Speciální znaky nástroje MSBuild | Microsoft Docs
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
ms.openlocfilehash: 5f18339dbbddb09e44e8c5fa53ba517f3d60c025
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566056"
---
# <a name="msbuild-special-characters"></a>Speciální znaky nástroje MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] vyhrazuje některé znaky pro speciální použití v konkrétních kontextech. Chcete-li je použít v kontextu, ve kterém jsou vyhrazené, stačí je pouze odsekvencit. Hvězdička má například zvláštní význam pouze v atributech `Include` a `Exclude` definice položky a v volání `CreateItem`. Pokud chcete, aby se hvězdička zobrazovala jako hvězdička v jednom z těchto kontextů, je nutné ji řídicím znakem. V každém jiném kontextu stačí zadat hvězdičku, kde se má objevit.

 Chcete-li zadat zvláštní znak, použijte syntaxi%\<xx >, kde \<xx > představuje šestnáctkovou hodnotu ASCII znaku. Další informace naleznete v tématu [How to: Escape Special Characters in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).

## <a name="special-characters"></a>Speciální znaky
 Následující tabulka uvádí [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] speciálních znaků:

|**Znak**|**ASCII**|**Rezervované využití**|
|-------------------|---------------|------------------------|
|%|%25|Odkazování na metadata|
|$|%24|Odkazování na vlastnosti|
|@|%40|Odkazy na seznamy položek|
|tokenu prostředku|%27|Podmínky a jiné výrazy|
|;|% 3B|Oddělovač seznamu|
|?|% 3F|Zástupný znak pro názvy souborů v atributech `Include` a `Exclude`|
|*|% 2A|Zástupný znak pro použití v názvech souborů v atributech `Include` a `Exclude`|

## <a name="see-also"></a>Viz také:
- [Pokročilé koncepty](../msbuild/msbuild-advanced-concepts.md)
- [Položky](../msbuild/msbuild-items.md)

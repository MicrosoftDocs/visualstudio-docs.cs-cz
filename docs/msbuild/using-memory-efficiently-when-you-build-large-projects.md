---
title: Efektivní použití paměti při sestavování rozsáhlých projektů | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af61c15c8ef65c062c1aab6eba079c613f99b5f8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595225"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Efektivní využití paměti při sestavování rozsáhlých projektů
Velké projekty často obsahují mnoho dílčích projektů a dalších závislostí, které mohou spotřebovat spoustu systémové paměti v době sestavení. Pokud dojde k poklesu dostupné systémové paměti, může se také snížit výkon systému. Starší verze [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektů zůstaly v paměti. Verze 3,5 odebrala starší verze projektů, ale výsledky sestavení byly uchovány v mezipaměti pro pozdější načtení.

 Verze 4,0 zpracovává tuto správu paměti automaticky a ukládá projekty z nutnosti používat vlastnosti, jako jsou `UnloadProjectsOnCompletion` a `UseResultsCache`.

### <a name="see-also"></a>Viz také:
- [Paralelní sestavení více projektů](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)

---
title: Efektivní využití paměti při vytváření velkých projektů | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: f40f2713d93e4f1ad9755efaea2f8fba5f0bda94
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631312"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Efektivní využití paměti při vytváření velkých projektů

Velké projekty často obsahují mnoho dílčích projektů a dalších závislostí, které mohou v době sestavení spotřebovat velké množství systémové paměti. Pokud je snížena dostupná systémová paměť, může být snížen také výkon systému. Starší verze projektů MSBuild zůstaly v paměti. Verze 3.5 odebrala starší verze projektů, ale zachovala výsledky sestavení v mezipaměti pro pozdější načtení.

 Verze 4.0 zpracovává tuto správu paměti automaticky, což `UnloadProjectsOnCompletion` šetří `UseResultsCache`projekty z nutnosti používat vlastnosti, jako jsou a .

### <a name="see-also"></a>Viz také

- [Paralelní vytváření více projektů](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)

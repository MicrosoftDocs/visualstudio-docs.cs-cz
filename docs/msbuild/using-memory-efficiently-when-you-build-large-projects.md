---
title: Efektivní použití paměti při sestavování rozsáhlých projektů | Microsoft Docs
description: Přečtěte si, jak MSBuild spravuje paměť automaticky, jako je uvolnění starších verzí a načítání mezipamětí při sestavování rozsáhlých projektů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 99cee9cfbf779bbee97c00fb76f9670e1d609b00
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965899"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Efektivní využití paměti při sestavování rozsáhlých projektů

Velké projekty často obsahují mnoho dílčích projektů a dalších závislostí, které mohou spotřebovat spoustu systémové paměti v době sestavení. Pokud dojde k poklesu dostupné systémové paměti, může se také snížit výkon systému. Starší verze projektů MSBuild zůstaly v paměti. Verze 3,5 odebrala starší verze projektů, ale výsledky sestavení byly uchovány v mezipaměti pro pozdější načtení.

 Verze 4,0 zpracovává tuto správu paměti automaticky a ukládá projekty z nutnosti používat vlastnosti, jako jsou  `UnloadProjectsOnCompletion` a `UseResultsCache` .

### <a name="see-also"></a>Viz také

- [Paralelní sestavení více projektů](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)

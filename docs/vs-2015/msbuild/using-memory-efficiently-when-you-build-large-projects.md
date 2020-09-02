---
title: Efektivní použití paměti při sestavování rozsáhlých projektů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 28d9f3d43faa53731b101dfdf58fe1e68a0920c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178303"
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>Efektivní využívání paměti při sestavování rozsáhlých projektů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Velké projekty často obsahují mnoho dílčích projektů a další závislosti a ty mohou spotřebovat spoustu systémové paměti v době sestavení. Pokud dojde k poklesu dostupné systémové paměti, může se také snížit výkon systému. Starší verze [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektů zůstaly v paměti nebo ve verzi 3,5 byly odebrány projekty, ale při pozdějším načtení zachovaly výsledky sestavení v mezipaměti.  
  
 Verze 4,0 zpracovává tuto správu paměti automaticky a ukládá projekty z nutnosti používat vlastnosti, jako jsou  `UnloadProjectsOnCompletion` a `UseResultsCache` .  
  
## <a name="see-also"></a>Viz také  
 [Paralelní sestavování více projektů](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)

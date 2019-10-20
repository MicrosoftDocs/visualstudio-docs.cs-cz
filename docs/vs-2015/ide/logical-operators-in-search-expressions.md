---
title: Logické operátory ve výrazech hledání | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, logical operators in search
- logical operators in search [Help Viewer 2.0]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3d56f2dfc2924008a6be293fe1498f0ffe32abaf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651430"
---
# <a name="logical-operators-in-search-expressions"></a>Logické operátory ve vyhledávacích výrazech
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí logických operátorů můžete upřesnit hledání obsahu vytvořením složitějších vyhledávacích výrazů od jednodušších. Jak ukazuje následující tabulka, logické operátory určují, jak se má v vyhledávacím dotazu kombinovat více hledaných výrazů.

> [!IMPORTANT]
> Je nutné zadat logické operátory do všech velkých písmen pro vyhledávací modul, aby je bylo možné rozpoznat.

|Hledání|Použití|Příklad|Výsledek|
|-------------------|---------|-------------|------------|
|Oba výrazy ve stejném tématu|AND|DIB a paleta|Témata, která obsahují "DIB" i "paleta".|
|Podmínka v tématu|NEBO|rastrový nebo vektorový|Témata, která obsahují buď rastrový nebo vektorový.|
|První výraz bez druhého termínu ve stejném tématu|MĚNÍ|operační systém bez DOS|Témata obsahující "operační systém", ale ne "DOS".|
|Obě tyto výrazy se společně nacházejí v tématu.|LEVÉMU|uživatel poblíž jádra|Témata, která obsahují slovo "uživatel" v blízkosti blízkosti "jádra".|

## <a name="see-also"></a>Viz také
 [Tipy pro fulltextové vyhledávání](../ide/full-text-search-tips.md) [najít informace](../ide/locate-information.md)

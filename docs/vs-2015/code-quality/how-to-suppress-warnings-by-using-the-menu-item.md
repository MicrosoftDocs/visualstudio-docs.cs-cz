---
title: 'Postupy: potlačení upozornění pomocí položky nabídky | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 96b7433ff4f696989142aa2c2ce47982006b93b2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610016"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Postupy: Potlačení upozornění použitím položky nabídky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ZNAČTE
> V potlačení zdrojového kódu není podporováno pro webové projekty.

 Pro potlačení upozornění analýzy kódu lze použít okno Analýza kódu. Potlačení upozornění není stejné jako jeho zakázání. Když potlačíte upozornění, vztahuje se pouze na určitou instanci porušení. Další porušení stejného upozornění budou uvedena i v okně Seznam chyb.

 Po spuštění analýzy kódu můžete určit, že jedno nebo více upozornění analýzy kódu, která jsou zobrazena v okně Analýza kódu, se nevztahují na vaši aplikaci. Například je možné určit, že kód je správný, jak je. Nebo může to být případ, že některá porušení jsou nízká priorita a nebudou opravena v aktuálním vývojovém cyklu. Bez ohledu na důvod je často užitečné upozornit, že upozornění je nevhodné, aby členové týmu věděli, že kód byl zkontrolován a že bylo zjištěno, že upozornění může být potlačeno. Při potlačení zdroje je užitečné, protože umožňuje vložit potlačení blízko místa, kde se vygeneruje upozornění.

 Můžete zvolit, zda se má potlačení zobrazovat ve zdrojovém kódu nebo v souboru globálního potlačení. Některá potlačení musí být umístěna do globálního souboru potlačení. Pokud se jedná o tento případ, bude možnost **v možnosti zdroj** zakázána.

### <a name="to-suppress-a-warning-by-using-menu-item"></a>Chcete-li potlačit upozornění pomocí položky nabídky

1. V nabídce **analyzovat** zvolte **okna** a pak zvolte **Analýza kódu**.

2. V okně **Analýza kódu** zaškrtněte políčko potlačit upozornění.

3. Zvolte akce, pak zvolte **Potlačit zprávy**a potom zvolte buď **ve zdroji** , nebo **v souboru potlačení projektu**.

     Konkrétní upozornění je potlačeno a upozornění se zobrazí v okně Analýza kódu přeškrtnuté.

> [!NOTE]
> Potlačení, která nemají cíl, se zobrazí v souboru globálního potlačení.

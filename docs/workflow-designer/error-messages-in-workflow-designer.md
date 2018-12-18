---
title: Chybové zprávy v návrháři postupu provádění
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83cbde06b10d1201c7e69c1823714007dfa57397
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755580"
---
# <a name="error-messages-in-workflow-designer"></a>Chybové zprávy v návrháři postupu provádění

Toto téma popisuje typy chybové zprávy, které mohou být zjištěny při práci s návrháře pracovních postupů.

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Situace, v nichž dochází k chybám v Návrháři pracovních postupů

Chyby v Návrháři pracovních postupů objevit v následujících situacích:

1.  Ve výrazu dojde k chybě.

2.  Omezení ověřování aktivity nebyly splněny.

3.  Jsou chyby v souboru XAML, které způsobí selhání načtení aktivitu.

4.  Jsou chyby v souboru XAML, které způsobí spuštění pracovního postupu se nepovedlo načíst.

Neplatný výrazy a omezení spokojeni ověřování nezpůsobí selhání k vytvoření pracovního postupu. Vytváření pracovního postupu úspěšné, ale <xref:System.Activities.InvalidWorkflowException> je vyvolána za běhu. Pokud nejsou chyby v souboru XAML, sestavení selže.

V sadě Visual Studio, když pracovní postup je načtena, jeho chyby se zobrazí v **seznam chyb**. Přejděte na aktivitu, která je zdrojem chyby, dvakrát klikněte na chybu v **seznam chyb**.

### <a name="expression-errors"></a>Výraz chyby
 Červené kolečko obsahující bílý vykřičníkem vedle výraz je označený jako neplatný výraz. Ukazatele myši na tuto ikonu zobrazí popis, který popisuje zdroji této chyby. V sadě Visual Studio klikněte na tlačítko výrazu si řádek, který podtrhne zdroji této chyby. Ukazatele myši zobrazí linkované text popisku, který popisuje zdroji této chyby.

### <a name="activity-validation-errors"></a>Chyby ověření aktivity
 Omezení ověřování aktivity nebyly splněny, zobrazí se v pravém horním rohu aktivity červené kolečko obsahující bílý vykřičník. Ukazatele myši na tuto ikonu zobrazí popis, který popisuje zdroji této chyby.

### <a name="xaml-load-errors"></a>Chyba načtení XAML
 Když aktivita se nepodaří načíst, zobrazí se červené pole s textem "aktivity nelze načíst z důvodu chyb v XAML". K tomu obvykle dochází, když typ aktivity nelze přeložit. Výběrem červeným rámečkem a odstranění se dá odstranit neplatný aktivity v návrháři.

### <a name="workflow-load-errors"></a>Chyba načtení pracovního postupu
 Když pracovního postupu se nepodaří načíst, zobrazí se text "Návrháře pracovního postupu došlo k problémům s dokumentem" na plochu návrháře, společně s informace o výjimce, která způsobila selhání pracovního postupu se načíst. K tomu obvykle dochází, když nelze analyzovat souboru XAML.
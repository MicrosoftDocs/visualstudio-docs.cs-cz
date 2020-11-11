---
title: Chybové zprávy v návrháři postupu provádění
description: Přečtěte si o typech chybových zpráv, se kterými se můžete setkat při práci s Návrhář postupu provádění.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f3886739cbc6deefd13570ae0f49da7e89ad9b1
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438032"
---
# <a name="error-messages-in-workflow-designer"></a>Chybové zprávy v návrháři postupu provádění

Toto téma popisuje typy chybových zpráv, které mohou být zjištěny při práci s Návrhář postupu provádění.

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Situace, ve kterých dochází k chybám Návrhář postupu provádění

K chybám v Návrhář postupu provádění dochází v následujících situacích:

1. Ve výrazu je chyba.

2. Nebyla splněna omezení ověření aktivity.

3. V souboru XAML jsou chyby, které způsobují selhání načtení aktivity.

4. V souboru XAML jsou chyby, které způsobují, že se pracovní postup nepodařilo načíst.

Neplatné výrazy a nesplněná omezení ověřování nezpůsobí, že se pracovní postup nedaří sestavit. Sestavení pracovního postupu je úspěšné, ale <xref:System.Activities.InvalidWorkflowException> v době běhu je vyvolána výjimka. Pokud v souboru XAML dojde k chybám, sestavení selhalo.

V rámci sady Visual Studio se při načtení pracovního postupu zobrazí jeho chyby v **Seznam chyb**. Chcete-li přejít k aktivitě, která je zdrojem chyby, dvakrát klikněte na chybu v **Seznam chyb**.

### <a name="expression-errors"></a>Chyby výrazu
 Neplatný výraz je označen červeným kroužkem s bílým vykřičníkem vedle výrazu. Po najetí myší na tuto ikonu se zobrazí popis, který popisuje zdroj chyby. V aplikaci Visual Studio klikněte na výraz, abyste zobrazili řádek, který je podtržený zdrojem chyby. Při najetí myší na řádek textu se zobrazí popis, který popisuje zdroj chyby.

### <a name="activity-validation-errors"></a>Chyby ověřování aktivity
 Pokud nebyla splněna omezení ověření aktivity, v pravém horním rohu aktivity se zobrazí červené kolečko s bílým vykřičníkem. Po najetí myší na tuto ikonu se zobrazí popis, který popisuje zdroj chyby.

### <a name="xaml-load-errors"></a>Chyby načtení XAML
 Pokud se aktivita nepovede načíst, nepovedlo se načíst červené pole s textem "aktivita", protože se zobrazí chyby v kódu XAML. K tomu obvykle dochází, když typ aktivity nelze přeložit. Neplatnou aktivitu lze v Návrháři odstranit tak, že vyberete červené pole a odstraníte ji.

### <a name="workflow-load-errors"></a>Chyby načtení pracovního postupu
 V případě, že se pracovní postup nepodařilo načíst, text "Návrhář postupu provádění zjistil problémy s dokumentem" na návrhové ploše, spolu s informacemi o výjimkách, které způsobily selhání pracovního postupu při načtení. K tomu obvykle dochází v případě, že soubor XAML nelze analyzovat.

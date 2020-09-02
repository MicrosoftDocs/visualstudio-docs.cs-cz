---
title: Chybové zprávy v Návrhář postupu provádění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d89c0dcad23a91ec6057311b9afde7d6d4702772
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656756"
---
# <a name="error-messages-in-workflow-designer"></a>Chybové zprávy v návrháři postupu provádění
Toto téma popisuje typy chybových zpráv, které mohou být zjištěny při práci s nástrojem [!INCLUDE[wfd1](../includes/wfd1-md.md)] .

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Situace, ve kterých dochází k chybám Návrhář postupu provádění
 K chybám [!INCLUDE[wfd2](../includes/wfd2-md.md)] dochází v následujících situacích:

1. Ve výrazu je chyba.

2. Nebyla splněna omezení ověření aktivity.

3. V souboru XAML jsou chyby, které způsobují selhání načtení aktivity.

4. V souboru XAML jsou chyby, které způsobují, že se pracovní postup nepodařilo načíst.

   Neplatné výrazy a nesplněná omezení ověřování nezpůsobí, že se pracovní postup nedaří sestavit. Sestavení pracovního postupu je úspěšné, ale <xref:System.Activities.InvalidWorkflowException> je vyvolána za běhu. Pokud v souboru XAML dojde k chybám, sestavení selhalo.

   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]V případě, že je pracovní postup načten, zobrazí se jeho chyby v **Seznam chyb**. Chcete-li přejít k aktivitě, která je zdrojem chyby, dvakrát klikněte na chybu v **Seznam chyb**.

### <a name="expression-errors"></a>Chyby výrazu
 Neplatný výraz je označen červeným kroužkem s bílým vykřičníkem vedle výrazu. Po najetí myší na tuto ikonu se zobrazí popis, který popisuje zdroj chyby. V rámci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] klikněte na výraz, abyste zobrazili řádek, který je podtržený zdrojem chyby. Při najetí myší na řádek textu se zobrazí popis, který popisuje zdroj chyby.

### <a name="activity-validation-errors"></a>Chyby ověřování aktivity
 Pokud nebyla splněna omezení ověření aktivity, v pravém horním rohu aktivity se zobrazí červené kolečko s bílým vykřičníkem. Po najetí myší na tuto ikonu se zobrazí popis, který popisuje zdroj chyby.

### <a name="xaml-load-errors"></a>Chyby načtení XAML
 Pokud se aktivita nepovede načíst, nepovedlo se načíst červené pole s textem "aktivita", protože se zobrazí chyby v kódu XAML. K tomu obvykle dochází, když typ aktivity nelze přeložit. Neplatnou aktivitu lze v Návrháři odstranit tak, že vyberete červené pole a odstraníte ji.

### <a name="workflow-load-errors"></a>Chyby načtení pracovního postupu
 V případě, že se pracovní postup nepodařilo načíst, text "Návrhář postupu provádění zjistil problémy s dokumentem" na návrhové ploše, spolu s informacemi o výjimkách, které způsobily selhání pracovního postupu při načtení. K tomu obvykle dochází v případě, že soubor XAML nelze analyzovat.
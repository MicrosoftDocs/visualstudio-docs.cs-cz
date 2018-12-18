---
title: Chybové zprávy v Návrháři pracovních postupů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: efd6bc680be42f1074da8d2313b1a4b8e9307580
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894843"
---
# <a name="error-messages-in-workflow-designer"></a>Chybové zprávy v návrháři postupu provádění
Toto téma popisuje typy chybové zprávy, které mohou nastat při práci s [!INCLUDE[wfd1](../includes/wfd1-md.md)].  
  
## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Situace, ve kterých dojde k chybám v Návrháři postupu provádění  
 Chyby v [!INCLUDE[wfd2](../includes/wfd2-md.md)] dojít v následujících situacích:  
  
1. Ve výrazu dojde k chybě.  
  
2. Omezení ověřování aktivity nebyly splněny.  
  
3. Existují chyby v souboru XAML, které způsobují aktivitu na nepodaří zavést.  
  
4. Existují chyby v souboru XAML, které způsobí selhání načtení pracovního postupu.  
  
   Neplatné výrazy a omezení nespokojen/nespokojena ověření nespouštějí pracovní postup sestavení nezdaří. Vytvoření pracovního postupu bude úspěšné, ale <xref:System.Activities.InvalidWorkflowException> je vyvolána výjimka za běhu. Pokud nejsou chyby v souboru XAML, sestavení selže.  
  
   Uvnitř [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], když je načten pracovní postup, jeho chyby zobrazují v **seznam chyb**. Přejděte na aktivitu, která je zdrojem chyby klikněte dvakrát na chybu v **seznam chyb**.  
  
### <a name="expression-errors"></a>Výraz chyby  
 Neplatný výraz označuje symbolem červené kolečko s bílým vykřičníkem vedle výraz. Ukazatel myši tuto ikonu zobrazí popisek, který popisuje zdroje chyby. Uvnitř [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], klikněte na výraz, který má zobrazit na řádek, který podtrhuje zdroje chyby. Ukazatel myši zobrazí řádkovaný text popisu, který popisuje zdroje chyby.  
  
### <a name="activity-validation-errors"></a>Chyby ověřování aktivit  
 Když splněné omezení ověřování aktivity, zobrazí se v pravém horním rohu aktivity červené kolečko s bílým vykřičník. Ukazatel myši tuto ikonu zobrazí popisek, který popisuje zdroje chyby.  
  
### <a name="xaml-load-errors"></a>Chyby načítání XAML  
 Když aktivity se nepodaří načíst, zobrazí se červená pole s textem "aktivitu nelze načíst z důvodu chyby v XAML". K tomu obvykle dochází, když nelze rozpoznat typ aktivity. Neplatný aktivity můžete odstranit v Návrháři výběrem červeným rámečkem a jeho odstranění.  
  
### <a name="workflow-load-errors"></a>Chyby načtení pracovního postupu  
 Když pracovní postup se nepodaří načíst, text "Návrháře postupu provádění došlo k problémům s vaším dokumentem" se zobrazí na návrhové ploše, spolu s, která způsobila Chyba pracovního postupu se načíst informace o výjimce. K tomu obvykle dochází, když nelze analyzovat soubor XAML.
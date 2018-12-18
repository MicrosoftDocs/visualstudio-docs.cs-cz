---
title: 'Postupy: nastavení zarážek v pracovních postupech | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: b3dedba320ce8a783b7d54df54a30b0759a6bd00
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896221"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Postupy: nastavení zarážek v pracovních postupech
Při použití [!INCLUDE[wfd1](../includes/wfd1-md.md)], můžete nastavit zarážky na grafické pracovních postupů, jako byste to udělali v kódu jazyka Visual Basic nebo C#. Podle očekávání, zastaví provádění pracovního postupu u každé zarážky, které jste nastavili.  
  
 Zarážka má tři stavy: *čekající*, *vázán*, a *chyba*. Pokud nastavíte zarážku, čeká na vyřízení a je reprezentována solid červenou ikonu. Při načítání pracovního postupu typu modulu runtime vázán. Pokud zadáte nesprávný formát pro zarážku, jako je například název aktivity, která není platná, zobrazí se okno aplikace chyba. Zarážka je přidána do okna zarážky, ale je označena s malým "x".  
  
> [!NOTE]
>  Nastavení zarážek v pracovních postupech, vyvolali se nepodporuje.  
> 
> [!WARNING]
>  Ujistěte se, že vyberete možnost **povolit volbu pouze vlastní kód (pouze spravované)** z **nástroje**, **možnosti**, **ladění** nabídku před ladění. Pokud máte dvou sekvencí, které jsou vnořené uvnitř jiné pořadí a nastavit bod přerušení na první vnitřní pořadí, stisknutím klávesy **F11** nebude ladění do druhé vnitřní pořadí, pokud <strong>povolit volbu pouze vlastní kód (pouze spravované)</strong>možnost není vybraná.  
> 
> [!WARNING]
>  V pracovním postupu nebudete získáte zarážky pokud úplná cesta k vlastnosti souboru XAML není přesné. Úplná cesta k souboru XAML není přesné po přesunutí projektu nebo řešení do jiné složky nebo do jiného počítače. Vyberte kombinaci kláves Ctrl + S uložte a aktualizujte vlastnost úplnou cestu.  
  
### <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Chcete-li nastavit zarážku pro aktivitu v návrhovém zobrazení  
  
1.  Vyberte aktivitu má ladicí program na přerušení na.  
  
2.  Na **ladění** nabídce vyberte možnost **Přepnout zarážku**. Červená ikona se zobrazí v levém horním okrajem aktivity.  
  
     Alternativně můžete také stisknout klávesovou zkratku **F9** klíče po výběru aktivity nebo je můžete klikněte pravým tlačítkem na aktivitu a vyberte **zarážku** pak **vložit zarážku**v místní nabídce.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vyvolání ladicího programu pracovních postupů](../workflow-designer/how-to-invoke-the-workflow-debugger.md)   
 [Ladění pracovních postupů pomocí návrháře postupu provádění](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)   
 [Postupy: Ladění XAML pomocí návrháře postupu provádění](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)
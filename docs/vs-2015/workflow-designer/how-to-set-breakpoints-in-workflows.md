---
title: 'Postupy: nastavení zarážek v pracovních postupech | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2d1bbb18a9015b52b3d65cb8f8fd02674693abc0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659142"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Postupy: nastavení zarážek v pracovních postupech
Když použijete [!INCLUDE[wfd1](../includes/wfd1-md.md)], můžete nastavit zarážky v grafických pracovních postupech tak, jak byste to provedete C# v Visual Basic nebo kódu. Jak bylo očekáváno, spuštění pracovního postupu se zastaví v každé zarážce, kterou jste nastavili.

 Zarážka má tři stavy: *nevyřízené*, *vázané*a *chybové*. Při nastavení zarážky čeká na vyřízení a je reprezentována plnou červenou ikonou. Když modul runtime načetl typ pracovního postupu, bude se jednat o vazbu. Pokud zadáte nesprávný formát pro zarážku, například název aktivity, který není platný, zobrazí se chybové okno. Zarážka je stále přidána do okna zarážky, ale je označena malým znakem "x".

> [!NOTE]
> Nastavení zarážek u vyvolaných pracovních postupů se nepodporuje.
>
> [!WARNING]
> Než budete ladit, ujistěte se, že jste v nabídce **nástroje**, **Možnosti**, **ladění** vybrali možnost **Povolit pouze můj kód (pouze spravované)** . Pokud máte dvě sekvence vnořené v jiné sekvenci a nastavíte bod přerušení na první vnitřní sekvenci, klávesa **F11** se nebude ladit do druhé vnitřní sekvence, pokud není vybraná možnost <strong>Povolit pouze můj kód (pouze spravované)</strong>.
>
> [!WARNING]
> Zarážky v pracovním postupu se neobjeví, pokud je vlastnost Úplná cesta k souboru XAML nepřesná. Úplná cesta k souboru XAML není po přesunutí projektu nebo řešení do jiné složky nebo jiného počítače přesná. Vyberte CTRL + S a uložte a aktualizujte vlastnost Úplná cesta.

### <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Nastavení zarážky u aktivity v zobrazení Návrh

1. Vyberte aktivitu, na které má být ladicí program přerušen.

2. V nabídce **ladění** vyberte možnost **Přepnout zarážku**. V levém horním rohu aktivity se zobrazí červená ikona.

     Alternativně můžete také po výběru aktivity stisknout klávesu **F9** , nebo můžete kliknout pravým tlačítkem myši na aktivitu a vybrat **zarážku** a pak **Vložit zarážku** z kontextové nabídky.

## <a name="see-also"></a>Viz také
 [Postupy: volání pracovních postupů ladění ladicího programu pracovního postupu](../workflow-designer/how-to-invoke-the-workflow-debugger.md) [s Návrhář postupu provádění](../workflow-designer/debugging-workflows-with-the-workflow-designer.md) [postupy: ladění XAML pomocí Návrhář postupu provádění](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)
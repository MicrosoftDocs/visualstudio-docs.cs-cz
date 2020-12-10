---
title: Nastavení zarážek v pracovních postupech
description: Naučte se používat Návrhář postupu provádění k nastavení zarážek ve vašich grafických pracovních postupech stejně jako v kódu Visual Basic nebo C#.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88516a4160c5236a5a4ef9f01d7f15620aee5cc3
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993299"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Postupy: nastavení zarážek v pracovních postupech

Při použití Návrhář postupu provádění můžete nastavit zarážky na vašich grafických pracovních postupech tak, jak byste to provedete v kódu Visual Basic nebo C#. Jak bylo očekáváno, spuštění pracovního postupu se zastaví v každé zarážce, kterou jste nastavili.

Zarážka má tři stavy: *nevyřízené*, *vázané* a *chybové*. Při nastavení zarážky čeká na vyřízení a je reprezentována plnou červenou ikonou. Když modul runtime načetl typ pracovního postupu, bude se jednat o vazbu. Pokud zadáte nesprávný formát pro zarážku, například název aktivity, který není platný, zobrazí se chybové okno. Zarážka je stále přidána do okna zarážky, ale je označena malým znakem "x".

> [!NOTE]
> Nastavení zarážek u vyvolaných pracovních postupů se nepodporuje.

> [!NOTE]
> Před laděním se ujistěte, že jste vybrali možnost **Povolit pouze můj kód (pouze spravované)** z   >    >  nabídky **ladění** možností nástrojů. Pokud možnost není vybrána a máte dvě sekvence vnořené v jiné sekvenci a nastavíte bod přerušení v první vnitřní sekvenci, stisknutí klávesy **F11** nebude ladit do druhé vnitřní sekvence.

> [!NOTE]
> Zarážky v pracovním postupu nejsou k dispozice, pokud úplná cesta k souboru XAML není přesná. Úplná cesta k souboru XAML není po přesunutí projektu nebo řešení do jiné složky nebo jiného počítače přesná. Vyberte **CTRL** + **S** a uložte a aktualizujte vlastnost Úplná cesta.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Nastavení zarážky u aktivity v zobrazení Návrh

1. Vyberte aktivitu, na které má být ladicí program přerušen.

2. V nabídce **ladění** vyberte možnost **Přepnout zarážku**. V levém horním rohu aktivity se zobrazí červená ikona.

   Případně můžete stisknout klávesu **F9** po výběru aktivity, nebo můžete kliknout pravým tlačítkem myši na aktivitu a vybrat **zarážku**  >  **Vložit** zarážku v nabídce kliknutím pravým tlačítkem myši.

## <a name="see-also"></a>Viz také

- [Ladění pracovních postupů pomocí návrháře postupu provádění](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Postupy: Ladění XAML pomocí návrháře postupu provádění](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)

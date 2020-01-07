---
title: Jak pohyb v integrovaném vývojovém prostředí
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.NextDocumentWindowNav
- IDE navigator
ms.assetid: 6c36b6eb-c93f-496b-af08-4199f7afd8bd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2febdedf5cf472132de936c37cad787df3d77518
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590992"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>Postupy: pohyb v integrovaném vývojovém prostředí sady Visual Studio

Integrované vývojové prostředí (IDE) byla navržená tak, aby bylo možné přesunout okno s a soubor se souborem několika různými způsoby v závislosti na požadavcích předvoleb nebo projektu. Můžete procházet soubory lze otevřít v editoru nebo cyklicky procházet všechny aktivní okna nástrojů v rozhraní IDE. Také můžete přepnout na libovolný soubor otevřít v editoru, bez ohledu na pořadí, ve kterém byl naposledy přistupovat přímo. Tyto funkce může pomoct zvýšit vaši produktivitu při práci v integrovaném vývojovém prostředí.

> [!NOTE]
> Dostupné možnosti v dialogových oknech, názvy a umístění příkazy nabídek, které se zobrazí, může lišit od co je popsaný v tomto článku, v závislosti na aktivních nastaveních nebo edici. Tento článek byl zapsán s **Obecné** nastavení v paměti. Chcete-li změnit nastavení, například k **Obecné** nebo **Visual C++** nastavení, zvolte **nástroje** > **nastavení importu a exportu**a klikněte na tlačítko **obnovit všechna nastavení**.

## <a name="keyboard-shortcuts"></a>Klávesové zkratky

Téměř každý příkaz v sadě Visual Studio nemá klávesovou zkratku. Můžete také vytvořit vlastní klávesové zkratky. Další informace najdete v tématu [identifikovat a přizpůsobení klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigate-among-files-in-the-editor"></a>Procházet soubory v editoru

Chcete-li procházet soubory otevřené v editoru můžete použít několik metod. Lze přesunout mezi soubory podle pořadí, ve kterém k nim přístup, použijte Navigátor rozhraní IDE a rychle najít všechny aktuálně otevřené soubory nebo PIN kód na kartě Oblíbené soubory také tak, aby ta jsou vždycky viditelná.

Přejít zpět a vpřed cyklu procházet otevřených souborů v editoru podle pořadí, ve kterém byly přístupné, většinu, jako jsou zpět a vpřed udělat pro historii zobrazení v aplikaci Internet Explorer.

### <a name="to-move-through-open-files-in-order-of-use"></a>Chcete-li procházet soubory lze otevřít v pořadí podle používání

- Chcete-li aktivovat otevřené dokumenty v pořadí, v jakém byly naposledy změněny, stiskněte klávesovou **zkratku Ctrl**+ **-** (pomlčka).

- Chcete-li aktivovat otevřené dokumenty v obráceném pořadí, stiskněte klávesovou **zkratku Ctrl**+**SHIFT**+ **-** (pomlčka).

    > [!NOTE]
    > **Přejděte zpět** a **přejít vpřed** také najdete na **zobrazení** nabídky.

Můžete také přepnout na určitý soubor otevřít v editoru, bez ohledu na to, kdy posledního otevření souboru, pomocí **IDE Navigátor**, **aktivních souborů** seznamu v editoru, nebo **Windows** dialogové okno.

**IDE Navigátor** funguje podobně jako přepínání aplikace Windows. Není k dispozici v nabídkách a je přístupný pouze pomocí klávesových zkratek. Můžete použít buď dva příkazy pro přístup k **IDE Navigátor** (viz dole) k cyklování skrze souborů, v závislosti na pořadí, ve kterém chcete procházet.

![Navigátor rozhraní IDE sady Visual Studio](../ide/media/vs2015_ide_navigator.png)

`Window.PreviousDocumentWindowNav` Umožňuje přesunout do posledního přístupu k souboru a `Window.NextDocumentWindowNav` vám umožní přesunout v obráceném pořadí. **Obecné vývojové nastavení** přiřadí **Shift**+**Alt**+**F7** k `Window.PreviousDocumentWindowNav` a **Alt**  + **F7** k `Window.NextDocumentWindowNav`.

> [!NOTE]
> Pokud používáte kombinaci nastavení už nemá klávesovou zkratku přiřazená tomuto příkazu, můžete přiřadit vlastní pomocí vlastního příkazu **klávesnice** stránce **možnosti** dialogové okno pole. Další informace najdete v tématu [identifikovat a přizpůsobení klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-specific-files-in-the-editor"></a>Přepnout na konkrétní soubory v editoru

- Stisknutím klávesy **Ctrl**+**kartu** zobrazíte **IDE Navigátor**. Podržte stisknutou klávesu **Ctrl** klíč a stiskněte klávesu **kartu** opakovaně, dokud vyberte soubor, který máte v úmyslu přepnout na.

    > [!TIP]
    > Pořadí, ve kterém můžete projít **aktivních souborů** seznamu, podržte stisknutou klávesu **Ctrl**+**Shift** klávesy a stisknutím kláves **kartu**.

    \- nebo –

- V pravém horním rohu editoru zvolte **aktivních souborů** tlačítko a pak vyberte soubor ze seznamu přepnout na.

    \- nebo –

- V panelu nabídky zvolte **okno** > **Windows**.

- V seznamu, vyberte soubor, který chcete zobrazit a pak zvolte **aktivovat**.

## <a name="navigate-among-tool-windows-in-the-ide"></a>Procházet okna nástrojů v prostředí IDE

**IDE Navigátor** také umožňuje cyklicky procházet okna nástrojů, je nutné otevřít v integrovaném vývojovém prostředí. Můžete použít buď dva příkazy pro přístup k **IDE Navigátor** budete cyklicky procházet okna nástrojů, v závislosti na pořadí, ve kterém chcete procházet. `Window.PreviousToolWindowNav` Umožňuje přesunout do posledního přístupu k souboru a `Window.NextToolWindowNav` vám umožní přesunout v obráceném pořadí. **Obecné vývojové nastavení** přiřadí **Shift**+**Alt**+**F7** k `Window.PreviousDocumentWindowNav` a **Alt**  + **F7** k `Window.NextDocumentWindowNav`.

> [!NOTE]
> Pokud používáte kombinaci nastavení už nemá klávesovou zkratku přiřazená tomuto příkazu, můžete přiřadit vlastní pomocí vlastního příkazu **klávesnice** stránce **možnosti** dialogové okno pole. Další informace najdete v tématu [identifikovat a přizpůsobení klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>Přejděte do okna konkrétní nástroje v integrovaném vývojovém prostředí

- Stisknutím klávesy **Alt**+**F7** zobrazíte **IDE Navigátor**. Podržte stisknutou klávesu **Alt** klíč a stiskněte klávesu **F7** opakovaně neprojeví, dokud nevyberete máte v úmyslu přepněte do okna.

    > [!TIP]
    > Pořadí, ve kterém můžete projít **aktivní nástroj Windows** seznamu, podržte stisknutou klávesu **Shift**+**Alt** klávesy a stisknutím kláves **F7**.

## <a name="see-also"></a>Viz také:

- [Přizpůsobení rozložení oken](../ide/customizing-window-layouts-in-visual-studio.md)
- [Výchozí klávesové zkratky](../ide/default-keyboard-shortcuts-in-visual-studio.md)

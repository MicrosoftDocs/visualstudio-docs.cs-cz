---
title: 'Postupy: pohyb v integrovaném vývojovém prostředí | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ea104d08216a4ef7bdb07fc42b5a22eb5352d757
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049616"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>Návody: Pohyb v integrovaném vývojovém prostředí sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Integrované vývojové prostředí (IDE) byla navržená tak, aby bylo možné přesunout okno s a soubor se souborem několika různými způsoby v závislosti na požadavcích předvoleb nebo projektu. Můžete procházet soubory lze otevřít v editoru nebo cyklicky procházet všechny aktivní okna nástrojů v rozhraní IDE. Také můžete přepnout na libovolný soubor otevřít v editoru, bez ohledu na pořadí, ve kterém byl naposledy přistupovat přímo. Tyto funkce může pomoct zvýšit vaši produktivitu při práci v integrovaném vývojovém prostředí.

> [!NOTE]
>  Dostupné možnosti v dialogových oknech, názvy a umístění příkazů, které vidíte, mohou lišit od informací uvedených v nápovědě v závislosti na aktivních nastaveních nebo edici. Tato stránka nápovědy byl zapsán s **obecným vývojovým nastavením** v úvahu. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="keyboard-shortcuts"></a>Klávesové zkratky
 Téměř každý příkaz v sadě Visual Studio nemá klávesovou zkratku. Můžete také vytvořit vlastní klávesové zkratky. Další informace najdete v tématu [určení a přizpůsobení klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigating-among-files-in-the-editor"></a>Procházení mezi soubory v editoru
 Chcete-li procházet soubory otevřené v editoru můžete použít několik metod. Lze přesunout mezi soubory podle pořadí, ve kterém k nim přístup, použijte Navigátor rozhraní IDE a rychle najít všechny aktuálně otevřené soubory nebo PIN kód na kartě Oblíbené soubory také tak, aby ta jsou vždycky viditelná.

 Navigovat zpět a přejít vpřed cyklicky procházet otevřených souborů v editoru podle pořadí, ve kterém byly přístupné, většina jako zpět a vpřed udělat pro historii zobrazení v aplikaci Internet Explorer.

#### <a name="to-move-through-open-files-in-order-of-use"></a>Chcete-li procházet soubory lze otevřít v pořadí podle používání

- Pokud chcete aktivovat otevřených dokumentů v pořadí, ve kterém byly naposledy změněny, stiskněte klávesy CTRL + mínus.

- Pokud chcete aktivovat otevřené dokumenty v obráceném pořadí, stiskněte CTRL + SHIFT + mínus.

  > [!NOTE]
  >  **Přejděte zpět** a **přejít vpřed** také najdete na **zobrazení** nabídky.

  Můžete také přepnout na určitý soubor otevřít v editoru, bez ohledu na to, kdy posledního otevření souboru, pomocí **IDE Navigátor**, **aktivních souborů** seznamu v editoru, nebo **Windows** dialogové okno.

  **IDE Navigátor** funguje podobně jako přepínání aplikace Windows. Není k dispozici v nabídkách a je přístupný pouze pomocí klávesových zkratek. Můžete použít buď dva příkazy pro přístup k **IDE Navigátor** (viz dole) k cyklování skrze souborů, v závislosti na pořadí, ve kterém chcete procházet.

  ![Visual Studio IDE Navigátor](../ide/media/vs2015-ide-navigator.png "VS2015_IDE_Navigator")

  `Window.PreviousDocumentWindowNav` Umožňuje přesunout do posledního přístupu k souboru a `Window.NextDocumentWindowNav` vám umožní přesunout v obráceném pořadí. Obecné vývojové nastavení přiřadí CTRL + SHIFT + TAB `Window.PreviousDocumentWindowNav` a CTRL + TAB `Window.NextDocumentWindowNav`.

> [!NOTE]
>  Pokud používáte kombinaci nastavení už nemá klávesovou zkratku přiřazená tomuto příkazu, můžete přiřadit vlastní pomocí vlastního příkazu **klávesnice** stránce **možnosti** dialogové okno pole. Další informace najdete v tématu [určení a přizpůsobení klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

#### <a name="to-switch-to-specific-files-in-the-editor"></a>Přepnout na konkrétní soubory v editoru

-   Stisknutím kláves CTRL + TAB zobrazíte **IDE Navigátor**. Podržte stisknutou klávesu CTRL a stiskněte klávesu TAB ve opakovaně, dokud nevyberete soubor, který máte v úmyslu přepnout na.

    > [!TIP]
    >  Pořadí, ve kterém můžete projít **aktivních souborů** seznamu, podržte klávesu CTRL + SHIFT – klávesy a stisknutím klávesy TAB.

     \- nebo –

-   V pravém horním rohu editoru zvolte **aktivních souborů** tlačítko a pak vyberte soubor ze seznamu přepnout na.

     \- nebo –

-   V panelu nabídky zvolte **okno**, **Windows**.

-   V seznamu, vyberte soubor, který chcete zobrazit a pak zvolte **aktivovat**.

## <a name="navigating-among-tool-windows-in-the-ide"></a>Procházení mezi nástroji Windows v prostředí IDE
 **IDE Navigátor** také umožňuje cyklicky procházet okna nástrojů, je nutné otevřít v integrovaném vývojovém prostředí. Můžete použít buď dva příkazy pro přístup k **IDE Navigátor** budete cyklicky procházet okna nástrojů, v závislosti na pořadí, ve kterém chcete procházet. `Window.PreviousToolWindowNav` Umožňuje přesunout do posledního přístupu k souboru a `Window.NextToolWindowNav` vám umožní přesunout v obráceném pořadí. Obecné vývojové nastavení přiřadí SHIFT + ALT + F7 `Window.PreviousDocumentWindowNav` a ALT + F7 `Window.NextDocumentWindowNav`.

> [!NOTE]
>  Pokud používáte kombinaci nastavení už nemá klávesovou zkratku přiřazená tomuto příkazu, můžete přiřadit vlastní pomocí vlastního příkazu **klávesnice** stránce **možnosti** dialogové okno pole. Další informace najdete v tématu [určení a přizpůsobení klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

#### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>Přejděte do okna konkrétní nástroje v integrovaném vývojovém prostředí

-   Stisknutím klávesy ALT + F7 zobrazíte **IDE Navigátor**. Podržte stisknutou klávesu ALT a stisknutím klávesy F7 ve opakovaně, dokud nevyberete, kterou chcete přepnout do okna.

    > [!TIP]
    >  Pořadí, ve kterém můžete projít **aktivní nástroj Windows** seznamu, podržte klávesu SHIFT + ALT – klávesy a stisknutím klávesy F7.

## <a name="see-also"></a>Viz také
 [Přizpůsobení rozložení oken](../ide/customizing-window-layouts-in-visual-studio.md) [výchozí klávesové zkratky](../ide/default-keyboard-shortcuts-in-visual-studio.md)

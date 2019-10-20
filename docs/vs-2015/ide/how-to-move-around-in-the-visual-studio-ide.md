---
title: 'Postupy: pohyb v integrovaném vývojovém prostředí (IDE) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 89c4447eb6bbc4b2ae9f7667672626d5119c61d6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651788"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>Návody: Pohyb v integrovaném vývojovém prostředí sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Integrované vývojové prostředí (IDE) bylo navrženo tak, aby bylo možné přesouvat z okna do okna a souboru do souboru několika různými způsoby v závislosti na požadavcích na preference nebo projektu. Můžete se rozhodnout přepínat v editoru otevřené soubory nebo cyklicky procházet všechna aktivní okna nástrojů v integrovaném vývojovém prostředí (IDE). Můžete také přepnout přímo na libovolný soubor otevřený v editoru bez ohledu na pořadí, ve kterém byl naposledy použit. Tyto funkce mohou zvýšit vaši produktivitu při práci v integrovaném vývojovém prostředí.

> [!NOTE]
> Možnosti dostupné v dialogových oknech a názvy a umístění příkazů nabídky, které vidíte, se mohou lišit od toho, co je popsáno v nápovědě v závislosti na aktivních nastaveních nebo edici. Tato stránka Help se napsala s **obecným nastavením pro vývoj** . Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="keyboard-shortcuts"></a>Klávesové zkratky
 Téměř všechny příkazy nabídky v aplikaci Visual Studio mají klávesovou zkratku. Můžete také vytvořit vlastní zástupce. Další informace najdete v tématu [identifikace a přizpůsobení klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigating-among-files-in-the-editor"></a>Navigace mezi soubory v editoru
 K přesunu souborů otevřených v editoru můžete použít několik metod. Můžete přecházet mezi soubory na základě pořadí, ve kterém k nim přistupujete, pomocí Navigátoru IDE můžete rychle najít libovolný otevřený soubor nebo připnout oblíbené soubory na kartu a zajistit, aby byly vždy viditelné.

 Přejděte zpět a procházejte vpřed v editoru podle pořadí, ve kterém byly použity, podobně jako u back-mailů a vpřed pro zobrazení historie v aplikaci Microsoft Internet Explorer.

#### <a name="to-move-through-open-files-in-order-of-use"></a>Procházení otevřených souborů v pořadí podle použití

- Chcete-li aktivovat otevřené dokumenty v pořadí, v jakém byly naposledy změněny, stiskněte klávesu CTRL + mínus SIGN.

- Chcete-li aktivovat otevřené dokumenty v obráceném pořadí, stiskněte klávesy CTRL + SHIFT + mínus SIGN.

  > [!NOTE]
  > **Přejít zpět** a **Přejít vpřed** také najdete v nabídce **zobrazení** .

  Můžete také přepnout do konkrétního souboru otevřeného v editoru, bez ohledu na to, kdy jste ho naposledy otevřeli, pomocí seznamu aktivní soubory v editoru **rozhraní IDE**, seznam **aktivních souborů** nebo okna **Windows** .

  **Rozhraní IDE navigátor** funguje podobně jako přepínač aplikace systému Windows. Není k dispozici z nabídek a lze k nim získat přístup pouze pomocí klávesových zkratek. K zacyklování **souborů v závislosti** na pořadí, ve kterém chcete cyklicky procházet, můžete použít kterýkoli ze dvou příkazů.

  ![Visual Studio – navigátor IDE](../ide/media/vs2015-ide-navigator.png "VS2015_IDE_Navigator")

  `Window.PreviousDocumentWindowNav` vám umožňuje přesunout se k souboru, který se naposledy otevřel, a `Window.NextDocumentWindowNav` vám umožní přesunout se v obráceném pořadí. Nastavení obecného vývoje přiřadí klávesovou zkratku CTRL + SHIFT + TAB pro `Window.PreviousDocumentWindowNav` a CTRL + TAB `Window.NextDocumentWindowNav`.

> [!NOTE]
> Pokud kombinace nastavení, kterou používáte, ještě nemá přiřazenou kombinaci klávesových zkratek, můžete přiřadit vlastní příkaz pomocí stránky **klávesnice** dialogového okna **Možnosti** . Další informace najdete v tématu [identifikace a přizpůsobení klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

#### <a name="to-switch-to-specific-files-in-the-editor"></a>Přepnutí na konkrétní soubory v editoru

- Stisknutím kombinace kláves CTRL + TAB zobrazte **navigátor IDE**. Podržte stisknutou klávesu CTRL a stiskněte klávesu Tabulátor opakovaně, dokud nevyberete soubor, na který chcete přepnout.

    > [!TIP]
    > Chcete-li změnit pořadí, ve kterém procházíte seznamem **aktivních souborů** , podržte stisknuté klávesy CTRL + SHIFT a stiskněte klávesu TAB.

     \- nebo-

- V pravém horním rohu editoru klikněte na tlačítko **aktivní soubory** a potom vyberte soubor ze seznamu, na který chcete přejít.

     \- nebo-

- Na panelu nabídek vyberte možnost **okno**, okna **.**

- V seznamu vyberte soubor, který chcete zobrazit, a pak zvolte **aktivovat**.

## <a name="navigating-among-tool-windows-in-the-ide"></a>Navigace mezi okny nástrojů v integrovaném vývojovém prostředí
 **Rozhraní IDE Navigator** také umožňuje cyklicky procházet okna nástrojů, která jste otevřeli v integrovaném vývojovém prostředí (IDE). Můžete použít kterýkoli ze dvou příkazů pro přístup k **navigátoru IDE** pro přepínání mezi okny nástrojů v závislosti na pořadí, ve kterém chcete cyklicky přepínat. `Window.PreviousToolWindowNav` vám umožňuje přesunout se k souboru, který se naposledy otevřel, a `Window.NextToolWindowNav` vám umožní přesunout se v obráceném pořadí. Nastavení obecného vývoje přiřadí klávesy SHIFT + ALT + F7 k `Window.PreviousDocumentWindowNav` a ALT + F7 pro `Window.NextDocumentWindowNav`.

> [!NOTE]
> Pokud kombinace nastavení, kterou používáte, ještě nemá přiřazenou kombinaci klávesových zkratek, můžete přiřadit vlastní příkaz pomocí stránky **klávesnice** dialogového okna **Možnosti** . Další informace najdete v tématu [identifikace a přizpůsobení klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

#### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>Přepnutí na určité okno nástrojů v integrovaném vývojovém prostředí

- Stisknutím kombinace kláves ALT + F7 zobrazte **navigátor IDE**. Podržte stisknutou klávesu ALT a stiskněte klávesu F7 opakovaně, dokud nevyberete okno, na které chcete přepnout.

    > [!TIP]
    > Chcete-li změnit pořadí, ve kterém procházíte seznamem **oken aktivních nástrojů** , podržte klávesy Shift + Alt a stiskněte klávesu F7.

## <a name="see-also"></a>Viz také
 [Přizpůsobení](../ide/customizing-window-layouts-in-visual-studio.md) [výchozích klávesových zkratek](../ide/default-keyboard-shortcuts-in-visual-studio.md) pro rozložení oken

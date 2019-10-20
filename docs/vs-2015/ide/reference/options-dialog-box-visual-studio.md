---
title: Dialogové okno Možnosti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages
helpviewer_keywords:
- Tools Options settings
- Options dialog box
- Options dialog box, development environment
- tools [Visual Studio], customizing
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ed637943d7a849357338593ffc684e4f45c09a30
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662436"
---
# <a name="options-dialog-box-visual-studio"></a>Dialogové okno Možnosti (Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dialogové okno **Možnosti** umožňuje nakonfigurovat integrované vývojové prostředí (IDE) podle vašich potřeb. Můžete například vytvořit výchozí umístění pro uložení pro vaše projekty, změnit výchozí vzhled a chování systému Windows a vytvořit zástupce pro běžně používané příkazy. K dispozici jsou také možnosti specifické pro váš vývojový jazyk a platformu. **Možnosti** přístupu můžete získat z nabídky **nástroje** .

> [!NOTE]
> Možnosti dostupné v dialogových oknech a názvy a umístění příkazů nabídky, které vidíte, se mohou lišit od toho, co je popsáno v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="layout-of-the-options-dialog-box"></a>Rozložení dialogového okna Možnosti
 Dialogové okno **Možnosti** je rozdělené na dvě části: navigační podokno vlevo a oblast zobrazení na pravé straně. Strom ovládacího prvku v navigačním podokně obsahuje uzly složek, jako je prostředí, textový editor, projekty a řešení a Správa zdrojového kódu. Rozbalte uzel všechny složky a seznamte se se stránkami možností, které obsahuje. Když vyberete uzel pro konkrétní stránku, zobrazí se jeho možnosti v oblasti zobrazení.

 Možnosti pro funkci IDE se v navigačním podokně nezobrazí, dokud se funkce nenačte do paměti. Proto se stejné možnosti nemusí zobrazit při zahájení nové relace, která se zobrazila jako poslední. Při vytváření projektu nebo spuštění příkazu, který používá konkrétní aplikaci, jsou do dialogového okna Možnosti přidány uzly pro příslušné možnosti. Tyto přidané možnosti budou zůstat dostupné, pokud funkce IDE zůstane v paměti.

> [!NOTE]
> Některé kolekce nastavení rozsahují počet stránek, které se zobrazí v navigačním podokně dialogového okna Možnosti. Kliknutím na tlačítko **Zobrazit všechna nastavení**můžete zobrazit všechny možné stránky.

## <a name="how-options-are-applied"></a>Způsob použití možností
 Kliknutím na OK v dialogovém okně **Možnosti** uložíte všechna nastavení na všech stránkách. Kliknutím na zrušit na každé stránce se zruší všechny žádosti o změnu, včetně těch, které se právě udělaly na jiných stránkách **možností** . Některé změny nastavení možností, jako jsou provedené v [písmech a barvách, prostředí, dialogové okno Možnosti](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md), se projeví až po zavření a opětovném spuštění sady Visual Studio.

### <a name="show-all-settings"></a>Zobrazit všechna nastavení
 Výběr nebo zrušit výběr **Zobrazit všechna nastavení** aplikuje všechny změny provedené v dialogovém okně **Možnosti** , i když jste ještě nekliknuli na **tlačítko OK**.

## <a name="see-also"></a>Viz také
 [Vlastní nastavení editoru](../../ide/customizing-the-editor.md)

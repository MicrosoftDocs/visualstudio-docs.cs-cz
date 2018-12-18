---
title: Dialogové okno Možnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.toolsoptionspages
helpviewer_keywords:
- Tools Options settings
- Options dialog box
- Options dialog box, development environment
- tools [Visual Studio], customizing
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 373c6ad006d915412252f48ac536bb50c7ff44bf
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53048512"
---
# <a name="options-dialog-box-visual-studio"></a>Dialogové okno Možnosti (Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]


**Možnosti** dialogové okno umožňuje konfigurovat integrované vývojové prostředí (IDE) podle vašich potřeb. Můžete například vytvořit výchozí umístění pro uložení pro vaše projekty, změnit výchozí vzhled a chování systému windows a vytvoření zkratky pro často používané příkazy. Existují také možnosti specifické pro vývojový jazyk a platformu. Můžete přistupovat **možnosti** z **nástroje** nabídky.

> [!NOTE]
>  Dostupné možnosti v dialogových oknech, názvy a umístění příkazů, které vidíte, mohou lišit od informací uvedených v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="layout-of-the-options-dialog-box"></a>Rozložení dialogové okno Možnosti
 **Možnosti** dialogové okno je rozdělena na dva oddíly: navigačního podokna na levé straně a zobrazení plochy na pravé straně. Ovládací prvek stromové struktury v navigačním podokně obsahuje uzly složek, jako je například prostředí, textového editoru, projekty a řešení a správy zdrojového kódu. Rozbalte uzel všechny složky do seznamu na stránkách možností, které obsahuje. Když vyberete uzel pro konkrétní stránce, jeho možnosti se zobrazí v oblasti zobrazení.

 Možnosti pro funkci integrovaného vývojového prostředí v navigačním podokně nezobrazí, dokud tato funkce je načten do paměti. Proto nemusí být zobrazeny stejné možnosti jako zahájit novou relaci, která se zobrazí jako dokončená poslední. Při vytváření projektu nebo spustit příkaz, který používá konkrétní aplikace, uzly pro příslušné možnosti jsou přidány do dialogového okna Možnosti. Tyto přidané možnosti pak zůstanou dostupné tak dlouho, dokud zůstává funkce integrovaného vývojového prostředí v paměti.

> [!NOTE]
>  Některé nastavení kolekce oboru počet stránek, které se zobrazí v navigačním podokně dialogovém okně Možnosti. Můžete také zobrazit všechny možné stránky tak, že vyberete **zobrazit všechna nastavení**.

## <a name="how-options-are-applied"></a>Jak se používají možnosti
 Kliknutím na OK v **možnosti** dialogové okno uloží všechna nastavení na všech stránkách. Kliknutím na Storno na libovolné stránce zruší všechny žádosti o změnu, včetně všech říkám na jiné **možnosti** stránky. Některé změny nastavení možnosti, například změny na [písma a barvy, prostředí, dialogové okno Možnosti](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md), bude pouze projeví po můžete zavřít a znovu otevřete Visual Studio.

### <a name="show-all-settings"></a>Zobrazit všechna nastavení
 Výběr nebo zrušení výběru **zobrazit všechna nastavení** platí všechny změny provedené v **možnosti** dialogové okno, i když jste ještě na **OK**.

## <a name="see-also"></a>Viz také
 [Vlastní nastavení editoru](../../ide/customizing-the-editor.md)

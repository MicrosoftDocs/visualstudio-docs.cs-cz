---
title: Dialogové okno Možnosti
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages
helpviewer_keywords:
- Tools Options settings
- Options dialog box
- Options dialog box, development environment
- tools [Visual Studio], customizing
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c864a10af9ad15d47e2342bb148af464b8f2a0d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591499"
---
# <a name="options-dialog-box-visual-studio"></a>Dialogové okno Možnosti (Visual Studio)

**Možnosti** dialogové okno umožňuje konfigurovat integrované vývojové prostředí (IDE) podle vašich potřeb. Můžete například vytvořit výchozí umístění pro uložení pro vaše projekty, změnit výchozí vzhled a chování systému windows a vytvoření zkratky pro často používané příkazy. Existují také možnosti specifické pro vývojový jazyk a platformu. Můžete přistupovat **možnosti** z **nástroje** nabídky.

## <a name="layout-of-the-options-dialog-box"></a>Rozložení dialogové okno Možnosti

**Možnosti** dialogové okno je rozdělena na dva oddíly: navigačního podokna na levé straně a zobrazení plochy na pravé straně. Ovládací prvek stromové struktury v navigačním podokně obsahuje uzly složek, jako je například prostředí, textového editoru, projekty a řešení a správy zdrojového kódu. Rozbalte uzel všechny složky do seznamu na stránkách možností, které obsahuje. Když vyberete uzel pro konkrétní stránce, jeho možnosti se zobrazí v oblasti zobrazení.

Možnosti pro funkci integrovaného vývojového prostředí v navigačním podokně nezobrazí, dokud tato funkce je načten do paměti. Proto nemusí být zobrazeny stejné možnosti jako zahájit novou relaci, která se zobrazí jako dokončená poslední. Při vytváření projektu nebo spustit příkaz, který používá konkrétní aplikace, uzly pro příslušné možnosti jsou přidány do dialogového okna Možnosti. Tyto přidané možnosti pak zůstanou dostupné tak dlouho, dokud zůstává funkce integrovaného vývojového prostředí v paměti.

> [!NOTE]
> Některé nastavení kolekce oboru počet stránek, které se zobrazí v navigačním podokně dialogovém okně Možnosti. Můžete také zobrazit všechny možné stránky tak, že vyberete **zobrazit všechna nastavení**.

## <a name="how-options-are-applied"></a>Jak se používají možnosti

Kliknutím na OK v **možnosti** dialogové okno uloží všechna nastavení na všech stránkách. Kliknutím na Storno na libovolné stránce zruší všechny žádosti o změnu, včetně všech říkám na jiné **možnosti** stránky. Některé změny nastavení možnosti, například změny na [písma a barvy, prostředí, dialogové okno Možnosti](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md), bude pouze projeví po můžete zavřít a znovu otevřete Visual Studio.

### <a name="show-all-settings"></a>Zobrazit všechna nastavení

Výběr nebo zrušení výběru **zobrazit všechna nastavení** platí všechny změny provedené v **možnosti** dialogové okno, i když jste ještě na **OK**.

## <a name="see-also"></a>Viz také:

- [Vlastní nastavení editoru](../how-to-change-text-case-in-the-editor.md)

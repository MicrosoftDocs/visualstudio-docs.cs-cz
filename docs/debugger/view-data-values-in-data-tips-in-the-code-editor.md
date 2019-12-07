---
title: Zobrazení hodnot proměnných v datových tipech | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f121c7aadb605e6eb87089556ddaf1b1f4999dbb
ms.sourcegitcommit: 0b90e1197173749c4efee15c2a75a3b206c85538
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2019
ms.locfileid: "74903878"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Zobrazení hodnot dat v datových tipech v editoru kódu

DataTips poskytují pohodlný způsob, jak zobrazit informace o proměnných ve svém programu během ladění. DataTips fungovat pouze v režimu pozastavení a pouze s proměnnými, které jsou v aktuálním oboru spuštění. Pokud se jedná o první pokus o ladění kódu, můžete si před tím, než projdete Tento článek, přečíst [ladění pro naprostou začátečníky](../debugger/debugging-absolute-beginners.md) a [techniky a nástroje pro ladění](../debugger/write-better-code-with-visual-studio.md) .

## <a name="work-with-datatips"></a>Práce s DataTips

Datové tipy se zobrazí pouze v režimu pozastavení a jenom na proměnné, které jsou v aktuálním oboru spuštění.

### <a name="display-a-datatip"></a>Zobrazit DataTip

1. Nastavte zarážku v kódu a spuštění ladění stisknutím kombinace kláves **F5** nebo jeho výběru **ladění** > **spustit ladění**.

1. Při pozastavení na zarážce, najeďte myší všechny proměnné v aktuálním oboru. Zobrazí se DataTip, včetně názvu a aktuální hodnota proměnné.

### <a name="make-a-datatip-transparent"></a>Průhledný DataTip

Aby DataTip transparentní zobrazíte kód, který je pod ním při DataTip, stiskněte klávesu **Ctrl**. DataTip zůstává transparentní tak dlouho, dokud podržení **Ctrl** klíč. To nebude fungovat pro DataTips připojené nebo s plovoucí desetinnou čárkou.
### <a name="pin-a-datatip"></a>PIN kód DataTip

Pokud chcete připnout DataTip tak, aby zůstane otevřený, vyberte na ikonu připínáčku **připojit ke zdroji** ikonu.

![Připnout DataTip](../debugger/media/dbg-tips-data-tips-pinned.png "PIN kód DataTip")

Připnuté DataTip můžete přesunout přetažením kolem okna kódu. Ikoně připínáčku se zobrazí ve hřbetu vedle řádku, který DataTip je připnutá k.

>[!NOTE]
>Datové tipy jsou vždy vyhodnoceny v kontextu, ve kterém je spuštění pozastaveno, nikoli na aktuální kurzor nebo umístění datového tipu. Pokud je ukazatel myši nad proměnnou v jiné funkci, která má stejný název jako proměnné v aktuálním kontextu, zobrazí se hodnota proměnné v aktuálním kontextu.

### <a name="unpin-a-datatip-from-source"></a>Odepnout DataTip ze zdroje

Uvolnění připnuté DataTip, najeďte myší DataTip a vyberte ikonu připínáčku v místní nabídce.

Ikoně připínáčku se změní na nepřipnuté pozice a DataTip teď čísel s plovoucí čárkou nebo můžete přetáhnout nad všemi okny. S plovoucí desetinnou čárkou DataTips zavřete při ukončení relace ladění.

### <a name="repin-a-datatip"></a>Repin DataTip

Chcete-li repin DataTip s plovoucí desetinnou čárkou ke zdroji, najetí ukazatelem v editoru kódu a vyberte ikonu připínáčku. Ikoně připínáčku se změní na připojený pozice a DataTip je znovu připnout pouze do okna kódu.

Pokud je číslo s plovoucí čárkou DataTip období bez zdrojového kódu, není k dispozici na ikonu připínáčku a nemůže být DataTip repinned. Pro přístup k ikoně připínáčku, vrátíte DataTip oknem editoru kódu přetažením nebo vstup okna kódu.

### <a name="close-a-datatip"></a>Zavřete DataTip

Zavřete DataTip, najeďte myší DataTip a vyberte uzavření (**x**) ikony v místní nabídce.

### <a name="close-all-datatips"></a>Zavřete všechny DataTips

Zavřete všechny DataTips na **ladění** nabídce vyberte možnost **vymazat všechny DataTips**.

### <a name="close-all-datatips-for-a-specific-file"></a>Zavřete všechny DataTips pro konkrétní soubor

Zavřete všechny DataTips pro konkrétní soubor, na **ladění** nabídce vyberte možnost **vymazat všechny DataTips připojené k \<název souboru >** .

## <a name="expand-and-edit-information"></a>Rozbalte a upravit informace
Používání tipů DataTips rozbalte pole, struktury nebo objektu pro zobrazení členů. Můžete také upravit hodnotu proměnné z DataTip.

### <a name="expand-a-variable"></a>Rozbalit proměnnou

Rozbalte objekt v datovém tipu zobrazíte jeho prvky, najeďte myší na šipky rozbalte před názvy položek zobrazení prvků ve formuláři stromu. Připnuté DataTip, vyberte **+** před proměnnou název a potom rozbalte stromovou strukturu.

![Rozbalení DataTip](../debugger/media/dbg-tour-data-tips.png "Rozbalení DataTip")

Chcete-li přesunout nahoru a dolů v rozšířené zobrazení, můžete použít myši nebo klávesy se šipkami na klávesnici.

Můžete také připnout rozbalené položky do definovaného datového tipu ukázáním a výběrem jeho ikony připínáčku. Prvky se pak zobrazí v připojených datového tipu po sbalené stromové struktuře.

### <a name="edit-the-value-of-a-variable"></a>Upravit hodnoty proměnné

Upravte hodnotu proměnné nebo element v DataTip, vyberte hodnotu, zadejte novou hodnotu a stiskněte klávesu **Enter**. Výběr je zakázaný pro hodnoty jen pro čtení.

::: moniker range=">= vs-2019"

## <a name="pin-properties-in-datatips-supported-in-visual-studio-2019-version-164-preview-3-or-higher"></a>Vlastnosti PIN kódu v datových tipech (podporované ve verzi Visual Studio 2019 verze 16,4 Preview 3 nebo vyšší)

> [!NOTE]
> Tato funkce je podporovaná pro .NET Core 3,0 nebo vyšší.

V datatipech můžete pomocí nástroje **Pinnable Properties** rychle zkontrolovat objekty podle jejich vlastností.  Chcete-li použít tento nástroj, najeďte myší na vlastnost a vyberte ikonu připnutí, která se zobrazí, nebo klikněte pravým tlačítkem myši a v výsledné místní nabídce vyberte možnost **připnout člena jako oblíbenou** .  Tato vlastnost se zobrazí v horní části seznamu vlastností objektu a název vlastnosti a hodnota se zobrazí v pravém sloupci DataTip.  Chcete-li odebrat vlastnost, vyberte ikonu připnutí znovu nebo v místní nabídce vyberte možnost **odepnout člen jako oblíbenou** .

![Připnutí vlastnosti v DataTip](../debugger/media/basic-pin-datatip.gif "Připnutí vlastnosti v DataTip")

Při zobrazení seznamu vlastností objektu v DataTip můžete také přepínat názvy vlastností a odfiltrovat připnuté vlastnosti.  Přístup k některé možnosti získáte tak, že kliknete pravým tlačítkem myši na řádek obsahující vlastnost a vyberete možnost **Zobrazit pouze připnuté členy** nebo **Skrýt připnuté názvy členů v možnostech hodnot** v místní nabídce.

::: moniker-end

## <a name="visualize-complex-data-types"></a>Vizualizujte komplexních datových typů

Ikony lupy vedle proměnné nebo element v datovém tipu znamená, že jedna nebo více [vizualizéry](../debugger/create-custom-visualizers-of-data.md), například [Vizualizátor textu](../debugger/string-visualizer-dialog-box.md), jsou k dispozici pro proměnnou. Vizualizéry zobrazení informací lépe vystihuje, někdy grafické způsobem.

Chcete-li zobrazit prvek s použitím výchozího Vizualizér pro datový typ, vyberte ![ikonu](../debugger/media/dbg-tips-visualizer-icon.png "Ikona Vizualizátoru")lupy ikona zvětšovacího skla. Vyberte šipku vedle ikony lupy vyberte ze seznamu vizualizéry datového typu.

## <a name="add-a-variable-to-a-watch-window"></a>Přidání proměnné okno kukátka

Pokud chcete pokračovat a sledujte proměnné, můžete ji přidat **Watch** okna z DataTip. Klikněte pravým tlačítkem na proměnnou v DataTip a vyberte **Přidat kukátko**.

Proměnná se zobrazí v **Watch** okna. Pokud vaše verze sady Visual Studio podporuje více než jeden **Watch** , proměnné okno v **kukátko 1**.

## <a name="import-and-export-datatips"></a>Importovat a exportovat DataTips

Exportovat DataTips do souboru XML, který můžete sdílet nebo upravovat pomocí textového editoru. Můžete také importovat soubor XML datového tipu máte přijata nebo upravovat.

**Chcete-li exportovat DataTips:**

1. Vyberte **ladění** > **exportovat DataTips**.

1. V **exportovat DataTips** dialogové okno, přejděte do umístění pro uložení souboru XML, zadejte název souboru a pak vyberte **Uložit**.

**Chcete-li importovat datové tipy:**

1. Vyberte **ladění** > **mportovat datové tipy**.

1. V **importovat DataTips** dialogového okna, vyberte soubor DataTips XML, který chcete otevřít a pak vyberte **otevřete**.

## <a name="see-also"></a>Viz také:
- [Co je ladění?](../debugger/what-is-debugging.md)
- [Techniky a nástroje ladění](../debugger/write-better-code-with-visual-studio.md)
- [První pohled na ladění](../debugger/debugger-feature-tour.md)
- [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)
- [Okna Kukátko a Rychlé kukátko](../debugger/watch-and-quickwatch-windows.md)
- [Vytváření vlastních vizualizérů](../debugger/create-custom-visualizers-of-data.md)

---
title: Zobrazení hodnot proměnných v datatipůch | Microsoft Docs
description: Pomocí datových tipů můžete pohodlně zobrazovat informace o proměnných, včetně polí a struktur, při ladění. Můžete také upravit hodnoty.
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: 432fd50d30347972d7b1fc8222a430fc90a9e590
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149960"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Zobrazení hodnot dat v datových tipech v editoru kódu

Datové tipy poskytují pohodlný způsob zobrazení informací o proměnných v programu během ladění. Datové tipy pracují pouze v režimu pozastavení a pouze s proměnnými, které jsou v aktuálním oboru provádění. Pokud se jedná o první pokus o ladění kódu, můžete si před tím, než projdete Tento článek, přečíst [ladění pro naprostou začátečníky](../debugger/debugging-absolute-beginners.md) a [techniky a nástroje pro ladění](../debugger/write-better-code-with-visual-studio.md) .

## <a name="work-with-datatips"></a>Práce s datatipy

Datové tipy se zobrazí pouze v režimu pozastavení a pouze v proměnných, které jsou v aktuálním oboru provádění.

### <a name="display-a-datatip"></a>Zobrazit DataTip

1. Nastavte zarážku v kódu a spusťte ladění stisknutím klávesy **F5** nebo výběrem **ladění**  >  **Spustit ladění**.

1. Při pozastavení na zarážce umístěte ukazatel myši nad libovolnou proměnnou v aktuálním oboru. Zobrazí se DataTip se zobrazeným názvem a aktuální hodnotou proměnné.

### <a name="make-a-datatip-transparent"></a>Nastavení DataTip na průhledný

Aby bylo DataTip transparentní pro zobrazení kódu, který je pod ním, zatímco v DataTip, stiskněte klávesu **CTRL**. DataTip zůstane transparentní, Pokud podržíte klávesu **CTRL** . To nefunguje u připnutých nebo plovoucích datových tipů.
### <a name="pin-a-datatip"></a>Připnout DataTip

Pokud chcete DataTip připnout tak, aby zůstalo otevřené, vyberte ikonu připínáček **Připnout na zdroj** .

![Připnout DataTip](../debugger/media/dbg-tips-data-tips-pinned.png "Připnout DataTip")

Připnuté DataTip můžete přesunout přetažením kolem okna kódu. Na hřbetu vedle čáry, ke které je připnuté DataTip, se zobrazí ikona připínáčku.

>[!NOTE]
>Datové tipy jsou vždy vyhodnocovány v kontextu, kde je provádění pozastaveno, nikoli aktuální kurzor nebo umístění DataTip. Pokud najedete myší na proměnnou v jiné funkci, která má stejný název jako proměnná v aktuálním kontextu, zobrazí se hodnota proměnné v aktuálním kontextu.

### <a name="unpin-a-datatip-from-source"></a>Odepnout DataTip ze zdroje

Pokud chcete připnuté DataTip, najeďte myší na DataTip a vyberte ikonu připínáčku z kontextové nabídky.

Ikona připínáček se změní na nepřipnutý pozice a DataTip je teď floated nebo dá se přetáhnout nad všechna otevřená okna. Plovoucí datové tipy se zavřou po ukončení relace ladění.

### <a name="repin-a-datatip"></a>Znovu a DataTip

Pokud chcete znovu plovoucí DataTip na zdroj, najeďte na něj v editoru kódu a vyberte ikonu připínáčku. Ikona připínáček se změní na připnuté umístění a DataTip je znovu připnuté pouze do okna Code (kód).

Pokud je DataTip plovoucí v nezdrojovém okně kódu, ikona připínáček není k dispozici a DataTip nelze znovu připnout. Chcete-li získat přístup k ikoně připínáček, vraťte DataTip do okna editoru kódu tak, že ho přetáhnete nebo podělíte fokus okna kódu.

### <a name="close-a-datatip"></a>Zavřít DataTip

Pokud chcete DataTip zavřít, najeďte myší na DataTip a vyberte ikonu zavřít (**x**) z kontextové nabídky.

### <a name="close-all-datatips"></a>Zavřít všechny tipy

Chcete-li zavřít všechny tipy, vyberte v nabídce **ladit** možnost **Vymazat všechny datové tipy**.

### <a name="close-all-datatips-for-a-specific-file"></a>Zavřít všechny vlastnosti datatipů pro určitý soubor

Chcete-li zavřít všechny vlastnosti datatipů pro určitý soubor, v nabídce **ladění** vyberte možnost **Vymazat všechny popisy, které \<Filename> jsou připnuté na**.

## <a name="expand-and-edit-information"></a>Rozbalit a upravit informace
Můžete použít datové tipy k rozšíření pole, struktury nebo objektu k zobrazení členů. Můžete také upravit hodnotu proměnné z DataTip.

### <a name="expand-a-variable"></a>Rozbalit proměnnou

Chcete-li rozbalit objekt v DataTip a zobrazit jeho prvky, najeďte myší na šipky rozbalení před názvy položek, aby se zobrazily elementy ve formě stromu. Pro připnutý DataTip vyberte **+** před názvem proměnné a potom rozbalte strom.

![Rozbalení DataTip](../debugger/media/dbg-tour-data-tips.png "Rozbalení DataTip")

K přesunu nahoru a dolů v rozbaleném zobrazení můžete použít myš nebo klávesy se šipkami na klávesnici.

Roztažené položky můžete také připnout na připnutý DataTip tak, že je najedete myší a vyberete jejich ikony připínáčku. Prvky se pak zobrazí v připnutých DataTip po sbalení stromu.

### <a name="edit-the-value-of-a-variable"></a>Úprava hodnoty proměnné

Chcete-li upravit hodnotu proměnné nebo prvku v DataTip, vyberte hodnotu, zadejte novou hodnotu a stiskněte klávesu **ENTER**. Výběr je zakázaný pro hodnoty jen pro čtení.

::: moniker range=">= vs-2019"

## <a name="pin-properties-in-datatips"></a>Vlastnosti PIN kódu v datových tipech

> [!NOTE]
> Tato funkce je podporovaná pro .NET Core 3,0 nebo vyšší.

V datatipech můžete pomocí nástroje **Pinnable Properties** rychle zkontrolovat objekty podle jejich vlastností.  Chcete-li použít tento nástroj, najeďte myší na vlastnost a vyberte ikonu připnutí, která se zobrazí, nebo klikněte pravým tlačítkem myši a v výsledné místní nabídce vyberte možnost **připnout člena jako oblíbenou** .  Tato vlastnost se zobrazí v horní části seznamu vlastností objektu a název vlastnosti a hodnota se zobrazí v pravém sloupci DataTip.  Chcete-li odebrat vlastnost, vyberte ikonu připnutí znovu nebo v místní nabídce vyberte možnost **odepnout člen jako oblíbenou** .

![Připnutí vlastnosti v DataTip](../debugger/media/basic-pin-datatip.gif "Připnutí vlastnosti v DataTip")

Při zobrazení seznamu vlastností objektu v DataTip můžete také přepínat názvy vlastností a odfiltrovat připnuté vlastnosti.  Přístup k některé možnosti získáte tak, že kliknete pravým tlačítkem myši na řádek obsahující vlastnost a vyberete možnost **Zobrazit pouze připnuté členy** nebo **Skrýt připnuté názvy členů v možnostech hodnot** v místní nabídce.

::: moniker-end

## <a name="visualize-complex-data-types"></a>Vizualizace složitých datových typů

Ikona lupy vedle proměnné nebo elementu v DataTip znamená, že pro proměnnou je k dispozici jeden nebo více [vizualizací](../debugger/create-custom-visualizers-of-data.md), jako je například [Vizualizér textu](../debugger/string-visualizer-dialog-box.md). Vizualizace zobrazují informace smysluplnější, někdy grafickým způsobem.

Chcete-li zobrazit prvek s použitím výchozího Vizualizér pro datový typ, vyberte ![ikonu](../debugger/media/dbg-tips-visualizer-icon.png "Ikona Vizualizátoru")lupy ikona zvětšovacího skla. Vyberte šipku vedle ikony lupy a vyberte ze seznamu vizualizací pro datový typ.

## <a name="add-a-variable-to-a-watch-window"></a>Přidat proměnnou do okno Kukátko

Pokud chcete i nadále sledovat proměnnou, můžete ji přidat do okna **kukátka** z DataTip. Klikněte pravým tlačítkem na proměnnou v DataTip a vyberte **Přidat kukátko**.

Proměnná se zobrazí v okně **kukátko** . Pokud vaše edice sady Visual Studio podporuje více než jedno okno **kukátka** , proměnná se zobrazí v **kukátku 1**.

## <a name="import-and-export-datatips"></a>Import a export datových tipů

Můžete exportovat datatipů do souboru XML, který můžete sdílet nebo upravovat pomocí textového editoru. Můžete také importovat soubor XML DataTip, který jste přijali nebo upravili.

**Export datových tipů:**

1. Vyberte **ladit**  >  **Export datových tipů**.

1. V dialogovém okně **exportovat popisy** dat přejděte do umístění, kam chcete uložit soubor XML, zadejte název souboru a potom vyberte **Uložit**.

**Import datových tipů:**

1. Vyberte **ladit**  >  **Import datových tipů**.

1. V dialogovém okně **Import tipů pro** data vyberte soubor XML s popisem datatipů, který chcete otevřít, a pak vyberte **otevřít**.

## <a name="see-also"></a>Viz také
- [Co je ladění?](../debugger/what-is-debugging.md)
- [Techniky ladění a související nástroje](../debugger/write-better-code-with-visual-studio.md)
- [První pohled na ladění](../debugger/debugger-feature-tour.md)
- [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)
- [Okna Kukátko a Rychlé kukátko](../debugger/watch-and-quickwatch-windows.md)
- [Vytváření vlastních vizualizérů](../debugger/create-custom-visualizers-of-data.md)

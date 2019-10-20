---
title: Hledání a nahrazování textu a výběr vícenásobného kurzoru
ms.date: 08/14/2018
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- Find in Files dialog box
- text searches, finding and replacing text
- text, finding and replacing
- find and replace
- find text
- replace text
- multi-caret selection
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e5c4bd54e71357ff6a2d667c540953bc0057b70
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654236"
---
# <a name="find-and-replace-text"></a>Vyhledání a nahrazení textu

Text v editoru sady Visual Studio můžete vyhledat a nahradit pomocí**kláves** [Najít a nahradit](#find-and-replace-control) (CTRL +**F** nebo **CTRL** +**H**) nebo [Najít/nahradit v souborech](#find-in-files-and-replace-in-files) (**CTRL** +**SHIFT** 1 **F** nebo **CTRL** 4**SHIFT** 6**H**). Pomocí *[výběru více blikajících kurzorů](#multi-caret-selection)* můžete také vyhledat a nahradit pouze *některé* instance vzoru.

> [!TIP]
> Pokud přejmenováváte symboly kódu, jako jsou proměnné a metody, je lepší je *[Refaktorovat](../ide/reference/rename.md)* , než použití hledání a nahrazení. Refaktoring je inteligentní a pochopení rozsahu, zatímco v rámci hledání a nahrazení jsou všechny instance.

Funkce Find-and-Replace je k dispozici v editoru, v některých dalších textových oknech, jako jsou například okna **výsledků hledání** , v oknech návrháře, jako je například Návrhář XAML a Návrhář model Windows Forms, a v oknech nástrojů.

Můžete určit rozsah hledání na aktuální dokument, aktuální řešení nebo vlastní sadu složek. Můžete také zadat sadu přípon názvů souborů pro vyhledávání ve více souborech. Pomocí [regulárních výrazů](../ide/using-regular-expressions-in-visual-studio.md).NET Přizpůsobte syntaxi hledání.

> [!TIP]
> Pole [Najít/příkaz](../ide/find-command-box.md) je k dispozici jako ovládací prvek panelu nástrojů, ale ve výchozím nastavení není vidět. Chcete-li zobrazit pole **Najít/příkaz** , vyberte možnost **Přidat nebo odebrat tlačítka** na panelu nástrojů **standardní** a pak vyberte **Najít**.

## <a name="find-and-replace-control"></a>Najít a nahradit ovládací prvek

- Stiskněte klávesu **Ctrl** +**F** jako zástupce pro *vyhledání* řetězce v aktuálním souboru.
- Stisknutím **kombinace kláves Ctrl** +**H** *vyhledejte a nahraďte* řetězec v aktuálním souboru.

Ovládací prvek **Najít a nahradit** se zobrazí v pravém horním rohu okna Editor kódu. Okamžitě zvýrazní všechny výskyty daného hledaného řetězce v aktuálním dokumentu. Můžete přecházet z jednoho výskytu na jiný kliknutím na tlačítko **Najít další** nebo tlačítko **Najít předchozí** v ovládacím prvku hledání.

![Hledání a nahrazování v aplikaci Visual Studio](media/find-and-replace-box.png)

K možnostem nahrazení se dostanete tak, že vyberete tlačítko vedle textového pole **Najít** . Chcete-li provést nahrazení v jednom okamžiku, klikněte na tlačítko **nahradit další** vedle textového pole **nahradit** . Chcete-li nahradit všechny shody, klikněte na tlačítko **Nahradit vše** .

Chcete-li změnit barvu zvýraznění shody, zvolte nabídku **nástroje** , vyberte možnost **Možnosti**a pak zvolte možnost **prostředí**a vyberte možnost **písma a barvy**. V seznamu **Zobrazit nastavení pro** vyberte možnost **textový editor**a potom v seznamu **Zobrazit položky** vyberte možnost **Najít zvýraznění (rozšíření)** .

### <a name="search-tool-windows"></a>Hledání v oknech nástrojů

Můžete použít ovládací prvek **Najít** v okně Code nebo text, jako jsou například **výstupní** okna a okna **výsledků hledání** , a to tak, že vyberete **Upravit**  > **Najít a nahradit** nebo stisknout **CTRL + F**.

Verze ovládacího prvku **find** je také k dispozici v některých oknech nástrojů. Můžete například filtrovat seznam ovládacích prvků v okně **panelu nástrojů** zadáním textu do vyhledávacího pole. Další okna nástrojů, která umožňují hledání obsahu, zahrnují **Průzkumník řešení**, okno **vlastnosti** a **Team Explorer**.

## <a name="find-in-files-and-replace-in-files"></a>Najít v souborech a nahradit v souborech

- Stisknutím **kombinace kláves Ctrl** +**SHIFT** +**F** můžete *Najít* řetězec ve více souborech.
- Stisknutím **kombinace kláves Ctrl** +**SHIFT** +**H** *vyhledejte a nahraďte* řetězec ve více souborech.

Funkce **Najít/nahradit v souborech** funguje jako ovládací prvek **Najít a nahradit** s tím rozdílem, že můžete definovat rozsah pro hledání. V editoru můžete nejen vyhledat aktuální otevřený soubor, ale také všechny otevřené dokumenty, celé řešení, aktuální projekt a vybrané sady složek. Můžete také Hledat podle přípony názvu souboru. Chcete-li získat přístup k dialogovému oknu **Najít/nahradit v souborech** , vyberte v nabídce **Upravit** příkaz **Najít a nahradit** (nebo stiskněte klávesu **CTRL** +**SHIFT** +**F**).

![Najít v souborech v aplikaci Visual Studio](media/find-in-files-box.png)

### <a name="find-results"></a>Výsledky hledání

Když zvolíte **Najít vše**, otevře se okno **výsledky hledání** a zobrazí se seznam shod pro vaše hledání. Výběr výsledku v seznamu zobrazí přidružený soubor a zvýrazní shodu. Pokud soubor ještě není otevřen pro úpravy, je otevřen na kartě náhledu na pravé straně karty. Pomocí ovládacího prvku **hledání** můžete vyhledat seznam **výsledků hledání** .

### <a name="create-custom-search-folder-sets"></a>Vytváření vlastních sad složek výsledků hledání

Rozsah vyhledávání můžete definovat tak, že kliknete na tlačítko **Zvolit složky výsledků hledání** (vypadá to jako **...** ) vedle pole **Hledat v** . V dialogovém okně **Zvolit složky výsledků hledání** můžete zadat sadu složek, které se mají hledat, a uložit specifikaci, aby ji bylo možné znovu použít později.

> [!TIP]
> Pokud jste namapovali jednotku vzdáleného počítače na místní počítač, můžete určit složky, ve kterých se bude hledat na vzdáleném počítači.

### <a name="create-custom-component-sets"></a>Vytváření vlastních sad součástí

Sady součástí můžete definovat jako rozsah hledání tak, že vyberete tlačítko **Upravit sadu vlastních komponent** vedle pole **Hledat v** . Můžete určit nainstalované komponenty .NET nebo COM, projekty sady Visual Studio, které jsou součástí vašeho řešení, nebo jakékoli sestavení nebo knihovnu typů ( *. dll*, *. tlb*, *. olb*, *. exe*nebo *. ocx*). Chcete-li hledat odkazy, vyberte pole **Hledat v odkazech** .

## <a name="multi-caret-selection"></a>Výběr násobného kurzoru

> [!NOTE]
> Tato část se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [blokové výběry](/visualstudio/mac/block-selection).

**Představeno v aplikaci Visual Studio 2017 verze 15,8**

*Výběr vícenásobného kurzoru* umožňuje provést stejnou úpravu ve dvou nebo více místech současně. Můžete například vložit stejný text nebo upravit existující text ve více umístěních současně.

Na následujícím snímku obrazovky je `-0000` vybraný ve třech umístěních; Pokud uživatel stiskne klávesu **Delete**, odstraní se všechny tři výběry:

![Výběr více blikajících kurzorů v souboru XML v aplikaci Visual Studio](media/multi-caret-selection.png)

Chcete-li vybrat více blikajících kurzorů, klikněte nebo proveďte jako obvykle první výběr textu a potom stiskněte klávesu **ALT** a klikněte nebo vyberte text v každém dalším umístění. Můžete také automaticky přidat shodný text jako další výběry nebo vybrat textové pole, které lze na každém řádku upravit stejným způsobem.

> [!TIP]
> Pokud jste vybrali **ALT** jako modifikační klávesu pro možnost přejít na definici v **nabídce nástroje**  > **Možnosti**, je vícenásobný výběr vícenásobný zakázaný.

### <a name="commands"></a>Příkazy

Pro chování výběru s více kurzory použijte následující klíče a akce:

|Zástupce|Akce|
|-|-|
|**Ctrl** +**ALT** + kliknutí|Přidat sekundární blikající kurzor|
|**Ctrl** +**ALT** + poklikejte na|Přidat sekundární výběr slova|
|**Ctrl** +**ALT** + kliknutí a přetažením|Přidat sekundární výběr|
|**Shift** +**ALT** + **.**|Přidat další shodný text jako výběr|
|**Ctrl** +**Shift** +**ALT** + **,**|Přidat veškerý shodný text jako výběry|
|**Shift** +**ALT** + **,**|Odebrat poslední vybraný výskyt|
|**Ctrl** +**Shift** +**ALT** + **.**|Přeskočit další vyhovující výskyt|
|**ALT** + kliknutí|Přidat výběr pole|
|**ESC** nebo klikněte na|Vymazat všechny výběry|

Některé příkazy jsou k dispozici také v nabídce **Upravit** v části **více blikajících kurzorů**:

![Rozevírací nabídka více blikajících kurzorů v aplikaci Visual Studio](media/edit-menu-multiple-carets.png)

## <a name="see-also"></a>Viz také:

- [Použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
- [Refaktoring kódu v aplikaci Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Výběr bloku (Visual Studio pro Mac)](/visualstudio/mac/block-selection)
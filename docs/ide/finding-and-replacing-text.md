---
title: Hledání a nahrazování textu a výběr více stříšek
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffc31a0d0e2b6878b5dd5173a35ce4f538e135be
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590342"
---
# <a name="find-and-replace-text"></a>Vyhledání a nahrazení textu

Text můžete najít a nahradit v editoru Sady Visual Studio pomocí [funkce Najít a nahradit](#find-and-replace-control) **(Ctrl**+**F** nebo **Ctrl**+**H)** nebo [Najít/nahradit v souborech](#find-in-files-and-replace-in-files) **(Ctrl**+**Shift**+**F** nebo **Ctrl**+**Shift**+**H).** Můžete také najít a nahradit pouze *některé* instance vzoru pomocí *[výběru více stříšky](#multi-caret-selection)*.

> [!TIP]
> Pokud přejmenováváte symboly kódu, jako jsou proměnné a metody, je lepší je *[refaktorovat,](../ide/reference/rename.md)* než použít hledání a nahrazování. Refaktoring je inteligentní a rozumí oboru, zatímco hledání a nahrazování slepě nahrazuje všechny instance.

Funkce hledání a nahrazování je k dispozici v editoru, v některých dalších textových oknech, jako jsou okna **najít výsledky,** v návrhářských oknech, jako je například návrhář XAML a návrhář windows forms, a v oknech nástrojů.

Hledání podle rozsahu můžete do aktuálního dokumentu, aktuálního řešení nebo vlastní sady složek. Můžete také určit sadu přípon názvů souborů pro vyhledávání ve více souborech. Přizpůsobení syntaxe hledání pomocí [regulárních výrazů](../ide/using-regular-expressions-in-visual-studio.md)ROZHRANÍ .NET .

> [!TIP]
> Pole [Najít a příkaz](../ide/find-command-box.md) je k dispozici jako ovládací prvek panelu nástrojů, ale ve výchozím nastavení není viditelné. Chcete-li zobrazit pole **Najít nebo příkaz,** vyberte na panelu nástrojů **Standardní** položku Přidat **nebo odebrat tlačítka** a pak vyberte **najít**.

## <a name="find-and-replace-control"></a>Ovládací prvek Najít a nahradit

- Stisknutím **klávesy Ctrl**+**F** jako zástupce *vyhledejte* řetězec v aktuálním souboru.
- Stisknutím **klávesy Ctrl**+**H** jako zástupce *vyhledejte a nahraďte* řetězec v aktuálním souboru.

Ovládací prvek **Najít a nahradit** se zobrazí v pravém horním rohu okna editoru kódu. Okamžitě zvýrazní každý výskyt daného vyhledávacího řetězce v aktuálním dokumentu. Z jednoho výskytu na druhý můžete přecházet tak, že v ovládacím prvku hledání zvolíte tlačítko **Najít další** nebo **Najít předchozí.**

![Hledání a nahrazování v sadě Visual Studio](media/find-and-replace-box.png)

K možnostem nahrazení se dostanete výběrem tlačítka vedle textového pole **Najít.** Chcete-li provést jednu náhradu najednou, zvolte tlačítko **Nahradit další** vedle textového pole **Nahradit.** Chcete-li nahradit všechny shody, zvolte tlačítko **Nahradit vše.**

Chcete-li změnit barvu zvýraznění pro shody, zvolte nabídku **Nástroje,** vyberte **Možnosti**a pak zvolte **Prostředí**a vyberte **Písma a barvy**. V seznamu **Zobrazit nastavení vyberte** **Textový editor**a potom v seznamu **Zobrazit položky** vyberte **Najít zvýraznění (rozšíření).**

### <a name="search-tool-windows"></a>Hledat okna nástrojů

Ovládací prvek **Najít** můžete použít v kódových nebo textových oknech, například **ve výstupních** oknech a **oknech Najít výsledky,** tak, že vyberete **Upravit** > **hledání a nahrazení** nebo stisknete **Ctrl+F**.

Verze ovládacího prvku **Najít** je také k dispozici v některých oknech nástrojů. Můžete například filtrovat seznam ovládacích prvků v okně **Panel u nástrojů** zadáním textu do vyhledávacího pole. Mezi další okna nástrojů, která umožňují prohledávat jejich obsah, patří **Průzkumník řešení**, okno **Vlastnosti** a **Průzkumník týmu**.

## <a name="find-in-files-and-replace-in-files"></a>Najít v souborech a nahradit v souborech

- Stisknutím **klávesctrl**+**shift**+**f** jako zástupce *vyhledejte* řetězec ve více souborech.
- Stisknutím **klávesctrl**+**shift**+**H** jako zástupce *vyhledejte a nahraďte* řetězec ve více souborech.

**Hledání a nahrazení v souborech** funguje jako ovládací prvek **Najít a nahradit** s tím rozdílem, že můžete definovat obor pro hledání. Můžete nejen prohledávat aktuální otevřený soubor v editoru, ale také všechny otevřené dokumenty, celé řešení, aktuální projekt a vybrané sady složek. Můžete také vyhledávat podle přípony názvu souboru. Chcete-li získat přístup k dialogovému oknu **Najít nebo nahradit v souborech,** vyberte v nabídce **Úpravy** vyberte **Najít a nahradit** (nebo stiskněte **kombinaci kláves Ctrl**+**Shift**+**F).**

![Najít v souborech v sadě Visual Studio](media/find-in-files-box.png)

### <a name="find-results"></a>Najít výsledky

Když zvolíte **Najít vše**, otevře se okno **Najít výsledky** a zobrazí se seznam shod pro hledání. Výběrem výsledku v seznamu se zobrazí přidružený soubor a zvýrazní se shoda. Pokud soubor ještě není otevřený pro úpravy, otevře se na kartě náhledu na pravé straně karty dobře. Pomocí ovládacího prvku **Najít** můžete prohledávat seznam **Výsledků hledání.**

### <a name="create-custom-search-folder-sets"></a>Vytvoření vlastních sad složek hledání

Obor hledání můžete definovat tak, že vedle pole **Hledat v** zvolíte **možnost Zvolit složky výsledků hledání** (vypadá to jako **...**). V dialogovém okně **Zvolit složky výsledků hledání** můžete určit sadu složek, které chcete prohledat, a můžete ji uložit, abyste ji mohli později znovu použít.

> [!TIP]
> Pokud jste namapovali jednotku vzdáleného počítače na místní počítač, můžete zadat složky pro vyhledávání ve vzdáleném počítači.

### <a name="create-custom-component-sets"></a>Vytvoření vlastních sad součástí

Sady komponent můžete definovat jako obor hledání tak, že zvolíte tlačítko **Upravit vlastní sadu součástí** vedle pole Hledat **v.** Můžete určit nainstalované součásti .NET nebo COM, projekty sady Visual Studio, které jsou součástí vašeho řešení, nebo libovolnou knihovnu sestavení nebo typu (*DLL*, *.tlb*, *.olb*, *.exe*nebo *.ocx*). Chcete-li hledat odkazy, vyberte pole **Hledat v odkazech.**

## <a name="multi-caret-selection"></a>Výběr více stříšek

> [!NOTE]
> Tato část se týká sady Visual Studio v systému Windows. Visual Studio pro Mac najdete [v tématu Výběr bloků](/visualstudio/mac/block-selection).

**Představeno ve Visual Studiu 2017 verze 15.8**

Pomocí *výběru více stříšky* proveďte stejné úpravy na dvou nebo více místech současně. Můžete například vložit stejný text nebo upravit existující text ve více umístěních současně.

Na následujícím snímku `-0000` obrazovky je vybrána na třech místech; Pokud uživatel stiskne **klávesu Delete**, budou odstraněny všechny tři výběry:

![Výběr více stříšek v souboru XML v sadě Visual Studio](media/multi-caret-selection.png)

Chcete-li vybrat více stříšk, klepněte na první výběr textu nebo je proveďte obvyklým způsobem a stiskněte **klávesu Alt,** zatímco klepnete nebo vyberete text v každém dalším umístění. Můžete také automaticky přidat odpovídající text jako další výběry nebo vybrat pole textu, které chcete upravit stejně na každém řádku.

> [!TIP]
> Pokud jste jako modifikační klávesu pro příkaz Přejděte do definice v**možnostech** **nástrojů** > vybrali **možnost Alt** , výběr více stříšky je zakázán.

### <a name="commands"></a>Příkazy

Pro chování výběru více stříšky použijte následující klávesy a akce:

|Zástupce|Akce|
|-|-|
|**Ctrl**+**Alt** + klikněte|Přidání sekundární stříšky|
|**Ctrl**+**Alt** + poklepnutí|Přidání sekundárního výběru slov|
|**Ctrl**+**Alt** + klikněte + táhnout|Přidání sekundárního výběru|
|**Shift**+**Alt**+**.**|Přidání dalšího odpovídajícího textu jako výběru|
|**Ctrl**+**Shift**+**Alt**+**,**|Přidání všech odpovídajících textů jako výběrů|
|**Shift**+**Alt**+**,**|Odebrat naposledy vybraný výskyt|
|**Ctrl**+**Shift**+**Alt**+**.**|Přeskočit další odpovídající výskyt|
|**Alt** + kliknutí|Přidání výběru rámečku|
|**Esc** nebo klikněte|Vymazání všech výběrů|

Některé příkazy jsou také k dispozici v nabídce **Upravit** v části **Více sazek**:

![Více stříšky fly-out menu v sadě Visual Studio](media/edit-menu-multiple-carets.png)

## <a name="see-also"></a>Viz také

- [Použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
- [Refaktorovat kód v sadě Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Výběr bloků (Visual Studio pro Mac)](/visualstudio/mac/block-selection)

---
title: Najít a nahradit text a výběr více blikajícího kurzoru
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findinfiles
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6120d1ece56e24712fd1217090159ec627f88d61
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349098"
---
# <a name="find-and-replace-text"></a>Vyhledání a nahrazení textu

Můžete najít a nahradit text v editoru sady Visual Studio s použitím [najít a nahradit](#find-and-replace-control) nebo [najít/nahradit v souborech](#find-in-files-and-replace-in-files). Nová funkce v sadě Visual Studio 2017 verze 15.8, můžete najít a nahradit *některé* instance modelu s použitím  *[více blikající kurzor o výběr](#multi-caret-selection)*.

> [!TIP]
> Pokud se přejmenování symboly kódu, jako jsou proměnné a metody, je lepší *[Refaktorujte](../ide/reference/rename.md)* je než můžete najít a nahradit. Refaktoring je inteligentní a rozumí oboru, zatímco najít a nahradit slepě nahradí všechny instance.

Funkce Najít a nahradit je k dispozici v editoru, v některých jiných oknech založený na textu, jako **výsledky hledání** windows, v oknech návrháře, jako je například Návrhář XAML a Návrhář formulářů Windows a v oknech nástrojů.

Můžete nastavit obor hledání na aktuální dokument, aktuální řešení nebo vlastní sadu složek. Můžete také zadat sadu přípon názvů souborů pro vyhledávání s více soubory. Přizpůsobení syntaxi vyhledávání s použitím rozhraní .NET [regulární výrazy](../ide/using-regular-expressions-in-visual-studio.md).

> [!TIP]
> [Najít/příkaz](../ide/find-command-box.md) pole je k dispozici jako ovládací prvek panelu nástrojů, ale není ve výchozím nastavení viditelný. Chcete-li zobrazit **najít/příkaz** vyberte **přidat nebo odebrat tlačítka** na **standardní** nástrojů a pak vyberte **najít**.

## <a name="find-and-replace-control"></a>Najít a nahradit řídící prvek

**Najít a nahradit** ovládací prvek se zobrazí v pravém horním rohu okna editoru kódu. **Najít a nahradit** ovládací prvek okamžitě zvýrazní všechny výskyty daného hledaného řetězce v aktuálním dokumentu. Můžete přecházet z jednoho výskytu na jiný výběrem **najít další** tlačítko nebo **najít předchozí** tlačítka na ovládacím prvku hledání.

![Najít a nahradit v sadě Visual Studio](media/find-and-replace-box.png)

Možnostem výměny můžete přejít kliknutím na tlačítko vedle **najít** textového pole. Chcete-li nahrazovat po jednom čas, zvolte **nahradit další** vedle **nahradit** textového pole. Chcete-li nahradit všechny shody, zvolte **Nahradit vše** tlačítko.

Chcete-li změnit barvu zvýraznění shody, zvolte **nástroje** nabídce vyberte možnost **možnosti**a klikněte na tlačítko **prostředí**a vyberte **písma a barvy** . V **zobrazit nastavení pro** seznamu vyberte **textový Editor**a pak v **zobrazení položek** seznamu vyberte **najít zvýraznění (rozšíření)**.

### <a name="search-tool-windows"></a>Hledání oken nástrojů

Můžete použít **najít** v ovládacím prvku kódu nebo textových oknech, jako například **výstup** windows a **výsledky hledání** windows tak, že vyberete **upravit**  >  **Najít a nahradit** nebo stiskněte **Ctrl + F**.

Verze **najít** ovládací prvek je k dispozici také v některých oknech nástrojů. Například můžete filtrovat seznam ovládacích prvků v **nástrojů** okna tak, že zadáte text do vyhledávacího pole. Zahrnout ostatním oknům nástrojů, které umožňují prohledávat jejich obsah **Průzkumníku řešení**, **vlastnosti** okně a **Team Exploreru**.

## <a name="find-in-files-and-replace-in-files"></a>Najít v souborech a nahradit v souborech

**Najít/nahradit v souborech** funguje jako **najít a nahradit** řídit, s tím rozdílem, že můžete definovat rozsah hledání. Nejenže můžete vyhledávat v aktuálně otevřeném souboru v editoru, ale také všech otevřených dokumentech, celém řešení, aktuálního projektu a vybrané sadě složek. Můžete také vyhledat pomocí přípony názvu souboru. Přístup **najít/nahradit v souborech** dialogu **najít a nahradit** na **upravit** nabídky nebo stisknutím klávesy **Ctrl + Shift + F**.

![Najít v souborech v sadě Visual Studio](media/find-in-files-box.png)

### <a name="find-results"></a>Výsledky hledání

Pokud zvolíte **najít všechny**, **výsledky hledání** okno se otevře a zobrazí seznam odpovídajících položek pro hledání. Výběr výsledku v seznamu zobrazí přidružený soubor a zvýrazní shodu. Pokud soubor ještě není otevřený pro úpravy, bude otevřen v kartě preview na pravé straně karty dobře. Můžete použít **najít** ovládací prvek prohledávat **výsledky hledání** seznamu.

### <a name="create-custom-search-folder-sets"></a>Vytvoření sad složek pro vlastní vyhledávání

Můžete definovat obor hledání výběrem **zvolit složky pro hledání** tlačítko (vypadá jako **...** ) vedle položky **Hledat v** pole. V **zvolit složky pro hledání** dialogové okno, můžete určit sadu složek pro hledání a specifikaci můžete uložit tak, aby jej můžete znovu použít později.

> [!TIP]
> Pokud jste změnili jednotky vzdáleném počítači do svého místního počítače, můžete určit složky pro hledání na vzdáleném počítači.

### <a name="create-custom-component-sets"></a>Vytvoření vlastních sad součástí

Součást sady můžete definovat jako obor hledání výběrem **upravit sadu vlastních komponent** vedle **Hledat v** pole. Můžete určit nainstalované součásti .NET nebo COM, projekty aplikace Visual Studio, které jsou součástí vašeho řešení nebo libovolné sestavení nebo typ knihovny (*.dll*, *.tlb*, *.olb*, *.exe*, nebo *.ocx*). Chcete-li prohledat odkazy, vyberte **Hledat v odkazech** pole.

## <a name="multi-caret-selection"></a>Výběr více blikajícího kurzoru

> [!NOTE]
> Tato část se týká sady Visual Studio ve Windows. Visual Studio pro Mac, najdete v části [běr bloku](/visualstudio/mac/block-selection).

**Novinka v sadě Visual Studio 2017 verze 15.8**

Použití *více blikající kurzor o výběr* provádět stejné úpravy ve dvou nebo více míst ve stejnou dobu. Například můžete vložit stejný text nebo změnit stávající text v několika umístěních ve stejnou dobu.

Na následujícím snímku obrazovky `-0000` je vybrána ve třech umístěních; Pokud uživatel stiskne **odstranit**, odstraní se všechny tři možnosti:

![Výběr více blikající kurzor do souboru XML v sadě Visual Studio](media/multi-caret-selection.png)

Pokud chcete vybrat více střížek, klikněte na nebo obvyklým způsobem provést první výběr textu a stiskněte klávesu **Alt** klikněte na tlačítko nebo vybrat text v každé další umístění. Můžete také automaticky přidat odpovídající text jako další výběry nebo vyberte pole text, který má upravit stejně jako na každém řádku.

> [!TIP]
> Pokud jste vybrali **Alt** jako modifikační klávesa pro kliknutí myší přejít k definici v **nástroje** > **možnosti**, více blikající kurzor o výběr je zakázaný.

### <a name="commands"></a>Příkazy

Použijte následující klíče a akcí pro výběr více blikající kurzor o chování:

|Zástupce|Akce|
|-|-|
|**CTRL**+**Alt** + klikněte na|Přidat sekundární blikajícího kurzoru|
|**CTRL**+**Alt** + dvakrát klikněte na panel|Přidat sekundární slovo výběr|
|**CTRL**+**Alt** + klikněte na + přetažení|Přidat sekundární výběr|
|**SHIFT**+**Alt**+**.**|Přidejte další odpovídající text jako výběr|
|**CTRL**+**Shift**+**Alt**+**,**|Přidejte všechny odpovídající text jako výběry|
|**SHIFT**+**Alt**+**,**|Odebrat posledního výskytu vybrané|
|**CTRL**+**Shift**+**Alt**+**.**|Přeskočit další odpovídající výskyt|
|**ALT** + klikněte na|Přidat pole výběru|
|**ESC** nebo klikněte na tlačítko|Zrušte zaškrtnutí všech výběrů|

Některé příkazy jsou také k dispozici na **upravit** nabídky v části **více Střížek**:

![Více střížek rozevírací nabídce v sadě Visual Studio](media/edit-menu-multiple-carets.png)

## <a name="see-also"></a>Viz také:

- [Použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
- [Refaktorování kódu v sadě Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Výběr bloku (Visual Studio for Mac)](/visualstudio/mac/block-selection)
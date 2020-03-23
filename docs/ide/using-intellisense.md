---
title: Informace o parametrech, členy seznamu a rychlé informace
ms.date: 05/25/2018
ms.topic: conceptual
f1_keywords:
- vc.tools.intellisense
helpviewer_keywords:
- Quick info
- Parameter info
- Complete word
- List members
- IntelliSense [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34e038256d46909e135f8285cb1b3edc45d0ba3e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565341"
---
# <a name="intellisense-in-visual-studio"></a>Technologie IntelliSense v sadě Visual Studio

IntelliSense je podpora pro dokončení kódu, která obsahuje řadu funkcí: Seznam členů, Informace o parametrech, Rychlé informace a Kompletní word. Tyto funkce vám pomohou získat další informace o kódu, který používáte, sledovat parametry, které zadáváte, a přidávat volání do vlastností a metod s několika stisky kláves.

Mnoho aspektů technologie IntelliSense je specifických pro jazyk. Další informace o technologie IntelliSense pro různé jazyky naleznete v tématech uvedených v části [Viz také.](#see-also)

## <a name="list-members"></a>Vypsat členy

Seznam platných členů z typu (nebo oboru názvů) se zobrazí po zadání`.`znaku aktivační `::` události (například tečka ( ) ve spravovaném kódu nebo v jazyce C++). Pokud budete pokračovat v psaní znaků, seznam se vyfiltruje tak, aby zahrnoval pouze členy, které začínají těmito znaky nebo kde začátek *libovolného* slova v názvu začíná těmito znaky. IntelliSense také provádí "camel case" odpovídající, takže stačí zadat první písmeno každého velblouda-obalené slovo v názvu člena vidět zápasy.

Po výběru položky ji můžete vložit do kódu stisknutím **klávesy Tab** nebo zadáním mezery. Pokud vyberte položku a zadáte období, položka se zobrazí s uvedenou dobou, která vyvolá jiný seznam členů. Pokud vyberete položku, ale ještě před jejím vložením, zobrazí se rychlé informace pro položku.

V seznamu členů ikona vlevo představuje typ členu, například obor názvů, třídu, funkci nebo proměnnou. Seznam ikon naleznete v [tématu Zobrazení tříd a ikony prohlížeče objektů](../ide/class-view-and-object-browser-icons.md). Seznam může být poměrně dlouhý, takže můžete stisknout **PgUp** a **PgDn,** abyste se v seznamu posunuli nahoru nebo dolů.

![Seznam členů sady Visual Studio](../ide/media/vs2015_intellisense.png)

Funkci Členové **seznamu** můžete vyvolat ručně zadáním **klávesctrl**+**j**, výběrem **příkazu Upravit** > **členy seznamu****IntelliSense** > nebo výběrem tlačítka **Seznam členů** na panelu nástrojů editoru. Při vyvolání na prázdném řádku nebo mimo podporovaný rozsah zobrazí seznam symboly v globálním oboru názvů.

Chcete-li funkce Členové seznamu ve výchozím nastavení vypnout (aby se nezobrazovala, pokud není konkrétně vyvolána), přejděte na**možnosti** >  **nástrojů** > **Všechny jazyky** a zrušte výběr **členů seznamu Automaticky**. Pokud chcete vypnout seznam členů pouze pro určitý jazyk, přejděte do **obecného** nastavení pro daný jazyk.

Můžete také změnit nastavení na režim návrhu, ve kterém je do kódu vložen pouze text, který zadáte. Pokud například zadáte identifikátor, který není v seznamu, a stisknete **klávesu Tab**, v režimu dokončení by položka nahradila zadaný identifikátor. Chcete-li přepínat mezi režimem dokončení a režimem návrhů, stiskněte **kombinaci kláves Ctrl**+**Alt**+**Space**nebo zvolte **Upravit** > **režim dokončování technologie****IntelliSense** > .

## <a name="parameter-info"></a>Informace o parametrech

Informace o parametru poskytují informace o počtu, názvech a typech parametrů vyžadovaných metodou, atributem parametru obecného typu (v jazyce C#) nebo šablonou (v jazyce C++).

Parametr tučně označuje další parametr, který je vyžadován při zadávání funkce. Pro přetížené funkce můžete pomocí kláves se šipkami **nahoru** a **dolů** zobrazit informace o alternativních parametrech pro přetížení funkce.

![Informace o parametrech](../ide/media/vs2015_param_info.png)

Když opatřujete poznámkami funkce a parametry s komentáři XML dokumentace, komentáře se zobrazí jako informace o parametru. Další informace naleznete [v tématu Supply XML code comments](reference/generate-xml-documentation-comments.md).

Informace o parametrech můžete ručně vyvolat tak, že **zvolíte Upravit** > **informace o parametrech IntelliSense****IntelliSense** > , stisknutím **klávesctrlshift**+**Shift**+**mezery**nebo výběrem tlačítka Informace o **parametrech** na panelu nástrojů editoru.

## <a name="quick-info"></a>Rychlé informace

Rychlé informace zobrazí úplnou deklaraci pro libovolný identifikátor ve vašem kódu.

![Rychlé informace k Visual Studiu](../ide/media/vs2015_quick_info.png)

Když vyberete člena z pole **Členové seznamu,** zobrazí se také rychlé informace.

![Informace o parametru v souboru kódu C&#35;](../ide/media/vs2015_paraminfo.png)

Rychlé informace můžete ručně vyvolat tak, že **zvolíte Upravit** > **rychlé informace****technologie IntelliSense** > , stisknutím **klávesy Ctrl**+**I**nebo výběrem tlačítka **Rychlé informace** na panelu nástrojů editoru.

Pokud je funkce přetížena, technologie IntelliSense nemusí zobrazit informace pro všechny formy přetížení.

Funkce Rychlé informace pro kód c++ můžete vypnout tak, že přejdete do**Options** > **textového editoru textových** >  **editorů nástroje** > **C/C++** > **a**nastavíte automatické rychlé **informace** na `false`.

## <a name="complete-word"></a>Dokončit slovo

Dokončit aplikaci Word dokončí zbytek proměnné, příkazu nebo názvu funkce poté, co jste zadali dostatek znaků pro rozmíslábnout termín. Aplikaci Complete Word můžete vyvolat tak, že zvolíte **Upravit** > **aplikaci IntelliSense** > **Complete Word**, stisknutím **klávesy Ctrl**+**Space**nebo výběrem tlačítka **Dokončit slovo** na panelu nástrojů editoru.

## <a name="intellisense-options"></a>Možnosti technologie IntelliSense

Možnosti technologie IntelliSense jsou standardně povoleny. Chcete-li je vypnout, zvolte**Textový editor** **možností** >  **nástroje** > a odznačte **informace o parametrech** nebo **členy automatického seznamu,** pokud nechcete, aby byla funkce Seznam členů.

## <a name="intellisense-icons"></a>Ikony technologie IntelliSense
Ikony v systému IntelliSense mohou s modifikátory ikon zprostředkovat další význam. Jedná se o hvězdy, srdce a zámky vrstvené na ikonu objektu, které vyjadřují chráněné, interní nebo soukromé.

|    Ikona    |    Přístupnost    |    Popis    |
|------------|--------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![Modifikátor veřejné ikony](../ide/media/intellisensePublicNoModifier.png)       |    Veřejná třída    |    Přístup není omezen.   |
| ![Modifikátor chráněné ikony](../ide/media/intellisenseProtectedModifier.png)       |    Chráněná třída    |    Přístup je omezen na obsahující třídy nebo typy odvozené z obsahující třídy.    |
| ![Modifikátor chráněné vnitřní ikony](../ide/media/intellisenseProtectedInternalModifier.png)       |    Chráněná vnitřní třída    |    Přístup je omezen na aktuální sestavení nebo typy odvozené z obsahující třídy.    |
| ![Modifikátor vnitřní ikony](../ide/media/intellisenseInternalModifier.png)       |    Vnitřní třída    |    Přístup je omezen na aktuální sestavení.    |
|![Modifikátor soukromé ikony](../ide/media/intellisensePrivateModifier.png)        |    Soukromá třída    |    Přístup je omezen na obsahující třídy nebo typy odvozené z obsahující třídy v rámci aktuálního sestavení. (K dispozici od C# 7.2.)    |

## <a name="troubleshoot-intellisense"></a>Poradce při potížích s technologiemi IntelliSense

Možnosti technologie IntelliSense nemusí v určitých případech fungovat podle očekávání.

**Kurzor je pod chybou kódu.** Je možné, že technologie IntelliSense nebude možné použít, pokud v kódu nad kurzorem existuje neúplná funkce nebo jiná chyba, protože technologie IntelliSense nemusí být schopna analyzovat prvky kódu. Tento problém lze vyřešit okomentováním odpovídajícího kódu.

**Kurzor je v komentáři kódu.** IntelliSense nelze použít, pokud je kurzor v komentáři ve zdrojovém souboru.

**Kurzor je v řetězci literálu.** IntelliSense nelze použít, pokud je kurzor v uvozovkách kolem literálu řetězce, jako v následujícím příkladu:

```cpp
MessageBox( hWnd, "String literal|")
```

**Automatické možnosti jsou vypnuty.** Ve výchozím nastavení funguje technologie IntelliSense automaticky, ale můžete ji zakázat. Použít funkci IntelliSense můžete i v případě, že je zakázáno automatické dokončování.

## <a name="see-also"></a>Viz také

- [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md)
- [C# IntelliSense](../ide/visual-csharp-intellisense.md)
- [JavaScript IntelliSense](../ide/javascript-intellisense.md)
- [Psát a refaktorovat kód (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Zadat komentáře kódu XML](reference/generate-xml-documentation-comments.md)

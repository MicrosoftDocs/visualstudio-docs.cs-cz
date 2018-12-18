---
title: Informace o parametrech, vypsat členy a rychlé informace
ms.date: 05/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vc.tools.intellisense
helpviewer_keywords:
- Quick info
- Parameter info
- Complete word
- List members
- IntelliSense [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e00b43f1705079a86d511239d7b38119868d8f4
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748472"
---
# <a name="intellisense-in-visual-studio"></a>IntelliSense v sadě Visual Studio

IntelliSense je podpory doplňování kódu, který zahrnuje celou řadu funkcí: seznam členů, informace o parametrech, rychlé informace a úplný Word. Tyto funkce umožňují získat další informace o kód, který používáte, udržování přehledu o parametry při psaní a přidejte volání metody s jenom pár stisknutí kláves a vlastnosti.

Mnoho aspektů technologie IntelliSense je specifických pro jazyk. Další informace o technologii IntelliSense pro různé jazyky, najdete v tématech uvedených v [viz také](#see-also) části.

## <a name="list-members"></a>Vypsat členy

Po zadání znaku aktivační události se zobrazí seznam platný členy z typu (nebo obor názvů) (například dobu (`.`) ve spravovaném kódu nebo `::` v jazyce C++). Pokud budete pokračovat, zadejte znaky, je v seznamu vyfiltrován, aby obsahoval pouze členové, které začínají tyto znaky nebo kde začátku *žádné* slova v názvu začíná tyto znaky. IntelliSense také provede "camelCase" párování, takže první písmeno každého slova ve formátu camelCase můžete zadat jenom název člena můžete zobrazit shody.

Po výběru položky, můžete jej přidat do vašeho kódu stisknutím **kartě** nebo zadáním mezerou. Pokud vyberte položku a zadáte období, položka se zobrazí s uvedenou dobou, která vyvolá jiný seznam členů. Pokud vyberete položku, ale ještě před jejím vložením, zobrazí se rychlé informace pro položku.

V seznamu členů ikona vlevo představuje typ členu, například obor názvů, třídu, funkci nebo proměnnou. Seznam ikon, naleznete v části [ikony zobrazení třídy a prohlížeč objektů](../ide/class-view-and-object-browser-icons.md). V seznamu může být poměrně dlouho, můžete stisknout **PgUp** a **Page Down** přesunout nahoru nebo dolů v seznamu.

![Seznam členů v sadě Visual Studio](../ide/media/vs2015_intellisense.png)

Můžete vyvolat **vypsat členy** funkce ručně zadáním **Ctrl**+**J**, výběrem možnosti **upravit**  >  **IntelliSense** > **vypsat členy**, nebo výběrem **vypsat členy** tlačítka na panelu nástrojů editoru. Při vyvolání na prázdném řádku nebo mimo podporovaný rozsah zobrazí seznam symboly v globálním oboru názvů.

Chcete-li vypsat členy vypnout ve výchozím nastavení (tak to nezobrazí, dokud konkrétně vyvolat), přejděte na **nástroje** > **možnosti** > **všechny jazyky**a zrušte výběr **automatický seznam členů**. Pokud chcete vypnout vypsat členy pouze pro konkrétní jazyk, přejděte k **Obecné** nastavení pro tento jazyk.

Můžete také změnit nastavení na režim návrhu, ve kterém je do kódu vložen pouze text, který zadáte. Například zadejte identifikátor, který se nenachází v seznamu a stiskněte klávesu **kartě**, při dokončení by režimu položku nahradit identifikátor typu. K přepnutí mezi dokončení režim a režim návrhu, stiskněte klávesu **Ctrl**+**Alt**+**místo**, nebo zvolte **upravit**  >  **IntelliSense** > **přepnout režim dokončení**.

## <a name="parameter-info"></a>Informace o parametrech

Informace o parametru poskytují informace o počtu, názvech a typech parametrů vyžadovaných metodou, atributem parametru obecného typu (v jazyce C#) nebo šablonou (v jazyce C++).

Parametr tučně označuje další parametr, který je vyžadován při zadávání funkce. Přetížené funkce, můžete použít **až** a **dolů** klávesy se šipkami zobrazit informace o alternativní parametr pro přetížení funkce.

![Informace o parametrech](../ide/media/vs2015_param_info.png)

Když opatřujete poznámkami funkce a parametry s komentáři XML dokumentace, komentáře se zobrazí jako informace o parametru. Další informace najdete v tématu [komentáře kódu XML zadat](../ide/supplying-xml-code-comments.md).

Informace o parametrech můžete vyvolat ručně tak, že zvolíte **upravit** > **IntelliSense** > **informace o parametrech**, stisknutím klávesy **Ctrl**  + **Shift**+**místo**, nebo výběrem **informace o parametrech** tlačítka na panelu nástrojů editoru.

## <a name="quick-info"></a>Rychlé informace

Rychlé informace zobrazí úplnou deklaraci pro libovolný identifikátor ve vašem kódu.

![Rychlé informace sadě Visual Studio](../ide/media/vs2015_quick_info.png)

Když vyberete člena z **vypsat členy** pole, se také zobrazí rychlé informace.

![Informace o parametrech v a C&#35; souboru kódu](../ide/media/vs2015_paraminfo.png)

Rychlé informace můžete vyvolat ručně tak, že zvolíte **upravit** > **IntelliSense** > **rychlé informace**, stisknutím klávesy **Ctrl** + **I**, nebo výběrem **rychlé informace** tlačítka na panelu nástrojů editoru.

Pokud je funkce přetížena, technologie IntelliSense nemusí zobrazit informace pro všechny formy přetížení.

Můžete vypnout rychlé informace pro C++ – kód přechodem na **nástroje** > **možnosti** > **textového editoru** > **C / C++** > **Upřesnit**a nastavení **automaticky rychlé informace** k `false`.

## <a name="complete-word"></a>Dokončit slovo

Dokončení Word dokončí zbytek proměnnou, příkaz nebo název funkce po zadání dostatečný počet znaků k rozlišení termín. Dokončení Word můžete vyvolat výběrem **upravit** > **IntelliSense** > **dokončení Word**, stisknutím klávesy **Ctrl** + **Místo**, nebo výběrem **dokončení Word** tlačítka na panelu nástrojů editoru.

## <a name="intellisense-options"></a>Možnosti IntelliSense

Možnosti technologie IntelliSense jsou standardně povoleny. Chcete-li je vypnout, vyberte **nástroje** > **možnosti** > **textového editoru** a zrušte výběr **informace o parametrech**nebo **automatický seznam členů** Pokud nechcete, aby funkci seznamu členů.

## <a name="troubleshoot-intellisense"></a>Řešení potíží s IntelliSense

Možnosti technologie IntelliSense nemusí v určitých případech fungovat podle očekávání.

**Kurzor je pod chybě s kódem.** Není možné použít technologii IntelliSense, pokud neúplná funkce nebo jiná chyba existuje v kódu výše kurzor, protože nemusí být schopen analyzovat elementy kódu technologie IntelliSense. Tento problém lze vyřešit okomentováním odpovídajícího kódu.

**Kurzor se nachází v komentář ke kódu.** IntelliSense nelze použít, pokud kurzor se nachází v komentáře ve zdrojovém souboru.

**Kurzor se nachází v řetězcový literál.** IntelliSense nelze použít, pokud kurzor se nachází v uvozovkách řetězcový literál, jako v následujícím příkladu:

```cpp
MessageBox( hWnd, "String literal|")
```

**Možnosti automatického jsou vypnuté.** Ve výchozím nastavení IntelliSense funguje automaticky, ale můžete ji zakázat. Použít funkci IntelliSense můžete i v případě, že je zakázáno automatické dokončování.

## <a name="see-also"></a>Viz také:

- [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md)
- [C# IntelliSense](../ide/visual-csharp-intellisense.md)
- [JavaScript IntelliSense](../ide/javascript-intellisense.md)
- [Zápis a refactor kódu (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Zadat komentáře kódu XML](../ide/supplying-xml-code-comments.md)
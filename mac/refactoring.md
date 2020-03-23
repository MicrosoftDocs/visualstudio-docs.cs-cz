---
title: Refaktoring kódu
description: Vylepšování kódu pomocí Visual Studia pro Mac a rychlých akcí.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 5a87b87f3a14462daec1e069fe222164818d2a19
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "67691288"
---
# <a name="refactoring"></a>Refaktoring

Refaktoring kód je způsob, jak změnit uspořádání, restrukturalizaci a objasnění existující kód při zajištění, že celkové chování kódu nezmění.

Refaktoring vytváří zdravější základ kódu, takže je použitelnější, čitelnější a udržovatelné pro vás nebo jiného vývojáře nebo uživatele, který může odkazovat na kód.

Visual Studio pro integraci Macu s Roslyn, open source platformou kompilátoru .NET od Microsoftu, umožňuje další refaktoringové operace.

## <a name="renaming"></a>Přejmenování

Příkaz *Rename* refactoring lze použít na libovolný identifikátor kódu (například název třídy, název vlastnosti atd.) k vyhledání všech výskytů tohoto identifikátoru a jejich změně. Chcete-li symbol přejmenovat, klikněte na něj pravým tlačítkem myši a zvolte **Přejmenovat...** nebo použijte vazbu kláves **Cmd (啦) + R:**

![Přejmenovat položku nabídky](media/refactoring-renaming1.png)

Tím se symbol a všechny odkazy na něj zvýrazní. Když začnete psát nový název, automaticky změní všechny odkazy v kódu a změny můžete potvrdit stisknutím **klávesy Enter**:

![Přejmenování a identifikátor](media/refactoring-renaming2.png)

## <a name="quick-actions"></a>Rychlé akce

Rychlé akce umožňují snadno refaktorovat, generovat nebo jinak upravovat kód pomocí jediné akce.

Rychlé akce lze použít k:

* Použití opravy kódu pro porušení pravidel analyzátoru kódu
* Potlačení porušení pravidel analyzátoru kódu
* Použití refaktoringu (například vložky dočasné proměnné)
* Generovat kód (například zavést místní proměnnou)

Rychlé akce lze použít pomocí ![ikony žárovky](media/quick-actions-light-bulb-icon.png) nebo ![ikony](media/quick-actions-screwdriver-icon.png) ikon šroubováku šroubováku nebo stisknutím tlačítka **Option (?)**+**Enter,** když je kurzor na řádku kódu, pro který je k dispozici akce. Pokud je k dispozici ![červená vlnovka](media/quick-actions-error-light-bulb-icon.png) označující chybu, zobrazí se ikona chybové žárovky chyby žárovky a visual studio má k dispozici opravu pro tuto chybu.

Pro libovolný jazyk mohou třetí strany poskytnout vlastní diagnostiku a návrhy, například jako součást sady SDK, a žárovky sady Visual Studio se na základě těchto pravidel rozsvítí.

### <a name="quick-action-icons"></a>Ikony rychlé akce
Ikona, která se zobrazí, když je k dispozici rychlá akce, ukazuje typ opravy nebo refaktoringu, který je k dispozici. ](media/quick-actions-screwdriver-icon.png) Ikona *šroubováku šroubováku* ![označuje pouze to, že jsou k dispozici akce pro změnu kódu, ale neměli byste je nutně používat. Ikona *žárovky žluté žárovky* ![označuje, že jsou k dispozici akce, které byste měli udělat pro zlepšení kódu. *should* ](media/quick-actions-light-bulb-icon.png) Ikona chybové *žárovky* ![error bulb indikuje, že je k dispozici akce, která opravuje chybu ve vašem kódu.](media/quick-actions-error-light-bulb-icon.png)

### <a name="to-see-a-light-bulb-or-screwdriver"></a>Zobrazení žárovky nebo šroubováku

- Pokud je k dispozici oprava, žárovky se spontánně zobrazí, když najedete myší na místo chyby.

   ![Žárovka s myší vznášející se](media/refactoring-lightbulb-hover.png)

- Žárovky a šroubováky se zobrazí v levém okraji editoru, když přesunete stříška do řádku kódu, pro který je k dispozici rychlá akce.

- Stisknutím **klávesy Option ((?)**+**Zadejte** libovolné místo na řádku, abyste viděli seznam dostupných rychlých akcí a refaktoringů.

![Zobrazit kontextové položky](media/refactoring-context-action.png)

Najetím na libovolnou kontextovou akce získáte náhled toho, co bude přidáno nebo odebráno z vašeho kódu.

![Možnost zadat položky kontextu](media/refactoring-image2a.png)

Chcete-li tyto možnosti povolit, musíte vybrat *možnost Povolit zdrojovou analýzu otevřených souborů* v možnostech **Visual Studio for Mac > Preferences > Textový editor > zdrojové analýzy**:

![Povolení zdrojové analýzy](media/refactoring-options.png)

Existuje více než 100 možných akcí, které lze navrhnout, které jsou povolené nebo zakázané procházením **Visual Studio pro Mac > předvolby > zdrojové analýzy > C# > akce kódu** a výběrem nebo zrušením výběru pole vedle akce:

![Akce analýzy zdroje jazyka C#](media/refactoring-image3a.png)

### <a name="common-quick-actions"></a>Běžné rychlé akce

Další informace o běžných rychlých akcích najdete v článku [Běžné rychlé akce.](/visualstudio/ide/common-quick-actions)

## <a name="source-analysis"></a>Zdrojová analýza

Zdrojová analýza analyzuje váš kód průběžně tím, že zdůrazňuje potenciální chyby a porušení stylu a poskytuje automatické opravy jako kontextové akce.

Všechny výsledky zdrojové analýzy pro libovolný soubor můžete kdykoli zobrazit zobrazením posuvníku na pravé straně textového editoru:

![Postranní panel Zdrojová analýza](media/refactoring-image4a.png)

Pokud kliknete na kruh v horní části, můžete iterate přes každý návrh, s nejvyšší závažnosti problémy zobrazeny jako první. Najetím ukazatele na jednotlivý výsledek nebo řádek zobrazí problém, který lze opravit prostřednictvím kontextových akcí:

![Položka analýzy zdroje](media/refactoring-image5.png)

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>Viz také

- [Rychlé akce (Visual Studio ve Windows)](/visualstudio/ide/quick-actions)
- [Refaktoringový kód (Visual Studio v systému Windows)](/visualstudio/ide/refactoring-in-visual-studio)
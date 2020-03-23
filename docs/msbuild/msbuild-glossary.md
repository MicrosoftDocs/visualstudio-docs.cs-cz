---
title: Glosář MSBuild
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f20fdb4cd809e422bc33535f3143b45db99842f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633340"
---
# <a name="msbuild-glossary"></a>Glosář MSBuild

Tyto termíny se používají k popisu Modulu sestavení Microsoft (MSBuild) a jeho součástí.

## <a name="glossary"></a>Glosář

AssemblyFoldersEx\
Umístění registru, kde dodavatelé třetích stran ukládají cesty pro každou verzi rámce, které podporují, kde může řešení času návrhu vyhledat referenční sestavení.

dávkování\
Dávkování znamená rozdělení položek do různých kategorií známých jako *dávky*na základě metadat položky a následné spuštění cíle nebo úkolu jednou pomocí každé dávky. Dávkování je MSBuild ekvivalent for--loop konstrukce. Další informace naleznete v [tématu Batching](../msbuild/msbuild-batching.md).

obor sestavení\
Obor sestavení popisuje objekt MSBuild, například globální vlastnost, která je potenciálně viditelná pro projekt a všechny podřízené projekty, které jsou vytvořeny v sestavení více projektů.

podřízený projekt\
Viz *projekt, dítě*.

podmínka\
Mnoho prvků MSBuild lze definovat podmíněně; to znamená, `Condition` že atribut se zobrazí v prvku. Obsah podmíněných prvků jsou ignorovány, pokud `true`podmínka vyhodnotí . Další informace naleznete v tématu [Podmínky](../msbuild/msbuild-conditions.md).

definice, položka\
Viz *definice položky*.

vyzařují položku\
Během fáze provádění sestavení lze položky vytvořit nebo upravit `Output` úkoly, `ItemName` které mají podřízené prvky, které mají atribut. Úkol je řekl, aby "vyzařovat" nové položky.

vyzařovat vlastnost\
Během fáze provádění sestavení mohou být vlastnosti vytvořeny nebo `Output` změněny úkoly, které mají podřízené prvky, které mají `PropertyName` atribut. Úkol je řekl, aby "vyzařovat" nový majetek.

fáze hodnocení\
Hodnocení je první fáze sestavení projektu. Všechny vlastnosti a položky jsou vyhodnocovány v pořadí, ve kterém se zobrazují v projektu. Importované projekty jsou vyhodnocovány tak, jak se vyskytují v projektu. Cíle a úkoly nejsou spuštěny až do fáze provádění a všechny vlastnosti nebo položky, které deklarují nebo vyzařují, jsou během hodnocení ignorovány.

fáze provádění\
Spuštění je druhá fáze sestavení projektu. Vybrané cíle jsou sestaveny a úlohy jsou spuštěny. Vlastnosti a položky lze vytvořit nebo upravit ve srovnání s jejich hodnotami vyhodnocení.

funkce, vlastnost\
Viz *funkce vlastnosti*.

funkce, položka\
Viz funkce položky.

položka\
Položky jsou vstupy do systému sestavení a jsou seskupeny do typů položek na základě jejich názvů prvků. Položky obvykle představují soubory. Vzhledem k tomu, že položky jsou pojmenovány podle typu položky, ke které patří, lze zaměnitelné termíny *a* *hodnotu položky.* Další informace naleznete v [tématu Items](../msbuild/msbuild-items.md).

definice položky\
Skupiny definic položek obsahují definice položek, které přidávají výchozí metadata k libovolnému typu položky. Stejně jako známá metadata je výchozí metadata přidružena ke všem položkám zadaného typu položky. Výchozí metadata mohou být explicitně přepsána v definici položky. Další informace naleznete v [tématu Definice položek](../msbuild/item-definitions.md).

funkce položky\
Funkce položky získat informace o položkách v projektu. Tyto funkce zjednodušit získávání Distinct() položky a jsou rychlejší než opakování prostřednictvím položek. Existují funkce pro manipulaci s cestami a řetězci položek. Další informace naleznete v [tématu Item functions](../msbuild/item-functions.md).

metadata položky\
Viz *metadata, položka*.

typ položky\
Typy položek jsou pojmenované seznamy položek, které lze použít jako parametry pro úkoly. Úkoly používají hodnoty položek k provedení kroků procesu sestavení. Další informace naleznete v [tématu Items](../msbuild/msbuild-items.md).

metadata, položka\
Metadata položky je kolekce párů název-hodnota, která je přidružena k položce. Metadata poskytuje popisné informace pro položku a je volitelné, s výjimkou známých metadat. Další informace naleznete v [tématu Items](../msbuild/msbuild-items.md).

metadata, dobře známá\
Známá metadata jsou metadata položky jen pro čtení, která je inicializována pomocí předdefinované hodnoty. Známá metadata poskytují popisné informace pro položku, která odkazuje na soubor. Například hodnota známých metadat s názvem `FullPath` je úplná cesta odkazovaného souboru. Další informace naleznete v [tématu Items](../msbuild/msbuild-items.md).

multicílení\
Možnost pro aplikace nebo sestavení projektu cílit mnoho různých CLR a architektury z MSBuild a z Visual Studio.

profil\
Podmnožina úplného rámce. Používá se k minimalizaci množství, které je třeba stáhnout do počítače.

soubor projektu\
Soubor projektu obsahuje skript MSBuild, který řídí sestavení. Soubory projektu mají obvykle příponu souboru, která končí *proj*, například *.csproj* nebo *.vbproj*. Soubory projektu mohou importovat soubory vlastností a cílové soubory.

vlastnost\
Vlastnost je pár klíč hodnota, který se používá k řízení procesu sestavení. Další informace naleznete v tématu [MSBuild vlastnosti](../msbuild/msbuild-properties.md).

vlastnost, prostředí\
Vlastnost prostředí je vlastnost, která je automaticky inicializována na hodnotu proměnné systémového prostředí, která má stejný název. Další informace naleznete v tématu [MSBuild vlastnosti](../msbuild/msbuild-properties.md).

soubor vlastností\
Soubor vlastností je soubor projektu, který obsahuje převážně skupiny vlastností a skupiny položek, které řídí sestavení. Podle konvence, To má příponu *.props*. Soubory vlastností se obvykle importují na začátku přidružených souborů projektu.

vlastnost, funkce\
Funkce vlastnosti je vlastnost systému nebo metoda, kterou lze použít k vyhodnocení skriptů MSBuild. Metody vlastností lze použít ke čtení systémového času, porovnání řetězců, shody regulárních výrazů a provádění dalších akcí. Další informace naleznete v [tématu Property functions](../msbuild/property-functions.md).

vlastnost, vnořené\
Funkce vlastností mohou být kombinovány tak, aby vytvářely složitější funkce. Například:

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

Další informace naleznete v [tématu Property functions](../msbuild/property-functions.md).

vlastnost, globální\
Globální vlastnost je pár klíč hodnota, který se používá k řízení procesu sestavení. Globální vlastnosti jsou nastaveny na příkazovém řádku nebo pomocí `Properties` atributu [úlohy MSBuild](../msbuild/msbuild-task.md)a nelze je změnit během fáze hodnocení sestavení. Další informace naleznete v tématu [MSBuild vlastnosti](../msbuild/msbuild-properties.md).

vlastnost, místní\
Místní vlastnost je pár klíč hodnota, který se používá k řízení procesu sestavení. Tento termín se používá pouze k rozlišení vlastnosti, která není globální vlastnost.

vlastnost, registr\
Vlastnost registru má hodnotu, která je nastavena pomocí speciální syntaxe, která čte hodnotu podklíče systémového registru. Další informace naleznete v tématu [MSBuild vlastnosti](../msbuild/msbuild-properties.md).

vlastnost, vyhrazeno\
Rezervovaná vlastnost je pár klíč hodnota, který se používá k řízení procesu sestavení. Rezervované vlastnosti jsou automaticky inicializovány na předdefinované hodnoty. Další informace naleznete v tématu [MSBuild vlastnosti](../msbuild/msbuild-properties.md).

obor projektu\
Obor projektu popisuje Objekt MSBuild, například místní vlastnost, která je viditelná pouze v obsahující soubor projektu a všechny projekty, které importuje.

projekt, podřízený\
Podřízený projekt je vytvořen úkolem MSBuild během sestavení projektu. Tento nový projekt je podřízený projekt, který obsahuje nebo importuje cíl, který obsahuje úkol MSBuild. Podřízený projekt dědí globální vlastnosti nadřazeného `Properties` projektu, pokud nejsou změněny atributem.

redist list\
Redistribution list: seznam sestavení, které odpovídají dané rámci.

referenční sestavení\
Sestavení, které se používá během návrhu k vytvoření aplikace. Referenční sestavení může mít skutečný kód a privátní rozhraní z něj odebrána, takže pouze metadata a veřejná rozhraní.

vlastnost registru\
Viz *vlastnost, registr*.

cíl\
Cíl seskupuje úkoly v určitém pořadí a zpřístupňuje části souboru projektu jako vstupní body do procesu sestavení. Další informace naleznete v tématu [Cíle](../msbuild/msbuild-targets.md).

cíl, budova\
Podívejte se na cíl, běží.

cíl, vyhodnocení\
Z důvodu přírůstkové kompilace musí být cíle analyzovány pro potenciální změny vlastností a položek. I v případě, že cíl je přeskočen, tyto změny musí být provedeny. Vyhodnocení cíle znamená provedení této analýzy a provedení těchto změn. Další informace naleznete [v tématu Přírůstková sestavení](../msbuild/incremental-builds.md).

cíl, provedení\
Provedení cíle znamená vyhodnocení a provádění všech úloh, které nemají žádné podmínky nebo jejichž podmínky jsou vyhodnoceny jako pravdivé. Během přírůstkové kompilace mohou být cíle přeskočeny nebo provedeny, ale jsou vždy vyhodnoceny. Další informace naleznete v tématu cíl, hodnocení.

cíl, spuštěný\
Cíl, který má podmínku, která je vyhodnocena jako false není spuštěna, to znamená, že nemá žádný vliv na sestavení. Cíle, které běží, jsou buď provedeny nebo přeskočeny. V obou případech je cíl vyhodnocen. Další informace naleznete v tématu cíl, hodnocení.

cíl, přeskakování\
Pokud přírůstková kompilace určuje, že všechny výstupní soubory jsou aktuální, pak je cíl přeskočen, to znamená, že cíl je vyhodnocen, ale úkoly v rámci cíle nejsou provedeny. Další informace naleznete v tématu cíl, hodnocení.

zástupný název rozhraní target\
Název, který popisuje rámec (například . NETFramework, Silverlight atd.), verze a profil (například Klient, Server atd.), na které chcete cílit.

balíček cílení\
Seznam sestavení, které jsou distribuovány s danou rámci a sadu referenčních sestavení pro tento rámec.

cílí na soubor\
Soubor cílů je soubor projektu, který obsahuje převážně cíle a úkoly, které řídí sestavení. Podle konvence, Má příponu *.targets*. Cílové soubory se obvykle importují na konci přidružených souborů projektu.

úkol\
Úkoly jsou jednotky spustitelného kódu, které projekty MSBuild používají k provádění operací sestavení. Úloha může například zkompilovat vstupní soubory nebo spustit externí nástroj. Další informace naleznete v [tématu Úkoly](../msbuild/msbuild-tasks.md).

transformace\
Transformace je převod 1:1 jedné kolekce položek do jiné. Kromě povolení projektu převést kolekce položek, transformace umožňuje cíl identifikovat přímé mapování mezi jeho vstupy a výstupy. Další informace naleznete v [tématu Transformace](../msbuild/msbuild-transforms.md).

známá metadata\
Viz *metadata, dobře známá*.

## <a name="see-also"></a>Viz také

- [Msbuild](../msbuild/msbuild.md)

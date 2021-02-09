---
title: Slovníček nástroje MSBuild
description: Seznamte se s terminologie Microsoft Build Engine (MSBuild), které popisují modul sestavení a jeho součásti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e6e5ef85ffc4a10719cfbef79cbaf6dad08bdbf0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919119"
---
# <a name="msbuild-glossary"></a>Slovníček nástroje MSBuild

Tyto výrazy slouží k popisu Microsoft Build Engine (MSBuild) a jeho součástí.

## <a name="assemblyfoldersex"></a>AssemblyFoldersEx

Umístění v registru, kde dodavatelé třetích stran uchovávají cesty pro každou verzi rozhraní .NET Framework, které podporují, kde řešení pro dobu návrhu může vyhledat referenční sestavení.

## <a name="batching"></a>dávkování

Dávkování znamená rozdělení položek do různých kategorií, které jsou v závislosti na metadatech položek známé jako *dávky*, a následným spuštěním cíle nebo úlohy jednou pomocí každé dávky. Dávkování je ekvivalentem konstruktoru smyčky for--Loop. Další informace najdete v tématu [dávkování](../msbuild/msbuild-batching.md).

## <a name="build-scope"></a>obor sestavení

Obor sestavení popisuje objekt MSBuild, například globální vlastnost, která je potenciálně viditelná pro projekt, a pro všechny podřízené projekty, které jsou vytvořeny v sestavení více projektů.

## <a name="child-project"></a>podřízený projekt

Viz *projekt, podřízená položka*.

## <a name="condition"></a>pomocné

Mnoho elementů MSBuild lze definovat podmíněně. To znamená, že `Condition` se atribut objeví v elementu. Obsah podmíněných elementů je ignorován, pokud není podmínka vyhodnocena jako `true` . Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).

## <a name="definition-item"></a>definice, položka

Viz *definice položky*.

## <a name="emit-item"></a>Generovat položku

Během fáze provádění sestavení mohou být položky vytvořeny nebo upraveny úlohami, které mají podřízené `Output` prvky, které mají `ItemName` atribut. Tato úloha se označuje jako "generování" nových položek.

## <a name="emit-property"></a>Emit – vlastnost

Během fáze provádění sestavení lze vlastnosti vytvořit nebo upravit pomocí úloh, které mají podřízené `Output` prvky, které mají `PropertyName` atribut. Tato úloha se označuje jako "vygenerování" nové vlastnosti.

## <a name="evaluation-phase"></a>fáze hodnocení

Hodnocení je první fází sestavení projektu. Všechny vlastnosti a položky jsou vyhodnocovány v pořadí, v jakém jsou uvedeny v projektu. Importované projekty jsou vyhodnocovány při jejich zjištění v projektu. Cíle a úkoly nejsou spuštěny, dokud fáze provádění a žádné vlastnosti nebo položky, které by mohly být deklarovány nebo generovány, se během hodnocení ignorují.

## <a name="execution-phase"></a>fáze provádění

Provádění je druhá fáze sestavení projektu. Vybrané cíle jsou sestavené a úlohy jsou spouštěny. Vlastnosti a položky lze vytvořit nebo upravit v porovnání s hodnotami jejich vyhodnocování.

## <a name="function-property"></a>funkce, vlastnost

Viz *funkce vlastnosti*.

## <a name="function-item"></a>funkce, položka

Viz funkce Item.

## <a name="item"></a>položka

Položky jsou vstupy do systému sestavení a jsou seskupeny do typů položek, které jsou založeny na jejich názvech elementů. Položky obvykle reprezentují soubory. Vzhledem k tomu, že položky jsou pojmenovány typem položky, ke kterému patří, lze s hodnotou *položku* a *hodnota položky* použít zaměnitelné. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).

## <a name="item-definition"></a>definice položky

Skupiny definic položek obsahují definice položek, které přidávají výchozí metadata k libovolnému typu položky. Podobně jako dobře známá metadata jsou výchozí metadata spojena se všemi položkami zadaného typu položky. Výchozí metadata lze explicitně přepsat v definici položky. Další informace naleznete v tématu [Definice položek](../msbuild/item-definitions.md).

## <a name="item-function"></a>Item – funkce

Funkce položky získávají informace o položkách v projektu. Tyto funkce zjednodušují získání jedinečných položek () a jsou rychlejší než přechází mezi položkami. K dispozici jsou funkce pro manipulaci s cestami a řetězci položek. Další informace najdete v tématu [funkce položek](../msbuild/item-functions.md).

## <a name="item-metadata"></a>metadata položky

Viz *metadata, položka*.

## <a name="item-type"></a>typ položky

Typy položek jsou pojmenované seznamy položek, které lze použít jako parametry pro úlohy. Úkoly používají hodnoty položek k provedení kroků procesu sestavení. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).

## <a name="metadata-item"></a>metadata, položka

Metadata položky jsou kolekce párů název-hodnota, které jsou přidruženy k položce. Metadata poskytují popisné informace pro položku a jsou volitelné, s výjimkou dobře známých metadat. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).

## <a name="metadata-well-known"></a>dobře známá metadata

Dobře známá metadata jsou metadata položky jen pro čtení, která jsou inicializována pomocí předdefinované hodnoty. Dobře známá metadata poskytují popisné informace pro položku, která odkazuje na soubor. Například hodnota známých metadat s názvem `FullPath` je úplná cesta k odkazovanému souboru. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).

## <a name="multitargeting"></a>cílení na více verzí

Schopnost projektu aplikace nebo sestavení cílit na mnoho různých rozhraní CLR a z nástroje MSBuild a ze sady Visual Studio.

## <a name="profile"></a>profil

Podmnožina celého rozhraní. Slouží k minimalizaci množství, které je třeba stáhnout do počítače.

## <a name="project-file"></a>soubor projektu

Soubor projektu obsahuje skript MSBuild, který řídí sestavení. Soubory projektu mají obvykle příponu souboru, která končí na *proj*, jako je například *. csproj* nebo *. vbproj*. Soubory projektu mohou importovat soubory vlastností a cílové soubory.

## <a name="property"></a>property

Vlastnost je pár klíč-hodnota, který slouží k řízení procesu sestavení. Další informace najdete v tématu [Vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md).

## <a name="property-environment"></a>vlastnost, prostředí

Vlastnost prostředí je vlastnost, která se automaticky inicializuje na hodnotu systémové proměnné prostředí, která má stejný název. Další informace najdete v tématu [Vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md).

## <a name="property-file"></a>soubor vlastností

Soubor vlastností je soubor projektu, který obsahuje převážně skupiny vlastností a skupiny položek, které sestavují sestavení. Podle konvence má Přípona souboru *. props*. Soubory vlastností jsou obvykle importovány na začátek přidružených souborů projektu.

## <a name="property-function"></a>vlastnost, funkce

Funkce vlastnosti je systémová vlastnost nebo metoda, která se dá použít k vyhodnocení skriptů MSBuild. Metody vlastností lze použít ke čtení systémového času, porovnávání řetězců, porovnávání regulárních výrazů a provádění dalších akcí. Další informace najdete v tématu [funkce vlastností](../msbuild/property-functions.md).

## <a name="property-function-nested"></a>funkce Property, vnořená

Funkce vlastností mohou být kombinovány pro vytvoření složitějších funkcí. Třeba

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

Další informace najdete v tématu [funkce vlastností](../msbuild/property-functions.md).

## <a name="property-global"></a>vlastnost, globální

Globální vlastnost je pár klíč-hodnota, který slouží k řízení procesu sestavení. Globální vlastnosti jsou nastaveny na příkazovém řádku nebo pomocí `Properties` atributu [úlohy MSBuild](../msbuild/msbuild-task.md)a nelze je změnit během fáze hodnocení sestavení. Další informace najdete v tématu [Vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md).

## <a name="property-local"></a>vlastnost, místní

Místní vlastnost je pár klíč-hodnota, který slouží k řízení procesu sestavení. Tento termín slouží pouze k odlišení vlastnosti, která není globálních vlastností.

## <a name="property-registry"></a>vlastnost, registr

Vlastnost registru obsahuje hodnotu, která je nastavena pomocí speciální syntaxe, která čte hodnotu podklíče systémového registru. Další informace najdete v tématu [Vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md).

## <a name="property-reserved"></a>vlastnost, vyhrazená

Vyhrazená vlastnost je pár klíč-hodnota, který slouží k řízení procesu sestavení. Vyhrazené vlastnosti jsou automaticky inicializovány na předdefinované hodnoty. Další informace najdete v tématu [Vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md).

## <a name="project-scope"></a>projekt – rozsah

Obor projektu popisuje objekt MSBuild, například místní vlastnost, která je viditelná pouze v obsahujícím souboru projektu a na všech projektech, které importuje.

## <a name="project-child"></a>projekt, podřízený

Podřízený projekt je vytvořen úlohou MSBuild během sestavení projektu. Tento nový projekt je podřízenou položkou projektu, který obsahuje nebo importuje cíl, který obsahuje úlohu MSBuild. Podřízený projekt dědí globální vlastnosti nadřazeného projektu, pokud nejsou upraveny `Properties` atributem.

## <a name="redist-list"></a>seznam Redist

Seznam opětovných distribucí: seznam sestavení, která odpovídají danému rozhraní.

## <a name="reference-assembly"></a>referenční sestavení

Sestavení, které se používá během doby návrhu k vytvoření aplikace. Referenční sestavení může mít z něj odebrán skutečný kód a privátní rozhraní a přitom ponechává jenom metadata a veřejná rozhraní.

## <a name="registry-property"></a>vlastnost registru

Viz *vlastnost, registr*.

## <a name="target"></a>cílové

Cílová skupina seskupuje úlohy v určitém pořadí a zpřístupňuje oddíly souboru projektu jako vstupní body do procesu sestavení. Další informace najdete v tématu [cíle](../msbuild/msbuild-targets.md).

## <a name="target-building"></a>cíl, sestavení

Viz cíl, spuštěno.

## <a name="target-evaluating"></a>cíl, vyhodnocení

Z důvodu přírůstkové kompilace je nutné analyzovat cíle pro případné změny vlastností a položek. I v případě, že je cíl vynechán, je nutné provést tyto změny. Vyhodnocení cíle znamená provedení této analýzy a provedení těchto změn. Další informace naleznete v tématu [přírůstkové sestavení](../msbuild/incremental-builds.md).

## <a name="target-executing"></a>cíl, provádění

Provedení cíle znamená vyhodnocení a spuštění všech úloh, které nemají žádné podmínky nebo jejichž podmínky jsou vyhodnoceny jako pravdivé. Během přírůstkové kompilace mohou být cíle vynechány nebo vykonány, ale jsou vždy vyhodnoceny. Další informace najdete v tématu cíl a vyhodnocení.

## <a name="target-running"></a>cíl, spuštěný

Cíl, který má podmínku, která je vyhodnocena jako false, není spuštěn, to znamená, že nemá na sestavení žádný vliv. Cíle, které běží, se spustí nebo přeskočí. V obou případech se cíl vyhodnocuje. Další informace najdete v tématu cíl a vyhodnocení.

## <a name="target-skipping"></a>cíl, přeskočení

Pokud přírůstková kompilace zjistí aktuálnost všech výstupních souborů, bude cíl vynechán, to znamená, že cíl je vyhodnocen, ale úkoly v cíli nebudou provedeny. Další informace najdete v tématu cíl a vyhodnocení.

## <a name="target-framework-moniker"></a>moniker cílového rozhraní .NET Framework

Název, který popisuje rozhraní (například. NETFramework, Silverlight atd.), verzi a profil (například klient, server atd.), na který chcete cílit.

## <a name="targeting-pack"></a>sada targeting pack

Seznam sestavení, která jsou distribuována pomocí dané architektury a sady referenčních sestavení pro tuto architekturu.

## <a name="targets-file"></a>soubor cílů

Soubor cílů je soubor projektu, který obsahuje hlavně cíle a úlohy, které sestavují sestavení. Podle konvence má příponu souboru *. targets*. Cílové soubory jsou obvykle importovány na konci přidružených souborů projektu.

## <a name="task"></a>úkol

Úlohy jsou jednotky spustitelného kódu, který projekty MSBuild používají k provádění operací sestavení. Například úloha může kompilovat vstupní soubory nebo spustit externí nástroj. Další informace najdete v tématu [úlohy](../msbuild/msbuild-tasks.md).

## <a name="transform"></a>transform

Transformace je převod 1:1 na jednu kolekci položek na jiný. Kromě povolení projektu pro převod kolekcí položek umožňuje transformace cíli identifikovat přímé mapování mezi vstupy a výstupy. Další informace najdete v tématu [transformace](../msbuild/msbuild-transforms.md).

## <a name="well-known-metadata"></a>dobře známá metadata

Podívejte *se na metadata, dobře známá*.

## <a name="see-also"></a>Viz také

- [MSBuild](../msbuild/msbuild.md)

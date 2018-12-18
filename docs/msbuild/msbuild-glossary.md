---
title: Slovníček nástroje MSBuild | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf51cbc4cd20401f17f5e92def47713c6107f3d2
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078752"
---
# <a name="msbuild-glossary"></a>Slovníček nástroje MSBuild
Tyto podmínky se používají k popisu Microsoft Build Engine (MSBuild) a jeho součástí.  
  
## <a name="glossary"></a>Slovníček  
 AssemblyFoldersEx  
 Umístění registru, kam ukládat externích dodavatelů cesty pro každou verzi rozhraní framework, které podporují, kde můžete zobrazit návrh čas rozlišení lze nalézt odkaz na sestavení.  
  
 dávkování  
 Dávkování znamená, že dělení položek do různých kategorií známo jako *dávky*založená na metadata položky a pak spusťte cíl nebo úloha jeden čas pomocí jednotlivých dávek. Dávkování je ekvivalentem MSBuild pro--smyčky konstrukce. Další informace najdete v tématu [dávkování](../msbuild/msbuild-batching.md).  
  
 obor sestavení  
 Obor sestavení popisuje objekt MSBuild, třeba globální vlastností, která je potenciálně viditelný na projekt a všechny podřízené projekty, které jsou vytvořené v sestaveních s více projekty.  
  
 podřízený projekt  
 Zobrazit *projektu, podřízené*.  
  
 Podmínka  
 Mnoho prvků MSBuild může podmíněně; definovaný To znamená `Condition` atributu se zobrazí v elementu. Obsah podmíněných prvků se ignoruje, pokud je podmínka vyhodnocena jako `true`. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).  
  
 definice, položky  
 Zobrazit *položky definice*.  
  
 Generování položky  
 Během fáze spuštění sestavení, můžete položky vytvořené nebo změněné úloh, které mají podřízené `Output` prvky, které mají `ItemName` atribut. Úloha se říká, že "generování" nové položky.  
  
 Generovat vlastnost  
 Během fáze spuštění sestavení, můžete být vlastnosti vytvoření nebo úpravě úlohy, které mají podřízené `Output` prvky, které mají `PropertyName` atribut. Úloha se říká, že "generování" novou vlastnost.  
  
 fáze hodnocení  
 Hodnocení je první fáze sestavení projektu. Všechny vlastnosti a položky se vyhodnocují v pořadí, v jakém jsou uvedeny v projektu. Importované projekty jsou vyhodnocovány, jak se vyskytují v projektu. Cíle a úlohy se nespustí, dokud fáze spuštění a žádné vlastnosti nebo položky by deklarovat nebo generování ignorují během vyhodnocení.  
  
 fáze spuštění  
 Spuštění je druhá fáze sestavení projektu. Vybrané cíle jsou integrované a jsou spouštěny úkoly. Může být vytvoření nebo úpravě vlastností a položek ve srovnání s jejich hodnoty hodnocení.  
  
 Funkce, vlastnost  
 Zobrazit *vlastnost funkce*.  
  
 funkce položek  
 Zobrazit položky funkce.  
  
 položka  
 Položky jsou vstupy do systému sestavení a jsou seskupeny do typů položek podle jejich názvy elementů. Položky obvykle představují soubory. Protože položky jsou pojmenovány podle typu položky patří do podmínky *položky* a *hodnota položky* zaměnitelné. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).  
  
 definice položky  
 Skupinách definic položek obsahovat definice položek, které aplikacím dodávají výchozí metadat na libovolný typ položky. Stejně jako známých metadat je přidružen k všechny položky daného typu určenou položku metadat výchozí. V definici položky lze explicitně přepsat výchozí metadat. Další informace najdete v tématu [definice položek](../msbuild/item-definitions.md).  
  
 Funkce Item  
 Funkce položek získat informace o položkách v projektu. Tyto funkce zjednodušují získávání Distinct() položek a jsou rychlejší než položky ve smyčce. Nejsou k dispozici funkce pro manipulaci s cesty položky a řetězce. Další informace najdete v tématu [položky funkce](../msbuild/item-functions.md)  
  
 metadata položky  
 Zobrazit *metadata položky*.  
  
 Typ položky  
 Seznam položek, které lze použít jako parametry pro úkoly jsou pojmenované typy položek. Úkoly pomocí hodnoty položek k provedení kroků procesu sestavení. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).  
  
 metadata, položka  
 Metadata položky je kolekce dvojic název hodnota, která je přidružena položce. Metadata poskytuje popisné informace pro položku a je volitelné, s výjimkou dobře známé metadat. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).  
  
 metadata známé  
 Metadata známé je jen pro čtení položky metadat, který je inicializován pomocí předdefinované hodnoty. Metadata známé poskytuje popisné informace pro položku, která odkazuje na soubor. Například hodnota dobře známé metadat s názvem `FullPath` je úplná cesta odkazovaný soubor. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).  
  
 cílení na více verzí  
 Možnost pro aplikace nebo sestavení projekt cílit na mnoha různých CLR a rozhraní MSBuild a ze sady Visual Studio.  
  
 Profil  
 Podmnožinu úplné rozhraní framework. To umožňuje minimalizovat, kterou je potřeba stáhnout do počítače.  
  
 soubor projektu  
 Soubor projektu obsahuje MSBuild skript, který určuje sestavení. Soubory projektu obvykle mají příponu souboru, který končí *proj*, jako například *.csproj* nebo *.vbproj*. Soubory projektu mohou importovat soubory vlastnost a cílové soubory.  
  
 property  
 Vlastnost je pár klíč hodnota, která slouží k řízení procesu sestavení. Další informace najdete v tématu [vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md).  
  
 vlastnost, prostředí  
 Vlastnost prostředí je vlastnost, která je automaticky inicializován na hodnotu proměnné prostředí systému, který má stejný název. Další informace najdete v tématu [vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md).  
  
 Vlastnosti souboru  
 Soubor vlastností je soubor projektu, který obsahuje většinou vlastnosti skupin a skupin položek, které provedou sestavení. Podle konvence má příponu souboru *.props*. Soubory vlastností se importují obvykle na začátku přidružené soubory projektu.  
  
 Vlastnost – funkce  
 Systémová vlastnost nebo metoda, která slouží k vyhodnocení skriptů nástroje MSBuild je vlastnost funkce. Metody vlastností je možné přečíst systémový čas, porovnat řetězce, porovnat regulární výrazy a provádět jiné akce. Další informace najdete v tématu [funkce vlastností](../msbuild/property-functions.md).  
  
 Vlastnosti funkce, vnořené  
 Funkce vlastností mohou být kombinovány do další komplexní funkce. Například  
  
 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`  
  
 Další informace najdete v tématu [funkce vlastností](../msbuild/property-functions.md).  
  
 Vlastnost global  
 Globální vlastnost je pár klíč hodnota, která slouží k řízení procesu sestavení. Globální vlastnosti jsou nastaveny na příkazovém řádku nebo pomocí `Properties` atribut [úlohy nástroje MSBuild](../msbuild/msbuild-task.md)a nelze změnit během fáze vyhodnocení sestavení. Další informace najdete v tématu [vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md).  
  
 Vlastnosti místní  
 Místní vlastnost je pár klíč hodnota, která slouží k řízení procesu sestavení. Tento termín slouží pouze k odlišení vlastnost, která není globální vlastnost.  
  
 vlastnost, registr  
 Vlastnost registru má hodnotu, která byla nastavena pomocí speciální syntaxe, která načte hodnotu podklíče registru systému. Další informace najdete v tématu [vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md).  
  
 rezervované vlastnosti  
 Rezervované vlastnosti je pár klíč hodnota, která slouží k řízení procesu sestavení. Rezervované vlastnosti jsou automaticky inicializovány na předem definovaných hodnot. Další informace najdete v tématu [vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md).  
  
 rozsah projektu  
 Rozsah projektu popisuje objekt MSBuild, například místní vlastnost, která je viditelná pouze v obsahující soubor projektu a všechny projekty, které importuje.  
  
 projekt, podřízené  
 Během sestavování projektu se vytvoří projekt podřízené úlohy nástroje MSBuild. Tímto novým projektem je podřízený projekt, který obsahuje nebo importuje cíl, který obsahuje úkol MSBuild. Podřízený projekt dědí zadaná globální vlastnosti nadřazený projekt, pokud se změnil `Properties` atribut.  
  
 seznam REDIST  
 Distribuční seznam: seznam sestavení, které odpovídají dané rozhraní.  
  
 referenční sestavení  
 Sestavení, který slouží k vytvoření aplikace v době návrhu. Referenční sestavení může mít skutečný kód a privátním rozhraním odebrány, byste museli opustit pouze metadata a veřejných rozhraní.  
  
 Vlastnosti registru  
 Zobrazit *vlastnost, registru*.  
  
 Cíl  
 Cíl seskupuje úlohy v určitém pořadí a zpřístupňuje části souboru projektu jako vstupní body do procesu sestavení. Další informace najdete v tématu [cíle](../msbuild/msbuild-targets.md).  
  
 cíl sestavení  
 Najdete v tématu cíle, spuštěná.  
  
 cíl, vyhodnocování  
 Z důvodu přírůstkové kompilace musí být analyzován na cíle potenciálních změn vlastností a položek. I v případě, že je cíl vynechán, tyto změny musí provést. Vyhodnocení cíl znamená, že provádí tuto analýzu a provedení těchto změn. Další informace najdete v tématu [přírůstková sestavení](../msbuild/incremental-builds.md).  
  
 cíl provádění  
 Cíl provádění znamená, že vyhodnocení a provádění všech úloh, které mají žádné podmínky nebo jejíž podmínky vyhodnocen na hodnotu true. Během přírůstkové kompilace cíle může přeskočená nebo spustit, ale jsou vždy vyhodnoceny. Další informace najdete v tématu cílit, vyhodnocování.  
  
 cíl spuštění  
 Cíl, který má podmínku, která se vyhodnotí na hodnotu false není spuštěn, to znamená, nemá žádný vliv na sestavení. Cíle, na kterých běží jsou proveden nebo vynechán. V obou případech se vyhodnotí cíl. Další informace najdete v tématu cílit, vyhodnocování.  
  
 cíl, přeskakuje se  
 Pokud se přírůstková kompilace zjistí, že všechny výstupní soubory jsou aktuální, pak je cíl vynechán, to znamená, vyhodnotí cíl, ale nejsou provedeny úlohy v rámci cíle. Další informace najdete v tématu cílit, vyhodnocování.  
  
 moniker cílového rozhraní framework  
 Název, který popisuje rozhraní framework (například. NETFramework, Silverlight, atd.), verze a profilu (například klienta, Server atd.), který chcete cílit.  
  
 Targeting pack  
 Seznam sestavení, které jsou distribuovány s danou architekturu a sadu referenčních sestavení pro dané rozhraní.  
  
 soubor cílů  
 Soubor cílů je soubor projektu, který obsahuje většinou cíle a úlohy, které provede sestavení. Podle konvence má příponu souboru *.targets*. Cílové soubory obvykle importují na konci přidružené soubory projektu.  
  
 – úloha  
 Úkoly jsou jednotky spustitelného kódu, který [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekty používají k provádění operací sestavení. Úkol může například kompilovat vstupní soubory nebo spustit externí nástroj. Další informace najdete v tématu [úlohy](../msbuild/msbuild-tasks.md).  
  
 transform  
 Transformace je 1: 1 převod jednu položku kolekce do druhé. Kromě povolení projekt převést položky kolekce, umožňuje transformace cíl k identifikaci přímé mapování mezi její vstupy a výstupy. Další informace najdete v tématu [transformuje](../msbuild/msbuild-transforms.md).  
  
 známá metadata  
 Zobrazit *metadat, dobře známé*.  
  
## <a name="see-also"></a>Viz také:  
 [MSBuild](../msbuild/msbuild.md)
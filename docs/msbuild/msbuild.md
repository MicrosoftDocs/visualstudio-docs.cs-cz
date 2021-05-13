---
title: MsBuild – | Microsoft Docs
description: Přečtěte si, jak Microsoft Build Engine (MSBuild) poskytuje soubor projektu se schématem XML pro řízení sestavení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 372fc5c81b963cbb8e46cab689713e476fcfff7d
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848276"
---
# <a name="msbuild"></a>MSBuild

The Microsoft Build Engine is a platform for building applications. Tento modul, který se také označuje jako MSBuild, poskytuje schéma XML pro soubor projektu, který řídí, jak platforma sestavení zpracovává a sestavuje software. Visual Studio nástroj MSBuild, ale nástroj MSBuild nezávisí na Visual Studio. Vyvoláním *msbuild.exe* projektu nebo souboru řešení můžete orchestrovat a sestavovat produkty v prostředích, Visual Studio nejsou nainstalovaná.

 Visual Studio pomocí nástroje MSBuild načítá a sestaví spravované projekty. Soubory projektu v souboru Visual Studio (*.csproj*, *.vbproj*, *.vcxproj* a další) obsahují kód MSBuild XML, který se spustí při sestavování projektu pomocí integrovaného vývojového prostředí (IDE). Visual Studio importují všechna potřebná nastavení a sestavují procesy pro typickou vývojovou práci, ale můžete je rozšířit nebo upravit v rámci Visual Studio nebo pomocí editoru XML.

 Informace o nástroji MSBuild pro jazyk C++ najdete v tématu [MSBuild (C++).](/cpp/build/msbuild-visual-cpp)

 Následující příklady ilustrují, kdy můžete spustit sestavení vyvoláním nástroje MSBuild z příkazového řádku namísto Visual Studio IDE.

- Visual Studio není nainstalovaný. ([Stáhněte msBuild bez Visual Studio](https://visualstudio.microsoft.com/downloads/?q=build+tools).)

- Chcete použít 64bitovou verzi nástroje MSBuild. Tato verze nástroje MSBuild je obvykle nepotřebná, ale umožňuje nástroji MSBuild přistupovat k více paměti.

- Chcete spustit sestavení ve více procesech. K dosažení stejného výsledku u projektů v jazyce C++ a C# ale můžete použít integrované vývojové prostředí (IDE).

- Chcete upravit systém sestavení. Můžete například chtít povolit následující akce:

  - Předběžné zpracování souborů před tím, než se dostanou do kompilátoru.

  - Zkopírujte výstupy sestavení na jiné místo.

  - Vytvoří komprimované soubory z výstupů sestavení.

  - Proveďte krok po zpracování. Například může být vhodné razítko sestavení s jinou verzí.

Můžete napsat kód v integrovaném vývojovém prostředí sady Visual Studio, ale spustit sestavení pomocí nástroje MSBuild. Jako další alternativu můžete vytvořit kód v rozhraní IDE na vývojovém počítači, ale spustit nástroj MSBuild z příkazového řádku a vytvořit kód, který je integrován od více vývojářů. K sestavování projektů .NET Core můžete použít také [rozhraní příkazového řádku (CLI) .NET Core](/dotnet/core/tools/), které používá nástroj MSBuild.

> [!NOTE]
> Můžete použít Azure Pipelines k automatické kompilaci, testování a nasazení vaší aplikace. Systém sestavení může automaticky spouštět sestavení při vrácení kódu se změnami vývojáři (například jako součást strategie průběžné integrace) nebo podle plánu (například sestavení testu na noční sestavení pro ověření). Azure Pipelines zkompiluje kód pomocí nástroje MSBuild. Další informace najdete v tématu [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

Tento článek poskytuje přehled nástroje MSBuild. Úvodní kurz najdete v tématu [Návod: použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="use-msbuild-at-a-command-prompt"></a>Použití nástroje MSBuild na příkazovém řádku

 Chcete-li spustit nástroj MSBuild na příkazovém řádku, předejte soubor projektu do *MSBuild.exe* spolu s příslušnými parametry příkazového řádku. Možnosti příkazového řádku umožňují nastavit vlastnosti, spustit konkrétní cíle a nastavit další možnosti, které řídí proces sestavení. Například použijte následující syntaxi příkazového řádku k sestavení souboru *MyProj. proj* s `Configuration` vlastností nastavenou na `Debug` .

```cmd
MSBuild.exe MyProj.proj -property:Configuration=Debug
```

 Další informace o možnostech příkazového řádku MSBuild naleznete v tématu [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md).

> [!IMPORTANT]
> Před stažením projektu určete důvěryhodnost kódu.

## <a name="project-file"></a>Soubor projektu

 Nástroj MSBuild používá formát souboru projektu založeného na jazyce XML, který je jednoduchý a rozšiřitelný. Formát souboru projektu MSBuild umožňuje vývojářům popsat položky, které mají být sestaveny, a také způsob jejich sestavení pro různé operační systémy a konfigurace. Kromě toho formát souboru projektu umožňuje vývojářům vytvářet opakovaně použitelná pravidla sestavení, která lze připravit na samostatné soubory, aby sestavení lze provádět konzistentně napříč různými projekty v produktu.

 Následující části popisují některé základní prvky formátu souboru projektu MSBuild. Kurz o tom, jak vytvořit základní soubor projektu, naleznete v tématu [Návod: vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

### <a name="properties"></a><a name="BKMK_Properties"></a> Vlastnosti

 Vlastnosti reprezentující páry klíč/hodnota, které lze použít ke konfiguraci sestavení. Vlastnosti jsou deklarovány vytvořením prvku, který má název vlastnosti jako podřízený prvek elementu [Property](../msbuild/propertygroup-element-msbuild.md) . Například následující kód vytvoří vlastnost s názvem `BuildDir` , která má hodnotu `Build` .

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 Můžete definovat vlastnost podmíněně umístěním `Condition` atributu v elementu. Obsah podmíněných elementů je ignorován, pokud není podmínka vyhodnocena jako `true` . V následujícím příkladu `Configuration` je definován prvek, pokud ještě nebyl definován.

```xml
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 Na vlastnosti lze odkazovat v rámci souboru projektu pomocí syntaxe $ ( \<PropertyName> ). Například můžete odkazovat na vlastnosti v předchozích příkladech pomocí `$(BuildDir)` a `$(Configuration)` .

 Další informace o vlastnostech naleznete v tématu [MSBuild Properties](../msbuild/msbuild-properties.md).

### <a name="items"></a><a name="BKMK_Items"></a> Položek

 Položky jsou vstupy do systému sestavení a obvykle reprezentují soubory. Položky jsou seskupeny do typů položek na základě uživatelsky definovaných názvů položek. Tyto typy položek lze použít jako parametry pro úlohy, které používají jednotlivé položky k provedení kroků procesu sestavení.

 Položky jsou deklarovány v souboru projektu vytvořením prvku, který má název typu položky jako podřízený prvek skupiny [Item](../msbuild/itemgroup-element-msbuild.md) . Například následující kód vytvoří typ položky s názvem `Compile` , který obsahuje dva soubory.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Na typy položek je možné odkazovat v celém souboru projektu pomocí syntaxe @( \<ItemType> ). Na typ položky v příkladu by se například odkazoval pomocí `@(Compile)` .

 V nástroji MSBuild rozlišují názvy elementů a atributů velká a malá písmena. Názvy vlastností, položek a metadat ale nikoli. Následující příklad vytvoří typ položky , nebo jakoukoli jinou variantu a poskytne typu položky `Compile` `comPile` hodnotu "one.cs;two.cs".

```xml
<ItemGroup>
  <Compile Include="one.cs" />
  <Compile Include="two.cs" />
</ItemGroup>
```

 Položky lze deklarovat pomocí zástupných znaků a mohou obsahovat další metadata pro pokročilejší scénáře sestavení. Další informace o položkách najdete v tématu [Items](../msbuild/msbuild-items.md).

### <a name="tasks"></a><a name="BKMK_Tasks"></a> Úkoly

 Úlohy jsou jednotky spustitelného kódu, které projekty MSBuild používají k provádění operací sestavení. Úloha může například zkompilovat vstupní soubory nebo spustit externí nástroj. Úkoly je možné opakovaně používat a mohou je sdílet různými vývojáři v různých projektech.

 Logika provádění úlohy je zapsána ve spravovaném kódu a namapována na MSBuild pomocí [elementu UsingTask.](../msbuild/usingtask-element-msbuild.md) Vlastní úlohu můžete napsat tak, že napíšete spravovaný typ, který implementuje <xref:Microsoft.Build.Framework.ITask> rozhraní. Další informace o tom, jak psát úlohy, najdete v tématu [Zápis úloh.](../msbuild/task-writing.md)

 Nástroj MSBuild obsahuje běžné úlohy, které můžete upravit tak, aby vyhovovaly vašim požadavkům. Příkladem je [copy](../msbuild/copy-task.md), který kopíruje [soubory, MakeDir](../msbuild/makedir-task.md), který vytváří adresáře, a [Csc](../msbuild/csc-task.md), který kompiluje soubory zdrojového kódu Visual C#. Seznam dostupných úkolů spolu s informacemi o využití najdete v tématu [Referenční informace o úlohách.](../msbuild/msbuild-task-reference.md)

 Úloha je spuštěna v souboru projektu MSBuild vytvořením elementu, který má název úlohy jako podřízený prvek [Target.](../msbuild/target-element-msbuild.md) Úkoly obvykle přijímají parametry, které se předá jako atributy elementu. Jako parametry lze použít jak vlastnosti a položky nástroje MSBuild. Například následující kód volá úlohu [MakeDir –](../msbuild/makedir-task.md) a předá jí hodnotu `BuildDir` vlastnosti, která byla deklarována v předchozím příkladu.

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir  Directories="$(BuildDir)" />
</Target>
```

 Další informace o úlohách najdete v tématu [úlohy](../msbuild/msbuild-tasks.md).

### <a name="targets"></a><a name="BKMK_Targets"></a> Cíle

 Cílí seskupení úkolů v určitém pořadí a vystavení oddílů souboru projektu jako vstupní body do procesu sestavení. Cíle jsou často seskupené do logických oddílů ke zvýšení čitelnosti a k umožnění rozšíření. Přerušení kroků sestavení do cílů umožňuje volat jednu část procesu sestavení z jiných cílů bez kopírování tohoto oddílu kódu do každého cíle. Například pokud několik vstupních bodů do procesu sestavení vyžaduje, aby byly sestaveny odkazy, můžete vytvořit cíl, který sestaví odkazy a potom spustí tento cíl z každého vstupního bodu, kde je vyžadován.

 Cíle jsou deklarovány v souboru projektu pomocí [cílového](../msbuild/target-element-msbuild.md) prvku. Například následující kód vytvoří cíl s názvem `Compile` , který pak zavolá úlohu [CSC](../msbuild/csc-task.md) , která má seznam položek deklarovaný v předchozím příkladu.

```xml
<Target Name="Compile">
    <Csc Sources="@(Compile)" />
</Target>
```

 V pokročilejších scénářích lze cíle použít k popisu vztahů mezi sebou a provádět analýzu závislostí, aby bylo možné přeskočit celé části procesu sestavení, pokud je tento cíl aktuální. Další informace o cílech najdete v tématu [cíle](../msbuild/msbuild-targets.md).

## <a name="build-logs"></a>Protokoly sestavení

 Zprávy o chybách, upozorněních a zprávách sestavení můžete protokolovat do konzoly nebo jiného výstupního zařízení. Další informace najdete v tématu [získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md) a [protokolování v nástroji MSBuild](../msbuild/logging-in-msbuild.md).

## <a name="use-msbuild-in-visual-studio"></a>Použití nástroje MSBuild v aplikaci Visual Studio

 Visual Studio používá formát souboru projektu MSBuild k ukládání informací o sestavení spravovaných projektů. Nastavení projektu, která jsou přidána nebo změněna pomocí rozhraní sady Visual Studio, se projeví v *. \* soubor proj* , který je vygenerován pro každý projekt. Visual Studio používá hostovanou instanci MSBuild k sestavení spravovaných projektů. To znamená, že spravovaný projekt je možné vytvořit v Visual Studio nebo na příkazovém řádku (i když Visual Studio není nainstalovaný) a výsledky budou identické.

 Kurz použití nástroje MSBuild v nástroji Visual Studio v tématu [Návod: Použití nástroje MSBuild.](../msbuild/walkthrough-using-msbuild.md)

## <a name="multitargeting"></a><a name="BKMK_Multitargeting"></a> Cílení na více verzí

 Pomocí Visual Studio můžete zkompilovat aplikaci, která se spustí na některé z několika verzí .NET Framework. Můžete například zkompilovat aplikaci, která po spuštění na 32bitové platformě běží na .NET Framework 2.0 .NET Framework, a stejnou aplikaci můžete zkompilovat tak, aby se spouštěla na 4,5 na 64bitové platformě. Možnost kompilace do více než jedné architektury má název multitargeting (cílení na více verzí).

 Toto jsou některé z výhod cílení na více verzí:

- Můžete vyvíjet aplikace, které cílí na starší .NET Framework, například verze 2.0, 3.0 a 3.5.

- Můžete cílit na jiné architektury než .NET Framework, například Silverlight.

- Můžete cílit *na profil architektury*, což je předdefinovaná podmnožina cílové architektury.

- Pokud je vydaná aktualizace Service Pack pro .NET Framework verzi, můžete na něj cílit.

- Cílení na více verzí zaručuje, že aplikace používá pouze funkce, které jsou k dispozici v cílové platformě a platformě.

Další informace najdete v tématu [Cílení na více verzí.](../msbuild/msbuild-multitargeting-overview.md)

## <a name="see-also"></a>Viz také

| Nadpis | Popis |
| - | - |
| [Návod: Vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Ukazuje, jak přírůstkově vytvořit základní soubor projektu pomocí pouze textového editoru. |
| [Návod: Použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md) | Představuje stavební bloky nástroje MSBuild a ukazuje, jak zapisovat projekty MSBuild, manipulovat s nimi a ladit je bez zavření Visual Studio IDE. |
| [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md) | Představuje čtyři stavební bloky nástroje MSBuild: vlastnosti, položky, cíle a úlohy. |
| [Položky](../msbuild/msbuild-items.md) | Popisuje obecné koncepty formátu souboru MSBuild a způsob, jakým části zapadají do sebe. |
| [vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md) | Zavádí vlastnosti a kolekce vlastností. Vlastnosti jsou páry klíč-hodnota, které lze použít ke konfiguraci sestavení. |
| [Targets](../msbuild/msbuild-targets.md) | Vysvětluje, jak seskupit úlohy v konkrétním pořadí a povolit volání částí procesu sestavení na příkazovém řádku. |
| [Úlohy](../msbuild/msbuild-tasks.md) | Ukazuje, jak vytvořit jednotku spustitelného kódu, kterou může nástroj MSBuild použít k provádění atomických operací sestavení. |
| [Podmínky](../msbuild/msbuild-conditions.md) | Popisuje způsob použití `Condition` atributu v elementu MSBuild. |
| [Pokročilé koncepty](../msbuild/msbuild-advanced-concepts.md) | Představuje dávkování, provádění transformací, cílení na více verzí a další pokročilé techniky. |
| [Protokolování v nástroji MSBuild](../msbuild/logging-in-msbuild.md) | Popisuje, jak protokolovat události sestavení, zprávy a chyby. |
| [Jak MSBuild sestavuje projekty](build-process-overview.md) | Popisuje interní proces sestavení používaný v nástroji MSBuild. |
| [Další materiály](https://social.msdn.microsoft.com/forums/vstudio/home?forum=msbuild) | Uvádí komunitu a zdroje podpory, ve které najdete další informace o nástroji MSBuild. |

## <a name="reference"></a>Reference

- [Referenční informace k nástroji MSBuild](../msbuild/msbuild-reference.md)\
 Odkazy na témata, která obsahují referenční informace.

- [Slovníček](msbuild-glossary.md)\
 Definuje běžné termíny nástroje MSBuild.

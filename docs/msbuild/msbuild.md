---
title: MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2387526860b7d6da136a72cf83727f6714e2e52
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633067"
---
# <a name="msbuild"></a>MSBuild

Microsoft Build Engine je platforma pro vytváření aplikací. Tento modul, který je také známý jako MSBuild, poskytuje schéma XML pro soubor projektu, který určuje, jak platforma sestavení zpracovává a sestavuje software. Visual Studio používá MSBuild, ale nástroj MSBuild nezávisí na aplikaci Visual Studio. Vyvoláním nástroje *MSBuild. exe* v souboru projektu nebo řešení můžete orchestrovat a sestavovat produkty v prostředích, kde není nainstalována aplikace Visual Studio.

 Visual Studio používá MSBuild k načtení a sestavení spravovaných projektů. Soubory projektu v aplikaci Visual Studio ( *. csproj*, *vbproj*, *. vcxproj*a jiné) obsahují kód XML nástroje MSBuild, který se spouští při vytváření projektu pomocí integrovaného vývojového prostředí (IDE). Projekty sady Visual Studio importují veškerá potřebná nastavení a procesy sestavení pro provádění typických vývojových prací, ale můžete je roztáhnout nebo upravit v rámci sady Visual Studio nebo pomocí editoru XML.

 Další informace o nástroji MSBuild C++pro naleznete v tématu [MSBuild (C++)](/cpp/build/msbuild-visual-cpp).

 Následující příklady ilustrují, když můžete spustit sestavení voláním MSBuild z příkazového řádku namísto integrovaného vývojového prostředí (IDE) sady Visual Studio.

- Visual Studio není nainstalované. ([Stáhnout MSBuild bez sady Visual Studio](https://visualstudio.microsoft.com/downloads/?q=build+tools).)

- Chcete použít 64 verzi nástroje MSBuild. Tato verze nástroje MSBuild je obvykle zbytečná, ale umožňuje nástroji MSBuild získat přístup k více paměti.

- Chcete spustit sestavení ve více procesech. Můžete však použít rozhraní IDE k dosažení stejného výsledku pro projekty v C++ a. C#

- Chcete upravit systém sestavení. Například může být vhodné povolit následující akce:

  - Předzpracovat soubory před tím, než dosáhnou kompilátoru.

  - Zkopírujte výstupy sestavení na jiné místo.

  - Vytvoří komprimované soubory z výstupů sestavení.

  - Proveďte krok po zpracování. Například může být vhodné razítko sestavení s jinou verzí.

Můžete napsat kód v integrovaném vývojovém prostředí sady Visual Studio, ale spustit sestavení pomocí nástroje MSBuild. Jako další alternativu můžete vytvořit kód v rozhraní IDE na vývojovém počítači, ale spustit nástroj MSBuild z příkazového řádku a vytvořit kód, který je integrován od více vývojářů. K sestavování projektů .NET Core můžete použít také [rozhraní příkazového řádku (CLI) .NET Core](/dotnet/core/tools/), které používá nástroj MSBuild.

> [!NOTE]
> Můžete použít Azure Pipelines k automatické kompilaci, testování a nasazení vaší aplikace. Systém sestavení může automaticky spouštět sestavení při vrácení kódu se změnami vývojáři (například jako součást strategie průběžné integrace) nebo podle plánu (například sestavení testu na noční sestavení pro ověření). Azure Pipelines zkompiluje kód pomocí nástroje MSBuild. Další informace najdete v tématu [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

Tento článek poskytuje přehled nástroje MSBuild. Úvodní kurz najdete v tématu [Návod: použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="use-msbuild-at-a-command-prompt"></a>Použití nástroje MSBuild na příkazovém řádku

 Chcete-li spustit nástroj MSBuild na příkazovém řádku, předejte soubor projektu nástroje *MSBuild. exe*spolu s příslušnými parametry příkazového řádku. Možnosti příkazového řádku umožňují nastavit vlastnosti, spustit konkrétní cíle a nastavit další možnosti, které řídí proces sestavení. Například použijte následující syntaxi příkazového řádku k sestavení souboru *MyProj. proj* s vlastností `Configuration` nastavenou na hodnotu `Debug`.

```cmd
MSBuild.exe MyProj.proj -property:Configuration=Debug
```

 Další informace o možnostech příkazového řádku MSBuild naleznete v tématu [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md).

> [!IMPORTANT]
> Před stažením projektu určete důvěryhodnost kódu.

## <a name="project-file"></a>Soubor projektu

 Nástroj MSBuild používá formát souboru projektu založeného na jazyce XML, který je jednoduchý a rozšiřitelný. Formát souboru projektu MSBuild umožňuje vývojářům popsat položky, které mají být sestaveny, a také způsob jejich sestavení pro různé operační systémy a konfigurace. Kromě toho formát souboru projektu umožňuje vývojářům vytvářet opakovaně použitelná pravidla sestavení, která lze připravit na samostatné soubory, aby sestavení lze provádět konzistentně napříč různými projekty v produktu.

 Následující části popisují některé základní prvky formátu souboru projektu MSBuild. Kurz o tom, jak vytvořit základní soubor projektu, naleznete v tématu [Návod: vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

### <a name="BKMK_Properties"></a>Vlastnosti

 Vlastnosti reprezentující páry klíč/hodnota, které lze použít ke konfiguraci sestavení. Vlastnosti jsou deklarovány vytvořením prvku, který má název vlastnosti jako podřízený prvek elementu [Property](../msbuild/propertygroup-element-msbuild.md) . Například následující kód vytvoří vlastnost s názvem `BuildDir`, která má hodnotu `Build`.

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 Můžete definovat vlastnost podmíněně umístěním atributu `Condition` v elementu. Obsah podmíněných elementů je ignorován, pokud podmínka není vyhodnocena jako `true`. V následujícím příkladu je definován prvek `Configuration`, pokud ještě nebyl definován.

```xml
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 Na vlastnosti lze odkazovat v rámci souboru projektu pomocí syntaxe $ (\<PropertyName >). Například můžete odkazovat na vlastnosti v předchozích příkladech pomocí `$(BuildDir)` a `$(Configuration)`.

 Další informace o vlastnostech naleznete v tématu [MSBuild Properties](../msbuild/msbuild-properties.md).

### <a name="BKMK_Items"></a>Položek

 Položky jsou vstupy do systému sestavení a obvykle reprezentují soubory. Položky jsou seskupeny do typů položek na základě uživatelsky definovaných názvů položek. Tyto typy položek lze použít jako parametry pro úlohy, které používají jednotlivé položky k provedení kroků procesu sestavení.

 Položky jsou deklarovány v souboru projektu vytvořením prvku, který má název typu položky jako podřízený prvek skupiny [Item](../msbuild/itemgroup-element-msbuild.md) . Například následující kód vytvoří typ položky s názvem `Compile`, který obsahuje dva soubory.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Na typy položek lze odkazovat v rámci souboru projektu pomocí syntaxe @ (\<ItemType >). Například typ položky v příkladu se odkazuje pomocí `@(Compile)`.

 V nástroji MSBuild názvy elementů a atributů rozlišují velká a malá písmena. Názvy vlastností, položek a metadat však nejsou. Následující příklad vytvoří typ položky `Compile`, `comPile`nebo jakoukoli jinou variaci písmen a udělí typu položky hodnotu One. cs; Two. cs.

```xml
<ItemGroup>
  <Compile Include="one.cs" />
  <comPile Include="two.cs" />
</ItemGroup>
```

 Položky mohou být deklarovány pomocí zástupných znaků a mohou obsahovat další metadata pro pokročilejší scénáře sestavení. Další informace o položkách naleznete v tématu [Items](../msbuild/msbuild-items.md).

### <a name="BKMK_Tasks"></a>Provádění

 Úlohy jsou jednotky spustitelného kódu, který projekty MSBuild používají k provádění operací sestavení. Například úloha může kompilovat vstupní soubory nebo spustit externí nástroj. Úlohy se dají znovu použít a můžou je sdílet s různými vývojáři v různých projektech.

 Logika spuštění úkolu je zapsána ve spravovaném kódu a mapována na MSBuild pomocí elementu [UsingTask](../msbuild/usingtask-element-msbuild.md) . Vlastní úlohu můžete napsat vytvářením spravovaného typu, který implementuje rozhraní <xref:Microsoft.Build.Framework.ITask>. Další informace o tom, jak psát úlohy, najdete v tématu [psaní úloh](../msbuild/task-writing.md).

 Nástroj MSBuild obsahuje běžné úlohy, které lze upravit tak, aby vyhovovaly vašim požadavkům. Příklady jsou [kopie](../msbuild/copy-task.md), které kopírují soubory, [MakeDir –](../msbuild/makedir-task.md), které vytvářejí adresáře a [CSC](../msbuild/csc-task.md), které kompiluje soubory Visual C# Source Code. Seznam dostupných úloh spolu s informacemi o použití naleznete v tématu [Task reference](../msbuild/msbuild-task-reference.md).

 Úloha je spuštěna v souboru projektu MSBuild vytvořením prvku, který má název úkolu jako podřízený prvek [cílového](../msbuild/target-element-msbuild.md) prvku. Úlohy obvykle přijímají parametry, které jsou předány jako atributy elementu. Jako parametry lze použít jak vlastnosti a položky nástroje MSBuild. Například následující kód volá úlohu [MakeDir –](../msbuild/makedir-task.md) a předá jí hodnotu vlastnosti `BuildDir`, která byla deklarována v předchozím příkladu.

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir  Directories="$(BuildDir)" />
</Target>
```

 Další informace o úlohách najdete v tématu [úlohy](../msbuild/msbuild-tasks.md).

### <a name="BKMK_Targets"></a>Cíle

 Cílí seskupení úkolů v určitém pořadí a vystavení oddílů souboru projektu jako vstupní body do procesu sestavení. Cíle jsou často seskupené do logických oddílů ke zvýšení čitelnosti a k umožnění rozšíření. Přerušení kroků sestavení do cílů umožňuje volat jednu část procesu sestavení z jiných cílů bez kopírování tohoto oddílu kódu do každého cíle. Například pokud několik vstupních bodů do procesu sestavení vyžaduje, aby byly sestaveny odkazy, můžete vytvořit cíl, který sestaví odkazy a potom spustí tento cíl z každého vstupního bodu, kde je vyžadován.

 Cíle jsou deklarovány v souboru projektu pomocí [cílového](../msbuild/target-element-msbuild.md) prvku. Například následující kód vytvoří cíl s názvem `Compile`, který pak zavolá úlohu [CSC](../msbuild/csc-task.md) , která má seznam položek deklarovaný v předchozím příkladu.

```xml
<Target Name="Compile">
    <Csc Sources="@(Compile)" />
</Target>
```

 V pokročilejších scénářích lze cíle použít k popisu vztahů mezi sebou a provádět analýzu závislostí, aby bylo možné přeskočit celé části procesu sestavení, pokud je tento cíl aktuální. Další informace o cílech najdete v tématu [cíle](../msbuild/msbuild-targets.md).

## <a name="build-logs"></a>Protokoly o sestavení

 Zprávy o chybách, upozorněních a zprávách sestavení můžete protokolovat do konzoly nebo jiného výstupního zařízení. Další informace najdete v tématu [získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md) a [protokolování v nástroji MSBuild](../msbuild/logging-in-msbuild.md).

## <a name="use-msbuild-in-visual-studio"></a>Použití nástroje MSBuild v aplikaci Visual Studio

 Visual Studio používá formát souboru projektu MSBuild k ukládání informací o sestavení spravovaných projektů. Nastavení projektu, která jsou přidána nebo změněna pomocí rozhraní sady Visual Studio, se projeví v souboru *.\*proj* , který je generován pro každý projekt. Visual Studio používá hostovanou instanci MSBuild k sestavení spravovaných projektů. To znamená, že spravovaný projekt může být sestaven v aplikaci Visual Studio nebo na příkazovém řádku (i v případě, že není nainstalována aplikace Visual Studio) a výsledky budou stejné.

 Kurz týkající se použití nástroje MSBuild v aplikaci Visual Studio naleznete v tématu [Návod: použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="BKMK_Multitargeting"></a>Cílení na více verzí

 Pomocí sady Visual Studio můžete zkompilovat aplikaci pro spuštění v některé z několika verzí .NET Framework. Například můžete zkompilovat aplikaci pro spuštění na .NET Framework 2,0 na 32 platformě a můžete zkompilovat stejnou aplikaci, aby běžela na .NET Framework 4,5 64 na 16bitové platformě. Možnost kompilace do více než jednoho rozhraní se nazývá cílení na více verzí.

 Toto jsou některé z výhod cílení na více verzí:

- Můžete vyvíjet aplikace, které cílí na starší verze .NET Framework, například verze 2,0, 3,0 a 3,5.

- Můžete cílit na jiné architektury než .NET Framework, například na Silverlight.

- Můžete cílit na *profil rozhraní*, což je předdefinovaná podmnožina cílové architektury.

- Pokud se uvolní aktualizace Service Pack pro aktuální verzi .NET Framework, můžete na ni cílit.

- Cílení na více verzí zaručuje, že aplikace používá pouze funkce, které jsou k dispozici v cílové architektuře a platformě.

Další informace najdete v tématu [cílení](../msbuild/msbuild-multitargeting-overview.md)na více verzí.

## <a name="see-also"></a>Viz také

| Název | Popis |
| - | - |
| [Návod: vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Ukazuje, jak vytvořit soubor základního projektu přírůstkově pomocí pouze textového editoru. |
| [Návod: Použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md) | Zavádí stavební kameny nástroje MSBuild a ukazuje, jak psát, manipulovat a ladit projekty MSBuild bez zavření prostředí IDE sady Visual Studio. |
| [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md) | Představuje čtyři stavební kameny nástroje MSBuild: vlastnosti, položky, cíle a úkoly. |
| [Položky](../msbuild/msbuild-items.md) | Popisuje obecné pojmy za formátem souboru MSBuild a způsob, jakým se tyto části vejdou dohromady. |
| [Vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md) | Zavádí vlastnosti a kolekce vlastností. Vlastnosti jsou páry klíč/hodnota, které lze použít ke konfiguraci sestavení. |
| [Cíle](../msbuild/msbuild-targets.md) | Vysvětluje, jak seskupit úkoly společně v určitém pořadí a povolit části procesu sestavení, které mají být volány v příkazovém řádku. |
| [Úlohy](../msbuild/msbuild-tasks.md) | Ukazuje, jak vytvořit jednotku spustitelného kódu, který může nástroj MSBuild použít k provedení atomických operací sestavení. |
| [Podmínky](../msbuild/msbuild-conditions.md) | Popisuje použití atributu `Condition` v elementu MSBuild. |
| [Pokročilé koncepty](../msbuild/msbuild-advanced-concepts.md) | Prezentuje dávkování, provádění transformací, cílení na více verzí a další pokročilé techniky. |
| [Protokolování v nástroji MSBuild](../msbuild/logging-in-msbuild.md) | Popisuje, jak protokolovat události sestavení, zprávy a chyby. |
| [Další materiály](https://social.msdn.microsoft.com/forums/vstudio/home?forum=msbuild) | Obsahuje seznam prostředků komunity a podpory, kde najdete další informace o nástroji MSBuild. |

## <a name="reference"></a>Referenční informace

- [Referenční](../msbuild/msbuild-reference.md)\ nástroje MSBuild
 Obsahuje odkazy na témata, která obsahují referenční informace.

- [Glosář](msbuild-glossary.md)\
 Definuje společné výrazy MSBuild.

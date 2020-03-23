---
title: MSBuild | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633067"
---
# <a name="msbuild"></a>MSBuild

Microsoft Build Engine je platforma pro vytváření aplikací. Tento modul, který je také známý jako MSBuild, poskytuje schéma XML pro soubor projektu, který řídí, jak platforma sestavení zpracovává a vytváří software. Visual Studio používá MSBuild, ale MSBuild nezávisí na Visual Studio. Vyvoláním *msbuild.exe* v souboru projektu nebo řešení můžete orchestrovat a vytvářet produkty v prostředích, kde není nainstalována sada Visual Studio.

 Visual Studio používá MSBuild k načtení a sestavení spravovaných projektů. Soubory projektu v sadě Visual Studio (*.csproj*, *.vbproj*, *.vcxproj*a další) obsahují kód XML MSBuild, který se spustí při vytváření projektu pomocí rozhraní IDE. Projekty sady Visual Studio importují všechna potřebná nastavení a vytvářejí procesy pro typické vývojové práce, ale můžete je rozšířit nebo upravit z aplikace Visual Studio nebo pomocí editoru XML.

 Informace o MSBuild pro C++ naleznete v tématu [MSBuild (C++)](/cpp/build/msbuild-visual-cpp).

 Následující příklady ilustrují, kdy můžete spustit sestavení vyvoláním MSBuild z příkazového řádku namísto IDE visual studio.

- Visual Studio není nainstalováno. (Stáhnout[MSBuild bez Visual Studio](https://visualstudio.microsoft.com/downloads/?q=build+tools).)

- Chcete použít 64bitovou verzi msbuild. Tato verze MSBuild je obvykle zbytečné, ale umožňuje MSBuild pro přístup k více paměti.

- Chcete spustit sestavení ve více procesech. Však můžete použít ide k dosažení stejného výsledku na projektech v jazyce C++ a C#.

- Chcete upravit systém sestavení. Můžete například povolit následující akce:

  - Předběžně zpracujte soubory dříve, než se dostanou k kompilátoru.

  - Zkopírujte výstupy sestavení na jiné místo.

  - Vytvořte komprimované soubory z výstupů sestavení.

  - Proveďte krok po zpracování. Můžete například chtít razítko sestavení s jinou verzí.

Můžete psát kód v ide sady Visual Studio, ale spustit sestavení pomocí MSBuild. Jako další alternativu můžete vytvořit kód v integrovaném vývojovém prostředí ve vývojovém počítači, ale spustit MSBuild z příkazového řádku k vytvoření kódu, který je integrován z více vývojářů. K vytváření projektů .NET Core můžete také použít [rozhraní příkazového řádku .NET Core (CLI),](/dotnet/core/tools/)které používá MSBuild.

> [!NOTE]
> Azure Pipelines můžete použít k automatické kompilaci, testování a nasazení aplikace. Systém sestavení můžete automaticky spustit sestavení, když vývojáři vrácení se změnami kód (například jako součást strategie průběžné integrace) nebo podle plánu (například sestavení test ověření pro noční sestavení). Azure Pipelines zkompiluje váš kód pomocí MSBuild. Další informace najdete v tématu [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

Tento článek obsahuje přehled MSBuild. Úvodní kurz najdete v [tématu Návod: Použití msbuildu](../msbuild/walkthrough-using-msbuild.md).

## <a name="use-msbuild-at-a-command-prompt"></a>Použití msbuildu na příkazovém řádku

 Chcete-li spustit msbuild na příkazovém řádku, předejte soubor projektu *msbuild.exe*spolu s příslušnými možnostmi příkazového řádku. Možnosti příkazového řádku umožňují nastavit vlastnosti, provádět určité cíle a nastavovat další možnosti, které řídí proces sestavení. Například byste použili následující syntaxi příkazového řádku k vytvoření souboru `Configuration` *MyProj.proj* s vlastností nastavenou na `Debug`.

```cmd
MSBuild.exe MyProj.proj -property:Configuration=Debug
```

 Další informace o možnostech příkazového řádku MSBuild naleznete v [tématu Command-line reference](../msbuild/msbuild-command-line-reference.md).

> [!IMPORTANT]
> Před stažením projektu určete důvěryhodnost kódu.

## <a name="project-file"></a>Soubor projektu

 MSBuild používá formát souboru projektu založené na jazyce XML, který je jednoduchý a rozšiřitelný. Formát souboru projektu MSBuild umožňuje vývojářům popsat položky, které mají být sestaveny a také jak mají být vytvořeny pro různé operační systémy a konfigurace. Kromě toho formát souboru projektu umožňuje vývojářům vytvářet opakovaně použitelná pravidla sestavení, která lze zařadit do samostatných souborů, takže sestavení lze provádět konzistentně napříč různými projekty v produktu.

 Následující části popisují některé základní prvky formátu souboru projektu MSBuild. Kurz o vytvoření základního souboru projektu naleznete v [tématu Návod: Vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

### <a name="properties"></a><a name="BKMK_Properties"></a>Vlastnosti

 Vlastnosti představují dvojice klíč/hodnota, které lze použít ke konfiguraci sestavení. Vlastnosti jsou deklarovány vytvořením prvku, který má název vlastnosti jako podřízený [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) elementu. Například následující kód vytvoří vlastnost `BuildDir` s názvem, `Build`která má hodnotu .

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 Vlastnost můžete definovat podmíněně umístěním atributu `Condition` do prvku. Obsah podmíněných prvků jsou ignorovány, pokud `true`podmínka vyhodnotí . V následujícím příkladu `Configuration` je prvek definován, pokud ještě nebyl definován.

```xml
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 Vlastnosti lze odkazovat v celém souboru\<projektu pomocí syntaxe $( PropertyName>). Můžete například odkazovat na vlastnosti v `$(BuildDir)` předchozích příkladech pomocí a `$(Configuration)`.

 Další informace o vlastnostech naleznete v tématu [MSBuild properties](../msbuild/msbuild-properties.md).

### <a name="items"></a><a name="BKMK_Items"></a>Položky

 Položky jsou vstupy do systému sestavení a obvykle představují soubory. Položky jsou seskupeny do typů položek na základě uživatelem definovaných názvů položek. Tyto typy položek lze použít jako parametry pro úkoly, které používají jednotlivé položky k provedení kroků procesu sestavení.

 Položky jsou deklarovány v souboru projektu vytvořením prvku, který má název typu položky jako podřízený prvek [ItemGroup.](../msbuild/itemgroup-element-msbuild.md) Například následující kód vytvoří typ `Compile`položky s názvem , který obsahuje dva soubory.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Typy položek lze odkazovat v celém souboru\<projektu pomocí syntaxe @( ItemType>). Například typ položky v příkladu by `@(Compile)`odkazováno pomocí .

 V MSBuild, názvy prvků a atributů rozlišují malá a velká písmena. Názvy vlastností, položek a metadat však nejsou. Následující příklad vytvoří typ `Compile` `comPile`položky , nebo jakoukoli jinou variantu případu a zadá zadejte hodnotu "one.cs;two.cs".

```xml
<ItemGroup>
  <Compile Include="one.cs" />
  <comPile Include="two.cs" />
</ItemGroup>
```

 Položky mohou být deklarovány pomocí zástupných znaků a mohou obsahovat další metadata pro pokročilejší scénáře sestavení. Další informace o položkách naleznete v [tématu Položky](../msbuild/msbuild-items.md).

### <a name="tasks"></a><a name="BKMK_Tasks"></a>Úkoly

 Úkoly jsou jednotky spustitelného kódu, které projekty MSBuild používají k provádění operací sestavení. Úloha může například zkompilovat vstupní soubory nebo spustit externí nástroj. Úkoly lze znovu použít a mohou být sdíleny různými vývojáři v různých projektech.

 Logika spuštění úlohy je zapsána ve spravovaném kódu a mapována na MSBuild pomocí [usingTask](../msbuild/usingtask-element-msbuild.md) elementu. Můžete napsat vlastní úkol vytvořením spravovaného typu, <xref:Microsoft.Build.Framework.ITask> který implementuje rozhraní. Další informace o psaní úkolů naleznete v [tématu Psaní úkolů](../msbuild/task-writing.md).

 MSBuild obsahuje běžné úkoly, které můžete upravit tak, aby vyhovovaly vašim požadavkům. Příklady jsou [Copy](../msbuild/copy-task.md), který kopíruje soubory, [MakeDir](../msbuild/makedir-task.md), který vytváří adresáře, a [Csc](../msbuild/csc-task.md), který zkompiluje soubory zdrojového kódu Visual C#. Seznam dostupných úkolů spolu s informacemi o použití naleznete v [tématu Odkaz na úkol](../msbuild/msbuild-task-reference.md).

 Úloha je spouštěna v souboru projektu MSBuild vytvořením prvku, který má název úkolu jako podřízený [element Target.](../msbuild/target-element-msbuild.md) Úkoly obvykle přijímají parametry, které jsou předány jako atributy prvku. Vlastnosti msbuild a položky lze použít jako parametry. Například následující kód volá úkol [MakeDir](../msbuild/makedir-task.md) a předá `BuildDir` ji hodnotu vlastnosti, která byla deklarována v předchozím příkladu.

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir  Directories="$(BuildDir)" />
</Target>
```

 Další informace o úkolech naleznete v [tématu Úkoly](../msbuild/msbuild-tasks.md).

### <a name="targets"></a><a name="BKMK_Targets"></a>Cíle

 Cíle seskupí úkoly v určitém pořadí a zpřístupní části souboru projektu jako vstupní body do procesu sestavení. Cíle jsou často seskupeny do logických oddílů pro zvýšení čitelnosti a umožnění rozšíření. Rozdělení kroky sestavení do cílů umožňuje volat jednu část procesu sestavení z jiných cílů bez kopírování této části kódu do každého cíle. Například pokud několik vstupních bodů do procesu sestavení vyžadují odkazy, které mají být vytvořeny, můžete vytvořit cíl, který vytvoří odkazy a pak spustit tento cíl z každého vstupního bodu, kde je požadováno.

 Cíle jsou deklarovány v souboru projektu pomocí [Target](../msbuild/target-element-msbuild.md) element. Například následující kód vytvoří cíl `Compile`s názvem , který pak volá úkol [Csc,](../msbuild/csc-task.md) který má seznam položek, který byl deklarován v předchozím příkladu.

```xml
<Target Name="Compile">
    <Csc Sources="@(Compile)" />
</Target>
```

 V pokročilejších scénářích lze cíle použít k popisu vzájemných vztahů a k provedení analýzy závislostí, aby bylo možné přeskočit celé části procesu sestavení, pokud je tento cíl aktuální. Další informace o cílech naleznete v tématu [Cíle](../msbuild/msbuild-targets.md).

## <a name="build-logs"></a>Vytváření protokolů

 Chyby sestavení, upozornění a zprávy můžete protokolovat do konzoly nebo jiného výstupního zařízení. Další informace naleznete [v tématu Získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md) a [protokolování v MSBuild](../msbuild/logging-in-msbuild.md).

## <a name="use-msbuild-in-visual-studio"></a>Použití msbuildu v sadě Visual Studio

 Visual Studio používá formát souboru projektu MSBuild k ukládání informací o sestavení o spravovaných projektech. Nastavení projektu, které jsou přidány nebo změněny pomocí rozhraní sady Visual Studio se projeví v *rozhraní .\* proj* soubor, který je generován pro každý projekt. Visual Studio používá hostovanou instanci MSBuild k vytváření spravovaných projektů. To znamená, že spravovaný projekt může být vytvořen v sadě Visual Studio nebo na příkazovém řádku (i když visual studio není nainstalováno) a výsledky budou identické.

 Kurz o použití msbuildu v sadě Visual Studio najdete v [tématu Návod: Použití msbuildu](../msbuild/walkthrough-using-msbuild.md).

## <a name="multitargeting"></a><a name="BKMK_Multitargeting"></a>Multicílení

 Pomocí sady Visual Studio můžete zkompilovat aplikaci pro spuštění v některé z několika verzí rozhraní .NET Framework. Můžete například zkompilovat aplikaci pro spuštění na rozhraní .NET Framework 2.0 na 32bitové platformě a můžete zkompilovat stejnou aplikaci, která se bude spouštět v rozhraní .NET Framework 4.5 na 64bitové platformě. Schopnost kompilovat do více než jedné architektury se nazývá multitargeting.

 To jsou některé z výhod multitargeting:

- Můžete vyvíjet aplikace, které cílí na starší verze rozhraní .NET Framework, například verze 2.0, 3.0 a 3.5.

- Můžete cílit na jiné architektury než rozhraní .NET Framework, například Silverlight.

- Můžete cílit na *profil architektury*, což je předdefinovaná podmnožina cílového rozhraní.

- Pokud je vydána aktualizace Service Pack pro aktuální verzi rozhraní .NET Framework, můžete na něj cílit.

- Multitargeting zaručuje, že aplikace používá pouze funkce, které jsou k dispozici v cílové matné rozhraní a platformy.

Další informace naleznete v tématu [Multitargeting](../msbuild/msbuild-multitargeting-overview.md).

## <a name="see-also"></a>Viz také

| Nadpis | Popis |
| - | - |
| [Návod: Vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Ukazuje, jak vytvořit základní soubor projektu postupně pomocí pouze textového editoru. |
| [Návod: Použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md) | Představuje stavební bloky MSBuild a ukazuje, jak psát, manipulovat a ladit projekty MSBuild bez zavření IDE Visual Studio. |
| [Koncepty MSBuild](../msbuild/msbuild-concepts.md) | Představuje čtyři stavební bloky MSBuild: vlastnosti, položky, cíle a úkoly. |
| [Items](../msbuild/msbuild-items.md) | Popisuje obecné koncepty za formát souboru MSBuild a jak se kousky zapadají do sebe. |
| [Vlastnosti MSBuild](../msbuild/msbuild-properties.md) | Zavádí vlastnosti a kolekce vlastností. Vlastnosti jsou dvojice klíč/hodnota, které lze použít ke konfiguraci sestavení. |
| [Cíle](../msbuild/msbuild-targets.md) | Vysvětluje, jak seskupit úkoly v určitém pořadí a povolit části procesu sestavení, které mají být volány na příkazovém řádku. |
| [Úlohy](../msbuild/msbuild-tasks.md) | Ukazuje, jak vytvořit jednotku spustitelného kódu, který může msbuild použít k provádění operací atomového sestavení. |
| [Podmínky](../msbuild/msbuild-conditions.md) | Popisuje, jak použít `Condition` atribut v prvku MSBuild. |
| [Pokročilé koncepty](../msbuild/msbuild-advanced-concepts.md) | Představuje dávkování, provádění transformací, multitargeting a další pokročilé techniky. |
| [Protokolování v nástroji MSBuild](../msbuild/logging-in-msbuild.md) | Popisuje, jak protokolovat události sestavení, zprávy a chyby. |
| [Další zdroje](https://social.msdn.microsoft.com/forums/vstudio/home?forum=msbuild) | Seznam komunitních a podpůrných prostředků pro další informace o MSBuild. |

## <a name="reference"></a>Referenční informace

- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)\
 Odkazy na témata, která obsahují referenční informace.

- [Slovníček](msbuild-glossary.md)\
 Definuje běžné termíny MSBuild.

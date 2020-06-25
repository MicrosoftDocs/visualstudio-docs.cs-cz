---
title: Jak MSBuild sestavení projektů
ms.date: 05/18/2020
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, build process overview
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3c1cdc4738f60301435932b3700f14377f12172
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290429"
---
# <a name="how-msbuild-builds-projects"></a>Jak MSBuild sestavení projektů

Jak nástroj MSBuild skutečně funguje? V tomto článku se dozvíte, jak MSBuild zpracovává soubory projektu, ať už jsou vyvolány ze sady Visual Studio nebo z příkazového řádku nebo skriptu. Znalost toho, jak vám MSBuild funguje, vám umožní lépe diagnostikovat problémy a lépe přizpůsobit proces sestavení. Tento článek popisuje proces sestavení a je z velké části použitelný pro všechny typy projektů.

Celý proces sestavení se skládá z [počátečního spuštění](#startup), [vyhodnocení](#evaluation-phase)a [spuštění](#execution-phase) cílů a úkolů, které sestaví projekt. Kromě těchto vstupů externí import definuje podrobnosti procesu sestavení, včetně [standardních importů](#standard-imports) , jako je například *Microsoft. Common. targets* a [uživatelsky konfigurovatelné importy](#user-configurable-imports) na úrovni řešení nebo projektu.

## <a name="startup"></a>Spuštění

Nástroj MSBuild lze vyvolat z aplikace Visual Studio prostřednictvím modelu objektu MSBuild v *Microsoft.Build.dll*nebo vyvoláním spustitelného souboru přímo na příkazovém řádku nebo ve skriptu, například v systémech CI. V obou případech vstupy, které ovlivňují proces sestavení, zahrnují soubor projektu (nebo objekt Project Internal do sady Visual Studio), pravděpodobně soubor řešení, proměnné prostředí a přepínače příkazového řádku nebo jejich ekvivalenty objektového modelu. Během fáze spouštění se pro konfiguraci nastavení nástroje MSBuild, jako je třeba konfigurace protokolovacích nástrojů, používají možnosti příkazového řádku nebo ekvivalenty objektového modelu. Vlastnosti nastavené v příkazovém řádku pomocí `-property` přepínače nebo `-p` jsou nastaveny jako globální vlastnosti, které přepíšou všechny hodnoty, které by byly nastaveny v souborech projektu, i když jsou soubory projektu čteny později.

Další části se týkají vstupních souborů, jako jsou soubory řešení nebo soubory projektu.

### <a name="solutions-and-projects"></a>Řešení a projekty

Instance MSBuild se můžou skládat z jednoho projektu nebo mnoha projektů jako součást řešení. Soubor řešení není souborem MSBuild XML, ale nástroj MSBuild ho interpretuje, aby znal všechny projekty, které jsou nutné pro sestavení pro danou konfiguraci a nastavení platformy. Když nástroj MSBuild zpracovává tento vstup XML, je označován jako sestavení řešení. Má několik rozšiřitelných bodů, které umožňují spustit něco v každém sestavení řešení, ale vzhledem k tomu, že toto sestavení je samostatné spuštění z jednotlivých sestavení projektu, není pro každé sestavení projektu relevantní žádné nastavení vlastností nebo cílové definice z buildu řešení.

Informace o tom, jak roztáhnout sestavení řešení, najdete v tématu [přizpůsobení sestavení řešení](customize-your-build.md#customize-the-solution-build).

### <a name="visual-studio-builds-vs-msbuildexe-builds"></a>Sestavení sady Visual Studio vs. MSBuild.exe buildy

Existují významné rozdíly mezi tím, kdy se projekty sestavují v sadě Visual Studio vs. při vyvolání nástroje MSBuild přímo, buď pomocí spustitelného souboru MSBuild, nebo při použití modelu objektu MSBuild ke spuštění sestavení. Visual Studio spravuje pořadí sestavení projektu pro sestavení sady Visual Studio; volá pouze nástroj MSBuild na úrovni jednotlivých projektů a v případě, že je, je nastavena jedna z logických vlastností ( `BuildingInsideVisualStudio` , `BuildProjectReferences` ), které významně ovlivňují, co nástroj MSBuild dělá. V každém projektu probíhá spuštění stejným způsobem jako při vyvolání prostřednictvím nástroje MSBuild, ale rozdíl vzniká v odkazovaných projektech. V nástroji MSBuild, pokud jsou vyžadovány odkazované projekty, sestavení skutečně probíhá; To znamená, že spouští úlohy a nástroje a generuje výstup. Když sestavení sady Visual Studio najde odkazovaný projekt, nástroj MSBuild vrátí pouze očekávané výstupy z odkazovaného projektu. umožňuje aplikaci Visual Studio řídit sestavování těchto dalších projektů. Visual Studio určuje pořadí sestavení a volání nástroje MSBuild samostatně (podle potřeby), zcela v rámci řízení sady Visual Studio.

K dalšímu rozdílu dojde, když je nástroj MSBuild vyvolán pomocí souboru řešení, nástroj MSBuild analyzuje soubor řešení, vytvoří standardní vstupní soubor XML, vyhodnocuje ho a provede jej jako projekt. Sestavení řešení je spuštěno před jakýmkoli projektem. Při sestavování ze sady Visual Studio se žádná z těchto situací nestane. MSBuild nikdy nevidí soubor řešení. V důsledku toho je přizpůsobení sestavení řešení (pomocí *před). Řešení. sln. targets* a *After. Řešení. sln. targets*se vztahuje pouze na MSBuild.exe nebo objektový model řízený, nikoli na sestavení sady Visual Studio.

### <a name="project-sdks"></a>Sady SDK projektu

Funkce sady SDK pro soubory projektu MSBuild je relativně nová. Před touto změnou soubory projektu explicitně naimportovaly soubory *. targets* a *. props* , které definovaly proces sestavení pro konkrétní typ projektu.

Projekty .NET Core importují verzi sady .NET SDK, která je pro ně vhodná. Podívejte se na přehled, sady [SDK projektu .NET Core](/dotnet/core/project-sdk/overview)a odkaz na [vlastnosti](/dotnet/core/project-sdk/msbuild-props).

## <a name="evaluation-phase"></a>Fáze hodnocení

Tato část popisuje, jak jsou tyto vstupní soubory zpracovávány a analyzovány za účelem vytvoření objektů v paměti, které určují, co bude sestaveno.

Účelem fáze vyhodnocení je vytvořit struktury objektů v paměti na základě vstupních souborů XML a místního prostředí. Zkušební fáze se skládá z pěti průchodů, které zpracovávají vstupní soubory, jako jsou soubory XML projektu nebo, a importované soubory XML, obvykle pojmenované jako *. props* nebo *. targets* , v závislosti na tom, zda primárně nastavují vlastnosti nebo definují cíle sestavení. Každý Pass sestaví část objektů v paměti, které jsou později použity ve fázi spouštění pro sestavení projektů, ale během fáze hodnocení nedojde k žádným skutečným akcím sestavení. V rámci každého průchodu jsou prvky zpracovávány v pořadí, ve kterém jsou zobrazeny.

Fáze hodnocení jsou následující:

- Vyhodnocení proměnných prostředí
- Vyhodnotit importy a vlastnosti
- Vyhodnotit definice položek
- Vyhodnotit položky
- Vyhodnotit elementy [UsingTask](usingtask-element-msbuild.md)
- Vyhodnotit cíle

Pořadí těchto průchodů má významné důsledky a je důležité znát při úpravách souboru projektu. Viz [pořadí vyhodnocování vlastností a položek](comparing-properties-and-items.md#property-and-item-evaluation-order).

### <a name="evaluate-environment-variables"></a>Vyhodnocení proměnných prostředí

V této fázi se proměnné prostředí používají k nastavení ekvivalentních vlastností. Například proměnná prostředí PATH je zpřístupněna jako vlastnost `$(PATH)` . Při spuštění z příkazového řádku nebo skriptu se příkazové prostředí používá jako normální a při spuštění ze sady Visual Studio se použije prostředí, když se spustí Visual Studio.

### <a name="evaluate-imports-and-properties"></a>Vyhodnotit importy a vlastnosti

V této fázi je celý vstupní kód XML čten v, včetně souborů projektu a celého řetězce importů. Nástroj MSBuild vytvoří strukturu XML v paměti, která představuje XML projektu a všech importovaných souborů. V tuto chvíli jsou vyhodnoceny a nastaveny vlastnosti, které nejsou v cíli.

V důsledku toho, že nástroj MSBuild čte všechny vstupní soubory XML včas v procesu, jakékoli změny těchto vstupů během procesu sestavení neovlivní aktuální sestavení.

Vlastnosti mimo jakýkoliv cíl jsou zpracovávány jinak než v rámci cílů. V této fázi jsou vyhodnocovány pouze vlastnosti definované mimo libovolný cíl.

Vzhledem k tomu, že vlastnosti jsou zpracovávány v pořadí vlastností Pass, může vlastnost v jakémkoli okamžiku ve vstupu přistupovat k hodnotám vlastností, které se objeví dříve ve vstupu, ale nikoli vlastnosti, které se zobrazí později.

Vzhledem k tomu, že vlastnosti jsou zpracovány před vyhodnocením položek, nebudete mít přístup k hodnotě žádné položky během jakékoli části vlastností Pass. 

### <a name="evaluate-item-definitions"></a>Vyhodnotit definice položek

V této fázi jsou interpretovány [Definice položek](item-definitions.md) a jsou vytvořeny reprezentace v paměti těchto definic.

### <a name="evaluate-items"></a>Vyhodnotit položky

Položky definované v cíli jsou zpracovávány jinak než položky mimo libovolný cíl. V této fázi jsou zpracovávány položky mimo libovolný cíl a jejich přidružená metadata.  Metadata nastavená definicemi položek jsou přepsána nastavením metadata u položek. Vzhledem k tomu, že položky jsou zpracovávány v pořadí, ve kterém se zobrazí, můžete odkazovat na položky, které byly definovány dříve, ale ne na ty, které se zobrazí později. Vzhledem k tomu, že položky přecházejí po předání vlastností, mohou položky přistupovat k libovolné vlastnosti, pokud je definována mimo všechny cíle, bez ohledu na to, zda se definice vlastnosti zobrazí později.

### <a name="evaluate-usingtask-elements"></a>Vyhodnotit `UsingTask` elementy

V této fázi jsou čteny elementy [UsingTask](usingtask-element-msbuild.md) a úkoly jsou deklarovány pro pozdější použití během fáze provádění.

### <a name="evaluate-targets"></a>Vyhodnotit cíle

V této fázi se všechny cílové struktury objektů vytvoří v paměti, a to při přípravě na provedení. Neproběhne žádné skutečné provádění. 

## <a name="execution-phase"></a>Fáze provádění

Ve fázi provádění jsou cíle seřazené a spuštěné a všechny úlohy jsou spuštěny. Ale první, vlastnosti a položky, které jsou definovány v rámci cílů, jsou vyhodnocovány společně v jedné fázi v pořadí, ve kterém se zobrazí. Pořadí zpracování je obzvláště odlišné od toho, jak se zpracovávají vlastnosti a položky, které nejsou v cíli: nejprve všechny vlastnosti a pak všechny položky v samostatných průchodech. Změny vlastností a položek v rámci cíle lze pozorovat po cíli, kde byly změněny.

### <a name="target-build-order"></a>Pořadí cílového sestavení

V jednom projektu cíle provádí sériové provádění. Hlavní problém je způsob, jak určit, jak se má sestavit vše, aby se závislosti používaly k sestavení cílů ve správném pořadí.  

Cílové pořadí sestavení je určeno použitím `BeforeTargets` `DependsOnTargets` atributů, a `AfterTargets` v každém cíli. Pořadí pozdějších cílů může být ovlivněno během provádění dřívějšího cíle, pokud předchozí cíl upraví vlastnost, na kterou se odkazuje v těchto atributech.

Pravidla pro řazení jsou popsána v tématu [určení cílové objednávky sestavení](target-build-order.md#determine-the-target-build-order). Proces je určen strukturou zásobníku obsahující cíle pro sestavení. Cíl v horní části této úlohy spouští provádění, a pokud závisí na cokoli jiného, pak jsou tyto cíle vloženy do horní části zásobníku a začnou se spouštět.  Pokud je cíl bez jakýchkoli závislostí, provede se dokončení a jeho nadřazený cíl pokračuje.

### <a name="project-references"></a>Odkazy na projekty

Existují dvě cesty kódu, které může nástroj MSBuild provést, což je normální, popsané zde a možnost grafu popsaná v následující části.

Jednotlivé projekty určují jejich závislost na dalších projektech prostřednictvím `ProjectReference` položek. Při zahájení sestavování projektu v horní části zásobníku dosáhne bodu, ve kterém se `ResolveProjectReferences` cíl spustí, standardní cíl definovaný v běžných cílových souborech.

`ResolveProjectReferences`vyvolá úlohu MSBuild se vstupními `ProjectReference` položkami pro získání výstupů. `ProjectReference`Položky jsou transformovány na místní položky, jako je například `Reference` . Fáze provádění MSBuild pro aktuální projekt se pozastaví, zatímco fáze provádění začne zpracovávat odkazovaný projekt (fáze vyhodnocení se v takovém případě vyžaduje). Odkazovaný projekt se sestaví pouze po zahájení sestavování závislého projektu, a proto vytvoří strom sestavení projektů.

Visual Studio umožňuje vytváření závislostí projektu v souborech řešení (. sln). Závislosti jsou zadány v souboru řešení a jsou respektovány pouze při sestavování řešení nebo při sestavování v rámci sady Visual Studio. Pokud sestavíte jeden projekt, tento typ závislosti se ignoruje. Odkazy na řešení jsou transformovány nástrojem MSBuild do `ProjectReference` položek a následně jsou zpracovány stejným způsobem.

### <a name="graph-option"></a>Možnost grafu

Zadáte-li přepínač pro sestavení grafu ( `-graphBuild` nebo), bude se jednat `-graph` `ProjectReference` o koncept první třídy, který je používán nástrojem MSBuild. Nástroj MSBuild analyzuje všechny projekty a vytvoří graf pořadí sestavení, skutečný graf závislosti projektů, který pak projde k určení pořadí sestavení. Stejně jako u cílů v jednotlivých projektech MSBuild zajišťuje, aby odkazované projekty byly sestaveny po projektech, na kterých jsou závislé.

## <a name="parallel-execution"></a>Paralelní provádění

Pokud používáte podporu více procesorů ( `-maxCpuCount` nebo `-m` přepínač), nástroj MSBuild vytvoří uzly, které jsou procesy MSBuild využívající dostupné jádra procesoru. Každý projekt je odeslán do dostupného uzlu. V rámci uzlu spustí jednotlivé sestavení projektu sériové.

Úlohy mohou být povoleny pro paralelní spouštění nastavením logické proměnné <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> , která je nastavena podle hodnoty `$(BuildInParallel)` vlastnosti v nástroji MSBuild. Pro úlohy, které jsou povoleny pro paralelní spouštění, spravuje pracovní Plánovač uzly a přiřazuje práci k uzlům.

Viz [sestavování více projektů paralelně s nástrojem MSBuild](building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="standard-imports"></a>Standardní importy

*Microsoft. Common. props* a *Microsoft. Common. targets* jsou importovány soubory projektu .NET (explicitně nebo implicitně v projektech se styly sady SDK) a jsou umístěny ve složce *MSBuild\Current\bin* v instalaci sady Visual Studio. Projekty C++ mají svou vlastní hierarchii importů; viz [interní nástroje MSBuild pro projekty C++](/cpp/build/reference/msbuild-visual-cpp-overview).

Soubory *Microsoft. Common. props* nastaví výchozí hodnoty, které můžete přepsat. Je importován (explicitně nebo implicitně) na začátku souboru projektu. Tímto způsobem se nastavení vašeho projektu zobrazí po výchozích nastaveních, aby se přepsaly.

Soubor *Microsoft. Common.* TARGETS a cílové soubory, které importuje, definují standardní proces sestavení pro projekty .NET. Poskytuje také Rozšiřovací body, které lze použít k přizpůsobení sestavení.

V implementaci, *Microsoft. Common. targets* je tenká obálka, která importuje *Microsoft. Common. CurrentVersion. targets*. Tento soubor obsahuje nastavení pro standardní vlastnosti a definuje skutečné cíle, které definují proces sestavení. `Build`Cíl je zde definován, ale ve skutečnosti je prázdný. `Build`Cíl však obsahuje `DependsOn` atribut, který určuje jednotlivé cíle, které tvoří vlastní kroky sestavení, které jsou, `BeforeBuild` `CoreBuild` a `AfterBuild` . `Build`Cíl je definován následujícím způsobem:

```xml
  <PropertyGroup>
    <BuildDependsOn>
      BeforeBuild;
      CoreBuild;
      AfterBuild
    </BuildDependsOn>
  </PropertyGroup>

  <Target
      Name="Build"
      Condition=" '$(_InvalidConfigurationWarning)' != 'true' "
      DependsOnTargets="$(BuildDependsOn)"
      Returns="@(TargetPathWithTargetPlatformMoniker)" />
```

`BeforeBuild`a `AfterBuild` jsou rozšiřovací body. Jsou prázdné v souboru *Microsoft. Common. CurrentVersion. targets* , ale projekty mohou poskytnout své vlastní `BeforeBuild` a `AfterBuild` cíle s úkoly, které je třeba provést před nebo po hlavním procesu sestavení. `AfterBuild`je spuštěn před cílem no-op, `Build` , protože `AfterBuild` se zobrazí v `DependsOn` atributu v `Build` cíli, ale nastane po `CoreBuild` .

`CoreBuild`Cíl obsahuje volání nástrojů sestavení následujícím způsobem:

```xml
  <PropertyGroup>
    <CoreBuildDependsOn>
      BuildOnlySettings;
      PrepareForBuild;
      PreBuildEvent;
      ResolveReferences;
      PrepareResources;
      ResolveKeySource;
      Compile;
      ExportWindowsMDFile;
      UnmanagedUnregistration;
      GenerateSerializationAssemblies;
      CreateSatelliteAssemblies;
      GenerateManifests;
      GetTargetPath;
      PrepareForRun;
      UnmanagedRegistration;
      IncrementalClean;
      PostBuildEvent
    </CoreBuildDependsOn>
  </PropertyGroup>
  <Target
      Name="CoreBuild"
      DependsOnTargets="$(CoreBuildDependsOn)">

    <OnError ExecuteTargets="_TimeStampAfterCompile;PostBuildEvent" Condition="'$(RunPostBuildEvent)'=='Always' or '$(RunPostBuildEvent)'=='OnOutputUpdated'"/>
    <OnError ExecuteTargets="_CleanRecordFileWrites"/>

  </Target>
```

Následující tabulka popisuje tyto cíle: Některé cíle platí pouze pro určité typy projektů.

| Cíl | Popis |
|--------|-------------|
| BuildOnlySettings | Nastavení pouze pro reálné sestavení, nikoli pro při vyvolání MSBuild při načtení projektu aplikací Visual Studio. |
| PrepareForBuild | Příprava požadavků pro sestavení |
| PreBuildEvent | Rozšiřovací bod pro projekty pro definování úkolů, které se mají provést před sestavením |
| ResolveProjectReferences | Analyzovat závislosti projektu a sestavit odkazované projekty |
| ResolveAssemblyReferences| Vyhledejte odkazovaná sestavení. |
| ResolveReferences | Se skládá z `ResolveProjectReferences` a `ResolveAssemblyReferences` k vyhledání všech závislostí. |
| PrepareResources | Zpracovat soubory prostředků |
| ResolveKeySource –| Vyřešte klíč se silným názvem, který se používá k podepsání sestavení, a certifikát použitý k podepsání manifestů [ClickOnce](../deployment/clickonce-security-and-deployment.md) . |
| Sestavení | Vyvolá kompilátor. |
| ExportWindowsMDFile | Vygeneruje soubor [winmd](/uwp/winrt-cref/winmd-files) ze souborů WinMDModule generovaných kompilátorem. |
| UnmanagedUnregistration | Odebrat/vyčistit položky registru [zprostředkovatele komunikace s objekty COM](/dotnet/standard/native-interop/cominterop) z předchozího sestavení |
| GenerateSerializationAssemblies | Vygenerujte sestavení serializace XML pomocí [sgen.exe](/dotnet/standard/serialization/xml-serializer-generator-tool-sgen-exe).|
| CreateSatelliteAssemblies | Vytvořte jedno satelitní sestavení pro každou jedinečnou jazykovou verzi v prostředcích. |
| Generovat manifesty | Generuje aplikace [ClickOnce](../deployment/clickonce-security-and-deployment.md) a manifesty nasazení nebo nativní manifest. |
| Gettargetpath | Vrátí položku obsahující produkt sestavení (spustitelný soubor nebo sestavení) pro tento projekt s metadaty. |
| PrepareForRun | Výstupy sestavení zkopírujte do konečného adresáře, pokud se změnily. |
| UnmanagedRegistration | Nastavení položek registru pro [zprostředkovatele komunikace s objekty COM](/dotnet/standard/native-interop/cominterop) |
| IncrementalClean | Odstraňte soubory, které byly vytvořeny v předchozím buildu, ale nebyly vytvořeny v aktuálním sestavení. To je nezbytné pro `Clean` práci v přírůstkových sestaveních. |
| PostBuildEvent | Rozšiřovací bod pro projekty pro definování úloh, které se spustí po sestavení |

Mnoho cílů v předchozí tabulce se nachází v importech specifických pro konkrétní jazyk, jako je například *Microsoft. CSharp. targets*. Tento soubor definuje kroky v rámci standardního procesu sestavení specifického pro projekty C# .NET. Například obsahuje `Compile` cíl, který ve skutečnosti volá kompilátor jazyka C#.

## <a name="user-configurable-imports"></a>Uživatelsky konfigurovatelné importy

Kromě standardního importu existuje několik importů, které lze přidat pro přizpůsobení procesu sestavení.

- *Directory. Build. props*
- *Directory. Build. targets*

Tyto soubory jsou čteny standardním importem pro všechny projekty v jakékoli podsložce. To je obvykle na úrovni řešení pro nastavení pro řízení všech projektů v řešení, ale může být také vyšší v systému souborů až po kořen jednotky.

Soubor *Directory. Build. props* je importován souborem *Microsoft. Common. props*, takže vlastnosti definované v této složce jsou k dispozici v souboru projektu. Lze je předefinovat v souboru projektu pro přizpůsobení hodnot v jednotlivých projektech. Soubor *Directory. Build. targets* je čten za souborem projektu. Obvykle obsahuje cíle, ale zde můžete také definovat vlastnosti, které nechcete předefinovat jednotlivými projekty.

## <a name="customizations-in-a-project-file"></a>Přizpůsobení v souboru projektu

Visual Studio aktualizuje soubory projektu, když provedete změny v **Průzkumník řešení**, v okně **vlastnosti** nebo ve **vlastnostech projektu**, ale můžete také provádět vlastní změny přímo úpravou souboru projektu.

Mnoho chování sestavení lze nakonfigurovat nastavením vlastností MSBuild buď v souboru projektu pro nastavení místní pro projekt, nebo jak je uvedeno v předchozí části vytvořením souboru *Directory. Build. props* pro nastavení vlastností globálně pro celé složky projektů a řešení. Pro ad hoc sestavení na příkazovém řádku nebo skripty můžete použít také `/p` možnost na příkazovém řádku k nastavení vlastností pro konkrétní vyvolání nástroje MSBuild. Informace o vlastnostech, které lze nastavit, naleznete v tématu [běžné vlastnosti projektu nástroje MSBuild](common-msbuild-project-properties.md) .

## <a name="next-steps"></a>Další kroky

Proces MSBuild má několik dalších rozšiřujících bodů než ty, které jsou zde popsané. Viz [přizpůsobení sestavení](customize-your-build.md). a [jak rozšíříte proces sestavení sady Visual Studio](how-to-extend-the-visual-studio-build-process.md).

## <a name="see-also"></a>Viz také

[Nástroji](msbuild.md)
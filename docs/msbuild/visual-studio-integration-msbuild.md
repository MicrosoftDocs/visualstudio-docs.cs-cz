---
title: Integrace sady Visual Studio (MSBuild)
titleSuffix: ''
description: Zjistěte, Visual Studio můžete hostovat projekty ve formátu MSBuild, i když byly autory různými nástroji a měly přizpůsobené procesy sestavení.
ms.custom: seodec18, SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, reference resolution
- MSBuild, well-known target names
- MSBuild, hosting
- MSBuild, editing project files
- MSBuild, Visual Studio integration
- MSBuild, IntelliSense
- MSBuild, output groups
- MSBuild, in-process compilers
- MSBuild, design-time target execution
ms.assetid: 06cd6d7f-8dc1-4e49-8a72-cc9e331d7bca
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 63e78d935d515ccafda461a8f7af77623387940b
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2021
ms.locfileid: "112602152"
---
# <a name="visual-studio-integration-msbuild"></a>Integrace sady Visual Studio (MSBuild)

Visual Studio msBuild k načtení a sestavení spravovaných projektů. Vzhledem k tomu, že nástroj MSBuild zodpovídá za projekt, lze v nástroji Visual Studio úspěšně použít téměř jakýkoli projekt ve formátu MSBuild, a to i v případě, že byl projekt vytvořen jiným nástrojem a má přizpůsobený proces sestavení.

 Tento článek popisuje konkrétní aspekty hostování Visual Studio MSBuild, které je třeba zvážit při přizpůsobování projektů a *souborů .targets,* které chcete načíst a sestavit v Visual Studio. Pomohou vám zajistit, aby Visual Studio, jako je IntelliSense a ladění, fungovaly pro váš vlastní projekt.

 Informace o projektech C++ najdete v tématu [Soubory projektu](/cpp/build/reference/project-files).

## <a name="project-file-name-extensions"></a>Přípony názvů souborů projektu

 *MSBuild.exe* rozpozná jakoukoli příponu názvu souboru projektu odpovídající vzoru *. \* proj*. Ale Visual Studio pouze podmnožinu těchto přípon názvů souborů projektu, které určují systém projektu specifický pro jazyk, který projekt načte. Visual Studio nemá jazykově neutrální systém projektů založený na MSBuildu.

 Například systém projektu C# načte soubory *.csproj,* ale Visual Studio nemůže načíst *soubor .xxproj.* Soubor projektu pro zdrojové soubory v libovolném jazyce musí používat stejnou příponu jako soubory projektu Visual Basic nebo C#, které se mají načíst do Visual Studio.

## <a name="well-known-target-names"></a>Známé názvy cílů

 Kliknutím na **příkaz** Build Visual Studio spustíte výchozí cíl v projektu. Tento cíl má často také název `Build` . Výběrem příkazu **Rebuild** (Znovu sestavit) nebo **Clean (Vyčistit)** se v projektu pokusíte spustit cíl se stejným názvem. Kliknutím **na** Publikovat spustíte cíl s `PublishOnly` názvem v projektu.

## <a name="configurations-and-platforms"></a>Konfigurace a platformy

 Konfigurace jsou reprezentovány v projektech MSBuild podle vlastností seskupených `PropertyGroup` v elementu, který obsahuje `Condition` atribut. Visual Studio se na tyto podmínky podíváte, abyste vytvořili seznam konfigurací projektu a platforem, které se mají zobrazit. Pro úspěšné extrahování tohoto seznamu musí mít podmínky formát podobný následujícímu:

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 Visual Studio pro tento účel se podíváte na podmínky u `PropertyGroup` elementů , `ItemGroup` , , `Import` vlastností a položek.

## <a name="additional-build-actions"></a>Další akce sestavení

 Visual Studio umožňuje změnit název typu položky souboru v projektu pomocí vlastnosti **Akce** sestavení v **okně Vlastnosti** souboru. **V** této nabídce jsou vždy uvedené názvy typů položek Compile , **EmbeddedResource,** **Content** a **None** a také všechny ostatní názvy typů položek, které už v projektu máte. Pokud chcete zajistit, aby v této nabídce byly vždy dostupné všechny vlastní názvy typů položek, můžete je přidat do typu položky s názvem `AvailableItemName` . Například přidáním následujícího kódu do souboru projektu přidáte do této nabídky vlastní typ **JScript** pro všechny projekty, které ho importuje:

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

Přidání názvů typů položek do typu položky způsobí, že se položky tohoto typu zobrazí `AvailableItemName` **Průzkumník řešení**.

> [!NOTE]
> Některé názvy typů položek jsou pro Visual Studio speciální, ale nejsou uvedené v tomto rozevíracím seznamu.

## <a name="in-process-compilers"></a>Kompilátory v procesu

 Pokud je Visual Studio, nástroj se pokusí použít verzi v procesu nástroje Visual Basic pro zvýšení výkonu. (Nelze použít pro jazyk C#.) Aby to fungovalo správně, musí být splněny následující podmínky:

- V cíli projektu musí být úkol s názvem pro Visual Basic `Vbc` projekty.

- Parametr `UseHostCompilerIfAvailable` úlohy musí být nastaven na hodnotu true.

## <a name="design-time-intellisense"></a>Technologie IntelliSense v době návrhu

 Pokud chcete získat podporu Technologie IntelliSense Visual Studio, než sestavení vygeneruje výstupní sestavení, musí být splněny následující podmínky:

- Musí být cíl s názvem `Compile` .

- Cíl `Compile` nebo jedna z jeho závislostí musí volat úlohu kompilátoru pro projekt, například `Csc` nebo `Vbc` .

- Cíl nebo jedna z jeho závislostí musí způsobit, že kompilátor obdrží všechny potřebné parametry `Compile` pro IntelliSense, zejména všechny odkazy.

- Podmínky uvedené v [části Kompilátory v procesu](#in-process-compilers) musí být splněny.

## <a name="build-solutions"></a>Vytváření řešení

 V Visual Studio se pořadí sestavení projektu a souboru řešení řídí pomocí Visual Studio projektu. Při sestavování řešení *pomocímsbuild.exe* na příkazovém řádku nástroj MSBuild analyzuje soubor řešení a sesoudí sestavení projektu. V obou případech jsou projekty sestaveny jednotlivě v pořadí závislostí a odkazy mezi projekty nejsou procházené. Naopak při sestavení jednotlivých projektů pomocí *msbuild.exe* se prochádí odkazy mezi projekty.

 Při sestavování uvnitř Visual Studio je vlastnost `$(BuildingInsideVisualStudio)` nastavená na `true` . To lze použít v projektu nebo *v souborech .targets,* aby se sestavení chovalo jinak.

## <a name="display-properties-and-items"></a>Zobrazení vlastností a položek

 Visual Studio rozpoznává určité názvy a hodnoty vlastností. Například následující vlastnost v projektu způsobí, že se  aplikace **systému Windows** zobrazí v poli Typ aplikace v **Návrháři projektů**.

```xml
<OutputType>WinExe</OutputType>
```

 Hodnotu vlastnosti lze upravit v Návrháři **projektu** a uložit do souboru projektu. Pokud je této vlastnosti dána neplatná hodnota ručními úpravami, Visual Studio zobrazí při načtení projektu upozornění a nahradí neplatnou hodnotu výchozí hodnotou.

 Visual Studio výchozím hodnotám některých vlastností. Tyto vlastnosti se neuchová v souboru projektu, pokud nemají jiné než výchozí hodnoty.

 Vlastnosti s libovolnými názvy se v seznamu Visual Studio. Chcete-li upravit libovolné vlastnosti Visual Studio, musíte otevřít soubor projektu v editoru XML a ručně je upravit. Další informace najdete v části [Úprava souborů projektu v Visual Studio](#edit-project-files-in-visual-studio) dále v tomto tématu.

 Položky definované v projektu s libovolnými názvy typů položek se ve výchozím nastavení zobrazují **v Průzkumník řešení** pod jejich uzlem projektu. Pokud chcete položku skrýt před zobrazením, nastavte `Visible` metadata na `false` . Například následující položka se bude účastnit procesu sestavení, ale nebude zobrazena v **Průzkumník řešení**.

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> Metadata `Visible` jsou ignorována  Průzkumník řešení pro projekty C++. Položky se vždy zobrazí, i když `Visible` je nastavená hodnota false.

 Položky deklarované v souborech importovaných do projektu se ve výchozím nastavení nezobrazí. Položky vytvořené během procesu sestavení se nikdy nezobrazí v **Průzkumník řešení**.

## <a name="conditions-on-items-and-properties"></a>Podmínky pro položky a vlastnosti

 Během sestavování jsou všechny podmínky plně respektovány.

 Při určování hodnot vlastností, které se mají zobrazit, se vlastnosti, které Visual Studio konfigurace, vyhodnotí jinak než vlastnosti, které považuje za nezávislé na konfiguraci. U vlastností, které považuje za závislé na konfiguraci, Visual Studio a odpovídajícím způsobem nastaví vlastnosti a a instruuje nástroj MSBuild, aby projekt znovu `Configuration` `Platform` vyhodnotil. U vlastností, které považuje za nezávislé na konfiguraci, je neurčité, jak se budou podmínky vyhodnocovat.

 Podmíněné výrazy u položek se vždy ignorují pro účely rozhodování, jestli se má položka zobrazit **v Průzkumník řešení**.

## <a name="debugging"></a>Ladění

 Aby bylo možné najít a spustit výstupní sestavení a připojit ladicí program, Visual Studio vlastnosti , a správně `OutputPath` `AssemblyName` `OutputType` definované. Ladicí program se nepodaří připojit, pokud proces sestavení nezpůsobí vygenerování souboru *.pdb* kompilátorem.

## <a name="design-time-target-execution"></a>Provedení cíle v době návrhu

 Visual Studio se při načítání projektu pokusí spustit cíle s určitými názvy. Mezi tyto cíle `Compile` patří , , , a `ResolveAssemblyReferences` `ResolveCOMReferences` `GetFrameworkPaths` `CopyRunEnvironmentFiles` . Visual Studio tyto cíle spouští tak, aby kompilátor mohl být inicializován pro poskytnutí technologie IntelliSense, lze inicializovat ladicí program a odkazy zobrazené v Průzkumník řešení lze vyřešit. Pokud tyto cíle nejsou k dispozici, projekt se načte a sestaví správně, ale prostředí při návrhu Visual Studio nebude plně funkční.

## <a name="edit-project-files-in-visual-studio"></a>Úprava souborů projektu v Visual Studio

 Chcete-li upravit projekt MSBuild přímo, můžete otevřít soubor projektu v Visual Studio XML.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Uvolnění projektu a jeho úprava v sadě Visual Studio

1. V **Průzkumník řešení** otevřete místní nabídku pro projekt a pak zvolte **Uvolnit projekt**.

     Projekt je označený **jako (nedostupný).**

2. V **Průzkumník řešení** otevřete místní nabídku pro nedostupný projekt a pak zvolte **Upravit \<Project File>**.

     Soubor projektu se otevře v editoru Visual Studio XML.

3. Upravte, uložte a zavřete soubor projektu.

4. V **Průzkumník řešení** otevřete místní nabídku pro nedostupný projekt a pak zvolte **Znovu načíst projekt.**

## <a name="intellisense-and-validation"></a>IntelliSense a ověřování

 Při použití editoru XML k úpravám souborů projektu je technologie IntelliSense a ověřování řízena soubory schématu nástroje MSBuild. Ty se instaluje do mezipaměti schématu, kterou najdete ve složce *\<Visual Studio installation directory> \Xml\Schemas\1033\MSBuild*.

 Základní typy MSBuild jsou definovány v *souboru Microsoft.Build.Core.xsd* a běžné typy používané službou Visual Studio jsou definovány v souboru *Microsoft.Build.CommonTypes.xsd.* Pokud chcete schémata přizpůsobit tak, abyste měli technologii IntelliSense a ověřování pro názvy, vlastnosti a úkoly vlastních položek, můžete buď upravit *soubor Microsoft.Build.xsd,* nebo vytvořit vlastní schéma, které zahrnuje schémata CommonTypes nebo Core. Pokud vytvoříte vlastní schéma, budete muset nasměrovejte editor XML, aby ho našel pomocí **okna** Vlastnosti.

## <a name="edit-loaded-project-files"></a>Úprava načtených souborů projektu

 Visual Studio ukládá do mezipaměti obsah souborů projektu a souborů importovaných soubory projektu. Pokud upravíte načtený soubor projektu, Visual Studio automaticky zobrazí výzvu k opětovnému načtení projektu, aby se změny projeví. Pokud ale upravíte soubor importovaný načteným projektem, nebude k dispozici žádná výzva k opětovnému načtení a musíte projekt uvolnit a znovu ručně načíst, aby se změny projeví.

## <a name="output-groups"></a>Výstupní skupiny

 Několik cílů definovaných v *Microsoft. Common. targets* má názvy končící `OutputGroups` nebo `OutputGroupDependencies` . Visual Studio volá tyto cíle a získá konkrétní seznamy výstupů projektu. Například `SatelliteDllsProjectOutputGroup` cíl vytvoří seznam všech satelitních sestavení, které vytvoří sestavení. Tyto výstupní skupiny jsou používány funkcemi, jako je publikování, nasazení a projekt, na odkazy na projekt. Projekty, které je nedefinují, se načítají a sestavují v aplikaci Visual Studio, ale některé funkce nemusí fungovat správně.

## <a name="reference-resolution"></a>Řešení odkazů

 Řešení odkazů je proces použití referenčních položek uložených v souboru projektu k vyhledání aktuálních sestavení. Aby bylo možné zobrazit podrobné vlastnosti pro každý odkaz v okně **vlastnosti** , musí Visual Studio aktivovat referenční rozlišení. Následující seznam popisuje tři typy odkazů a jejich řešení.

- Odkazy na sestavení:

   Systém projektu volá cíl se známým názvem `ResolveAssemblyReferences` . Tento cíl by měl vydávat položky s názvem typu položky `ReferencePath` . Každá z těchto položek by měla mít specifikaci položky (hodnota `Include` atributu položky) obsahující úplnou cestu k odkazu. Položky by měly mít všechna metadata ze vstupních položek předaných spolu s následujícími novými metadaty:

  - `CopyLocal`, označuje, zda má být sestavení zkopírováno do výstupní složky, nastavte na hodnotu true nebo false.

  - `OriginalItemSpec`obsahuje specifikaci původní položky odkazu.

  - `ResolvedFrom`, nastavte na "{TargetFrameworkDirectory}", pokud byla přeložena z adresáře .NET Framework.

- Odkazy modelu COM:

   Systém projektu volá cíl se známým názvem `ResolveCOMReferences` . Tento cíl by měl vydávat položky s názvem typu položky `ComReferenceWrappers` . Každá z těchto položek by měla mít specifikaci položky obsahující úplnou cestu k definičnímu sestavení pro odkaz COM. Položky by měly mít všechna metadata ze vstupních položek předaných do, kromě nových metadat s názvem `CopyLocal` , což označuje, zda má být sestavení zkopírováno do výstupní složky, nastaveno na hodnotu true nebo false.

- Nativní odkazy

   Systém projektu volá cíl se známým názvem `ResolveNativeReferences` . Tento cíl by měl vydávat položky s názvem typu položky `NativeReferenceFile` . Položky by měly mít všechna metadata ze vstupních položek předaných spolu s novou částí metadat s názvem `OriginalItemSpec` , která obsahuje specifikaci původní položky odkazu.

## <a name="performance-shortcuts"></a>Zástupci výkonu

 Použijete-li prostředí Visual Studio IDE pro spuštění ladění (buď výběrem klávesy F5, nebo výběrem možnosti **ladění**  >  **Spustit ladění** na panelu nabídek), nebo sestavením projektu (například řešení **sestavení sestavení**  >  ), proces sestavení používá k vylepšení výkonu funkci rychlé aktualizace. V některých případech, kdy přizpůsobená sestavení vytváří soubory, které jsou sestaveny, nerozpozná funkce Rychlá aktualizace změněné soubory správně. Projekty, které vyžadují důkladnější kontroly aktualizace, mohou vypnout rychlou kontrolu nastavením proměnné prostředí `DISABLEFASTUPTODATECHECK=1` . Projekty lze také nastavit jako vlastnost MSBuild v projektu nebo v souboru, který projekt importuje.

 Pro běžná sestavení v sadě Visual Studio se nepoužívá kontroler rychlé aktualizace a projekt se vytvoří, jako kdyby jste vyvolali sestavení na příkazovém řádku.

## <a name="see-also"></a>Viz také

- [Postupy: rozšiřování procesu sestavení sady Visual Studio](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [Spuštění sestavení z integrovaného vývojového prostředí (IDE)](../msbuild/starting-a-build-from-within-the-ide.md)
- [Registrovat rozšíření .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [Item – Element (MSBuild)](../msbuild/item-element-msbuild.md)
- [Property – element (MSBuild)](../msbuild/property-element-msbuild.md)
- [Target – element (MSBuild)](../msbuild/target-element-msbuild.md)
- [Csc – úloha](../msbuild/csc-task.md)
- [Vbc – úloha](../msbuild/vbc-task.md)

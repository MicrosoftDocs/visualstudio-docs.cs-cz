---
title: Integrace sady Visual Studio (MSBuild)
titleSuffix: ''
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3468ab5a6a185a759ab43229758c0ff4e9d00e35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77631195"
---
# <a name="visual-studio-integration-msbuild"></a>Integrace sady Visual Studio (MSBuild)

Visual Studio hostuje nástroj MSBuild za účelem načtení a sestavení spravovaných projektů. Vzhledem k tomu, že nástroj MSBuild zodpovídá za projekt, téměř jakýkoli projekt ve formátu MSBuild lze v aplikaci Visual Studio úspěšně použít, i v případě, že projekt byl vytvořen jiným nástrojem a má přizpůsobený proces sestavení.

 Tento článek popisuje konkrétní aspekty hostování MSBuild sady Visual Studio, které byste měli vzít v úvahu při přizpůsobení projektů a *. cílící* na soubory, které chcete načíst a sestavit v aplikaci Visual Studio. Ty vám pomůžou zajistit, aby funkce Visual studia jako IntelliSense a ladění fungovaly pro váš vlastní projekt.

 Další informace o projektech jazyka C++ naleznete v tématu [Project Files](/cpp/build/reference/project-files).

## <a name="project-file-name-extensions"></a>Přípony názvů souborů projektu

 *MSBuild.exe* rozpozná všechny přípony názvů souborů projektu, které odpovídají vzoru *. \* PROJ*. Sada Visual Studio však rozpoznává pouze podmnožinu těchto přípon názvů souborů projektu, které určují systém projektu pro konkrétní jazyk, který načte projekt. Visual Studio nemá jazykově neutrální systém projektů založený na MSBuildu.

 Například systém projektu C# načítá soubory *. csproj* , ale Visual Studio nemůže načíst soubor *. xxproj* . Soubor projektu pro zdrojové soubory v libovolném jazyce musí používat stejnou příponu jako soubory projektu Visual Basic nebo C#, které mají být načteny v aplikaci Visual Studio.

## <a name="well-known-target-names"></a>Známé názvy cílů

 Kliknutím na příkaz **sestavit** v aplikaci Visual Studio se spustí výchozí cíl v projektu. Tento cíl je často také pojmenován `Build` . Výběrem příkazu **znovu sestavit** nebo **vyčistit** se pokusíte spustit cíl se stejným názvem v projektu. Kliknutím na **publikovat** se spustí cíl s názvem `PublishOnly` v projektu.

## <a name="configurations-and-platforms"></a>Konfigurace a platformy

 Konfigurace jsou reprezentovány v projektech nástroje MSBuild podle vlastností seskupených v `PropertyGroup` prvku, který obsahuje `Condition` atribut. Pokud chcete vytvořit seznam konfigurací projektu a platforem pro zobrazení, Visual Studio si tyto podmínky vyhledá. Chcete-li úspěšně extrahovat tento seznam, podmínky musí mít formát podobný následujícímu:

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 Visual Studio hledá v `PropertyGroup` tomto účelu podmínky pro `ItemGroup` prvky,, `Import` , vlastnosti a položky.

## <a name="additional-build-actions"></a>Další akce sestavení

 Visual Studio umožňuje změnit název typu položky souboru v projektu pomocí vlastnosti **Akce sestavení** okna **vlastností souboru** . Názvy typů položek **kompilovat**, **EmbeddedResource**, **Content**a **none** jsou vždy uvedeny v této nabídce společně s jinými názvy typů položek, které jsou již v projektu. Aby bylo zajištěno, že všechny vlastní názvy typů položek jsou v této nabídce vždy k dispozici, můžete názvy přidat k typu položky s názvem `AvailableItemName` . Například přidáním následujícího do souboru projektu se přidá vlastní typ **JScript** do této nabídky pro všechny projekty, které je naimportují:

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

> [!NOTE]
> Některé názvy typů položek jsou pro Visual Studio speciální, ale nejsou uvedené v tomto rozevíracím seznamu.

## <a name="in-process-compilers"></a>Vnitroprocesové kompilátory

 Pokud je to možné, Visual Studio se pokusí o zvýšení výkonu pomocí vnitroprocesové verze kompilátoru Visual Basic. (Neplatí pro C#.) Aby to fungovalo správně, musí se splnit následující podmínky:

- V cíli projektu musí existovat úkol s názvem `Vbc` pro Visual Basic projekty.

- `UseHostCompilerIfAvailable`Parametr úlohy musí být nastaven na hodnotu true.

## <a name="design-time-intellisense"></a>Technologie IntelliSense v době návrhu

 Chcete-li získat podporu technologie IntelliSense v aplikaci Visual Studio předtím, než sestavení vygeneruje výstupní sestavení, musí být splněny následující podmínky:

- Musí existovat cíl s názvem `Compile` .

- Buď `Compile` cíl nebo jedna z jeho závislostí musí volat úlohu kompilátoru pro projekt, například `Csc` nebo `Vbc` .

- Buď `Compile` cíl nebo jedna z jeho závislostí musí způsobit, že kompilátor obdrží všechny nezbytné parametry pro technologii IntelliSense, zejména všechny odkazy.

- Podmínky uvedené v části [kompilátory v rámci procesu](#in-process-compilers) musí být splněné.

## <a name="build-solutions"></a>Vytváření řešení

 V sadě Visual Studio je řazení souborů řešení a sestavení projektu řízeno samotným systémem Visual Studio. Při sestavování řešení pomocí *msbuild.exe* na příkazovém řádku nástroj MSBuild analyzuje soubor řešení a seřadí sestavení projektu. V obou případech jsou projekty sestaveny jednotlivě v pořadí závislosti a odkazy z projektu na projekt nejsou procházeny. Na rozdíl od toho, když jsou jednotlivé projekty sestaveny s *msbuild.exe*, jsou odkazy z projektu na projekt procházeny.

 Při sestavování v sadě Visual Studio `$(BuildingInsideVisualStudio)` je vlastnost nastavena na `true` . To lze použít ve vašem projektu nebo souborech *. targets* , aby se sestavení mohlo chovat jinak.

## <a name="display-properties-and-items"></a>Zobrazení vlastností a položek

 Visual Studio rozpoznává určité názvy vlastností a jejich hodnoty. Například následující vlastnost v projektu způsobí, že se **aplikace systému Windows** zobrazí v poli **Typ aplikace** v **Návrháři projektu**.

```xml
<OutputType>WinExe</OutputType>
```

 Hodnotu vlastnosti lze upravit v **Návrháři projektu** a Uložit do souboru projektu. Pokud je takové vlastnosti předána neplatnou hodnotou ruční úpravou, Visual Studio zobrazí upozornění, když je projekt načtený, a nahradí neplatnou hodnotu výchozí hodnotou.

 Visual Studio rozumí výchozím nastavením pro některé vlastnosti. Tyto vlastnosti nebudou uchovány do souboru projektu, pokud nemají hodnoty, které nejsou výchozími hodnotami.

 Vlastnosti s libovolnými názvy nejsou v aplikaci Visual Studio zobrazeny. Chcete-li upravit libovolné vlastnosti v aplikaci Visual Studio, je nutné otevřít soubor projektu v editoru XML a upravit je ručně. Další informace naleznete v části [Úpravy souborů projektu v aplikaci Visual Studio](#edit-project-files-in-visual-studio) dále v tomto tématu.

 Položky definované v projektu s libovolnými názvy typů položek jsou ve výchozím nastavení zobrazeny v **Průzkumník řešení** pod jejich uzlem projektu. Chcete-li skrýt položku ze zobrazení, nastavte `Visible` metadata na `false` . Například následující položka se bude účastnit procesu sestavení, ale nebude se zobrazovat v **Průzkumník řešení**.

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> `Visible`Metadata jsou ignorována **Průzkumník řešení** pro projekty v jazyce C++. Položky budou vždy zobrazeny, i když `Visible` je nastavena na hodnotu false.

 Položky deklarované v souborech importovaných do projektu se ve výchozím nastavení nezobrazují. Položky vytvořené během procesu sestavení nejsou nikdy zobrazeny v **Průzkumník řešení**.

## <a name="conditions-on-items-and-properties"></a>Podmínky pro položky a vlastnosti

 Během sestavení jsou všechny podmínky plně dodržovány.

 Při určování hodnot vlastností, které se mají zobrazit, se vlastnosti, které Visual Studio považují za závislé na konfiguraci, vyhodnotí jinak než vlastnosti, které považují Pro vlastnosti, které považuje za závislé na konfiguraci, sada Visual Studio `Configuration` správně nastaví vlastnosti a a `Platform` instruuje nástroj MSBuild, aby projekt znovu vyhodnotil. U vlastností, které považuje za nezávislé na konfiguraci, je neurčité, jak budou podmínky vyhodnoceny.

 Podmíněné výrazy u položek se vždycky ignorují pro účely rozhodování o tom, jestli se má položka zobrazit v **Průzkumník řešení**.

## <a name="debugging"></a>Ladění

 Aby bylo možné najít a spustit výstupní sestavení a připojit ladicí program, Visual Studio potřebuje vlastnosti `OutputPath` , `AssemblyName` a `OutputType` správně definované. Ladicí program se nepodaří připojit, pokud proces sestavení nezpůsobil, že kompilátor vygeneroval soubor *. pdb* .

## <a name="design-time-target-execution"></a>Provádění cílů v době návrhu

 Visual Studio se pokusí provést cíle s určitými názvy při načtení projektu. Mezi tyto cíle patří,,, `Compile` `ResolveAssemblyReferences` `ResolveCOMReferences` `GetFrameworkPaths` a `CopyRunEnvironmentFiles` . Visual Studio spouští tyto cíle, aby bylo možné inicializovat kompilátor pro poskytování technologie IntelliSense, ladicí program lze inicializovat a odkazy zobrazené v Průzkumník řešení lze vyřešit. Pokud tyto cíle nejsou k dispozici, projekt se načte a sestaví správně, ale prostředí pro dobu návrhu v aplikaci Visual Studio nebude plně funkční.

## <a name="edit-project-files-in-visual-studio"></a>Úpravy souborů projektu v aplikaci Visual Studio

 Chcete-li upravit projekt MSBuild přímo, můžete otevřít soubor projektu v editoru XML sady Visual Studio.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Uvolnění projektu a jeho úprava v sadě Visual Studio

1. V **Průzkumník řešení**otevřete místní nabídku pro projekt a pak zvolte **Uvolnit projekt**.

     Projekt je označený **(není k dispozici)**.

2. V **Průzkumník řešení**otevřete místní nabídku pro nedostupný projekt a pak zvolte **Upravit \<Project File> **.

     Soubor projektu se otevře v editoru XML sady Visual Studio.

3. Upravte, uložte a zavřete soubor projektu.

4. V **Průzkumník řešení**otevřete místní nabídku pro nedostupný projekt a pak zvolte **znovu načíst projekt**.

## <a name="intellisense-and-validation"></a>IntelliSense a ověřování

 Při použití editoru XML k úpravám souborů projektu je technologie IntelliSense a ověřování ovládána pomocí souborů schématu MSBuild. Ty jsou nainstalované v mezipaměti schématu, které najdete v * \<Visual Studio installation directory> \Xml\Schemas\1033\MSBuild*.

 Základní typy nástroje MSBuild jsou definovány v *Microsoft. Build. Core. xsd* a běžné typy používané v aplikaci Visual Studio jsou definovány v *Microsoft. Build. CommonTypes. xsd*. Chcete-li přizpůsobit schémata, abyste měli IntelliSense a ověřování pro vlastní názvy typů položek, vlastnosti a úkoly, můžete buď upravit *Microsoft. Build. xsd*, nebo vytvořit vlastní schéma, které obsahuje schémata CommonTypes nebo Core. Pokud vytvoříte vlastní schéma, budete muset nasměrovat editor XML, abyste ho našli pomocí okna **vlastnosti** .

## <a name="edit-loaded-project-files"></a>Upravit načtené soubory projektu

 Visual Studio ukládá do mezipaměti obsah souborů projektu a souborů importovaných soubory projektu. Pokud upravíte načtený soubor projektu, Visual Studio vás automaticky vyzve k opětovnému načtení projektu, aby se změny projevily. Pokud však upravíte soubor importovaný načteným projektem, nezobrazí se výzva k opakovanému načtení a je nutné znovu načíst a znovu načíst projekt, aby se změny projevily.

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

 Použijete-li prostředí Visual Studio IDE pro spuštění ladění (buď výběrem klávesy F5, nebo výběrem možnosti **ladění**  >  **Spustit ladění** na panelu nabídek), nebo sestavením projektu (například řešení **sestavení sestavení**  >  **Build Solution**), proces sestavení používá k vylepšení výkonu funkci rychlé aktualizace. V některých případech, kdy přizpůsobená sestavení vytváří soubory, které jsou sestaveny, nerozpozná funkce Rychlá aktualizace změněné soubory správně. Projekty, které vyžadují důkladnější kontroly aktualizace, mohou vypnout rychlou kontrolu nastavením proměnné prostředí `DISABLEFASTUPTODATECHECK=1` . Projekty lze také nastavit jako vlastnost MSBuild v projektu nebo v souboru, který projekt importuje.

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

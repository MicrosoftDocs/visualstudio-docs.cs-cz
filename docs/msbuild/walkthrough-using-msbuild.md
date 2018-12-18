---
title: 'Návod: Použití nástroje MSBuild | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 94fdbb5f143d1c087d97490961d230ace239f348
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880146"
---
# <a name="walkthrough-use-msbuild"></a>Návod: Použití nástroje MSBuild
Nástroj MSBuild je platforma sestavení pro společnost Microsoft a sady Visual Studio. Tento návod vás seznámí s stavební kameny nástroje MSBuild a ukazuje, jak psát, manipulaci a ladit projekty MSBuild. Kurzu se naučíte:

-   Vytváření a manipulaci se soubor projektu.

-   Postup při využívání vlastností sestavení

-   Jak používat sestavení položky.

Můžete spustit nástroj MSBuild ze sady Visual Studio nebo z **příkazové okno**. V tomto návodu vytvoříte soubor projektu MSBuild pomocí sady Visual Studio. Úprava souboru projektu v sadě Visual Studio a použít **příkazové okno** se projekt sestavil a podívejte se na výsledky.

## <a name="create-an-msbuild-project"></a>Vytvoření projektu nástroje MSBuild
 Systém projektu sady Visual Studio je založen na MSBuild. To usnadňuje vytvoření nového souboru projektu pomocí sady Visual Studio. V této části vytvoříte soubor projektu Visual C#. Můžete místo toho vytvořte soubor projektu jazyka Visual Basic. V rámci tohoto návodu rozdíl mezi dvěma projektu soubory je menší.

#### <a name="to-create-a-project-file"></a>K vytvoření souboru projektu

1.  Otevřít Visual Studio.

2.  Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.

3.  V **nový projekt** dialogové okno, vyberte **Visual C#** typ projektu a pak vyberte **formulářová aplikace Windows** šablony. V **název** zadejte `BuildApp`. Zadejte **umístění** pro řešení, například *D:\\*. Přijměte výchozí hodnoty pro **vytvořit adresář pro řešení** (vybrané), **přidat do správy zdrojových kódů** (nevybráno), a **název řešení** (**BuildApp**).

4.    Klikněte na tlačítko **OK** k vytvoření souboru projektu.

## <a name="examine-the-project-file"></a>Zkontrolujte v souboru projektu
 V předchozí části jste použili Visual Studio k vytvoření souboru projektu Visual C#. Soubor projektu je vyjádřena v **Průzkumníka řešení** uzel projektu s názvem BuildApp. Editor kódu sady Visual Studio můžete použít k prozkoumání souboru projektu.

#### <a name="to-examine-the-project-file"></a>K prozkoumání souboru projektu

1.  V **Průzkumníka řešení**, klikněte na uzel projektu **BuildApp**.

2.  V **vlastnosti** prohlížeče, Všimněte si, že **soubor projektu** vlastnost *BuildApp.csproj*. Všechny soubory projektu jsou pojmenované s příponou *proj*. Pokud jste vytvořili projekt jazyka Visual Basic, název souboru projektu by *BuildApp.vbproj*.

3.  Klikněte pravým tlačítkem na uzel projektu a pak klikněte na **uvolnit projekt**.

4.  Znovu klikněte pravým tlačítkem na uzel projektu a pak klikněte na **upravit BuildApp.csproj**.

     Soubor projektu se zobrazí v editoru kódu.

## <a name="targets-and-tasks"></a>Cíle a úlohy
Soubory projektu jsou soubory ve formátu XML s kořenový uzel [projektu](../msbuild/project-element-msbuild.md).

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

V elementu projektu je nutné zadat obor názvů xmlns. Pokud `ToolsVersion` je k dispozici v novém projektu, musí být "15.0".

Sestavování aplikace práci s [cílové](../msbuild/target-element-msbuild.md) a [úloh](../msbuild/task-element-msbuild.md) elementy.

-   Úloha je nejmenší jednotka práce, jinými slovy, "atom" sestavení. Úlohy jsou nezávislé spustitelný komponenty, které mohou mít vstupy a výstupy. Nejsou žádné úkoly právě odkazované nebo definované v souboru projektu. Přidání úkolů do souboru projektu v následujících částech. Další informace najdete v tématu [úlohy](../msbuild/msbuild-tasks.md) tématu.

-   Cíl je pojmenovaný pořadí úloh. Další informace najdete v tématu [cíle](../msbuild/msbuild-targets.md) tématu.

Výchozí cíl není definován v souboru projektu. Místo toho se zadává v importované projekty. [Import](../msbuild/import-element-msbuild.md) prvek určuje importované projekty. Například výchozí cíl v projektu jazyka C#, importována ze souboru *Microsoft.CSharp.targets*.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

Importované soubory efektivně vloženy do souboru projektu bez ohledu na to se na ně odkazuje.

> [!NOTE]
> Některé typy projektů, jako je .NET Core použijte zjednodušené schéma s `Sdk` atribut namísto `ToolsVersion`. Tyto projekty mají implicitní importy a různé výchozí hodnoty atributů.

Nástroj MSBuild sleduje cíle sestavení a zaručuje, že každý cíl je vytvořeno více než jednou.

## <a name="add-a-target-and-a-task"></a>Přidání cíle a úlohy
 Přidání cíle do souboru projektu. Přidejte úkol do cíle, který vytiskne zprávu.

#### <a name="to-add-a-target-and-a-task"></a>Chcete-li přidat cíl a úkol

1.  Přidejte tyto řádky do souboru projektu, hned za příkaz importu:

    ```xml
    <Target Name="HelloWorld">
    </Target>
    ```

     To vytvoří cíl s názvem Hello World. Všimněte si, že máte podporu technologie IntelliSense při úpravách souboru projektu.

2.  Přidáte řádky do cíle HelloWorld, tak, aby výsledný oddíl vypadá takto:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Hello"></Message>  <Message Text="World"></Message>
    </Target>
    ```

3.  Uložte soubor projektu.

Úloha zprávy je jedním z celé řadě úloh, která se dodává s nástrojem MSBuild. Úplný seznam dostupných úkolů a informace o použití najdete v části [úkolů odkaz](../msbuild/msbuild-task-reference.md).

Úloha zprávy přijímá řetězcovou hodnotu atributu Text jako vstup a zobrazí ho na výstupním zařízení. Cíl HelloWorld provede úkol zpráv dvakrát: nejprve k zobrazení "Hello" a potom zobrazíte "World".

## <a name="build-the-target"></a>Cíl sestavení
 Spustit nástroj MSBuild z **příkazový řádek sady Visual Studio** sestavit cíl HelloWorld výše. Použití - cíl nebo -t přepínač příkazového řádku a vyberte cíl.

> [!NOTE]
>  Budeme **příkazový řádek sady Visual Studio** jako **příkazové okno** v následujících částech.

#### <a name="to-build-the-target"></a>K sestavení cíle

1.  Klikněte na tlačítko **Start**, pak klikněte na tlačítko **všechny programy**. Vyhledejte a klikněte **příkazový řádek sady Visual Studio** v **Visual Studio Tools** složky.

2.  V příkazovém řádku přejděte do složky obsahující soubor projektu, v tomto případě *D:\BuildApp\BuildApp*.

3.  Spuštění nástroje msbuild pomocí příkazu Přepnout - t: HelloWorld. To vybere a sestavuje cílový HelloWorld:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  Prohlédněte si výstup v **příkazové okno**. Měli byste vidět dva řádky "Hello" a "World":

    ```
    Hello
    World
    ```

> [!NOTE]
>  Pokud místo toho uvidíte `The target "HelloWorld" does not exist in the project` pak pravděpodobně jste zapomněli uložte soubor projektu v editoru kódu. Uložte soubor a zkuste to znovu.

 Podle střídavých mezi editorem kódu a příkazového okna, můžete změnit soubor projektu a rychle zobrazit výsledky.

## <a name="build-properties"></a>Vlastnosti sestavení
 Vlastnosti sestavení jsou páry název hodnota, která provede sestavení. Několik vlastností sestavení jsou již definovány v horní části souboru projektu:

```xml
<PropertyGroup>
...
  <ProductVersion>10.0.11107</ProductVersion>
  <SchemaVersion>2.0</SchemaVersion>
  <ProjectGuid>{30E3C9D5-FD86-4691-A331-80EA5BA7E571}</ProjectGuid>
  <OutputType>WinExe</OutputType>
...
</PropertyGroup>
```

 Všechny vlastnosti jsou podřízené elementy PropertyGroup prvků. Název vlastnosti je název podřízeného prvku a hodnota vlastnosti je textový prvek podřízeného prvku. Například

```xml
<TargetFrameworkVersion>v15.0</TargetFrameworkVersion>
```

 definuje vlastnost s názvem TargetFrameworkVersion, že mu poskytneme řetězcovou hodnotu "v15.0".

 Vytvoření vlastnosti může kdykoli znovu definovat. If

```xml
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
```

 Zobrazí se později v souboru projektu nebo v souboru importu později v souboru projektu, pak TargetFrameworkVersion přijímá nová hodnota "v3.5".

## <a name="examine-a-property-value"></a>Zkontrolujte hodnotu vlastnosti
 Pokud chcete získat hodnotu vlastnosti, použijte následující syntaxi, kde hodnota PropertyName je název vlastnosti:

```xml
$(PropertyName)
```

 Použijte následující syntaxi k prozkoumání některých vlastností v souboru projektu.

#### <a name="to-examine-a-property-value"></a>Chcete-li zkontrolovat hodnotu vlastnosti

1.  Z editoru kódu nahraďte HelloWorld cíl s tímto kódem:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Configuration is $(Configuration)" />
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />
    </Target>
    ```

2.  Uložte soubor projektu.

3.  Z **příkazové okno**, zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  Zkontrolujte výstup příkazu. Zobrazí se tyto dva řádky (.NET Framework verze se může lišit):

    ```
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2017\<Visual Studio SKU>\MSBuild\15.0\Bin
    ```

> [!NOTE]
>  Pokud se tyto řádky pak jste pravděpodobně zapomněli uložte soubor projektu v editoru kódu. Uložte soubor a zkuste to znovu.

### <a name="conditional-properties"></a>Podmíněné vlastnosti
 Mnoho vlastností, jako je konfigurace jsou definovány podmíněně, to znamená, se zobrazí v prvku vlastnost atributu podmínky. Podmíněné vlastnosti jsou definované nebo znovu definovat pouze v případě, že bude podmínka vyhodnocena jako "true". Všimněte si, že nedefinovanými vlastnostmi jsou uvedeny výchozí hodnotu prázdný řetězec. Například

```xml
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 znamená "Pokud ještě nebyl definován konfigurační vlastnosti, definujte ho a přiřaďte jí hodnotu"Ladění"".

 Téměř všechny elementy MSBuild může mít atribut podmínku. Další informace o použití atributu podmínky najdete v článku [podmínky](../msbuild/msbuild-conditions.md).

### <a name="reserved-properties"></a>Rezervované vlastnosti
 Nástroj MSBuild rezervuje některé názvy vlastností k ukládání informací o souboru projektu a binární soubory nástroje MSBuild. MSBuildToolsPath je příkladem rezervované vlastnosti. Rezervované vlastnosti je odkazováno pomocí zápisu $ jakékoli jiné vlastnosti. Další informace najdete v tématu [postupy: odkazování na název nebo umístění souboru projektu](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) a [MSBuild vyhrazené a dobře známé vlastnosti](../msbuild/msbuild-reserved-and-well-known-properties.md).

### <a name="environment-variables"></a>Proměnné prostředí
 Proměnné prostředí v souborech projektu může odkazovat stejným způsobem, jak vlastnosti sestavení. Například použít proměnné prostředí PATH v souboru projektu, použijte příkaz $(Path). Obsahuje-li projekt definici vlastnosti, který má stejný název jako proměnné prostředí, přepíše vlastnost v projektu hodnotu proměnné prostředí. Další informace najdete v tématu [postupy: použití proměnných prostředí v sestavení](../msbuild/how-to-use-environment-variables-in-a-build.md).

## <a name="set-properties-from-the-command-line"></a>Nastavit vlastnosti z příkazového řádku
 Vlastnosti mohou být definovány pomocí příkazového řádku / vlastnost nebo -p přepínač příkazového řádku. Vlastnost hodnoty přijatých z příkazového řádku přepisují hodnoty vlastností nastavené v proměnné prostředí a souboru projektu.

#### <a name="to-set-a-property-value-from-the-command-line"></a>Chcete-li nastavit hodnotu vlastnosti z příkazového řádku

1.  Z **příkazové okno**, zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld -p:Configuration=Release
    ```

2.  Zkontrolujte výstup příkazu. Zobrazí se tento řádek:

    ```
    Configuration is Release.
    ```

Nástroj MSBuild vytvoří vlastnost konfigurace a dá jí hodnotu "Verze".

## <a name="special-characters"></a>Speciální znaky
 Některé znaky mají speciální význam v souborech projektu MSBuild. Příklady těchto znaků: středníkem (;) a hvězdičky (*). Chcete-li použít tyto speciální znaky jako literály v souboru projektu, se musí zadat pomocí syntaxe %\<xx >, kde \<xx > představuje znak šestnáctkové hodnoty ASCII.

 Změna zpráva úlohy aby se zobrazila hodnota konfigurační vlastnosti se speciálními znaky, aby byl lépe čitelný.

#### <a name="to-use-special-characters-in-the-message-task"></a>Použití speciálních znaků v úloha zprávy

1.  Z editoru kódu nahraďte oba úkoly zpráva tento řádek:

    ```xml
    <Message Text="%24(Configuration) is %22$(Configuration)%22" />
    ```

2.  Uložte soubor projektu.

3.  Z **příkazové okno**, zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  Zkontrolujte výstup příkazu. Zobrazí se tento řádek:

    ```
    $(Configuration) is "Debug"
    ```

Další informace najdete v tématu [speciální znaky nástroje MSBuild](../msbuild/msbuild-special-characters.md).

## <a name="build-items"></a>Vytvoření položky
 Položka je určitý údaj, obvykle zadat název souboru, který se používá jako vstup do systému sestavení. Například mohla být předána kolekci položek představující zdrojové soubory pro úlohu s názvem kompilace pro jejich zkompilování do sestavení.

 Všechny položky jsou podřízené prvky ItemGroup prvků. Název položky je název podřízeného prvku, a hodnotu položky se hodnota atributu Include podřízeného prvku. Hodnoty položek se stejným názvem se shromáždí do typů položek s tímto názvem.  Například

```xml
<ItemGroup>
    <Compile Include="Program.cs" />
    <Compile Include="Properties\AssemblyInfo.cs" />
</ItemGroup>
```

 Definuje skupinu položky obsahující dvě položky. Typ položky kompilace má dvě hodnoty: *Program.cs* a *Properties\AssemblyInfo.cs*.

 Následující kód vytvoří stejný typ položky deklarováním oba soubory v jednom atributu Include, oddělené středníky.

```xml
<ItemGroup>
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />
</ItemGroup>
```

Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).

> [!NOTE]
>  Cesty k souboru jsou relativní vzhledem ke složce obsahující soubor projektu MSBuild.

## <a name="examine-item-type-values"></a>Zkontrolujte položky typu hodnoty
 K získání hodnot typu položky, použijte následující syntaxi, kde je ItemType název typu položky:

```xml
@(ItemType)
```

 Použijte následující syntaxi pro zjištění kompilace typ položky v souboru projektu.

#### <a name="to-examine-item-type-values"></a>Prozkoumat položky typu hodnoty

1.  Z editoru kódu nahraďte úloh HelloWorld cíl s tímto kódem:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Compile item type contains @(Compile)" />
    </Target>
    ```

2.  Uložte soubor projektu.

3.  Z **příkazové okno**, zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  Zkontrolujte výstup příkazu. Měli byste vidět tento dlouhý řádek:

    ```
    Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
    ```

Hodnoty typu položky jsou oddělené středníkem, ve výchozím nastavení.

Chcete-li změnit oddělovač typ položky, použijte následující syntaxi, kde ItemType je typ položky a oddělovač je řetězec jeden nebo více oddělovacích znaků:

```xml
@(ItemType, Separator)
```

Úloha zprávy konce řádků a řádek informačních kanálů změnit (% 0A %0 D) zobrazíte kompilace položek na jeden řádek.

#### <a name="to-display-item-type-values-one-per-line"></a>Chcete-li zobrazit položky typu hodnoty na jeden řádek

1.  Z editoru kódu nahraďte tento řádek úloha zprávy:

    ```xml
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />
    ```

2.  Uložte soubor projektu.

3.  Z **příkazové okno**, zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  Zkontrolujte výstup příkazu. Měli byste vidět tyto řádky:

    ```
    Compile item type contains Form1.cs
    Form1.Designer.cs
    Program.cs
    Properties\AssemblyInfo.cs
    Properties\Resources.Designer.cs
    Properties\Settings.Designer.cs
    ```

### <a name="include-exclude-and-wildcards"></a>Zahrnout, vyloučit a zástupné znaky
 Můžete použít zástupné znaky "*","\*\*", a "?" s atributem zahrnout přidání položek do typ položky. Například

```xml
<Photos Include="images\*.jpeg" />
```

 Přidá všechny soubory s příponou souboru *.jpeg* v *imagí* složku pro typ položky fotografie, zatímco

```xml
<Photos Include="images\**.jpeg" />
```

 Přidá všechny soubory s příponou souboru *.jpeg* v *imagí* složka a všechny její podsložky, typu položky fotografie. Další příklady najdete v tématu [postupy: výběr souborů pro sestavení](../msbuild/how-to-select-the-files-to-build.md).

 Všimněte si, jak jsou deklarovány položky se přidají do typu položky. Například

```xml
<Photos Include="images\*.jpeg" />
<Photos Include="images\*.gif" />
```

 Vytvoří typ položky s názvem fotografií, který obsahuje všechny soubory v *image* složku s příponou souboru buď *.jpeg* nebo *.gif*. Toto je shodné s následující řádek:

```xml
<Photos Include="images\*.jpeg;images\*.gif" />
```

 Položky můžete vyloučit z typu položky s atributem vyloučení. Například

```xml
<Compile Include="*.cs" Exclude="*Designer*">
```

 Přidá všechny soubory s příponou souboru *.cs* typu položky kompilace, s výjimkou souborů jejichž názvy obsahují řetězec *návrháře*. Další příklady najdete v tématu [postupy: vyloučení souborů ze sestavení](../msbuild/how-to-exclude-files-from-the-build.md).

Atribut vyloučení ovlivňuje pouze položky přidané v atributu Include v prvku položky, která obsahuje oba. Například

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

nebude vyjměte soubor *Form1.cs*, která byla přidána do předchozí prvek položky.

##### <a name="to-include-and-exclude-items"></a>Chcete zahrnout a vyloučit položky

1.  Z editoru kódu nahraďte tento řádek úloha zprávy:

    ```xml
    <Message Text="XFiles item type contains @(XFiles)" />
    ```

2.  Tato skupina položek přidejte hned za importovaný prvek:

    ```xml
    <ItemGroup>
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />
    </ItemGroup>
    ```

3.  Uložte soubor projektu.

4.  Z **příkazové okno**, zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

5.  Zkontrolujte výstup příkazu. Zobrazí se tento řádek:

    ```
    XFiles item type contains Form1.cs;Program.cs;Properties/Resources.resx
    ```

## <a name="item-metadata"></a>Metadata položky
 Položky mohou obsahovat metadata kromě informace získané z atributy zahrnutí a vyloučení. Tato metadata je možné podle úlohy, které vyžadují další informace o položkách než hodnotu položky.

 Metadata položek je deklarována v souboru projektu vytvořením prvku s názvem metadat jako podřízený prvek položky. Položka může mít nula nebo více hodnot metadat. Například následující položka CSFile neobsahuje jazykové verze metadata s hodnotou "Fr":

```xml
<ItemGroup>
    <CSFile Include="main.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 K získání hodnoty metadat typu položky, použijte následující syntaxi, kde je ItemType název typu položky a MetaDataName je název metadat:

```xml
%(ItemType.MetaDataName)
```

#### <a name="to-examine-item-metadata"></a>Prozkoumat metadata položky

1.  Z editoru kódu nahraďte tento řádek úloha zprávy:

    ```xml
    <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />
    ```

2.  Uložte soubor projektu.

3.  Z **příkazové okno**, zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  Zkontrolujte výstup příkazu. Měli byste vidět tyto řádky:

    ```
    Compile.DependentUpon:
    Compile.DependentUpon: Form1.cs
    Compile.DependentUpon: Resources.resx
    Compile.DependentUpon: Settings.settings
    ```

Všimněte si, jak frázi "Compile.DependentUpon" zobrazuje několikrát. Používání metadat pomocí této syntaxe v rámci cíle způsobí, že "dávkování". Dávkování znamená, že po spuštění úlohy v rámci cíl pro každou hodnotu jedinečný metadat. To je ekvivalentní skript MSBuild nejběžnější "smyčka" for programovací konstrukce. Další informace najdete v tématu [dávkování](../msbuild/msbuild-batching.md).

### <a name="well-known-metadata"></a>známá metadata
 Při každém přidání položky do seznamu položek této položky je přiřazen některé známé metadat. Například %(Filename) vrátí název souboru žádné položky. Úplný seznam známých metadata, najdete v části [známá metadata položky](../msbuild/msbuild-well-known-item-metadata.md).

##### <a name="to-examine-well-known-metadata"></a>Prozkoumat dobře známé metadat

1.  Z editoru kódu nahraďte tento řádek úloha zprávy:

    ```xml
    <Message Text="Compile Filename: %(Compile.Filename)" />
    ```

2.  Uložte soubor projektu.

3.  Z **příkazové okno**, zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  Zkontrolujte výstup příkazu. Měli byste vidět tyto řádky:

    ```
    Compile Filename: Form1
    Compile Filename: Form1.Designer
    Compile Filename: Program
    Compile Filename: AssemblyInfo
    Compile Filename: Resources.Designer
    Compile Filename: Settings.Designer
    ```

Porovnáním obou výše uvedených příkladech vidíte, že když ne každá položka v kompilaci typu položky nemá DependentUpon metadat, všechny položky mít dobře známý název souboru metadat.

### <a name="metadata-transformations"></a>Metadata transformace
 Seznamy se dají transformovat položky do nové položky seznamů. Transformace seznam položek, použijte následující syntaxi, kde \<ItemType > je název typu položky a \<MetadataName > je název metadat:

```xml
@(ItemType -> '%(MetadataName)')
```

Například je možné transformovat seznam položek zdrojových souborů do kolekce souborů objektů vlastnosti autorefresh pomocí výrazu jako `@(SourceFiles -> '%(Filename).obj')`. Další informace najdete v tématu [transformuje](../msbuild/msbuild-transforms.md).

##### <a name="to-transform-items-using-metadata"></a>Chcete-li transformovat pomocí metadat položky

1.  Z editoru kódu nahraďte tento řádek úloha zprávy:

    ```xml
    <Message Text="Backup files: @(Compile->'%(filename).bak')" />
    ```

2.  Uložte soubor projektu.

3.  Z **příkazové okno**, zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4.  Zkontrolujte výstup příkazu. Zobrazí se tento řádek:

    ```
    Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak
    ```

Všimněte si, že se tato metadata v této syntaxe nezpůsobí dávkování.

## <a name="whats-next"></a>Co se chystá?
 Zjistěte, jak vytvořit jednoduchý projekt jeden krok souborů najednou, vyzkoušejte si [návod: vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

## <a name="see-also"></a>Viz také:

- [Přehled nástroje MSBuild](../msbuild/msbuild.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)

---
title: 'Návod: Použití msbuild | Dokumenty společnosti Microsoft'
ms.date: 03/20/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3e3f0ec3938136370daf15954d8c13da5905ba4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631078"
---
# <a name="walkthrough-use-msbuild"></a>Návod: Použití MSBuild

MSBuild je platforma sestavení pro Microsoft a Visual Studio. Tento návod vás seznámí se stavebními bloky MSBuild a ukáže, jak psát, manipulovat a ladit projekty MSBuild. Dozvíte se o:

- Vytváření a manipulace se souborem projektu.

- Použití vlastností sestavení

- Použití položek sestavení.

MSBuild můžete spustit z visual studia nebo z **příkazového okna**. V tomto návodu vytvoříte soubor projektu MSBuild pomocí sady Visual Studio. Soubor projektu můžete upravit v sadě Visual Studio a pomocí **příkazového okna** vytvořit projekt a prozkoumat výsledky.

## <a name="create-an-msbuild-project"></a>Vytvoření projektu MSBuild

 Systém projektu sady Visual Studio je založen na msbuild. To usnadňuje vytvoření nového souboru projektu pomocí sady Visual Studio. V této části vytvoříte soubor projektu Visual C#. Místo toho můžete vytvořit soubor projektu jazyka Visual Basic. V kontextu tohoto návodu je rozdíl mezi dvěma soubory projektu menší.

**Vytvoření souboru projektu**

1. Otevřete Visual Studio a vytvořte projekt.

    ::: moniker range=">=vs-2019"
    Stisknutím **klávesy Esc** zavřete počáteční okno. Zadejte **Ctrl + Q,** chcete-li otevřít vyhledávací pole, zadejte **winforms**a pak zvolte **Vytvořit novou aplikaci Windows Forms App (.NET Framework).** V zobrazeném dialogovém okně zvolte **Vytvořit**.

    Do pole **Název** zadejte `BuildApp`. Zadejte **umístění** řešení, například *D:\\*. Přijměte výchozí hodnoty pro **řešení**, **název řešení** (**BuildApp**) a **framework**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **nového** > **projektu**. V levém podokně dialogového okna **Nový projekt** rozbalte **položku Visual C#** > **Windows Desktop**a pak zvolte Windows Forms **App (.NET Framework).** Pak zvolte **OK**.

    Do pole **Název** zadejte `BuildApp`. Zadejte **umístění** řešení, například *D:\\*. Přijmout výchozí hodnoty pro **Vytvořit adresář pro řešení** (vybrané), Přidat do správy **zdrojového kódu** (není vybráno) a Název **řešení** (**BuildApp**).
    ::: moniker-end

1. Chcete-li vytvořit soubor projektu, klepněte na **tlačítko OK** nebo **Vytvořit.**

## <a name="examine-the-project-file"></a>Zkontrolujte soubor projektu

 V předchozí části jste použili Visual Studio k vytvoření souboru projektu Visual C#. Soubor projektu je reprezentován v **Průzkumníku řešení** uznatým projektem s názvem BuildApp. Můžete použít editor kódu sady Visual Studio ke kontrole souboru projektu.

**Chcete-li zkontrolovat soubor projektu**

1. V **Průzkumníku řešení**klepněte na uzel projektu **BuildApp**.

2. V prohlížeči **Vlastnosti** si všimněte, že vlastnost **Soubor projektu** je *BuildApp.csproj*. Všechny soubory projektu jsou pojmenovány s příponou *proj*. Pokud jste vytvořili projekt jazyka Visual Basic, název souboru projektu by *buildapp.vbproj*.

3. Klikněte pravým tlačítkem myši na uzel projektu a potom klikněte na **příkaz Uvolnit projekt**.

4. Znovu klikněte pravým tlačítkem myši na uzel projektu a potom klikněte na **příkaz Upravit soubor BuildApp.csproj**.

     Soubor projektu se zobrazí v editoru kódu.

## <a name="targets-and-tasks"></a>Cíle a úkoly

Soubory projektu jsou soubory ve formátu XML s kořenovým uzlem [Project](../msbuild/project-element-msbuild.md).

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

V elementu Project je nutné zadat obor názvů xmlns. Pokud `ToolsVersion` je přítomen v novém projektu, musí být "15.0".

Práce vytváření aplikace se provádí s [Target](../msbuild/target-element-msbuild.md) a [Task](../msbuild/task-element-msbuild.md) prvky.

- Úkol je nejmenší jednotka práce, jinými slovy, "atom" sestavení. Úkoly jsou nezávislé spustitelné součásti, které mohou mít vstupy a výstupy. V souboru projektu nejsou aktuálně odkazovány nebo definovány žádné úkoly. Úkoly přidáte do souboru projektu v následujících částech. Další informace naleznete v tématu [Úkoly.](../msbuild/msbuild-tasks.md)

- Cíl je pojmenovaná posloupnost úkolů. Další informace naleznete v tématu [Cíle.](../msbuild/msbuild-targets.md)

Výchozí cíl není v souboru projektu definován. Místo toho je zadán v importovaných projektech. Prvek [Import](../msbuild/import-element-msbuild.md) určuje importované projekty. Například v projektu Jazyka C# je výchozí cíl importován ze souboru *Microsoft.CSharp.targets*.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

Importované soubory jsou efektivně vloženy do souboru projektu všude tam, kde jsou odkazovány.

> [!NOTE]
> Některé typy projektů, například .NET Core, používají zjednodušené schéma s atributem `Sdk` namísto `ToolsVersion`. Tyto projekty mají implicitní importy a různé výchozí hodnoty atributů.

MSBuild udržuje přehled o cílesestavení a zaručuje, že každý cíl je sestaven ne více než jednou.

## <a name="add-a-target-and-a-task"></a>Přidání cíle a úkolu

 Přidejte cíl do souboru projektu. Přidejte úkol k cíli, který vytiskne zprávu.

**Přidání cíle a úkolu**

1. Přidejte tyto řádky do souboru projektu hned za příkazimportem:

    ```xml
    <Target Name="HelloWorld">
    </Target>
    ```

     Tím se vytvoří cíl s názvem HelloWorld. Všimněte si, že máte podporu Technologie IntelliSense při úpravách souboru projektu.

2. Přidejte řádky do cíle HelloWorld, aby výsledný oddíl vypadal takto:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Hello"></Message>  <Message Text="World"></Message>
    </Target>
    ```

3. Uložte soubor projektu.

Message úkol je jedním z mnoha úkolů, které jsou dodávány s MSBuild. Úplný seznam dostupných úkolů a informace o použití naleznete v [tématu Odkaz na úkol](../msbuild/msbuild-task-reference.md).

Zpráva úloha bere hodnotu řetězce Text atribut jako vstup a zobrazí jej na výstupním zařízení. HelloWorld cíl provede message úlohu dvakrát: nejprve zobrazit "Hello", a pak zobrazit "World".

## <a name="build-the-target"></a>Sestavení cíle

 Spusťte MSBuild z **příkazového řádku pro vývojáře** pro Visual Studio k vytvoření výše definovaného cíle HelloWorld. Pomocí přepínače příkazového řádku -target nebo -t vyberte cíl.

> [!NOTE]
> **Příkazový řádek pro vývojáře** budeme označovat jako **příkazové okno** v následujících částech.

**Chcete-li vytvořit cíl**

1. Otevřete **příkazové okno**.

   (Windows 10) Do vyhledávacího pole na hlavním panelu začněte psát název `dev` `developer command prompt`nástroje, například nebo . Tím se zobrazí seznam nainstalovaných aplikací, které odpovídají vašemu vyhledávacímu vzoru.

   Pokud jej potřebujete najít ručně, soubor je *LaunchDevCmd.bat* ve *verzi\>\<instalační složky<visualstudio>\Common7\Tools.*

2. Z příkazového okna přejděte do složky obsahující soubor projektu, v tomto případě *D:\BuildApp\BuildApp*.

3. Spusťte msbuild s přepínačem příkazu -t:HelloWorld. Tím vyberete a sestavíte cíl HelloWorld:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Zkontrolujte výstup v **okně Příkaz**. Měli byste vidět dva řádky "Hello" a "World":

    ```
    Hello
    World
    ```

> [!NOTE]
> Pokud místo `The target "HelloWorld" does not exist in the project` toho vidíte, pak jste pravděpodobně zapomněli uložit soubor projektu v editoru kódu. Uložte soubor a akci opakujte.

 Střídáním mezi editorem kódu a příkazovým oknem můžete změnit soubor projektu a rychle zobrazit výsledky.

## <a name="build-properties"></a>Vlastnosti sestavení

 Vlastnosti sestavení jsou dvojice název-hodnota, které řídí sestavení. V horní části souboru projektu je již definováno několik vlastností sestavení:

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

 Všechny vlastnosti jsou podřízené prvky PropertyGroup prvky. Název vlastnosti je název podřízeného prvku a hodnota vlastnosti je textový majeřský prvek. Například:

```xml
<TargetFrameworkVersion>v15.0</TargetFrameworkVersion>
```

 definuje vlastnost s názvem TargetFrameworkVersion, která mu dává hodnotu řetězce "v15.0".

 Vlastnosti sestavení mohou být kdykoli předefinovány. Pokud uživatel

```xml
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
```

 se zobrazí později v souboru projektu nebo v souboru importovaném později v souboru projektu, pak TargetFrameworkVersion převezme novou hodnotu "v3.5".

## <a name="examine-a-property-value"></a>Zkontrolujte hodnotu vlastnosti

 Chcete-li získat hodnotu vlastnosti, použijte následující syntaxi, kde PropertyName je název vlastnosti:

```xml
$(PropertyName)
```

 Tato syntaxe slouží ke kontrole některých vlastností v souboru projektu.

**Chcete-li zkontrolovat hodnotu vlastnosti**

1. Z editoru kódu nahraďte cíl HelloWorld tímto kódem:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Configuration is $(Configuration)" />
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />
    </Target>
    ```

2. Uložte soubor projektu.

3. Z **příkazového okna**zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Zkontrolujte výstup příkazu. Měli byste vidět tyto dva řádky (vaše verze rozhraní .NET Framework se může lišit):

    ::: moniker range=">=vs-2019"

    ```
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2019\<Visual Studio SKU>\MSBuild\15.0\Bin
    ```

    ::: moniker-end
    ::: moniker range="vs-2017"

    ```
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2017\<Visual Studio SKU>\MSBuild\15.0\Bin
    ```

    ::: moniker-end

> [!NOTE]
> Pokud tyto řádky nevidíte, pravděpodobně jste zapomněli uložit soubor projektu v editoru kódu. Uložte soubor a akci opakujte.

### <a name="conditional-properties"></a>Podmíněné vlastnosti

 Mnoho vlastností, jako je konfigurace jsou definovány podmíněně, to znamená, že Condition atribut se zobrazí v elementu vlastnosti. Podmíněné vlastnosti jsou definovány nebo předefinovány pouze v případě, že podmínka vyhodnotí na "true". Všimněte si, že nedefinované vlastnosti jsou uvedeny výchozí hodnotu prázdného řetězce. Například:

```xml
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 znamená "Pokud vlastnost Configuration ještě nebyla definována, definujte ji a přidejte jí hodnotu "Ladění".

 Téměř všechny prvky MSBuild mohou mít atribut Condition. Další diskuse o použití atributu Podmínka naleznete v tématu [Podmínky](../msbuild/msbuild-conditions.md).

### <a name="reserved-properties"></a>Rezervované vlastnosti

 MSBuild rezervuje některé názvy vlastností pro ukládání informací o souboru projektu a binárních souborech MSBuild. MSBuildToolsPath je příkladem vyhrazené vlastnosti. Vyhrazené vlastnosti jsou odkazovány zápisem $ jako jakákoli jiná vlastnost. Další informace naleznete v [tématu Postup: Odkaz na název nebo umístění souboru projektu](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) a [MSBuild vyhrazené a dobře známé vlastnosti](../msbuild/msbuild-reserved-and-well-known-properties.md).

### <a name="environment-variables"></a>Proměnné prostředí

 Proměnné prostředí v souborech projektu můžete odkazovat stejným způsobem jako vlastnosti sestavení. Chcete-li například použít proměnnou prostředí PATH v souboru projektu, použijte $(Path). Pokud projekt obsahuje definici vlastnosti, která má stejný název jako proměnná prostředí, vlastnost v projektu přepíše hodnotu proměnné prostředí. Další informace naleznete v [tématu How to: Use environment variables in a build](../msbuild/how-to-use-environment-variables-in-a-build.md).

## <a name="set-properties-from-the-command-line"></a>Nastavení vlastností z příkazového řádku

 Vlastnosti mohou být definovány na příkazovém řádku pomocí přepínače příkazového řádku -property nebo -p. Hodnoty vlastností přijaté z příkazového řádku přepíší hodnoty vlastností nastavené v souboru projektu a proměnných prostředí.

**Nastavení hodnoty vlastnosti z příkazového řádku**

1. Z **příkazového okna**zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld -p:Configuration=Release
    ```

2. Zkontrolujte výstup příkazu. Měli byste vidět tento řádek:

    ```
    Configuration is Release.
    ```

MSBuild vytvoří Vlastnost Configuration a dává mu hodnotu "Release".

## <a name="special-characters"></a>Speciální znaky

 Některé znaky mají zvláštní význam v souborech projektu MSBuild. Příklady těchto znaků patří středníky (;) a hvězdičky (*). Chcete-li použít tyto speciální znaky jako literály v souboru projektu,\<musí být \<zadány pomocí syntaxe % xx>, kde xx> představuje šestnáctkovou hodnotu znaku ASCII.

 Změňte úkol Zpráva tak, aby zobrazovala hodnotu vlastnosti Configuration se speciálními znaky, aby byla čitelnější.

**Použití speciálních znaků v úkolu Zpráva**

1. V editoru kódu nahraďte obě úlohy zprávy tímto řádkem:

    ```xml
    <Message Text="%24(Configuration) is %22$(Configuration)%22" />
    ```

2. Uložte soubor projektu.

3. Z **příkazového okna**zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Zkontrolujte výstup příkazu. Měli byste vidět tento řádek:

    ```
    $(Configuration) is "Debug"
    ```

Další informace naleznete v tématu [MSBuild speciální znaky](../msbuild/msbuild-special-characters.md).

## <a name="build-items"></a>Vytváření položek

 Položka je informace, obvykle název souboru, který se používá jako vstup do systému sestavení. Například kolekce položek představujících zdrojové soubory může být předána úloze s názvem Kompilace, aby byly zkompilovány do sestavení.

 Všechny položky jsou podřízené prvky ItemGroup prvky. Název položky je název podřízeného prvku a hodnota položky je hodnota atributu Include podřízeného prvku. Hodnoty položek se stejným názvem jsou shromažďovány do typů položek tohoto názvu.  Například:

```xml
<ItemGroup>
    <Compile Include="Program.cs" />
    <Compile Include="Properties\AssemblyInfo.cs" />
</ItemGroup>
```

 definuje skupinu položek obsahující dvě položky. Typ položky Kompilace má dvě hodnoty: *Program.cs* a *Properties\AssemblyInfo.cs*.

 Následující kód vytvoří stejný typ položky deklarováním obou souborů v jednom atributu Include, odděleného středníkem.

```xml
<ItemGroup>
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />
</ItemGroup>
```

Další informace naleznete v [tématu Items](../msbuild/msbuild-items.md).

> [!NOTE]
> Cesty k souborům jsou relativní vzhledem ke složce obsahující soubor projektu MSBuild.

## <a name="examine-item-type-values"></a>Zkontrolovat hodnoty typu položky

 Chcete-li získat hodnoty typu položky, použijte následující syntaxi, kde ItemType je název typu položky:

```xml
@(ItemType)
```

 Tato syntaxe slouží ke kontrole typu položky Kompilace v souboru projektu.

**Zkontrolujte hodnoty typu položky**

1. Z editoru kódu nahraďte cílovou úlohu HelloWorld tímto kódem:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Compile item type contains @(Compile)" />
    </Target>
    ```

2. Uložte soubor projektu.

3. Z **příkazového okna**zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Zkontrolujte výstup příkazu. Měli byste vidět tuto dlouhou čáru:

    ```
    Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
    ```

Hodnoty typu položky jsou ve výchozím nastavení odděleny středníky.

Chcete-li změnit oddělovač typu položky, použijte následující syntaxi, kde ItemType je typ položky a Oddělovač je řetězec jednoho nebo více oddělujících znaků:

```xml
@(ItemType, Separator)
```

Změňte úkol Zpráva tak, aby se funkce konce řádků a řádkové kanály (%0A%0D) zobrazovala pro kompilaci položek jedna na řádek.

**Zobrazení hodnot typu položky 1 na řádek**

1. V editoru kódu nahraďte úlohu Zpráva tímto řádkem:

    ```xml
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />
    ```

2. Uložte soubor projektu.

3. Z **příkazového okna**zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Zkontrolujte výstup příkazu. Měli byste vidět tyto řádky:

    ```
    Compile item type contains Form1.cs
    Form1.Designer.cs
    Program.cs
    Properties\AssemblyInfo.cs
    Properties\Resources.Designer.cs
    Properties\Settings.Designer.cs
    ```

### <a name="include-exclude-and-wildcards"></a>Zahrnout, vyloučit a zástupné znaky

 Pomocí zástupných znaků "*",\*\*" "a "?" s atributem Zahrnout můžete přidat položky do typu položky. Například:

```xml
<Photos Include="images\*.jpeg" />
```

 přidá všechny soubory s příponou *.jpeg* ve složce *Obrázky* do typu položky Fotografie, zatímco

```xml
<Photos Include="images\**\*.jpeg" />
```

 přidá všechny soubory s příponou *.jpeg* souboru ve složce *obrazy* a všechny její podsložky do typu položky Fotografie. Další příklady najdete v [tématu Postup: Vyberte soubory, které chcete vytvořit](../msbuild/how-to-select-the-files-to-build.md).

 Všimněte si, že jako položky jsou deklarovány jsou přidány do typu položky. Například:

```xml
<Photos Include="images\*.jpeg" />
<Photos Include="images\*.gif" />
```

 vytvoří typ položky s názvem Fotografie obsahující všechny soubory ve složce *obrázky* s příponou *souboru .jpeg* nebo *.gif*. To odpovídá následujícímu řádku:

```xml
<Photos Include="images\*.jpeg;images\*.gif" />
```

 Položku můžete vyloučit z typu položky pomocí atributu Vyloučit. Například:

```xml
<Compile Include="*.cs" Exclude="*Designer*">
```

 Přidá všechny soubory s příponou *.cs* do typu kompilace položky, s výjimkou souborů, jejichž názvy obsahují *návrhář estrukce*. Další příklady najdete [v tématu Postup: Vyloučení souborů ze sestavení](../msbuild/how-to-exclude-files-from-the-build.md).

Atribut Exclude ovlivňuje pouze položky přidané atributem Include v elementu položky, který je obsahuje oba. Například:

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

nevyloučila by soubor *Form1.cs*, který byl přidán do předchozího prvku položky.

**Zahrnutí a vyloučení položek**

1. V editoru kódu nahraďte úlohu Zpráva tímto řádkem:

    ```xml
    <Message Text="XFiles item type contains @(XFiles)" />
    ```

2. Přidejte tuto skupinu položek hned za prvek Import:

    ```xml
    <ItemGroup>
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />
    </ItemGroup>
    ```

3. Uložte soubor projektu.

4. Z **příkazového okna**zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

5. Zkontrolujte výstup příkazu. Měli byste vidět tento řádek:

    ```
    XFiles item type contains Form1.cs;Program.cs;Properties/Resources.resx
    ```

## <a name="item-metadata"></a>Metadata položky

 Položky mohou obsahovat metadata kromě informací shromážděných z zahrnout a vyloučit atributy. Tato metadata mohou být použita úkoly, které vyžadují více informací o položkách než pouze hodnotu položky.

 Metadata položky je deklarována v souboru projektu vytvořením prvku s názvem metadat jako podřízený prvek položky. Položka může mít nulové nebo více hodnot metadat. Například následující položka CSFile má metadata jazykové verze s hodnotou "Fr":

```xml
<ItemGroup>
    <CSFile Include="main.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Chcete-li získat hodnotu metadat typu položky, použijte následující syntaxi, kde ItemType je název typu položky a MetaDataName je název metadat:

```xml
%(ItemType.MetaDataName)
```

**Chcete-li zkontrolovat metadata položky**

1. V editoru kódu nahraďte úlohu Zpráva tímto řádkem:

    ```xml
    <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />
    ```

2. Uložte soubor projektu.

3. Z **příkazového okna**zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Zkontrolujte výstup příkazu. Měli byste vidět tyto řádky:

    ```
    Compile.DependentUpon:
    Compile.DependentUpon: Form1.cs
    Compile.DependentUpon: Resources.resx
    Compile.DependentUpon: Settings.settings
    ```

Všimněte si, jak se fráze "Compile.DependentUpon" zobrazí několikrát. Použití metadat s touto syntaxí v rámci cíle způsobí "dávkování". Dávkování znamená, že úkoly v rámci cíle jsou provedeny jednou pro každou jedinečnou hodnotu metadat. Toto je ekvivalent skriptu MSBuild společného programovacího konstruktu "for loop". Další informace naleznete v [tématu Batching](../msbuild/msbuild-batching.md).

### <a name="well-known-metadata"></a>Známá metadata

 Při každém přidání položky do seznamu položek je této položce přiřazena některá známá metadata. Například %(Název_souboru) vrátí název souboru libovolné položky. Úplný seznam známých metadat naleznete v [tématu Známá metadata položek](../msbuild/msbuild-well-known-item-metadata.md).

**Chcete-li prozkoumat známá metadata**

1. V editoru kódu nahraďte úlohu Zpráva tímto řádkem:

    ```xml
    <Message Text="Compile Filename: %(Compile.Filename)" />
    ```

2. Uložte soubor projektu.

3. Z **příkazového okna**zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Zkontrolujte výstup příkazu. Měli byste vidět tyto řádky:

    ```
    Compile Filename: Form1
    Compile Filename: Form1.Designer
    Compile Filename: Program
    Compile Filename: AssemblyInfo
    Compile Filename: Resources.Designer
    Compile Filename: Settings.Designer
    ```

Porovnáním dvou výše uvedených příkladů můžete vidět, že zatímco ne každá položka v typu kompilace má metadata DependentUpon, všechny položky mají dobře známá metadata filename.

### <a name="metadata-transformations"></a>Transformace metadat

 Seznamy položek lze transformovat do nových seznamů položek. Chcete-li transformovat seznam položek, použijte \<následující syntaxi, kde Název \<položky> Je název typu položky a Název metadat> je název metadat:

```xml
@(ItemType -> '%(MetadataName)')
```

Například seznam položek zdrojových souborů lze transformovat do kolekce souborů objektů `@(SourceFiles -> '%(Filename).obj')`pomocí výrazu jako . Další informace naleznete v [tématu Transformace](../msbuild/msbuild-transforms.md).

**Transformace položek pomocí metadat**

1. V editoru kódu nahraďte úlohu Zpráva tímto řádkem:

    ```xml
    <Message Text="Backup files: @(Compile->'%(filename).bak')" />
    ```

2. Uložte soubor projektu.

3. Z **příkazového okna**zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Zkontrolujte výstup příkazu. Měli byste vidět tento řádek:

    ```
    Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak
    ```

Všimněte si, že metadata vyjádřená v této syntaxi nezpůsobí dávkování.

## <a name="whats-next"></a>Co dále?

 Chcete-li se dozvědět, jak vytvořit jednoduchý soubor projektu jeden krok po kroku, vyzkoušejte [návod: Vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

## <a name="see-also"></a>Viz také

- [MSBuild – přehled](../msbuild/msbuild.md)
- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)

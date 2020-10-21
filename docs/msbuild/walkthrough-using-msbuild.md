---
title: Použití nástroje MSBuild
description: Seznamte se s různými částmi souboru projektu MSBuild, včetně položek, metadat položek, vlastností, cílů a úkolů.
ms.date: 10/19/2020
ms.topic: conceptual
ms.custom: contperfq2
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b26c13765daf5a82a9961e6509b36e24e18f4e0c
ms.sourcegitcommit: 6b62e09026b6f1446187c905b789645f967a371c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2020
ms.locfileid: "92298526"
---
# <a name="walkthrough-use-msbuild"></a>Návod: použití nástroje MSBuild

MSBuild je platforma sestavení pro Microsoft a Visual Studio. Tento návod vás seznámí se stavebními bloky nástroje MSBuild a ukazuje, jak psát, manipulovat a ladit projekty MSBuild. Naučíte se:

- Vytvoření a manipulace se souborem projektu.

- Jak používat vlastnosti sestavení

- Jak používat položky sestavení.

Nástroj MSBuild můžete spustit ze sady Visual Studio nebo z **příkazového okna**. V tomto návodu vytvoříte soubor projektu MSBuild pomocí sady Visual Studio. Soubor projektu upravíte v aplikaci Visual Studio a pomocí **okna příkazového** řádku Sestavte projekt a prověřte výsledky.

## <a name="install-msbuild"></a>Instalace nástroje MSBuild

::: moniker range="vs-2017"

Pokud máte aplikaci Visual Studio, pak již máte nainstalován nástroj MSBuild. Chcete-li nainstalovat nástroj MSBuild 15 do systému, který nemá aplikaci Visual Studio, klikněte na možnost [Visual Studio starší soubory ke stažení](https://visualstudio.microsoft.com/vs/older-downloads/), rozbalte položku **Visual Studio 2017** a klikněte na tlačítko **Stáhnout** . Máte-li předplatné sady Visual Studio, přihlaste se a vyhledejte odkaz pro stažení nejnovější verze **nástrojů Build Tools pro sadu Visual studio 2017**. Pokud nemáte předplatné sady Visual Studio, můžete přesto nainstalovat nejnovější verzi nástrojů pro sestavení. Na této stránce se pomocí selektoru verzí přepněte na stránku verze 2019 a postupujte podle pokynů k instalaci.
::: moniker-end

::: moniker range="vs-2019"
Pokud máte aplikaci Visual Studio, pak již máte nainstalován nástroj MSBuild. Se sadou Visual Studio 2019 se instaluje do instalační složky sady Visual Studio. Pro typickou výchozí instalaci ve Windows 10 se MSBuild.exe nachází pod instalační složkou v *MSBuild\Current\Bin*.

Pokud chcete nástroj MSBuild nainstalovat do systému, který nemá Visual Studio, přejděte do sady [Visual Studio ke stažení](https://visualstudio.microsoft.com/downloads/) a přejděte dolů ke **všem souborům ke stažení**a pak rozbalte **Nástroje pro Visual Studio 2019**. Nainstalujte **Nástroje sestavení pro Visual Studio 2019**, které obsahují MSBuild, nebo nainstalujte [.NET Core SDK](/dotnet/core/sdk#acquiring-the-net-core-sdk).

V instalačním programu se ujistěte, že jsou vybrané nástroje MSBuild pro používané úlohy, a klikněte na **nainstalovat**.

![Instalace nástroje MSBuild](media/walkthrough-using-msbuild/installation-msbuild-tools.png)

::: moniker-end

## <a name="create-an-msbuild-project"></a>Vytvoření projektu MSBuild

 Systém projektu sady Visual Studio je založen na nástroji MSBuild. Díky tomu je snadné vytvořit nový soubor projektu pomocí sady Visual Studio. V této části vytvoříte soubor projektu Visual C#. Místo toho se můžete rozhodnout pro vytvoření souboru projektu Visual Basic. V kontextu tohoto návodu je rozdíl mezi dvěma soubory projektu nepatrný.

**Vytvoření souboru projektu**

1. Otevřete Visual Studio a vytvořte projekt.

    ::: moniker range=">=vs-2019"
    Stisknutím klávesy **ESC** zavřete okno Start. Zadáním **CTRL + Q** otevřete vyhledávací pole, zadejte **WinForms**a pak zvolte **vytvořit novou aplikaci model Windows Forms (.NET Framework)**. V dialogovém okně, které se zobrazí, vyberte **vytvořit**.

    Do pole **Název** zadejte `BuildApp`. Zadejte **umístění** pro řešení, například *D: \\ *. Přijměte výchozí hodnoty pro **řešení**, **název řešení** (**BuildApp**) a **rozhraní**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek vyberte **soubor**  >  **Nový**  >  **projekt**. V levém podokně dialogového okna **Nový projekt** rozbalte položku **Visual C#**  >  **Desktop Windows**a pak zvolte možnost **model Windows Forms aplikace (.NET Framework)**. Pak zvolte **OK**.

    Do pole **Název** zadejte `BuildApp`. Zadejte **umístění** pro řešení, například *D: \\ *. Přijměte výchozí hodnoty pro možnost **vytvořit adresář pro řešení** (vybráno), **Přidat do správy zdrojového kódu** (Nevybráno) a **název řešení** (**BuildApp**).
    ::: moniker-end

1. Kliknutím na tlačítko **OK** nebo **vytvořit** vytvořte soubor projektu.

## <a name="examine-the-project-file"></a>Kontrola souboru projektu

 V předchozí části jste použili aplikaci Visual Studio k vytvoření souboru projektu Visual C#. Soubor projektu je reprezentován v **Průzkumník řešení** uzlu projektu s názvem BuildApp. K prohlédnutí souboru projektu lze použít Editor kódu sady Visual Studio.

**Kontrola souboru projektu**

1. V **Průzkumník řešení**klikněte na uzel projektu **BuildApp**.

1. V prohlížeči **vlastností** si všimněte, že vlastnost **soubor projektu** je *BuildApp. csproj*. Všechny soubory projektu jsou pojmenovány s příponou *proj*. Pokud jste vytvořili Visual Basic projekt, název souboru projektu by byl *BuildApp. vbproj*.

1. Znovu klikněte pravým tlačítkem na uzel projektu a pak klikněte na **Upravit BuildApp. csproj**. 

     Soubor projektu se zobrazí v editoru kódu.

>[!NOTE]
> U některých typů projektů, jako je například C++, je nutné uvolnit projekt (kliknutím pravým tlačítkem myši na soubor projektu a výběrem možnosti **Uvolnit projekt**) předtím, než budete moci otevřít a upravit soubor projektu.

## <a name="targets-and-tasks"></a>Cíle a úkoly

Soubory projektu jsou soubory ve formátu XML s kořenovým uzlem [projektu](../msbuild/project-element-msbuild.md).

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Novější projekty .NET Core (sady SDK) mají `Sdk` atribut.

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

Pokud projekt není projekt ve stylu sady SDK, je nutné zadat obor názvů xmlns v elementu projektu. Pokud `ToolsVersion` se nachází v novém projektu, musí být "15,0".

Práce při sestavování aplikace se provádí s [cíli](../msbuild/target-element-msbuild.md) a prvky [úkolu](../msbuild/task-element-msbuild.md) .

- Úkol je nejmenší pracovní jednotka, jinými slovy "Atom" buildu. Úlohy jsou nezávislé spustitelné komponenty, které mohou mít vstupy a výstupy. V souboru projektu nejsou momentálně odkazovány nebo definovány žádné úlohy. Do souboru projektu přidáte úkoly v níže uvedených částech. Další informace najdete v tématu [úlohy](../msbuild/msbuild-tasks.md) .

- Cíl je pojmenované pořadí úkolů. Další informace najdete v tématu [cíle](../msbuild/msbuild-targets.md) .
- [může se jednat o pojmenovanou sekvenci úkolů, ale kriticky znamená, že má být sestavena nebo dokončena, takže by měla být definována v cíli orientovaném na cíle]

V souboru projektu není definován výchozí cíl. Místo toho je zadáno v importovaných projektech. [Import](../msbuild/import-element-msbuild.md) element určuje importované projekty. Například v projektu C# je výchozí cíl importován ze souboru *Microsoft. CSharp.* TARGETS.

```xml
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
```

Importované soubory jsou efektivně vloženy do souboru projektu kdekoli, kde jsou odkazovány.

V projektech se stylem sady SDK se tento prvek importu nezobrazuje, protože atribut sady SDK způsobí, že se tento soubor importuje implicitně.

Nástroj MSBuild sleduje cíle sestavení a zaručuje, že každý cíl je sestaven více než jednou.

## <a name="add-a-target-and-a-task"></a>Přidání cíle a úkolu

 Přidejte cíl do souboru projektu. Přidejte úkol do cíle, který vytiskne zprávu.

**Přidání cíle a úkolu**

1. Přidejte tyto řádky do souboru projektu hned za příkaz import:

    ```xml
    <Target Name="HelloWorld">
    </Target>
    ```

    Tím se vytvoří cíl s názvem HelloWorld. Všimněte si, že při úpravách souboru projektu máte podporu technologie IntelliSense.

2. Přidejte řádky do cíle HelloWorld, aby výsledný oddíl vypadal takto:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Hello"></Message>  <Message Text="World"></Message>
    </Target>
    ```

3. Uložte soubor projektu.

Úloha zprávy je jednou z mnoha úloh, které jsou dodávány s nástrojem MSBuild. Úplný seznam dostupných úloh a informací o využití najdete v tématu s [odkazem na úlohu](../msbuild/msbuild-task-reference.md).

Úloha zprávy převezme řetězcovou hodnotu atributu text jako vstup a zobrazí ji na výstupním zařízení (případně ji zapíše do jednoho nebo více protokolů, pokud je k dispozici). Cíl HelloWorld spustí úlohu zprávy dvakrát: nejprve zobrazí text "Hello" a potom zobrazí "World".

## <a name="build-the-target"></a>Sestavení cíle

Pokud se pokusíte sestavit tento projekt ze sady Visual Studio, nebude sestaven cíl, který jste definovali. To je proto, že Visual Studio zvolí výchozí cíl, což je stále ten v importovaném souboru *. targets* .

Spusťte MSBuild z **Developer Command Prompt** pro Visual Studio k sestavení cíle HelloWorld, který je definován výše. K výběru cíle použijte přepínač příkazového řádku-target nebo-t.

> [!NOTE]
> V níže uvedených částech budeme označovat **Developer Command Prompt** jako **příkazové okno** .

**Sestavení cíle:**

1. Otevřete **okno příkazového**řádku.

   (Windows 10) Do vyhledávacího pole na hlavním panelu začněte psát název nástroje, například `dev` nebo `developer command prompt` . Tím se zobrazí seznam nainstalovaných aplikací, které odpovídají vašemu vzoru hledání.

   Pokud ho potřebujete najít ručně, soubor se *LaunchDevCmd.bat* ve složce *<\> \<version> \Common7\Tools instalační složky* nástroje Visual Studio.

2. Z příkazového okna přejděte do složky, která obsahuje soubor projektu, v tomto případě *D:\BuildApp\BuildApp*.

3. Spusťte MSBuild s přepínačem příkazového řádku `-t:HelloWorld` . Tím se vybere a sestaví se cíl HelloWorld:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Projděte si výstup ve **okno příkaz**. Měli byste vidět dva řádky "Hello" a "World":

    ```output
    Hello
    World
    ```

> [!NOTE]
> Pokud místo toho vidíte, `The target "HelloWorld" does not exist in the project` pravděpodobně jste zapomněli uložit soubor projektu v editoru kódu. Uložte soubor a zkuste to znovu.

 Pomocí střídání mezi editorem kódu a oknem příkazového řádku můžete změnit soubor projektu a rychle zobrazit výsledky.

## <a name="build-properties"></a>Vlastnosti sestavení

 Vlastnosti buildu jsou páry název-hodnota, které provedou sestavení. V horní části souboru projektu jsou již definovány některé vlastnosti buildu:

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

 Všechny vlastnosti jsou podřízené prvky prvků vlastností. Název vlastnosti je název podřízeného prvku a hodnota vlastnosti je textový prvek podřízeného prvku. Příklad:

```xml
<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>
```

 definuje vlastnost s názvem TargetFrameworkVersion, která dává hodnotu řetězce "v 4.5".

 Vlastnosti sestavení lze kdykoli znovu definovat. Pokud uživatel

```xml
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
```

 se zobrazí později v souboru projektu nebo v souboru importovaném později v souboru projektu, TargetFrameworkVersion převezme novou hodnotu "v 3.5".

## <a name="examine-a-property-value"></a>Prověření hodnoty vlastnosti

 Chcete-li získat hodnotu vlastnosti, použijte následující syntaxi, kde `PropertyName` je název vlastnosti:

```xml
$(PropertyName)
```

Tuto syntaxi použijte k prohlédnutí některých vlastností v souboru projektu.

**Prověření hodnoty vlastnosti**

1. V editoru kódu nahraďte cíl HelloWorld tímto kódem:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Configuration is $(Configuration)" />
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />
    </Target>
    ```

1. Uložte soubor projektu.

1. V **příkazovém okně**zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Prohlédněte si výstup. Tyto dva řádky by se měly zobrazit (vaše verze .NET Framework se může lišit):

    ::: moniker range=">=vs-2019"

    ```output
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2019\<Visual Studio SKU>\MSBuild\15.0\Bin
    ```

    ::: moniker-end
    ::: moniker range="vs-2017"

    ```output
    Configuration is Debug
    MSBuildToolsPath is C:\Program Files (x86)\Microsoft Visual Studio\2017\<Visual Studio SKU>\MSBuild\15.0\Bin
    ```

    ::: moniker-end

### <a name="conditional-properties"></a>Podmíněné vlastnosti

Mnoho vlastností, jako `Configuration` jsou definovány, je podmíněně definováno, to znamená, že se `Condition` atribut zobrazí v elementu Property. Podmíněné vlastnosti jsou definovány nebo předefinovány pouze v případě, že je podmínka vyhodnocena jako "true". Všimněte si, že nedefinované vlastnosti jsou předány výchozí hodnotě prázdného řetězce. Příklad:

```xml
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

znamená, že pokud vlastnost Configuration ještě není definovaná, definujte ji a sdělte jí hodnotu ' ladit '.

Téměř všechny prvky MSBuild můžou mít atribut Condition. Další diskuzi o použití atributu Condition najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).

### <a name="reserved-properties"></a>Rezervované vlastnosti

Nástroj MSBuild si vyhrazuje některé názvy vlastností pro ukládání informací o souboru projektu a binárních souborech nástroje MSBuild. MSBuildToolsPath je příkladem rezervované vlastnosti. Na vyhrazené vlastnosti se odkazuje $ Notation, jako jakákoli jiná vlastnost. Další informace najdete v tématu [Postup: odkazování na název nebo umístění souboru projektu](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) a [rezervované a dobře známé vlastnosti nástroje MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).

### <a name="environment-variables"></a>Proměnné prostředí

Můžete odkazovat na proměnné prostředí v souborech projektu stejným způsobem jako vlastnosti sestavení. Chcete-li například použít proměnnou prostředí PATH v souboru projektu, použijte $ (cesta). Pokud projekt obsahuje definici vlastnosti, která má stejný název jako proměnná prostředí, vlastnost v projektu přepíše hodnotu proměnné prostředí. Další informace najdete v tématu [Postupy: použití proměnných prostředí v sestavení](../msbuild/how-to-use-environment-variables-in-a-build.md).

## <a name="set-properties-from-the-command-line"></a>Nastavení vlastností z příkazového řádku

Vlastnosti mohou být definovány v příkazovém řádku pomocí přepínače-Property nebo-p na příkazovém řádku. Hodnoty vlastností obdržené z příkazového řádku přepisují hodnoty vlastností nastavené v souboru projektu a proměnných prostředí.

**Nastavení hodnoty vlastnosti z příkazového řádku:**

1. V **příkazovém okně**zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld -p:Configuration=Release
    ```

1. Prohlédněte si výstup. Měl by se zobrazit tento řádek:

    ```output
    Configuration is Release.
    ```

Nástroj MSBuild vytvoří vlastnost konfigurace a poskytne jí hodnotu "Release".

## <a name="special-characters"></a>Speciální znaky

Některé znaky mají v souborech projektu MSBuild zvláštní význam. Mezi příklady těchto znaků patří středník (;) a hvězdičky (*). Aby bylo možné použít tyto speciální znaky jako literály v souboru projektu, musí být určeny pomocí syntaxe% \<xx> , kde \<xx> představuje šestnáctkovou hodnotu ASCII znaku.

Změnou úlohy zprávy zobrazíte hodnotu vlastnosti konfigurace se speciálními znaky, aby byly čitelnější.

**Použití speciálních znaků v úloze zprávy:**

1. V editoru kódu nahraďte obě úlohy zprávy tímto řádkem:

    ```xml
    <Message Text="%24(Configuration) is %22$(Configuration)%22" />
    ```

1. Uložte soubor projektu.

1. V **příkazovém okně**zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Prohlédněte si výstup. Měl by se zobrazit tento řádek:

    ```output
    $(Configuration) is "Debug"
    ```

Další informace najdete v tématu [speciální znaky nástroje MSBuild](../msbuild/msbuild-special-characters.md).

## <a name="build-items"></a>Položky sestavení

Položka je část informací, obvykle název souboru, která se používá jako vstup do systému sestavení. Například kolekce položek, které představují zdrojové soubory, mohou být předány úloze s názvem Compile pro jejich zkompilování do sestavení.

Všechny položky jsou podřízené prvky prvků Item. Název položky je název podřízeného prvku a hodnota položky je hodnota atributu Include podřízeného prvku. Hodnoty položek se stejným názvem jsou shromažďovány do typů položek daného názvu.  Příklad:

```xml
<ItemGroup>
    <Compile Include="Program.cs" />
    <Compile Include="Properties\AssemblyInfo.cs" />
</ItemGroup>
```

definuje skupinu položek, která obsahuje dvě položky. Kompilace typu položky má dvě hodnoty: *program.cs* a *Properties\AssemblyInfo.cs*.

Následující kód vytvoří stejný typ položky deklarováním obou souborů v jednom vloženém atributu oddělené středníkem.

```xml
<ItemGroup>
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />
</ItemGroup>
```

Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).

> [!NOTE]
> Cesty k souborům jsou relativní vzhledem ke složce obsahující soubor projektu MSBuild, a to i v případě, že je soubor projektu importovaným souborem projektu. Existuje několik výjimek, například při použití elementů [Import](import-element-msbuild.md) a [UsingTask](usingtask-element-msbuild.md) .

## <a name="examine-item-type-values"></a>Prověření hodnot typu položky

 Chcete-li získat hodnoty typu položky, použijte následující syntaxi, kde ItemType je název typu položky:

```xml
@(ItemType)
```

Tuto syntaxi použijte k prohlédnutí typu položky kompilace v souboru projektu.

**Zjištění hodnot typu položky:**

1. V editoru kódu nahraďte cílovou úlohu Hello tímto kódem:

    ```xml
    <Target Name="HelloWorld">
      <Message Text="Compile item type contains @(Compile)" />
    </Target>
    ```

1. Uložte soubor projektu.

1. V **příkazovém okně**zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

1. Prohlédněte si výstup. Měla by se zobrazit tato dlouhá čára:

    ```
    Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
    ```

Hodnoty typu položky jsou ve výchozím nastavení oddělené středníkem.

Chcete-li změnit oddělovač typu položky, použijte následující syntaxi, kde ItemType je typ položky a oddělovač je řetězec jednoho nebo více oddělujících znaků:

```xml
@(ItemType, Separator)
```

Změňte úlohu zprávy na použití návratových znaků a kanálů řádků (% 0A% 0D) pro zobrazení položek kompilace po jednotlivých řádcích.

**Zobrazení hodnot typu položky na jednom řádku**

1. V editoru kódu nahraďte úlohu zprávy tímto řádkem:

    ```xml
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />
    ```

2. Uložte soubor projektu.

3. V **příkazovém okně**zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Prohlédněte si výstup. Měli byste vidět tyto řádky:

    ```
    Compile item type contains Form1.cs
    Form1.Designer.cs
    Program.cs
    Properties\AssemblyInfo.cs
    Properties\Resources.Designer.cs
    Properties\Settings.Designer.cs
    ```

### <a name="include-exclude-and-wildcards"></a>Zahrnutí, vyloučení a zástupné znaky

 K přidání položek do typu položky můžete použít zástupné znaky "*", " \* \* " a "?" s atributem include. Příklad:

```xml
<Photos Include="images\*.jpeg" />
```

 Přidá všechny soubory s příponou *. jpeg* ve složce *images* na typ položky fotky, zatímco

```xml
<Photos Include="images\**\*.jpeg" />
```

 Přidá všechny soubory s příponou *. jpeg* ve složce *images* a všech jejích podsložkách na typ položky fotky. Další příklady naleznete v tématu [Postupy: výběr souborů pro sestavení](../msbuild/how-to-select-the-files-to-build.md).

 Všimněte si, že když jsou deklarovány položky, jsou přidány do typu položky. Příklad:

```xml
<Photos Include="images\*.jpeg" />
<Photos Include="images\*.gif" />
```

 Vytvoří typ položky s názvem fotka obsahující všechny soubory ve složce *images* s příponou souboru *. jpeg* nebo *. gif*. To je ekvivalentní následujícímu řádku:

```xml
<Photos Include="images\*.jpeg;images\*.gif" />
```

 Můžete vyloučit položku z typu položky s atributem Exclude. Příklad:

```xml
<Compile Include="*.cs" Exclude="*Designer*">
```

 Přidá všechny soubory s příponou *. cs* na typ položky kompilace, s výjimkou souborů, jejichž názvy obsahují *Návrháře*řetězce. Další příklady naleznete v tématu [Postupy: vyloučení souborů ze sestavení](../msbuild/how-to-exclude-files-from-the-build.md).

Atribut Exclude ovlivňuje pouze položky přidané atributem include v prvku položky, který je obsahuje obě. Příklad:

```xml
<Compile Include="*.cs" />
<Compile Include="*.res" Exclude="Form1.cs">
```

nevylučuje soubor *Form1.cs*, který byl přidán do předchozí položky elementu.

**Zahrnutí a vyloučení položek**

1. V editoru kódu nahraďte úlohu zprávy tímto řádkem:

    ```xml
    <Message Text="XFiles item type contains @(XFiles)" />
    ```

2. Přidejte tuto skupinu položek hned za prvek importu:

    ```xml
    <ItemGroup>
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />
    </ItemGroup>
    ```

3. Uložte soubor projektu.

4. V **příkazovém okně**zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

5. Prohlédněte si výstup. Měl by se zobrazit tento řádek:

    ```
    XFiles item type contains Form1.cs;Program.cs;Properties/Resources.resx
    ```

## <a name="item-metadata"></a>Metadata položky

 Kromě informací shromážděných z atributů include a Exclude mohou položky obsahovat i metadata. Tato metadata mohou být použita úkoly, které vyžadují více informací o položkách než pouze hodnota položky.

 Metadata položky jsou deklarována v souboru projektu vytvořením prvku s názvem metadat jako podřízeným prvkem položky. Položka může mít nula nebo více hodnot metadat. Například následující položka CSFile má metadata jazykové verze s hodnotou "fr":

```xml
<ItemGroup>
    <CSFile Include="main.cs">
        <Culture>Fr</Culture>
    </CSFile>
</ItemGroup>
```

 Chcete-li získat hodnotu metadat typu položky, použijte následující syntaxi, kde typ ItemType je název položky a MetaData je název metadat:

```xml
%(ItemType.MetaDataName)
```

**Kontrola metadat položky:**

1. V editoru kódu nahraďte úlohu zprávy tímto řádkem:

    ```xml
    <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />
    ```

2. Uložte soubor projektu.

3. V **příkazovém okně**zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Prohlédněte si výstup. Měli byste vidět tyto řádky:

    ```output
    Compile.DependentUpon:
    Compile.DependentUpon: Form1.cs
    Compile.DependentUpon: Resources.resx
    Compile.DependentUpon: Settings.settings
    ```

Všimněte si, jak se fráze "zkompilovat. DependentUpon" zobrazuje několikrát. Použití metadat s touto syntaxí v rámci cíle způsobuje "dávkování". Dávkování znamená, že úkoly v rámci cíle se spustí jednou pro každou jedinečnou hodnotu metadat. Toto je ekvivalent skriptu MSBuild v rámci společné programovací konstrukce for Loop. Další informace najdete v tématu [dávkování](../msbuild/msbuild-batching.md).

### <a name="well-known-metadata"></a>Dobře známá metadata

 Pokaždé, když se do seznamu položek přidá nějaká položka, přiřadí se některá dobře známá metadata. Například% (filename) vrátí název souboru jakékoli položky. Úplný seznam známých metadat najdete v tématu [známá metadata položky](../msbuild/msbuild-well-known-item-metadata.md).

**Prověření dobře známých metadat:**

1. V editoru kódu nahraďte úlohu zprávy tímto řádkem:

    ```xml
    <Message Text="Compile Filename: %(Compile.Filename)" />
    ```

2. Uložte soubor projektu.

3. V **příkazovém okně**zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Prohlédněte si výstup. Měli byste vidět tyto řádky:

    ```output
    Compile Filename: Form1
    Compile Filename: Form1.Designer
    Compile Filename: Program
    Compile Filename: AssemblyInfo
    Compile Filename: Resources.Designer
    Compile Filename: Settings.Designer
    ```

Porovnáním dvou výše uvedených příkladů vidíte, že i když ne každá položka v typu položky kompilace má metadata DependentUpon, všechny položky mají dobře známá metadata filename.

### <a name="metadata-transformations"></a>Transformace metadat

 Seznamy položek lze transformovat na nové seznamy položek. Chcete-li transformovat seznam položek, použijte následující syntaxi, kde \<ItemType> je název typu položky a \<MetadataName> je název metadat:

```xml
@(ItemType -> '%(MetadataName)')
```

Například seznam položek zdrojových souborů lze transformovat na kolekci souborů objektů pomocí výrazu, jako je `@(SourceFiles -> '%(Filename).obj')` . Další informace najdete v tématu [transformace](../msbuild/msbuild-transforms.md).

**Transformace položek pomocí metadat:**

1. V editoru kódu nahraďte úlohu zprávy tímto řádkem:

    ```xml
    <Message Text="Backup files: @(Compile->'%(filename).bak')" />
    ```

2. Uložte soubor projektu.

3. V **příkazovém okně**zadejte a spusťte tento řádek:

    ```cmd
    msbuild buildapp.csproj -t:HelloWorld
    ```

4. Prohlédněte si výstup. Měl by se zobrazit tento řádek:

    ```output
    Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak
    ```

Všimněte si, že metadata vyjádřená v této syntaxi nezpůsobují dávkování.

## <a name="next-steps"></a>Další kroky

 Chcete-li zjistit, jak vytvořit jednoduchý soubor projektu v jednom kroku, postupujte podle [návodu: vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

## <a name="see-also"></a>Viz také

- [Přehled nástroje MSBuild](../msbuild/msbuild.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)

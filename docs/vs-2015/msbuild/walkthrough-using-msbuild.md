---
title: 'Návod: použití nástroje MSBuild | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b6e77934f8e565800eb4a7a753df4beb3b003fbb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64796887"
---
# <a name="walkthrough-using-msbuild"></a>Návod: Použití nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

MSBuild je platforma sestavení pro Microsoft a Visual Studio. Tento návod vás seznámí se stavebními bloky nástroje MSBuild a ukazuje, jak psát, manipulovat a ladit projekty MSBuild. Naučíte se:  
  
- Vytvoření a manipulace se souborem projektu.  
  
- Jak používat vlastnosti sestavení  
  
- Jak používat položky sestavení.  
  
  Nástroj MSBuild můžete spustit ze sady Visual Studio nebo z příkazového okna. V tomto návodu vytvoříte soubor projektu MSBuild pomocí sady Visual Studio. Soubor projektu upravíte v aplikaci Visual Studio a pomocí příkazového okna sestavíte projekt a provedete výsledky.  
  
## <a name="creating-an-msbuild-project"></a>Vytvoření projektu MSBuild  
 Systém projektu sady Visual Studio je založen na nástroji MSBuild. Díky tomu je snadné vytvořit nový soubor projektu pomocí sady Visual Studio. V této části vytvoříte soubor projektu Visual C#. Místo toho se můžete rozhodnout pro vytvoření souboru projektu Visual Basic. V kontextu tohoto návodu je rozdíl mezi dvěma soubory projektu nepatrný.  
  
#### <a name="to-create-a-project-file"></a>Vytvoření souboru projektu  
  
1. Otevřete sadu Visual Studio.  
  
2. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.  
  
3. V dialogovém okně **Nový projekt** vyberte typ projektu Visual C# a poté vyberte šablonu **aplikace model Windows Forms** . Do pole **Název** zadejte `BuildApp`. Zadejte **umístění** pro řešení, například `D:\` . Přijměte výchozí hodnoty pro možnost **vytvořit adresář pro řešení** (vybráno), **Přidat do správy zdrojového kódu** (Nevybráno) a **název řešení** ( `BuildApp` ).  
  
     Kliknutím na tlačítko **OK** vytvořte soubor projektu.  
  
## <a name="examining-the-project-file"></a>Prozkoumání souboru projektu  
 V předchozí části jste použili aplikaci Visual Studio k vytvoření souboru projektu Visual C#. Soubor projektu je reprezentován v **Průzkumník řešení** uzlu projektu s názvem BuildApp. K prohlédnutí souboru projektu lze použít Editor kódu sady Visual Studio.  
  
#### <a name="to-examine-the-project-file"></a>Kontrola souboru projektu  
  
1. V **Průzkumník řešení**klikněte na uzel projektu BuildApp.  
  
2. V prohlížeči **vlastností** si všimněte, že vlastnost **soubor projektu** je BuildApp. csproj. Všechny soubory projektu jsou pojmenovány s příponou "proj". Pokud jste vytvořili Visual Basic projekt, název souboru projektu by byl BuildApp. vbproj.  
  
3. Klikněte pravým tlačítkem myši na uzel projektu a pak klikněte na **Uvolnit projekt**.  
  
4. Znovu klikněte pravým tlačítkem na uzel projektu a pak klikněte na **Upravit BuildApp. csproj**.  
  
     Soubor projektu se zobrazí v editoru kódu.  
  
## <a name="targets-and-tasks"></a>Cíle a úkoly  
 Soubory projektu jsou soubory ve formátu XML s kořenovým uzlem [projektu](../msbuild/project-element-msbuild.md).  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<Project ToolsVersion="12.0" DefaultTargets="Build"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 V elementu projektu je nutné zadat obor názvů xmlns.  
  
 Práce při sestavování aplikace se provádí s [cíli](../msbuild/target-element-msbuild.md) a prvky [úkolu](../msbuild/task-element-msbuild.md) .  
  
- Úkol je nejmenší pracovní jednotka, jinými slovy "Atom" buildu. Úlohy jsou nezávislé spustitelné komponenty, které mohou mít vstupy a výstupy. V souboru projektu nejsou momentálně odkazovány nebo definovány žádné úlohy. Do souboru projektu přidáte úkoly v níže uvedených částech. Další informace najdete v tématu [úlohy](../msbuild/msbuild-tasks.md) .  
  
- Cíl je pojmenované pořadí úkolů. Na konci souboru projektu jsou dva cíle, které jsou aktuálně uzavřeny v komentářích jazyka HTML: BeforeBuild a AfterBuild.  
  
  ```  
  <Target Name="BeforeBuild">  
  </Target>  
  <Target Name="AfterBuild">  
  </Target>  
  ```  
  
   Další informace najdete v tématu [cíle](../msbuild/msbuild-targets.md) .  
  
  Uzel projektu má volitelný atribut DefaultTargets –, který v tomto případě sestaví výběr výchozího cíle pro sestavení.  
  
```  
<Project ToolsVersion="12.0" DefaultTargets="Build" ...  
```  
  
 Cíl sestavení není definován v souboru projektu. Místo toho je importován ze souboru Microsoft. CSharp. targets pomocí elementu [Import](../msbuild/import-element-msbuild.md) .  
  
```  
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
```  
  
 Importované soubory jsou efektivně vloženy do souboru projektu kdekoli, kde jsou odkazovány.  
  
 Nástroj MSBuild sleduje cíle sestavení a zaručuje, že každý cíl je sestaven více než jednou.  
  
## <a name="adding-a-target-and-a-task"></a>Přidání cíle a úkolu  
 Přidejte cíl do souboru projektu. Přidejte úkol do cíle, který vytiskne zprávu.  
  
#### <a name="to-add-a-target-and-a-task"></a>Přidání cíle a úkolu  
  
1. Přidejte tyto řádky do souboru projektu hned za příkaz import:  
  
   ```  
   <Target Name="HelloWorld">  
   </Target>  
   ```  
  
    Tím se vytvoří cíl s názvem HelloWorld. Všimněte si, že při úpravách souboru projektu máte podporu technologie IntelliSense.  
  
2. Přidejte řádky do cíle HelloWorld, aby výsledný oddíl vypadal takto:  
  
   ```  
   <Target Name="HelloWorld">  
     <Message Text="Hello"></Message>  <Message Text="World"></Message>  
   </Target>  
   ```  
  
3. Uložte soubor projektu.  
  
   Úloha zprávy je jednou z mnoha úloh, které jsou dodávány s nástrojem MSBuild. Úplný seznam dostupných úloh a informací o využití najdete v tématu s [odkazem na úlohu](../msbuild/msbuild-task-reference.md).  
  
   Úloha zprávy převezme řetězcovou hodnotu atributu text jako vstup a zobrazí ji na výstupním zařízení. Cíl HelloWorld spustí úlohu zprávy dvakrát: nejprve zobrazí text "Hello" a potom zobrazí "World".  
  
## <a name="building-the-target"></a>Sestavení cíle  
 Spusťte nástroj MSBuild z **příkazového řádku sady Visual Studio** a sestavte cíle HelloWorld definované výše. Pro výběr cíle použijte přepínač příkazového řádku/target nebo/t.  
  
> [!NOTE]
> Do **příkazového řádku sady Visual Studio** budeme odkazovat jako na **příkazové okno** v níže uvedených částech.  
  
#### <a name="to-build-the-target"></a>Sestavení cíle  
  
1. Klikněte na tlačítko **Start**a potom klikněte na položku **všechny programy**. Vyhledejte a klikněte na příkazový **řádek sady Visual Studio** ve složce **Visual Studio Tools** .  
  
2. Z příkazového okna přejděte do složky, která obsahuje soubor projektu, v tomto případě D:\BuildApp\BuildApp.  
  
3. Spusťte MSBuild pomocí příkazu switch/t: HelloWorld. Tím se vybere a sestaví se cíl HelloWorld:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4. Projděte si výstup ve **okno příkaz**. Měli byste vidět dva řádky "Hello" a "World":  
  
    ```  
    Hello  
    World  
    ```  
  
> [!NOTE]
> Pokud místo toho vidíte, `The target "HelloWorld" does not exist in the project` pravděpodobně jste zapomněli uložit soubor projektu v editoru kódu. Uložte soubor a zkuste to znovu.  
  
 Pomocí střídání mezi editorem kódu a oknem příkazového řádku můžete změnit soubor projektu a rychle zobrazit výsledky.  
  
> [!NOTE]
> Spouštíte-li nástroj MSBuild bez přepínače příkazu/t, nástroj MSBuild sestaví cíl zadaný atributem DefaultTarget elementu projektu v tomto případě "Build". Tím se vytvoří BuildApp.exe aplikace model Windows Forms.  
  
## <a name="build-properties"></a>Vlastnosti sestavení  
 Vlastnosti buildu jsou páry název-hodnota, které provedou sestavení. V horní části souboru projektu jsou již definovány některé vlastnosti buildu:  
  
```  
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
  
```  
<TargetFrameworkVersion>v12.0</TargetFrameworkVersion>  
```  
  
 definuje vlastnost s názvem TargetFrameworkVersion, která mu dává hodnotu řetězce "v 12.0".  
  
 Vlastnosti sestavení lze kdykoli znovu definovat. Pokud uživatel  
  
```  
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
```  
  
 se zobrazí později v souboru projektu nebo v souboru importovaném později v souboru projektu, TargetFrameworkVersion převezme novou hodnotu "v 3.5".  
  
## <a name="examining-a-property-value"></a>Zkoumání hodnoty vlastnosti  
 Chcete-li získat hodnotu vlastnosti, použijte následující syntaxi, kde PropertyName je název vlastnosti:  
  
```  
$(PropertyName)  
```  
  
 Tuto syntaxi použijte k prohlédnutí některých vlastností v souboru projektu.  
  
#### <a name="to-examine-a-property-value"></a>Prověření hodnoty vlastnosti  
  
1. V editoru kódu nahraďte cíl HelloWorld tímto kódem:  
  
    ```  
    <Target Name="HelloWorld">  
      <Message Text="Configuration is $(Configuration)" />  
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />  
    </Target>  
    ```  
  
2. Uložte soubor projektu.  
  
3. V **příkazovém okně**zadejte a spusťte tento řádek:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4. Prohlédněte si výstup. Tyto dva řádky by se měly zobrazit (vaše verze .NET Framework se může lišit):  
  
    ```  
    Configuration is Debug  
    MSBuildToolsPath is C:\Program Files\MSBuild\12.0\bin  
    ```  
  
> [!NOTE]
> Pokud tyto řádky nevidíte, pravděpodobně jste zapomněli uložit soubor projektu v editoru kódu. Uložte soubor a zkuste to znovu.  
  
### <a name="conditional-properties"></a>Podmíněné vlastnosti  
 Celá řada vlastností, jako je konfigurace, je definována podmíněně, to znamená, že atribut Condition se zobrazí v elementu Property. Podmíněné vlastnosti jsou definovány nebo předefinovány pouze v případě, že je podmínka vyhodnocena jako "true". Všimněte si, že nedefinované vlastnosti jsou předány výchozí hodnotě prázdného řetězce. Příklad:  
  
```  
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
```  
  
 znamená, že pokud vlastnost Configuration ještě není definovaná, definujte ji a sdělte jí hodnotu ' ladit '.  
  
 Téměř všechny prvky MSBuild můžou mít atribut Condition. Další diskuzi o použití atributu Condition najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).  
  
### <a name="reserved-properties"></a>Rezervované vlastnosti  
 Nástroj MSBuild si vyhrazuje některé názvy vlastností pro ukládání informací o souboru projektu a binárních souborech nástroje MSBuild. MSBuildToolsPath je příkladem rezervované vlastnosti. Na vyhrazené vlastnosti se odkazuje $ Notation, jako jakákoli jiná vlastnost. Další informace najdete v tématu [Postup: odkazování na název nebo umístění souboru projektu](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) a [rezervované a dobře známé vlastnosti nástroje MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
### <a name="environment-variables"></a>Proměnné prostředí  
 Můžete odkazovat na proměnné prostředí v souborech projektu stejným způsobem jako vlastnosti sestavení. Chcete-li například použít proměnnou prostředí PATH v souboru projektu, použijte $ (cesta). Pokud projekt obsahuje definici vlastnosti, která má stejný název jako proměnná prostředí, vlastnost v projektu přepíše hodnotu proměnné prostředí. Další informace najdete v tématu [Postupy: použití proměnných prostředí v sestavení](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
## <a name="setting-properties-from-the-command-line"></a>Nastavení vlastností z příkazového řádku  
 Vlastnosti lze definovat v příkazovém řádku pomocí přepínače příkazového řádku/Property nebo/p. Hodnoty vlastností obdržené z příkazového řádku přepisují hodnoty vlastností nastavené v souboru projektu a proměnných prostředí.  
  
#### <a name="to-set-a-property-value-from-the-command-line"></a>Nastavení hodnoty vlastnosti z příkazového řádku  
  
1. V **příkazovém okně**zadejte a spusťte tento řádek:  
  
   ```  
   msbuild buildapp.csproj /t:HelloWorld /p:Configuration=Release  
   ```  
  
2. Prohlédněte si výstup. Měl by se zobrazit tento řádek:  
  
   ```  
   Configuration is Release.  
   ```  
  
   Nástroj MSBuild vytvoří vlastnost konfigurace a poskytne jí hodnotu "Release".  
  
## <a name="special-characters"></a>Speciální znaky  
 Některé znaky mají v souborech projektu MSBuild zvláštní význam. Mezi příklady těchto znaků patří středník (;) a hvězdičky (*). Aby bylo možné použít tyto speciální znaky jako literály v souboru projektu, musí být zadány pomocí syntaxe% xx, kde xx představuje šestnáctkovou hodnotu ASCII znaku.  
  
 Změnou úlohy zprávy zobrazíte hodnotu vlastnosti konfigurace se speciálními znaky, aby byly čitelnější.  
  
#### <a name="to-use-special-characters-in-the-message-task"></a>Použití speciálních znaků v úloze zprávy  
  
1. V editoru kódu nahraďte obě úlohy zprávy tímto řádkem:  
  
   ```  
   <Message Text="%24(Configuration) is %22$(Configuration)%22" />  
   ```  
  
2. Uložte soubor projektu.  
  
3. V **příkazovém okně**zadejte a spusťte tento řádek:  
  
   ```  
   msbuild buildapp.csproj /t:HelloWorld  
   ```  
  
4. Prohlédněte si výstup. Měl by se zobrazit tento řádek:  
  
   ```  
   $(Configuration) is "Debug"  
   ```  
  
   Další informace najdete v tématu [speciální znaky nástroje MSBuild](../msbuild/msbuild-special-characters.md).  
  
## <a name="build-items"></a>Položky sestavení  
 Položka je část informací, obvykle název souboru, která se používá jako vstup do systému sestavení. Například kolekce položek, které představují zdrojové soubory, mohou být předány úloze s názvem Compile pro jejich zkompilování do sestavení.  
  
 Všechny položky jsou podřízené prvky prvků Item. Název položky je název podřízeného prvku a hodnota položky je hodnota atributu Include podřízeného prvku. Hodnoty položek se stejným názvem jsou shromažďovány do typů položek daného názvu.  Příklad:  
  
```  
<ItemGroup>  
    <Compile Include="Program.cs" />  
    <Compile Include="Properties\AssemblyInfo.cs" />  
</ItemGroup>  
```  
  
 definuje skupinu položek, která obsahuje dvě položky. Kompilace typu položky má dvě hodnoty: "Program.cs" a "Properties\AssemblyInfo.cs".  
  
 Následující kód vytvoří stejný typ položky deklarováním obou souborů v jednom vloženém atributu oddělené středníkem.  
  
```  
<ItemGroup>  
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />  
</ItemGroup>  
```  
  
 Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).  
  
> [!NOTE]
> Cesty k souborům jsou relativní vzhledem ke složce obsahující soubor projektu MSBuild.  
  
## <a name="examining-item-type-values"></a>Zkoumání hodnot typu položky  
 Chcete-li získat hodnoty typu položky, použijte následující syntaxi, kde ItemType je název typu položky:  
  
```  
@(ItemType)  
```  
  
 Tuto syntaxi použijte k prohlédnutí typu položky kompilace v souboru projektu.  
  
#### <a name="to-examine-item-type-values"></a>Prověření hodnot typu položky  
  
1. V editoru kódu nahraďte cílovou úlohu Hello tímto kódem:  
  
   ```  
   <Target Name="HelloWorld">  
     <Message Text="Compile item type contains @(Compile)" />  
   </Target>  
   ```  
  
2. Uložte soubor projektu.  
  
3. V **příkazovém okně**zadejte a spusťte tento řádek:  
  
   ```  
   msbuild buildapp.csproj /t:HelloWorld  
   ```  
  
4. Prohlédněte si výstup. Měla by se zobrazit tato dlouhá čára:  
  
   ```  
   Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs  
   ```  
  
   Hodnoty typu položky jsou ve výchozím nastavení oddělené středníkem.  
  
   Chcete-li změnit oddělovač typu položky, použijte následující syntaxi, kde ItemType je typ položky a oddělovač je řetězec jednoho nebo více oddělujících znaků:  
  
```  
@(ItemType, Separator)  
```  
  
 Změňte úlohu zprávy na použití návratových znaků a kanálů řádků (% 0A% 0D) pro zobrazení položek kompilace po jednotlivých řádcích.  
  
#### <a name="to-display-item-type-values-one-per-line"></a>Zobrazení hodnot typu položky na jednom řádku  
  
1. V editoru kódu nahraďte úlohu zprávy tímto řádkem:  
  
    ```  
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />  
    ```  
  
2. Uložte soubor projektu.  
  
3. V **příkazovém okně**zadejte a spusťte tento řádek:  
  
     `msbuild buildapp.csproj /t:HelloWorld`  
  
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
  
```  
<Photos Include="images\*.jpeg" />  
```  
  
 Přidá všechny soubory s příponou. jpeg ve složce images na typ položky fotky, zatímco  
  
```  
<Photos Include="images\**.jpeg" />  
```  
  
 Přidá všechny soubory s příponou. jpeg ve složce images a všech jejích podsložkách na typ položky fotky. Další příklady naleznete v tématu [Postupy: výběr souborů pro sestavení](../msbuild/how-to-select-the-files-to-build.md).  
  
 Všimněte si, že když jsou deklarovány položky, jsou přidány do typu položky. Příklad:  
  
```  
<Photos Include="images\*.jpeg" />  
<Photos Include="images\*.gif" />  
```  
  
 Vytvoří typ položky s názvem fotka obsahující všechny soubory ve složce image s příponou souboru. jpeg nebo. gif. To je ekvivalentní následujícímu řádku:  
  
```  
<Photos Include="images\*.jpeg;images\*.gif" />  
```  
  
 Můžete vyloučit položku z typu položky s atributem Exclude. Příklad:  
  
```  
<Compile Include="*.cs" Exclude="*Designer*">  
```  
  
 Přidá všechny soubory se souborem Extension". cs do typu položky kompilace, s výjimkou souborů, jejichž názvy obsahují řetězec" Designer ". Další příklady naleznete v tématu [Postupy: vyloučení souborů ze sestavení](../msbuild/how-to-exclude-files-from-the-build.md).  
  
 Atribut Exclude ovlivňuje pouze položky přidané atributem include v prvku položky, který je obsahuje obě. Příklad:  
  
```  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 nevylučuje soubor Form1.cs, který byl přidán do předchozí položky elementu.  
  
##### <a name="to-include-and-exclude-items"></a>Zahrnutí a vyloučení položek  
  
1. V editoru kódu nahraďte úlohu zprávy tímto řádkem:  
  
    ```  
    <Message Text="Compile item type contains @(XFiles)" />  
    ```  
  
2. Přidejte tuto skupinu položek hned za prvek importu:  
  
    ```  
    <ItemGroup>  
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />  
    </ItemGroup>  
    ```  
  
3. Uložte soubor projektu.  
  
4. V **příkazovém okně**zadejte a spusťte tento řádek:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
5. Prohlédněte si výstup. Měl by se zobrazit tento řádek:  
  
    ```  
    Compile item type contains Form1.cs;Program.cs;Properties/Resources.resx  
    ```  
  
## <a name="item-metadata"></a>Metadata položky  
 Kromě informací shromážděných z atributů include a Exclude mohou položky obsahovat i metadata. Tato metadata mohou být použita úkoly, které vyžadují více informací o položkách než pouze hodnota položky.  
  
 Metadata položky jsou deklarována v souboru projektu vytvořením prvku s názvem metadat jako podřízeným prvkem položky. Položka může mít nula nebo více hodnot metadat. Například následující položka CSFile má metadata jazykové verze s hodnotou "fr":  
  
```  
<ItemGroup>  
    <CSFile Include="main.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Chcete-li získat hodnotu metadat typu položky, použijte následující syntaxi, kde typ ItemType je název položky a MetaData je název metadat:  
  
```  
%(ItemType.MetaDataName)  
```  
  
#### <a name="to-examine-item-metadata"></a>Prohlédnutí metadat položky  
  
1. V editoru kódu nahraďte úlohu zprávy tímto řádkem:  
  
   ```  
   <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />  
   ```  
  
2. Uložte soubor projektu.  
  
3. V **příkazovém okně**zadejte a spusťte tento řádek:  
  
   ```  
   msbuild buildapp.csproj /t:HelloWorld  
   ```  
  
4. Prohlédněte si výstup. Měli byste vidět tyto řádky:  
  
   ```  
   Compile.DependentUpon:  
   Compile.DependentUpon: Form1.cs  
   Compile.DependentUpon: Resources.resx  
   Compile.DependentUpon: Settings.settings  
   ```  
  
   Všimněte si, jak se fráze "zkompilovat. DependentUpon" zobrazuje několikrát. Použití metadat s touto syntaxí v rámci cíle způsobuje "dávkování". Dávkování znamená, že úkoly v rámci cíle se spustí jednou pro každou jedinečnou hodnotu metadat. Toto je ekvivalent skriptu MSBuild v rámci společné programovací konstrukce for Loop. Další informace najdete v tématu [dávkování](../msbuild/msbuild-batching.md).  
  
### <a name="well-known-metadata"></a>Dobře známá metadata  
 Pokaždé, když se do seznamu položek přidá nějaká položka, přiřadí se některá dobře známá metadata. Například% (filename) vrátí název souboru jakékoli položky. Úplný seznam známých metadat najdete v tématu [známá metadata položky](../msbuild/msbuild-well-known-item-metadata.md).  
  
##### <a name="to-examine-well-known-metadata"></a>Kontrola dobře známých metadat  
  
1. V editoru kódu nahraďte úlohu zprávy tímto řádkem:  
  
   ```  
   <Message Text="Compile Filename: %(Compile.Filename)" />  
   ```  
  
2. Uložte soubor projektu.  
  
3. V **příkazovém okně**zadejte a spusťte tento řádek:  
  
   ```  
   msbuild buildapp.csproj /t:HelloWorld  
   ```  
  
4. Prohlédněte si výstup. Měli byste vidět tyto řádky:  
  
   ```  
   Compile Filename: Form1  
   Compile Filename: Form1.Designer  
   Compile Filename: Program  
   Compile Filename: AssemblyInfo  
   Compile Filename: Resources.Designer  
   Compile Filename: Settings.Designer  
   ```  
  
   Porovnáním dvou výše uvedených příkladů vidíte, že i když ne každá položka v typu položky kompilace má metadata DependentUpon, všechny položky mají dobře známá metadata filename.  
  
### <a name="metadata-transformations"></a>Transformace metadat  
 Seznamy položek lze transformovat na nové seznamy položek. Chcete-li transformovat seznam položek, použijte následující syntaxi, kde ItemType je název typu položky a metadata je název metadat:  
  
```  
@(ItemType -> '%(MetadataName)')  
```  
  
 Například seznam položek zdrojových souborů lze transformovat na kolekci souborů objektů pomocí výrazu, jako je `@(SourceFiles -> '%(Filename).obj')` . Další informace najdete v tématu [transformace](../msbuild/msbuild-transforms.md).  
  
##### <a name="to-transform-items-using-metadata"></a>Transformace položek pomocí metadat  
  
1. V editoru kódu nahraďte úlohu zprávy tímto řádkem:  
  
   ```  
   <Message Text="Backup files: @(Compile->'%(filename).bak')" />  
   ```  
  
2. Uložte soubor projektu.  
  
3. V **příkazovém okně**zadejte a spusťte tento řádek:  
  
   ```  
   msbuild buildapp.csproj /t:HelloWorld  
   ```  
  
4. Prohlédněte si výstup. Měl by se zobrazit tento řádek:  
  
   ```  
   Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak  
   ```  
  
   Všimněte si, že metadata vyjádřená v této syntaxi nezpůsobují dávkování.  
  
## <a name="whats-next"></a>Co dál?  
 Chcete-li zjistit, jak vytvořit jednoduchý soubor projektu v jednom kroku, postupujte podle [návodu: vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).  
  
## <a name="see-also"></a>Viz také
[Přehled nástroje MSBuild](msbuild.md)  
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)

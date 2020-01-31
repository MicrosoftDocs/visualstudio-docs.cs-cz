---
title: 'Návod: vytvoření souboru projektu MSBuild od začátku | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: e3acff7c-cb4e-4ae1-8be2-a871bcff847b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 891b0f1197ad178a705de5d64026beebc62615dd
ms.sourcegitcommit: 8cbced0fb46959a3a2494852df1e41db1177a26c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76826494"
---
# <a name="walkthrough-create-an-msbuild-project-file-from-scratch"></a>Návod: vytvoření souboru projektu MSBuild od začátku
Programovací jazyky, které cílí na .NET Framework používají soubory projektu MSBuild k popisu a řízení procesu sestavení aplikace. Při použití sady Visual Studio k vytvoření souboru projektu MSBuild je do souboru automaticky přidáno příslušné XML. Může však být užitečné pochopit, jak je kód XML uspořádán a jak jej lze změnit pro řízení sestavení.

 Informace o vytvoření souboru projektu pro C++ projekt naleznete v tématu [MSBuild (C++)](/cpp/build/msbuild-visual-cpp).

 Tento návod ukazuje, jak vytvořit soubor základního projektu přírůstkově pomocí pouze textového editoru. Tento návod se skládá z těchto kroků:

1. Vytvořte zdrojový soubor minimální aplikace.

2. Vytvořte minimální soubor projektu MSBuild.

3. Proměnnou prostředí PATH rozšíříte tak, aby zahrnovala nástroj MSBuild.

4. Sestavte aplikaci pomocí souboru projektu.

5. Přidejte vlastnosti pro řízení sestavení.

6. Řízení sestavení změnou hodnot vlastností.

7. Přidejte cíle do sestavení.

8. Řízení sestavení zadáním cílů.

9. Přírůstkové sestavení.

Tento návod ukazuje, jak sestavit projekt na příkazovém řádku a prohlédnout si výsledky. Další informace o nástroji MSBuild a o tom, jak spustit MSBuild v příkazovém řádku, naleznete v tématu [Návod: použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md).

Chcete-li dokončit tento návod, je nutné mít nainstalovanou .NET Framework (verze 2,0, 3,5, 4,0, 4,5 nebo novější), protože zahrnuje MSBuild a vizuální C# kompilátor, které jsou požadovány pro návod.

## <a name="create-a-minimal-application"></a>Vytvoření minimální aplikace
 V této části se dozvíte, jak C# vytvořit zdrojový soubor minimální aplikace pomocí textového editoru.

1. Na příkazovém řádku přejděte do složky, ve které chcete vytvořit aplikaci, například *\My documents\\* nebo *\Plocha\\* .

2. Zadejte **MD HelloWorld** pro vytvoření podsložky s názvem *\HelloWorld\\* .

3. Zadejte **CD HelloWorld** pro změnu do nové složky.

4. Spusťte Poznámkový blok nebo jiný textový editor a poté zadejte následující kód.

    ```csharp
    using System;

    class HelloWorld
    {
        static void Main()
        {
    #if DebugConfig
            Console.WriteLine("WE ARE IN THE DEBUG CONFIGURATION");
    #endif

            Console.WriteLine("Hello, world!");
        }
    }
    ```

5. Uložte tento soubor zdrojového kódu a pojmenujte ho *HelloWorld.cs*.

6. Sestavte aplikaci zadáním **csc HelloWorld.cs** na příkazovém řádku.

7. Otestujte aplikaci zadáním **HelloWorld** na příkazovém řádku.

     **Hello, World!** měla by se zobrazit zpráva.

8. Odstraňte aplikaci zadáním **del Hello. exe** z příkazového řádku.

## <a name="create-a-minimal-msbuild-project-file"></a>Vytvořit minimální soubor projektu MSBuild
 Teď, když máte minimální zdrojový soubor aplikace, můžete vytvořit minimální soubor projektu pro sestavení aplikace. Tento soubor projektu obsahuje následující prvky:

- Požadovaný kořenový uzel `Project`.

- Uzel `ItemGroup`, který obsahuje prvky položky.

- Element Item, který odkazuje na zdrojový soubor aplikace.

- Uzel `Target`, který obsahuje úlohy, které jsou nutné k sestavení aplikace.

- Element `Task`, který spustí vizuální C# kompilátor pro sestavení aplikace.

### <a name="to-create-a-minimal-msbuild-project-file"></a>Vytvoření minimálního souboru projektu MSBuild

1. V textovém editoru nahraďte existující text pomocí těchto dvou řádků:

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

2. Vložte tento `ItemGroup` uzel jako podřízený prvek uzlu `Project`:

    ```xml
    <ItemGroup>
      <Compile Include="helloworld.cs" />
    </ItemGroup>
    ```

     Všimněte si, že tento `ItemGroup` již obsahuje element Item.

3. Přidejte `Target` uzel jako podřízený prvek uzlu `Project`. Pojmenujte `Build`uzlu.

    ```xml
    <Target Name="Build">
    </Target>
    ```

4. Vložte tento element Task jako podřízený prvek uzlu `Target`:

    ```xml
    <Csc Sources="@(Compile)"/>
    ```

5. Uložte tento soubor projektu a pojmenujte ho *HelloWorld. csproj*.

Váš minimální soubor projektu by měl vypadat podobně jako následující kód:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <Csc Sources="@(Compile)"/>  
  </Target>
</Project>
```

Úlohy v cíli sestavení jsou spouštěny postupně. V tomto případě je úkol `Csc` C# Visual Compiler jediným úkolem. Očekává seznam zdrojových souborů, které mají být zkompilovány, a je dána hodnotou `Compile` položky. `Compile` položka odkazuje pouze na jeden zdrojový soubor, *HelloWorld.cs*.

> [!NOTE]
> V elementu Item můžete použít zástupný znak hvězdičky (\*) pro odkazování na všechny soubory, které mají příponu názvu souboru *. cs* následujícím způsobem:
>
> ```xml
> <Compile Include="*.cs" />
> ```
>
> Nedoporučujeme ale používat zástupné znaky, protože při přidávání nebo odstraňování zdrojových souborů je obtížné se zaměřit na ladění a selektivní cílení.

## <a name="extend-the-path-to-include-msbuild"></a>Rozšíří cestu pro zahrnutí nástroje MSBuild

Předtím, než budete moci získat přístup k nástroji MSBuild, je nutné roztáhnout proměnnou prostředí PATH, aby zahrnovala složku .NET Framework.

Počínaje Visual Studio 2013 můžete soubor *MSBuild. exe* najít ve složce MSBuild ( *%ProgramFiles%\MSBuild* v 32ém operačním systému nebo v *% ProgramFiles (x86)% \ MSBuild* na 64 operačním systému).

Na příkazovém řádku zadejte **set cesta =% Path%;%ProgramFiles%\MSBuild** nebo **set PATH =% Path%;% ProgramFiles (x86)% \ MSBuild**.

Případně, pokud máte nainstalovanou aplikaci Visual Studio, můžete použít **Developer Command Prompt pro Visual Studio**, která má cestu, která obsahuje složku *MSBuild* .

## <a name="build-the-application"></a>Sestavení aplikace
 Nyní k sestavení aplikace použijte soubor projektu, který jste právě vytvořili.

1. Na příkazovém řádku zadejte **MSBuild HelloWorld. csproj-t:Build**.

     Tím se vytvoří cíl sestavení souboru projektu HelloWorld vyvoláním vizuálního C# kompilátoru pro vytvoření aplikace HelloWorld.

2. Otestujte aplikaci zadáním **HelloWorld**.

     **Hello, World!** měla by se zobrazit zpráva.

> [!NOTE]
> Další podrobnosti o sestavení můžete zobrazit zvýšením úrovně podrobností. Chcete-li nastavit úroveň podrobností na "podrobné", zadejte tento příkaz na příkazovém řádku:
>
> **MSBuild HelloWorld. csproj-t:Build-detailed: detailed**

## <a name="add-build-properties"></a>Přidat vlastnosti sestavení
 Můžete přidat vlastnosti sestavení do souboru projektu k dalšímu řízení sestavení. Nyní přidejte tyto vlastnosti:

- Vlastnost `AssemblyName` pro určení názvu aplikace.

- Vlastnost `OutputPath` k určení složky, která má obsahovat aplikaci.

### <a name="to-add-build-properties"></a>Přidání vlastností sestavení

1. Odstraňte existující aplikaci zadáním **del Hello. exe** z příkazového řádku.

2. V souboru projektu vložte tento prvek `PropertyGroup` hned za otevřený `Project` element:

    ```xml
    <PropertyGroup>
      <AssemblyName>MSBuildSample</AssemblyName>
      <OutputPath>Bin\</OutputPath>
    </PropertyGroup>
    ```

3. Přidejte tento úkol do cíle sestavení těsně před úlohu `Csc`:

    ```xml
    <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />
    ```

     Úloha `MakeDir` vytvoří složku, která je pojmenována vlastností `OutputPath` za předpokladu, že v tuto chvíli neexistuje žádná složka s tímto názvem.

4. Přidejte tento atribut `OutputAssembly` do úlohy `Csc`:

    ```xml
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    ```

     To instruuje kompilátor vizuálu C# , aby vytvořil sestavení, které je pojmenováno vlastností `AssemblyName` a umístí ho do složky, která je pojmenována vlastností `OutputPath`.

5. Uložte provedené změny.

Soubor projektu by měl nyní vypadat podobně jako následující kód:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <AssemblyName>MSBuildSample</AssemblyName>
    <OutputPath>Bin\</OutputPath>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
  </Target>
</Project>
```

> [!NOTE]
> Doporučujeme přidat oddělovač cest zpětného lomítka (\\) na konec názvu složky při jeho zadání v elementu `OutputPath` namísto přidání do atributu `OutputAssembly` `Csc` úlohy. Třeba
>
> `<OutputPath>Bin\</OutputPath>`
>
> `OutputAssembly=="$(OutputPath)$(AssemblyName).exe" />`
>
> je lepší než
>
> `<OutputPath>Bin</OutputPath>`
>
> `OutputAssembly=="$(OutputPath)\$(AssemblyName).exe" />`

## <a name="test-the-build-properties"></a>Testování vlastností sestavení
 Nyní můžete sestavit aplikaci pomocí souboru projektu, ve kterém jste použili vlastnosti sestavení k určení výstupní složky a názvu aplikace.

1. Na příkazovém řádku zadejte **MSBuild HelloWorld. csproj-t:Build**.

     Tím se vytvoří složka *\bin\\* a potom se vyvolá kompilátor vizuálu C# , aby se vytvořila aplikace *aplikaci MSBuildSample* a umístí se do složky *\Bin\\* .

2. Chcete-li ověřit, zda byla vytvořena složka *\bin\\* a zda obsahuje aplikaci *aplikaci MSBuildSample* , zadejte příkaz **dir bin**.

3. Otestujte aplikaci zadáním **Bin\MSBuildSample**.

     **Hello, World!** měla by se zobrazit zpráva.

## <a name="add-build-targets"></a>Přidat cíle sestavení
 Dále přidejte do souboru projektu dva další cíle následujícím způsobem:

- Čistý cíl, který odstraní staré soubory.

- Cíl opětovného sestavení, který používá atribut `DependsOnTargets` k vynucení spuštění úlohy čištění před úlohou sestavení.

Teď, když máte více cílů, můžete nastavit cíl sestavení jako výchozí cíl.

### <a name="to-add-build-targets"></a>Přidání cílů sestavení

1. V souboru projektu přidejte tyto dva cíle hned po cíli sestavení:

    ```xml
    <Target Name="Clean" >
      <Delete Files="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
    ```

     Cíl vyčištění vyvolá úlohu odstranění pro odstranění aplikace. Cíl opětovného sestavení se nespustí, dokud se nespustí plán vyčištění i cíl sestavení. I když cíl opětovného sestavení nemá žádné úkoly, způsobí, že se čistý cíl spustí před cílem sestavení.

2. Přidejte tento atribut `DefaultTargets` do otevřeného elementu `Project`:

    ```xml
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    ```

     Tím se nastaví cíl sestavení jako výchozí cíl.

Soubor projektu by měl nyní vypadat podobně jako následující kód:

```xml
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <AssemblyName>MSBuildSample</AssemblyName>
    <OutputPath>Bin\</OutputPath>
  </PropertyGroup>
  <ItemGroup>
    <Compile Include="helloworld.cs" />
  </ItemGroup>
  <Target Name="Build">
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
  </Target>
  <Target Name="Clean" >
    <Delete Files="$(OutputPath)$(AssemblyName).exe" />
  </Target>
  <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
</Project>
```

## <a name="test-the-build-targets"></a>Testování cílů sestavení
 Nové cíle sestavení můžete vykonat pro otestování těchto funkcí souboru projektu:

- Sestavení výchozího sestavení.

- Nastavení názvu aplikace v příkazovém řádku.

- Odstranění aplikace před sestavením jiné aplikace.

- Odstranění aplikace bez sestavování jiné aplikace.

### <a name="to-test-the-build-targets"></a>Testování cílů sestavení

1. Na příkazovém řádku zadejte **MSBuild HelloWorld. csproj-p:AssemblyName = Greetings**.

     Vzhledem k tomu, že jste nepoužili přepínač **-t** k explicitnímu nastavení cíle, nástroj MSBuild spustí výchozí cíl sestavení. Přepínač **-p** přepíše vlastnost `AssemblyName` a získá novou hodnotu `Greetings`. Tím dojde k vytvoření nové aplikace, *Greetings. exe*ve složce *\Bin\\* .

2. Chcete-li ověřit, zda složka *\bin\\* obsahuje aplikaci *aplikaci MSBuildSample* i novou aplikaci *Greetings* , zadejte příkaz **dir bin**.

3. Otestujte aplikaci Greetings zadáním **Bin\Greetings**.

     **Hello, World!** měla by se zobrazit zpráva.

4. Odstraňte aplikaci aplikaci MSBuildSample zadáním **MSBuild Hello. csproj-t:Clean**.

     Tím se spustí úloha vyčistit pro odebrání aplikace, která má výchozí hodnotu vlastnosti `AssemblyName` `MSBuildSample`.

5. Odstraňte aplikaci Greetings zadáním **MSBuild Hello. csproj-t:Clean-p:AssemblyName = Greetings**.

     Tím se spustí úloha vyčistit pro odebrání aplikace, která má zadanou hodnotu vlastnosti **AssemblyName** , `Greetings`.

6. Chcete-li ověřit, zda je složka *\bin\\* nyní prázdná, zadejte příkaz **dir bin**.

7. Zadejte **MSBuild**.

     I když není zadán soubor projektu, MSBuild sestaví soubor *HelloWorld. csproj* , protože aktuální složka obsahuje pouze jeden soubor projektu. To způsobí, že se aplikace *aplikaci MSBuildSample* vytvoří ve složce *\Bin\\* .

     Chcete-li ověřit, zda složka *\bin\\* obsahuje aplikaci *aplikaci MSBuildSample* , zadejte příkaz **dir bin**.

## <a name="build-incrementally"></a>Přírůstkové sestavení
 Nástroj MSBuild můžete sdělit, aby vytvořil cíl pouze v případě, že se změnily zdrojové soubory nebo cílové soubory, na kterých je cíl závislý. Nástroj MSBuild používá časové razítko souboru k určení, zda došlo ke změně.

### <a name="to-build-incrementally"></a>Přírůstkové sestavení

1. V souboru projektu přidejte tyto atributy do úvodního cíle sestavení:

    ```xml
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"
    ```

     To určuje, že cíl sestavení závisí na vstupních souborech, které jsou zadány ve skupině položek `Compile` a zda je výstupním cílem soubor aplikace.

     Výsledný cíl sestavení by měl vypadat podobně jako následující kód:

    ```xml
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    ```

2. Otestujte cíl sestavení zadáním **MSBuild-v:d** do příkazového řádku.

     Nezapomeňte, že *HelloWorld. csproj* je výchozí soubor projektu a toto sestavení je výchozí cíl.

     Přepínač **-v:d** určuje podrobný popis procesu sestavení.

     Tyto řádky by měly být zobrazeny:

     **Vynechává se cíl "Build", protože všechny výstupní soubory jsou aktuální s ohledem na vstupní soubory.**

     **Vstupní soubory: HelloWorld.cs**

     **Výstupní soubory: BinMSBuildSample. exe**

     MSBuild přeskočí cíl sestavení, protože žádný ze zdrojových souborů se od posledního sestavení aplikace nezměnil.

## <a name="c-example"></a>C#případě

Následující příklad ukazuje soubor projektu, který zkompiluje C# aplikaci a zaznamená zprávu, která obsahuje název výstupního souboru.

### <a name="code"></a>Kód

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldCS</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input files of type CSFile -->
        <CSC
            Sources = "@(CSFile)"
            OutputAssembly = "$(appname).exe">
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="visual-basic-example"></a>Příklad Visual Basic

Následující příklad ukazuje soubor projektu, který zkompiluje Visual Basic aplikace a zaznamená zprávu, která obsahuje název výstupního souboru.

### <a name="code"></a>Kód

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldVB</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <VBFile Include = "consolehwvb1.vb"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual Basic compilation using input files of type VBFile -->
        <VBC
            Sources = "@(VBFile)"
            OutputAssembly= "$(appname).exe">
            <!-- Set the OutputAssembly attribute of the VBC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </VBC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="whats-next"></a>Co dále?
 Visual Studio může automaticky provádět spoustu práce, která je uvedená v tomto návodu. Informace o tom, jak používat Visual Studio k vytváření, úpravám, sestavování a testování souborů projektu MSBuild, najdete v tématu [Návod: použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="see-also"></a>Viz také:

- [Přehled nástroje MSBuild](../msbuild/msbuild.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)

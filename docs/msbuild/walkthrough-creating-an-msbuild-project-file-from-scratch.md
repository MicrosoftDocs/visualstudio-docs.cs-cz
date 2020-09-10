---
title: Vytvoření souboru projektu MSBuild od začátku
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
ms.openlocfilehash: edd5f3a01cc96a80403d1b030541e08e19d51eef
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2020
ms.locfileid: "89741732"
---
# <a name="walkthrough-create-an-msbuild-project-file-from-scratch"></a>Návod: vytvoření souboru projektu MSBuild od začátku

Programovací jazyky, které cílí na .NET Framework používají soubory projektu MSBuild k popisu a řízení procesu sestavení aplikace. Při použití sady Visual Studio k vytvoření souboru projektu MSBuild je do souboru automaticky přidáno příslušné XML. Může však být užitečné pochopit, jak je kód XML uspořádán a jak jej lze změnit pro řízení sestavení.

 Informace o vytvoření souboru projektu pro projekt C++ naleznete v tématu [MSBuild (C++)](/cpp/build/msbuild-visual-cpp).

 Tento návod ukazuje, jak vytvořit soubor základního projektu přírůstkově pomocí pouze textového editoru. Tento návod se skládá z těchto kroků:

1. Rozšíří proměnnou prostředí PATH.

2. Vytvořte zdrojový soubor minimální aplikace.

3. Vytvořte minimální soubor projektu MSBuild.

4. Sestavte aplikaci pomocí souboru projektu.

5. Přidejte vlastnosti pro řízení sestavení.

6. Řízení sestavení změnou hodnot vlastností.

7. Přidejte cíle do sestavení.

8. Řízení sestavení zadáním cílů.

9. Přírůstkové sestavení.

Tento návod ukazuje, jak sestavit projekt na příkazovém řádku a prohlédnout si výsledky. Další informace o nástroji MSBuild a o tom, jak spustit MSBuild v příkazovém řádku, naleznete v tématu [Návod: použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md).

Chcete-li dokončit tento návod, je nutné mít nainstalovanou aplikaci Visual Studio, protože obsahuje MSBuild a kompilátor Visual C#, které jsou požadovány pro návod.

## <a name="extend-the-path"></a>Rozšíří cestu

Než budete moct použít MSBuild, musíte proměnnou prostředí PATH zvětšit tak, aby zahrnovala všechny požadované nástroje. Můžete použít **Developer Command Prompt pro Visual Studio**. Vyhledejte ji ve Windows 10 ve vyhledávacím poli na panelu úloh Windows. Chcete-li nastavit prostředí v běžném příkazovém řádku nebo ve skriptovacím prostředí, spusťte *VSDevCmd.bat* v podsložce *Common7/Tools* instalace sady Visual Studio.

## <a name="create-a-minimal-application"></a>Vytvoření minimální aplikace

 V této části se dozvíte, jak vytvořit zdrojový soubor aplikace s minimálním jazykem C# pomocí textového editoru.

1. Na příkazovém řádku přejděte do složky, ve které chcete vytvořit aplikaci, například *\My Documents \\ * nebo *\Plocha \\ *.

2. Zadejte **MD HelloWorld** pro vytvoření podsložky s názvem *\HelloWorld \\ *.

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

8. Odstraňte aplikaci zadáním příkazu **del helloworld.exe** v příkazovém řádku.

## <a name="create-a-minimal-msbuild-project-file"></a>Vytvořit minimální soubor projektu MSBuild

 Teď, když máte minimální zdrojový soubor aplikace, můžete vytvořit minimální soubor projektu pro sestavení aplikace. Tento soubor projektu obsahuje následující prvky:

- Požadovaný kořenový `Project` uzel.

- `ItemGroup`Uzel, který obsahuje prvky položky.

- Element Item, který odkazuje na zdrojový soubor aplikace.

- `Target`Uzel, který obsahuje úlohy, které jsou požadovány k sestavení aplikace.

- `Task`Prvek pro spuštění kompilátoru Visual C# pro sestavení aplikace.

### <a name="to-create-a-minimal-msbuild-project-file"></a>Vytvoření minimálního souboru projektu MSBuild

1. V textovém editoru nahraďte existující text pomocí těchto dvou řádků:

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

2. Vložte tento `ItemGroup` uzel jako podřízený prvek `Project` uzlu:

    ```xml
    <ItemGroup>
      <Compile Include="helloworld.cs" />
    </ItemGroup>
    ```

     Všimněte si, že `ItemGroup` již obsahuje element Item.

3. Přidejte `Target` uzel jako podřízený prvek `Project` uzlu. Pojmenujte uzel `Build` .

    ```xml
    <Target Name="Build">
    </Target>
    ```

4. Vložte tento element Task jako podřízený prvek `Target` uzlu:

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

Úlohy v cíli sestavení jsou spouštěny postupně. V tomto případě je úkol kompilátoru Visual C# `Csc` jediným úkolem. Očekává seznam zdrojových souborů, které mají být zkompilovány, a je dána hodnotou `Compile` položky. `Compile`Položka odkazuje pouze na jeden zdrojový soubor *HelloWorld.cs*.

> [!NOTE]
> V elementu Item můžete použít zástupný znak hvězdičky ( \* ) pro odkazování na všechny soubory, které mají příponu názvu souboru *. cs* následujícím způsobem:
>
> ```xml
> <Compile Include="*.cs" />
> ```

## <a name="build-the-application"></a>Sestavení aplikace

 Nyní k sestavení aplikace použijte soubor projektu, který jste právě vytvořili.

1. Na příkazovém řádku zadejte **MSBuild HelloWorld. csproj-t:Build**.

     Tím se vytvoří cíl sestavení souboru projektu HelloWorld vyvoláním kompilátoru Visual C# pro vytvoření aplikace HelloWorld.

2. Otestujte aplikaci zadáním **HelloWorld**.

     **Hello, World!** měla by se zobrazit zpráva.

> [!NOTE]
> Další podrobnosti o sestavení můžete zobrazit zvýšením úrovně podrobností. Chcete-li nastavit úroveň podrobností na "podrobné", zadejte tento příkaz na příkazovém řádku:
>
> **MSBuild HelloWorld. csproj-t:Build-detailed: detailed**

## <a name="add-build-properties"></a>Přidat vlastnosti sestavení

 Můžete přidat vlastnosti sestavení do souboru projektu k dalšímu řízení sestavení. Nyní přidejte tyto vlastnosti:

- `AssemblyName`Vlastnost, která určuje název aplikace.

- `OutputPath`Vlastnost, která určuje složku, do které má být aplikace obsažena.

### <a name="to-add-build-properties"></a>Přidání vlastností sestavení

1. Odstraňte existující aplikaci zadáním příkazu **del helloworld.exe** v příkazovém řádku.

2. V souboru projektu vložte tento `PropertyGroup` prvek hned za otevřený `Project` element:

    ```xml
    <PropertyGroup>
      <AssemblyName>MSBuildSample</AssemblyName>
      <OutputPath>Bin\</OutputPath>
    </PropertyGroup>
    ```

3. Přidejte tento úkol do cíle sestavení těsně před `Csc` úlohu:

    ```xml
    <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />
    ```

     `MakeDir`Úloha vytvoří složku, která je pojmenována `OutputPath` vlastností za předpokladu, že v tuto chvíli neexistuje žádná složka s tímto názvem.

4. Přidejte tento `OutputAssembly` atribut do `Csc` úlohy:

    ```xml
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    ```

     To instruuje kompilátor Visual C#, aby vytvořil sestavení s názvem `AssemblyName` vlastností a umístil ho do složky, která je pojmenována `OutputPath` vlastností.

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
> Doporučujeme přidat oddělovač cest zpětného lomítka ( \\ ) na konec názvu složky při jeho zadání v `OutputPath` elementu namísto přidání do `OutputAssembly` atributu `Csc` úlohy. Z toho plyne:
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

     Tím se vytvoří *Složka \\ \Bin* a potom se kompilátor Visual C# vyvolá, aby se vytvořila aplikace *aplikaci MSBuildSample* a umístí se do *složky \\ \Bin* .

2. Chcete-li ověřit, zda byla vytvořena složka *\Bin \\ * a zda obsahuje aplikaci *aplikaci MSBuildSample* , zadejte příkaz **dir bin**.

3. Otestujte aplikaci zadáním **Bin\MSBuildSample**.

     **Hello, World!** měla by se zobrazit zpráva.

## <a name="add-build-targets"></a>Přidat cíle sestavení

 Dále přidejte do souboru projektu dva další cíle následujícím způsobem:

- Čistý cíl, který odstraní staré soubory.

- Cíl opětovného sestavení, který používá `DependsOnTargets` atribut k vynucení spuštění úlohy čištění před úlohou sestavení.

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

2. Přidejte tento `DefaultTargets` atribut do otevřeného `Project` elementu:

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

     Vzhledem k tomu, že jste nepoužili přepínač **-t** k explicitnímu nastavení cíle, nástroj MSBuild spustí výchozí cíl sestavení. Přepínač **-p** Přepisuje `AssemblyName` vlastnost a přidělí jí novou hodnotu, `Greetings` . To způsobí, že se ve složce *\Bin \\ * vytvoří nová aplikace, *Greetings.exe*.

2. Chcete-li ověřit, zda složka * \\ \Bin* obsahuje aplikaci *aplikaci MSBuildSample* i novou aplikaci *Greetings* , zadejte příkaz **dir bin**.

3. Otestujte aplikaci Greetings zadáním **Bin\Greetings**.

     **Hello, World!** měla by se zobrazit zpráva.

4. Odstraňte aplikaci aplikaci MSBuildSample zadáním **MSBuild Hello. csproj-t:Clean**.

     Tím se spustí úloha vyčistit pro odebrání aplikace, která má výchozí `AssemblyName` hodnotu vlastnosti `MSBuildSample` .

5. Odstraňte aplikaci Greetings zadáním **MSBuild Hello. csproj-t:Clean-p:AssemblyName = Greetings**.

     Tím se spustí úloha vyčistit pro odebrání aplikace, která má zadanou hodnotu vlastnosti **AssemblyName** `Greetings` .

6. Chcete-li ověřit, zda je složka * \\ \Bin* nyní prázdná, zadejte příkaz **dir bin**.

7. Zadejte **MSBuild**.

     I když není zadán soubor projektu, MSBuild sestaví soubor *HelloWorld. csproj* , protože aktuální složka obsahuje pouze jeden soubor projektu. To způsobí, že se aplikace *aplikaci MSBuildSample* vytvoří ve složce *\Bin \\ * .

     Chcete-li ověřit, zda složka *\Bin \\ * obsahuje aplikaci *aplikaci MSBuildSample* , zadejte příkaz **dir bin**.

## <a name="build-incrementally"></a>Přírůstkové sestavování

 Nástroj MSBuild můžete sdělit, aby vytvořil cíl pouze v případě, že se změnily zdrojové soubory nebo cílové soubory, na kterých je cíl závislý. Nástroj MSBuild používá časové razítko souboru k určení, zda došlo ke změně.

### <a name="to-build-incrementally"></a>Přírůstkové sestavení

1. V souboru projektu přidejte tyto atributy do úvodního cíle sestavení:

    ```xml
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"
    ```

     To určuje, že cíl sestavení závisí na vstupních souborech, které jsou zadány ve `Compile` skupině položek a zda je výstupním cílem soubor aplikace.

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

     **Výstupní soubory: BinMSBuildSample.exe**

     MSBuild přeskočí cíl sestavení, protože žádný ze zdrojových souborů se od posledního sestavení aplikace nezměnil.

## <a name="c-example"></a>Příklad jazyka C#

Následující příklad ukazuje soubor projektu, který zkompiluje aplikaci v jazyce C# a zaznamená zprávu, která obsahuje název výstupního souboru.

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

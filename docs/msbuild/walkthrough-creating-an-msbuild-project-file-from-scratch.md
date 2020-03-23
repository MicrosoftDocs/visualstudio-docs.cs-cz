---
title: 'Návod: Vytvoření souboru projektu MSBuild od začátku | Dokumenty společnosti Microsoft'
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
ms.openlocfilehash: 5fe9f052c10f31c4db0f8bf09f273be5814ff732
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263133"
---
# <a name="walkthrough-create-an-msbuild-project-file-from-scratch"></a>Návod: Vytvoření souboru projektu MSBuild od začátku

Programovací jazyky, které cílí na rozhraní .NET Framework, používají k popisu a řízení procesu sestavení aplikace soubory projektu MSBuild. Při použití sady Visual Studio k vytvoření souboru projektu MSBuild, příslušný XML je přidán do souboru automaticky. Může však být užitečné pochopit, jak je xml uspořádán a jak jej můžete změnit pro řízení sestavení.

 Informace o vytvoření souboru projektu pro projekt jazyka C++ naleznete v tématu [MSBuild (C++).](/cpp/build/msbuild-visual-cpp)

 Tento návod ukazuje, jak vytvořit základní soubor projektu postupně pomocí pouze textového editoru. Návod následuje následujícím způsobem:

1. Vytvořte minimální zdrojový soubor aplikace.

2. Vytvořte minimální soubor projektu MSBuild.

3. Rozšiřte proměnnou prostředí PATH tak, aby zahrnovala MSBuild.

4. Vytvořte aplikaci pomocí souboru projektu.

5. Přidejte vlastnosti pro řízení sestavení.

6. Ovládejte sestavení změnou hodnot vlastností.

7. Přidejte cíle do sestavení.

8. Řízení sestavení zadáním cílů.

9. Sestavení postupně.

Tento návod ukazuje, jak vytvořit projekt na příkazovém řádku a zkontrolujte výsledky. Další informace o msbuildu a způsobu spuštění msbuildu na příkazovém řádku naleznete v [tématu Návod: Použití msbuildu](../msbuild/walkthrough-using-msbuild.md).

Chcete-li dokončit návod, musíte mít nainstalovaný rozhraní .NET Framework (verze 2.0, 3.5, 4.0, 4.5 nebo novější), protože obsahuje MSBuild a kompilátor Visual C#, které jsou požadovány pro návod.

## <a name="create-a-minimal-application"></a>Vytvoření minimální aplikace

 Tato část ukazuje, jak vytvořit minimální zdrojový soubor aplikace C# pomocí textového editoru.

1. Na příkazovém řádku vyhledejte složku, do které chcete vytvořit aplikaci, například *\Dokumenty\\ * nebo *\Desktop\\*.

2. Zadejte **md HelloWorld** a vytvořte podsložku s názvem *\\\HelloWorld*.

3. Zadejte **cd HelloWorld** pro změnu do nové složky.

4. Spusťte poznámkový blok nebo jiný textový editor a zadejte následující kód.

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

5. Uložte tento soubor zdrojového kódu a *pojmenujte*jej Helloworld.cs .

6. Vytvořte aplikaci zadáním **csc helloworld.cs** na příkazovém řádku.

7. Otestujte aplikaci zadáním **helloworld** na příkazovém řádku.

     **Ahoj, světe!** zpráva by měla být zobrazena.

8. Odstraňte aplikaci zadáním **del helloworld.exe** na příkazovém řádku.

## <a name="create-a-minimal-msbuild-project-file"></a>Vytvoření minimálního souboru projektu MSBuild

 Nyní, když máte minimální zdrojový soubor aplikace, můžete vytvořit minimální soubor projektu k vytvoření aplikace. Tento soubor projektu obsahuje následující prvky:

- Požadovaný kořenový `Project` uzel.

- Uzel `ItemGroup` obsahující prvky položky.

- Prvek položky, který odkazuje na zdrojový soubor aplikace.

- Uzel `Target` obsahující úkoly, které jsou nutné k sestavení aplikace.

- Prvek `Task` pro spuštění kompilátoru Visual C# k sestavení aplikace.

### <a name="to-create-a-minimal-msbuild-project-file"></a>Vytvoření minimálního souboru projektu MSBuild

1. V textovém editoru nahraďte existující text pomocí těchto dvou řádků:

    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

2. Vložte `ItemGroup` tento uzel jako podřízený prvek `Project` uzlu:

    ```xml
    <ItemGroup>
      <Compile Include="helloworld.cs" />
    </ItemGroup>
    ```

     Všimněte `ItemGroup` si, že již obsahuje prvek položky.

3. Přidejte `Target` uzel jako podřízený `Project` prvek uzlu. Pojmenujte `Build`uzel .

    ```xml
    <Target Name="Build">
    </Target>
    ```

4. Vložte tento prvek úkolu jako `Target` podřízený prvek uzlu:

    ```xml
    <Csc Sources="@(Compile)"/>
    ```

5. Uložte tento soubor projektu a pojmenujte jej *Helloworld.csproj*.

Minimální soubor projektu by se měl podobat následujícímu kódu:

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

Úkoly v cíli sestavení jsou prováděny postupně. V tomto případě `Csc` je úkol kompilátoru Visual C# je jediný úkol. Očekává, že seznam zdrojových souborů ke kompilaci, a `Compile` to je dáno hodnotou položky. Položka `Compile` odkazuje pouze na jeden zdrojový *soubor, Helloworld.cs*.

> [!NOTE]
> V elementu item můžete použít zástupný znak\*hvězdičky ( ) k odkazování na všechny soubory, které mají příponu *.cs* název souboru, a to následovně:
>
> ```xml
> <Compile Include="*.cs" />
> ```

## <a name="extend-the-path-to-include-msbuild"></a>Rozšíření cesty tak, aby zahrnovala MSBuild

Před přístupem k msbuild, je nutné rozšířit proměnnou prostředí PATH zahrnout složku rozhraní .NET Framework.

Počínaje visual studio 2013 najdete *msbuild.exe* ve složce MSBuild (*%ProgramFiles%\MSBuild* na 32bitovém operačním systému nebo v *%ProgramFiles(x86)%\MSBuild* na 64bitovém operačním systému).

Na příkazovém řádku zadejte **příkaz PATH=%PATH%;%ProgramFiles%\MSBuild** nebo **PATH=%PATH%;%ProgramFiles(x86)%\MSBuild**.

Případně pokud máte nainstalovanou visual studio, můžete použít **příkazový řádek pro vývojáře pro Visual Studio**, který má cestu, která obsahuje složku *MSBuild.*

## <a name="build-the-application"></a>Sestavení aplikace

 Nyní k vytvoření aplikace použijte soubor projektu, který jste právě vytvořili.

1. Na příkazovém řádku zadejte **příkaz msbuild helloworld.csproj -t:Build**.

     To vytvoří sestavení cíl souboru projektu Helloworld vyvoláním Visual C# kompilátor u vytvořit aplikaci Helloworld.

2. Otestujte aplikaci zadáním **helloworld**.

     **Ahoj, světe!** zpráva by měla být zobrazena.

> [!NOTE]
> Můžete zobrazit další podrobnosti o sestavení zvýšením úroveň podrobností. Chcete-li nastavit úroveň podrobností na "podrobnou", zadejte tento příkaz na příkazovém řádku:
>
> **msbuild helloworld.csproj -t:Build -verbosity:detailní**

## <a name="add-build-properties"></a>Přidání vlastností sestavení

 Můžete přidat vlastnosti sestavení do souboru projektu k dalšímu řízení sestavení. Nyní přidejte tyto vlastnosti:

- Vlastnost `AssemblyName` zadejte název aplikace.

- Vlastnost `OutputPath` určit složku, která má obsahovat aplikaci.

### <a name="to-add-build-properties"></a>Přidání vlastností sestavení

1. Odstraňte existující aplikaci zadáním **souboru del helloworld.exe** na příkazovém řádku.

2. V souboru projektu `PropertyGroup` vložte tento `Project` prvek těsně za otevírací prvek:

    ```xml
    <PropertyGroup>
      <AssemblyName>MSBuildSample</AssemblyName>
      <OutputPath>Bin\</OutputPath>
    </PropertyGroup>
    ```

3. Přidejte tento úkol do cíle `Csc` sestavení těsně před úkolem:

    ```xml
    <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />
    ```

     Úloha `MakeDir` vytvoří složku, která `OutputPath` je pojmenována vlastností, za předpokladu, že aktuálně neexistuje žádná složka s tímto názvem.

4. Přidejte `OutputAssembly` tento `Csc` atribut do úkolu:

    ```xml
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    ```

     To instruuje kompilátor Visual C# k `AssemblyName` vytvoření sestavení, které je pojmenováno vlastností a umístit jej do složky, která je pojmenována `OutputPath` vlastností.

5. Uložte provedené změny.

Soubor projektu by se nyní měl podobat následujícímu kódu:

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
> Doporučujeme přidat oddělovač\\cest zpětného lomítka ( ) na konec `OutputPath` názvu složky, když `OutputAssembly` jej zadáte `Csc` v prvku, namísto jeho přidání do atributu úkolu. Proto:
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

 Nyní můžete vytvořit aplikaci pomocí souboru projektu, ve kterém jste použili vlastnosti sestavení k určení výstupní složky a názvu aplikace.

1. Na příkazovém řádku zadejte **příkaz msbuild helloworld.csproj -t:Build**.

     Tím se vytvoří složka *\Bin\\ * a potom vyvolá kompilátor Visual C# a vytvoří aplikaci *MSBuildSample* a vloží ji do složky *\Bin.\\ *

2. Chcete-li ověřit, zda byla složka *\\ \Bin* vytvořena a zda obsahuje aplikaci *MSBuildSample,* zadejte **dir Bin**.

3. Otestujte aplikaci zadáním **přihrádky\MSBuildSample**.

     **Ahoj, světe!** zpráva by měla být zobrazena.

## <a name="add-build-targets"></a>Přidání cílů sestavení

 Dále přidejte do souboru projektu další dva cíle takto:

- Cíl Clean, který odstraní staré soubory.

- Cíl znovu sestavit, `DependsOnTargets` který používá atribut k vynucení clean úlohy spustit před úlohou sestavení.

Teď, když máte více cílů, můžete nastavit cíl sestavení jako výchozí cíl.

### <a name="to-add-build-targets"></a>Přidání cílů sestavení

1. V souboru projektu přidejte tyto dva cíle hned za cíl sestavení:

    ```xml
    <Target Name="Clean" >
      <Delete Files="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    <Target Name="Rebuild" DependsOnTargets="Clean;Build" />
    ```

     Cíl Vyčistit vyvolá úlohu Delete k odstranění aplikace. Znovu sestavit cíl nelze spustit, dokud clean cíl a cíl sestavení spustit. Přestože cíl znovu sestavit nemá žádné úlohy, způsobí, že cíl Clean spustit před cíl sestavení.

2. Přidejte `DefaultTargets` tento atribut `Project` do počátečního prvku:

    ```xml
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    ```

     Tím nastavíte cíl sestavení jako výchozí cíl.

Soubor projektu by se nyní měl podobat následujícímu kódu:

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

 Můžete použít nové cíle sestavení k testování těchto funkcí souboru projektu:

- Vytváření výchozí sestavení.

- Nastavení názvu aplikace na příkazovém řádku.

- Odstranění aplikace před spuštěním jiné aplikace.

- Odstranění aplikace bez vytváření jiné aplikace.

### <a name="to-test-the-build-targets"></a>Testování cílů sestavení

1. Na příkazovém řádku zadejte **příkaz msbuild helloworld.csproj -p:AssemblyName=Greetings**.

     Vzhledem k tomu, že jste přepínač **-t** k explicitnímu nastavení cíle nepoužili, msbuild spustí výchozí cíl sestavení. Přepínač **-p** přepíše `AssemblyName` vlastnost a dá jí `Greetings`novou hodnotu . To způsobí, že nová aplikace *Greetings.exe*bude vytvořena ve složce *\Bin.\\ *

2. Chcete-li ověřit, zda složka *\\ \Bin* obsahuje aplikaci *MSBuildSample* i novou *aplikaci Pozdravy,* zadejte **dir Bin**.

3. Otestujte aplikaci Pozdravy zadáním **přihrádky\Pozdravy**.

     **Ahoj, světe!** zpráva by měla být zobrazena.

4. Odstraňte aplikaci MSBuildSample zadáním **příkazu msbuild helloworld.csproj -t:clean**.

     Tím spustí tečovou úlohu odebrání `AssemblyName` aplikace, `MSBuildSample`která má výchozí hodnotu vlastnosti .

5. Odstraňte aplikaci Pozdravy zadáním **příkazu msbuild helloworld.csproj -t:clean -p:AssemblyName=Greetings**.

     Tím spustí tečovou úlohu odebrání aplikace, která `Greetings`má danou hodnotu **vlastnosti AssemblyName** .

6. Chcete-li ověřit, zda je složka *\\ \Bin* nyní prázdná, zadejte **dir Bin**.

7. Zadejte **msbuild**.

     Přestože soubor projektu není zadán, MSBuild vytvoří soubor *helloworld.csproj,* protože v aktuální složce je pouze jeden soubor projektu. To způsobí, že aplikace *MSBuildSample* bude vytvořena ve složce *\Bin.\\ *

     Chcete-li ověřit, zda složka *\\ \Bin* obsahuje aplikaci *MSBuildSample,* zadejte **dir Bin**.

## <a name="build-incrementally"></a>Sestavení postupně

 MSBuild můžete říct, aby vytvořil cíl pouze v případě, že se změnily zdrojové soubory nebo cílové soubory, na kterých cíl závisí. MSBuild používá časové razítko souboru k určení, zda byl změněn.

### <a name="to-build-incrementally"></a>Chcete-li vytvořit postupně

1. V souboru projektu přidejte tyto atributy do počátečního cíle sestavení:

    ```xml
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"
    ```

     To určuje, že cíl sestavení závisí na vstupních `Compile` souborech, které jsou zadány ve skupině položek, a že výstupní cíl je soubor aplikace.

     Výsledný cíl sestavení by se měl podobat následujícímu kódu:

    ```xml
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />
    </Target>
    ```

2. Otestujte cíl sestavení zadáním **příkazu msbuild -v:d** na příkazovém řádku.

     Nezapomeňte, že *helloworld.csproj* je výchozí soubor projektu a že sestavení je výchozí cíl.

     Přepínač **-v:d** určuje podrobný popis procesu sestavení.

     Tyto řádky by měly být zobrazeny:

     **Přeskočení cíl "Build", protože všechny výstupní soubory jsou aktuální s ohledem na vstupní soubory.**

     **Vstupní soubory: HelloWorld.cs**

     **Výstupní soubory: BinMSBuildSample.exe**

     MSBuild přeskočí cíl sestavení, protože žádný ze zdrojových souborů se od posledního sestavení aplikace nezměnil.

## <a name="c-example"></a>Příklad jazyka C#

Následující příklad ukazuje soubor projektu, který zkompiluje aplikaci Jazyka C# a zaznamená zprávu, která obsahuje název výstupního souboru.

### <a name="code"></a>kód

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

## <a name="visual-basic-example"></a>Příklad jazyka Visual Basic

Následující příklad ukazuje soubor projektu, který zkompiluje aplikaci jazyka Visual Basic a zaznamená zprávu obsahující název výstupního souboru.

### <a name="code"></a>kód

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

 Visual Studio může automaticky provést většinu práce, která je zobrazena v tomto návodu. Informace o tom, jak pomocí sady Visual Studio vytvářet, upravovat, vytvářet a testovat soubory projektu MSBuild, naleznete [v tématu Návod: Použití msbuildu](../msbuild/walkthrough-using-msbuild.md).

## <a name="see-also"></a>Viz také

- [MSBuild – přehled](../msbuild/msbuild.md)
- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)

---
title: 'Návod: Vytvoření souboru projektu MSBuild od začátku | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, tutorial
ms.assetid: e3acff7c-cb4e-4ae1-8be2-a871bcff847b
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad32edc94bea49010dfb7073cacbd84419513783
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913888"
---
# <a name="walkthrough-creating-an-msbuild-project-file-from-scratch"></a>Návod: Vytvoření souboru projektu MSBuild od začátku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Programovací jazyky, které jsou cíleny rozhraní .NET Framework používají soubory projektu MSBuild k popisu a řízení procesu sestavení aplikace. Při použití sady Visual Studio k vytvoření souboru projektu MSBuild je odpovídající kód XML je automaticky přidán do souboru. Však může být pro vás užitečné porozumět uspořádání XML a jak můžete změnit, aby řídil sestavení.  
  
 Informace o vytváření souboru projektu pro projekt jazyka C++, naleznete v tématu [MSBuild (Visual C++)](http://msdn.microsoft.com/library/7a1be7ff-0312-4669-adf2-5f5bf507d560).  
  
 Tento návod ukazuje, jak vytvořit soubor základního projektu postupně pomocí textového editoru. Návod postupuje podle těchto kroků:  
  
- Vytvořte zdrojový soubor minimální aplikace.  
  
- Vytvořte minimální soubor projektu MSBuild.  
  
- Rozšiřte proměnnou prostředí PATH, aby zahrnovala nástroj MSBuild.  
  
- Sestavení aplikace pomocí souboru projektu.  
  
- Přidání vlastností do ovládacího prvku sestavení.  
  
- Řízení sestavení změnou hodnoty vlastnosti.  
  
- Přidání cílů pro sestavení.  
  
- Řízení sestavení určením cílů.  
  
- Přírůstkové sestavení.  
  
  Tento návod ukazuje, jak sestavit projekt na příkazovém řádku a zkontrolovat výsledky. Další informace o MSBuild a o způsobu spuštění MSBuild v příkazovém řádku naleznete v tématu [návod: použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
  Chcete-li dokončit tohoto průvodce, musíte mít rozhraní .NET Framework (verze 2.0, 3.5, 4.0 nebo 4.5) nainstalovat, protože obsahuje nástroj MSBuild a kompilátor Visual C#, které jsou požadovány v tomto návodu.  
  
## <a name="creating-a-minimal-application"></a>Vytvoření minimální aplikace  
 Tato část ilustruje způsob vytvoření minimální aplikace Visual C# aplikace zdrojový soubor pomocí textového editoru.  
  
#### <a name="to-create-the-minimal-application"></a>Vytvoření minimální aplikace  
  
1.  Na příkazovém řádku přejděte do složky, ve kterém chcete vytvořit aplikaci, například documents\ nebo \Desktop\\.  
  
2.  Typ **md HelloWorld** vytvořte podsložku s názvem \HelloWorld\\.  
  
3.  Typ **cd HelloWorld** přejdete do nové složky.  
  
4.  Spusťte Poznámkový blok nebo jiném textovém editoru a pak zadáním následujícího kódu.  
  
    ```  
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
  
5.  Uložte tento soubor zdrojového kódu a pojmenujte ho Helloworld.cs.  
  
6.  Sestavte aplikaci zadáním **csc helloworld.cs** příkazového řádku.  
  
7.  Otestujte aplikace zadáním **helloworld** příkazového řádku.  
  
     **Hello, world!** Zobrazí se zpráva.  
  
8.  Smazat aplikaci zadáním **del helloworld.exe** příkazového řádku.  
  
## <a name="creating-a-minimal-msbuild-project-file"></a>Vytváří se soubor minimálního projektu nástroje MSBuild  
 Teď, když máte zdrojový soubor minimální aplikace, můžete vytvořit minimální soubor projektu pro sestavení aplikace. Tento soubor projektu obsahuje následující prvky:  
  
-   Požadovaný kořenový `Project` uzlu.  
  
-   `ItemGroup` Uzel má obsahovat prvky položky.  
  
-   Prvek položky, který odkazuje na zdrojový soubor aplikace.  
  
-   A `Target` uzel obsahuje úkoly, které jsou nutné k vytvoření aplikace.  
  
-   A `Task` element spuštění kompilátoru Visual C# pro sestavení aplikace.  
  
#### <a name="to-create-a-minimal-msbuild-project-file"></a>Vytvořte minimální soubor projektu MSBuild  
  
1. V textovém editoru nahraďte existující text těmito dvěma řádky:  
  
   ```  
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   </Project>  
   ```  
  
2. Vložte tento `ItemGroup` uzel jako podřízený prvek `Project` uzlu:  
  
   ```  
   <ItemGroup>  
     <Compile Include="helloworld.cs" />  
   </ItemGroup>  
   ```  
  
    Všimněte si, že tento `ItemGroup` již obsahuje prvek položky.  
  
3. Přidat `Target` uzel jako podřízený prvek `Project` uzlu. Pojmenujte uzel `Build`.  
  
   ```  
   <Target Name="Build">  
   </Target>  
   ```  
  
4. Vložte tento prvek úkolu jako podřízený prvek `Target` uzlu:  
  
   ```  
   <Csc Sources="@(Compile)"/>  
   ```  
  
5. Uložte tento soubor projektu a pojmenujte ho Helloworld.csproj.  
  
   Váš soubor minimálního projektu by měl vypadat následovně:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
  </ItemGroup>  
  <Target Name="Build">  
    <Csc Sources="@(Compile)"/>    
  </Target>  
</Project>  
```  
  
 Úkoly v cíl sestavení jsou spouštěny postupně. V tomto případě kompilátor Visual C# `Csc` úkolu je jediným úkolem. Očekává seznam zdrojových souborů pro kompilaci, a ten je dán hodnotu `Compile` položky. `Compile` Položka odkazuje na právě jeden zdrojový soubor, Helloworld.cs.  
  
> [!NOTE]
>  V prvku položky můžete použít zástupný znak hvězdička (*) k odkazování na všechny soubory, které mají příponu názvu souboru .cs, takto:  
>   
>  `<Compile Include="*.cs" />`  
>   
>  Však nedoporučujeme použití zástupných znaků protože to ztěžuje ladění a selektivní Pokud jsou zdrojové soubory přidány nebo odstraněny.  
  
## <a name="extending-the-path-to-include-msbuild"></a>Rozšíření cesty, aby zahrnovala nástroj MSBuild  
 Před zpřístupněním MSBuild je třeba rozšířit proměnnou prostředí CESTU, aby zahrnovala složku rozhraní.NET Framework.  
  
#### <a name="to-add-msbuild-to-your-path"></a>Chcete-li přidat do cesty nástroje MSBuild  
  
-   Spouští se v sadě Visual Studio 2013, můžete najít MSBuild.exe ve složce nástroje MSBuild (`%ProgramFiles%\MSBuild` na 32bitové verzi operačního systému, nebo `%ProgramFiles(x86)%\MSBuild` na 64bitový operační systém).  
  
     Na příkazovém řádku zadejte **nastavit PATH=%PATH%;%ProgramFiles%\MSBuild** nebo **nastavte CESTU = % PATH %, % ProgramFiles (x86) %\MSBuild**.  
  
     Případně, pokud máte nainstalovanou sadu Visual Studio, můžete použít **příkazový řádek sady Visual Studio**, který obsahuje cestu obsahující složku nástroje MSBuild.  
  
## <a name="using-the-project-file-to-build-the-application"></a>Použití souboru projektu k sestavení aplikace  
 Teď pro sestavení aplikace pomocí souboru projektu, který jste právě vytvořili.  
  
#### <a name="to-build-the-application"></a>K sestavení aplikace  
  
1.  Na příkazovém řádku zadejte **msbuild helloworld.csproj /t:Build**.  
  
     To vytvoří cíl sestavení souboru projektu Helloworld vyvoláním kompilátoru Visual C# k vytvoření aplikace Helloworld.  
  
2.  Otestujte aplikace zadáním **helloworld**.  
  
     **Hello, world!** Zobrazí se zpráva.  
  
> [!NOTE]
>  Zobrazte podrobnosti o sestavení zvýšením úrovně podrobností. Pokud chcete nastavit úroveň podrobností na "podrobné", zadejte některý z těchto příkazů na příkazovém řádku:  
>   
>  **/ verbosity /t:Build helloworld.csproj MSBuild: podrobné**  
  
## <a name="adding-build-properties"></a>Přidání vlastností sestavení  
 Můžete přidat vlastnosti sestavení do souboru projektu k dalšímu řízení sestavení. Nyní přidejte tyto vlastnosti:  
  
-   `AssemblyName` Vlastnosti a určit název aplikace.  
  
-   `OutputPath` Vlastnosti k určení složky obsahující aplikaci.  
  
#### <a name="to-add-build-properties"></a>Přidání vlastností sestavení  
  
1. Smazat stávající aplikaci zadáním **del helloworld.exe** příkazového řádku.  
  
2. V souboru projektu vložte tento `PropertyGroup` ihned za úvodní prvek `Project` element:  
  
   ```  
   <PropertyGroup>  
     <AssemblyName>MSBuildSample</AssemblyName>  
     <OutputPath>Bin\</OutputPath>  
   </PropertyGroup>  
   ```  
  
3. Přidejte úkol do cíle sestavení, těsně před `Csc` úloh:  
  
   ```  
   <MakeDir Directories="$(OutputPath)"      Condition="!Exists('$(OutputPath)')" />  
   ```  
  
    `MakeDir` Úloh vytvoří složku s názvem definovaným `OutputPath` vlastnosti zadaná aktuálně neexistuje žádná složka s tímto názvem.  
  
4. Přidejte tuto `OutputAssembly` atribut `Csc` úloh:  
  
   ```  
   <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
   ```  
  
    Toto dá pokyn kompilátoru Visual C# k vytvoření sestavení, který je pojmenován podle `AssemblyName` vlastnost a vložit ho do složky, který je pojmenován podle `OutputPath` vlastnost.  
  
5. Uložte provedené změny.  
  
   Váš soubor projektu by měl nyní vypadat následovně:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <AssemblyName>MSBuildSample</AssemblyName>  
    <OutputPath>Bin\</OutputPath>  
  </PropertyGroup>  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
  </ItemGroup>  
  <Target Name="Build">  
    <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />  
    <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
  </Target>  
</Project>  
```  
  
> [!NOTE]
>  Doporučujeme, abyste přidali zpětné lomítko (\\) oddělovač cesty na konec názvu složky při jeho zadání v `OutputPath` element místo jeho přidání `OutputAssembly` atribut `Csc` úloh. Proto  
>   
>  `<OutputPath>Bin\</OutputPath>`  
>   
>  `OutputAssembly=="$(OutputPath)$(AssemblyName).exe" />`  
>   
>  je lepší než  
>   
>  `<OutputPath>Bin</OutputPath>`  
>   
>  `OutputAssembly=="$(OutputPath)\$(AssemblyName).exe" />`  
  
## <a name="testing-the-build-properties"></a>Testování vlastností sestavení  
 Teď můžete vytvářet aplikace pomocí souboru projektu, ve které jste použili vlastnosti sestavení k určení výstupní složky a názvu aplikace.  
  
#### <a name="to-test-the-build-properties"></a>Testování vlastností sestavení  
  
1.  Na příkazovém řádku zadejte **msbuild helloworld.csproj /t:Build**.  
  
     To vytvoří složku \Bin\ a poté vyvolá kompilátor Visual C# k vytvoření aplikace MSBuildSample a umístí do složky \Bin\.  
  
2.  Chcete-li ověřit, že byla složka \Bin\ vytvořena a zda obsahuje aplikaci MSBuildSample, zadejte **adresář Bin**.  
  
3.  Otestujte aplikace zadáním **Bin\MSBuildSample**.  
  
     **Hello, world!** Zobrazí se zpráva.  
  
## <a name="adding-build-targets"></a>Přidání cílů pro sestavení  
 V dalším kroku přidejte další dva cíle do souboru projektu následujícím způsobem:  
  
- Cíl čištění, který odstraní staré soubory.  
  
- Cíl opětovného sestavení, který používá `DependsOnTargets` atribut přinutit úkolu Vyčisti pro spuštění před úkolem sestavit.  
  
  Teď, když máte více cílů, lze nastavit cíl sestavení jako výchozí cíl.  
  
#### <a name="to-add-build-targets"></a>Přidání cílů pro sestavení  
  
1. V souboru projektu přidejte tyto dva cíle ihned za cíl sestavení:  
  
   ```  
   <Target Name="Clean" >  
     <Delete Files="$(OutputPath)$(AssemblyName).exe" />  
   </Target>  
   <Target Name="Rebuild" DependsOnTargets="Clean;Build" />  
   ```  
  
    Cíl vyčistit vyvolá úlohu odstranit pro odstranění aplikace. Cíl opětovného sestavení se nespustí, dokud nebude spuštění cíle vyčistit i cíl sestavení. Ačkoli cíl opětovného sestavení neobsahuje žádné úkoly, způsobí, že cílové cíl čištění se spustí před cílem sestavení.  
  
2. Přidejte tuto `DefaultTargets` atribut otevírací `Project` element:  
  
   ```  
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   ```  
  
    Tím se nastaví cíl sestavení jako výchozí cíl.  
  
   Váš soubor projektu by měl nyní vypadat následovně:  
  
```  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <AssemblyName>MSBuildSample</AssemblyName>  
    <OutputPath>Bin\</OutputPath>  
  </PropertyGroup>  
  <ItemGroup>  
    <Compile Include="helloworld.cs" />  
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
  
## <a name="testing-the-build-targets"></a>Testování cílů pro sestavení  
 Může zkoušet nové cíle sestavení k testování těchto funkcí souboru projektu:  
  
-   Vytváření výchozího sestavení.  
  
-   Nastavení názvu aplikace příkazového řádku.  
  
-   Odstranění aplikace před sestavením jiné aplikace.  
  
-   Odstranění aplikace bez sestavení jiné aplikace.  
  
#### <a name="to-test-the-build-targets"></a>Testování cílů pro sestavení  
  
1.  Na příkazovém řádku zadejte **msbuild helloworld.csproj /p:AssemblyName = Greetings**.  
  
     Vzhledem k tomu, že jste nepoužili **/t** přejděte k explicitnímu nastavení cíle, MSBuild spustí výchozí cíl sestavení. **/P** přepnout přepsání `AssemblyName` vlastnost a dává ji novou hodnotu `Greetings`. To způsobí, že nové aplikace, Greetings.exe, bude vytvořena ve složce \Bin\.  
  
2.  Chcete-li ověřit, zda složka \Bin\ obsahuje aplikaci MSBuildSample i novou aplikaci Greetings, zadejte **adresář Bin**.  
  
3.  Otestujte aplikaci Greetings zadáním **Bin\Greetings**.  
  
     **Hello, world!** Zobrazí se zpráva.  
  
4.  Odstraňte aplikaci msbuildsample zadáním **msbuild helloworld.csproj /t: vyčištění**.  
  
     To spustí úkolu Vyčisti pro odebrání aplikace, která má výchozí `AssemblyName` hodnota vlastnosti `MSBuildSample`.  
  
5.  Odstraňte aplikaci Greetings zadáním **msbuild helloworld.csproj /t: Vyčištění /p:AssemblyName = Greetings**.  
  
     To spustí úkolu Vyčisti pro odebrání aplikace, která má daném **AssemblyName** hodnota vlastnosti `Greetings`.  
  
6.  Ověřte, zda složka \Bin\ nyní prázdná, zadejte **adresář Bin**.  
  
7.  Typ **msbuild**.  
  
     I když není zadaný soubor projektu, MSBuild vytvoří vytvoří soubor helloworld.csproj, protože existuje pouze jeden soubor projektu v aktuální složce. To způsobí, že aplikace MSBuildSample bude vytvořena ve složce \Bin\.  
  
     Chcete-li ověřit, zda složka \Bin\ obsahuje aplikaci msbuildsample, zadejte **adresář Bin**.  
  
## <a name="building-incrementally"></a>Přírůstkové sestavování  
 Poznáte, MSBuild, aby vytvořil cíl pouze v případě, že zdrojové soubory nebo cílové soubory, které je cíl závislý, byly změněny. Nástroj MSBuild používá časové razítko souboru k určení, zda byla změněna.  
  
#### <a name="to-build-incrementally"></a>Přírůstkové sestavování  
  
1.  V souboru projektu přidejte tyto atributy do úvodního cíle sestavení:  
  
    ```  
    Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe"  
    ```  
  
     Toto nastavení určuje, že cíl sestavení závisí na vstupních souborech, které jsou určené v `Compile` skupiny položek a že cíl výstupu je soubor aplikace.  
  
     Cíl výsledného sestavení by měl vypadat následovně:  
  
    ```  
    <Target Name="Build" Inputs="@(Compile)" Outputs="$(OutputPath)$(AssemblyName).exe">  
      <MakeDir Directories="$(OutputPath)" Condition="!Exists('$(OutputPath)')" />  
      <Csc Sources="@(Compile)" OutputAssembly="$(OutputPath)$(AssemblyName).exe" />  
    </Target>  
    ```  
  
2.  Otestujte cíl sestavení zadáním **msbuild /v:d** příkazového řádku.  
  
     Mějte na paměti, že helloworld.csproj je výchozí soubor projektu a toto sestavení je výchozí cíl.  
  
     **/V:d** přepínač určuje podrobný popis procesu sestavení.  
  
     Tyto řádky by měly být zobrazeny:  
  
     **Cíl "Sestavení" přeskakuje, protože všechny výstupní soubory jsou aktuální s ohledem na vstupní soubory.**  
  
     **Vstupní soubory: HelloWorld.cs**  
  
     **Výstupní soubory: BinMSBuildSample.exe**  
  
     MSBuild vynechává cíl sestavení, protože žádné zdrojové soubory byly změněny od poslední byla vytvořena aplikace.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje soubor projektu, který se zkompiluje [!INCLUDE[csprcs](../includes/csprcs-md.md)] aplikace a zaznamená zprávu, která obsahuje název výstupního souboru.  
  
### <a name="code"></a>Kód  
  
```csharp  
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
  
### <a name="comments"></a>Komentáře  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje soubor projektu, který se zkompiluje [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] aplikace a zaznamená zprávu, která obsahuje název výstupního souboru.  
  
### <a name="code"></a>Kód  
  
```vb  
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
  
## <a name="whats-next"></a>Co se chystá?  
 Visual Studio může automaticky provést mnoho práce, která je uvedena v tomto návodu. Zjistěte, jak vytvářet, upravovat, vytvářet a testovat soubory projektu MSBuild pomocí sady Visual Studio, najdete v článku [návod: použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
## <a name="see-also"></a>Viz také  
[Přehled nástroje MSBuild](msbuild.md)  
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)



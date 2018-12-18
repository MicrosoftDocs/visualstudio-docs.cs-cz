---
title: 'Návod: Vytvoření vložené úlohy | Dokumentace Microsoftu'
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
- MSBuild, tasks
ms.assetid: 438194cb-668c-41a9-a7e2-c118d14c1ea7
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a399e8285b7b041488a4cecdf2007f8fd1647b2d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49840712"
---
# <a name="walkthrough-creating-an-inline-task"></a>Návod: Vytvoření vložené úlohy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Úlohy nástroje MSBuild se obvykle vytvářejí kompilováním třídy, která implementuje <xref:Microsoft.Build.Framework.ITask> rozhraní. Od verze rozhraní .NET Framework verze 4, můžete vytvořit úlohy vložené v souboru projektu. Není nutné vytvořit samostatné sestavení pro hostování úkolu. Další informace najdete v tématu [vložené úlohy](../msbuild/msbuild-inline-tasks.md).  
  
 Tento návod ukazuje, jak vytvářet a spouštět tyto vložené úlohy:  
  
- Úloha, která nemá žádné vstupní nebo výstupní parametry.  
  
- Úloha, která má jeden vstupní parametr a žádné výstupní parametry.  
  
- Úloha, která má dva vstupní parametry a jednu výstupní parametr, který vrátí vlastnost MSBuild.  
  
- Úloha, která má dva vstupní parametry a jednu výstupní parametr, který vrací položky nástroje MSBuild.  
  
  Vytvoření a spuštění úloh, pomocí sady Visual Studio a **Visual Studio okno příkazového řádku**, následujícím způsobem:  
  
- Vytvoření souboru projektu MSBuild pomocí sady Visual Studio.  
  
- Upravte soubor projektu v sadě Visual Studio k vytvoření vložené úlohy.  
  
- Použití **okno příkazového řádku** se projekt sestavil a podívejte se na výsledky.  
  
## <a name="creating-and-modifying-an-msbuild-project"></a>Vytvoření a úprava projektu MSBuild  
 Systém projektu sady Visual Studio je založen na MSBuild. Proto můžete vytvořit soubor projektu sestavení s použitím sady Visual Studio. V této části vytvoříte soubor projektu Visual C#. (Místo toho je můžete vytvořit soubor projektu jazyka Visual Basic. V rámci tohoto kurzu rozdíl mezi dvěma projektu soubory je menší.)  
  
#### <a name="to-create-and-modify-a-project-file"></a>K vytvoření a úprava souboru projektu  
  
1.  V sadě Visual Studio na **souboru** nabídky, klikněte na tlačítko **nový** a potom klikněte na tlačítko **projektu**.  
  
2.  V **nový projekt** dialogovém okně Visual C# typ projektu a pak vyberte **formulářová aplikace Windows** šablony. V **název** zadejte `InlineTasks`. Zadejte **umístění** pro řešení, například `D:\`. Ujistěte se, že **vytvořit adresář pro řešení** je vybrána, **přidat do správy zdrojových kódů** zaškrtnuté není, a **název řešení** je `InlineTasks`.  
  
     Klikněte na tlačítko **OK** k vytvoření souboru projektu.  
  
3.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu InlineTasks a potom klikněte na tlačítko **uvolnit projekt**.  
  
4.  Znovu klikněte pravým tlačítkem na uzel projektu a pak klikněte na tlačítko **upravit InlineTasks.csproj**.  
  
     Soubor projektu se zobrazí v editoru kódu.  
  
## <a name="adding-a-basic-hello-task"></a>Přidání úkolu základní Hello  
 Teď přidejte do souboru projektu základní úlohy, která zobrazí zprávu "Hello, world!" Přidejte také výchozí cíl TestBuild k vyvolání úlohy.  
  
#### <a name="to-add-a-basic-hello-task"></a>Základní hello úkol má přidat  
  
1. V kořenovém adresáři `Project` uzlu, změna `DefaultTargets` atribut `TestBuild`. Výsledná `Project` uzlu by měl podobat tomuto příkladu:  
  
    `<Project ToolsVersion="4.0" DefaultTargets="TestBuild" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">`  
  
2. Přidejte následující vložené úlohy a zacílit těsně před soubor projektu `</Project>` značky.  
  
   ```  
   <UsingTask TaskName="Hello" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
     <ParameterGroup />  
     <Task>  
       <Code Type="Fragment" Language="cs">  
         Log.LogMessage("Hello, world!", MessageImportance.High);  
       </Code>  
     </Task>  
   </UsingTask>  
   <Target Name="TestBuild">  
     <Hello />  
   </Target>  
   ```  
  
3. Uložte soubor projektu.  
  
   Tento kód vytvoří vložené úlohy, která je s názvem Hello a nemá žádné parametry, odkazy, nebo `Using` příkazy. Hello úloha obsahuje jen jeden řádek kódu, která zobrazuje zprávu hello v zařízení výchozí protokolování, obvykle v okně konzoly.  
  
### <a name="running-the-hello-task"></a>Spuštění úlohy Hello  
 Spustit nástroj MSBuild s použitím **okno příkazového řádku** k sestavení kompletních Hello úloh a ke zpracování, která jej volá cíl TestBuild.  
  
##### <a name="to-run-the-hello-task"></a>Ke spuštění úlohy Hello  
  
1. Klikněte na tlačítko **Start**, klikněte na tlačítko **všechny programy**a potom vyhledejte **Visual Studio Tools** složky a klikněte na tlačítko **příkazový řádek sady Visual Studio**.  
  
2. V **okno příkazového řádku**, vyhledejte složku, která obsahuje soubor projektu, v tomto případě D:\InlineTasks\InlineTasks\\.  
  
3. Typ **msbuild** bez přepínače příkaz a stiskněte klávesu ENTER. Ve výchozím nastavení vytvoří soubor InlineTasks.csproj a zpracovává výchozí cíl TestBuild, která vyvolá úlohu Hello.  
  
4. Prohlédněte si výstup v **okno příkazového řádku**. Zobrazí se tento řádek:  
  
    `Hello, world!`  
  
   > [!NOTE]
   >  Pokud se nezobrazí zpráva hello, zkuste to znovu uložit soubor projektu a pak spusťte úlohu Hello.  
  
   Podle střídavě editoru kódu a **okno příkazového řádku**, můžete změnit soubor projektu a rychle zobrazit výsledky.  
  
## <a name="defining-the-echo-task"></a>Definování úkolů Echo  
 Vytvoření vložené úlohy, která přijímá řetězcový parametr a zobrazí řetězec na výchozí protokolování zařízení.  
  
#### <a name="to-define-the-echo-task"></a>K definování úkolů Echo  
  
1. V editoru kódu nahraďte Hello úloh a cíl TestBuild pomocí následujícího kódu.  
  
   ```  
   <UsingTask TaskName="Echo" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
     <ParameterGroup>  
       <Text Required="true" />  
     </ParameterGroup>  
     <Task>  
       <Code Type="Fragment" Language="cs">  
         Log.LogMessage(Text, MessageImportance.High);  
       </Code>  
     </Task>  
   </UsingTask>  
   <Target Name="TestBuild">  
     <Echo Text="Greetings!" />  
   </Target>  
   ```  
  
2. V **okno příkazového řádku**, typ **msbuild** bez přepínače příkaz a stiskněte klávesu ENTER. Ve výchozím nastavení to zpracuje výchozí cíl TestBuild, která vyvolá úlohu odezvu.  
  
3. Prohlédněte si výstup v **okno příkazového řádku**. Zobrazí se tento řádek:  
  
    `Greetings!`  
  
   Tento kód definuje vložené úlohy, který má název odezvu a vyžaduje právě jeden vstupní parametr textu. Ve výchozím nastavení jsou parametry typu System.String. Hodnota parametru Text je nastavena při cíl TestBuild vyvolá úlohu odezvu.  
  
## <a name="defining-the-adder-task"></a>Definování přidávání úloh  
 Vytvoření vložené úlohy, který přidá dva celočíselné parametry a jejich součet jako vlastnost MSBuild generuje.  
  
#### <a name="to-define-the-adder-task"></a>Chcete-li definovat přidávání úloh  
  
1. V editoru kódu nahraďte Echo úloh a cíl TestBuild pomocí následujícího kódu.  
  
   ```  
   <UsingTask TaskName="Adder" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
     <ParameterGroup>  
       <A ParameterType="System.Int32" Required="true" />  
       <B ParameterType="System.Int32" Required="true" />  
       <C ParameterType="System.Int32" Output="true" />  
     </ParameterGroup>  
     <Task>  
       <Code Type="Fragment" Language="cs">  
         C = A + B;  
       </Code>  
     </Task>  
   </UsingTask>    
   <Target Name="TestBuild">  
     <Adder A="4" B="5">  
       <Output PropertyName="Sum" TaskParameter="C" />  
     </Adder>  
     <Message Text="The sum is $(Sum)" Importance="High" />  
   </Target>  
   ```  
  
2. V **okno příkazového řádku**, typ **msbuild** bez přepínače příkaz a stiskněte klávesu ENTER. Ve výchozím nastavení to zpracuje výchozí cíl TestBuild, která vyvolá úlohu odezvu.  
  
3. Prohlédněte si výstup v **okno příkazového řádku**. Zobrazí se tento řádek:  
  
    `The sum is 9`  
  
   Tento kód definuje vložené úlohy, který je pojmenován modul sčítání a má dvě požadované vstupní parametry celé číslo, A a B, a jeden celočíselný výstupní parametr, C. Přidávání úloh přidá dva vstupní parametry a vrátí součet výstupní parametr. Součet je vygenerován jako vlastnost MSBuild `Sum`. Hodnoty vstupních parametrů jsou nastavené, když cíl TestBuild vyvolá úlohu přidávání.  
  
## <a name="defining-the-regx-task"></a>Definování úkolů RegX  
 Vytvoření vložené úlohy, která přijímá skupinu položek a regulárních výrazů a vrátí seznam všech položek, které mají obsah souboru, který odpovídá výrazu.  
  
#### <a name="to-define-the-regx-task"></a>K definování úkolů RegX  
  
1. V editoru kódu nahraďte TestBuild cíl a přidávání úloh pomocí následujícího kódu.  
  
   ```  
   <UsingTask TaskName="RegX" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
     <ParameterGroup>  
       <Expression Required="true" />  
       <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />  
       <Result ParameterType="Microsoft.Build.Framework.ITaskItem[]" Output="true" />  
     </ParameterGroup>  
     <Task>  
       <Using Namespace="System.Text.RegularExpressions"/>  
       <Code Type="Fragment" Language="cs">  
   <![CDATA[  
         if (Files.Length > 0)  
         {  
           Result = new TaskItem[Files.Length];  
           for (int i = 0; i < Files.Length; i++)  
           {  
             ITaskItem item = Files[i];  
             string path = item.GetMetadata("FullPath");  
             using(StreamReader rdr = File.OpenText(path))  
             {  
               if (Regex.Match(rdr.ReadToEnd(), Expression).Success)  
               {  
                 Result[i] = new TaskItem(item.ItemSpec);  
               }  
             }  
           }  
         }  
   ]]>  
       </Code>  
     </Task>  
   </UsingTask>    
   <Target Name="TestBuild">  
     <RegX Expression="public|protected" Files="@(Compile)">  
       <Output ItemName="MatchedFiles" TaskParameter="Result" />  
     </RegX>  
     <Message Text="Input files: @(Compile)" Importance="High" />  
     <Message Text="Matched files: @(MatchedFiles)" Importance="High" />  
   </Target>  
   ```  
  
2. V **okno příkazového řádku**, typ **msbuild** bez přepínače příkaz a stiskněte klávesu ENTER. Ve výchozím nastavení to zpracuje TestBuild, která vyvolá úlohu RegX výchozí cíl.  
  
3. Prohlédněte si výstup v **okno příkazového řádku**. Měli byste vidět tyto řádky:  
  
    `Input files: Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs`  
  
    `Matched files: Form1.cs;Form1.Designer.cs;Properties\Settings.Designer.cs`  
  
   Tento kód definuje vložené úlohy, která má název RegX a má tyto tři parametry:  
  
- `Expression` je vstupní parametr vyžaduje řetězec, který má hodnotu, která je regulární výraz odpovídat. V tomto příkladu výraz odpovídá slovům, "public" nebo "chráněné".  
  
- `Files` je vstupní parametr požadovanou položku seznamu, který má hodnotu, která je seznam souborů, které mají hledat shody. V tomto příkladu `Files` nastavena `Compile` položku, která obsahuje zdrojové soubory projektu.  
  
- `Result` je výstupní parametr, který má hodnotu, která je seznam souborů, které mají obsah, které odpovídají regulárnímu výrazu.  
  
  Hodnota vstupní parametry jsou nastaveny při cíl TestBuild vyvolá úlohu RegX. Úloha RegX přečte každý soubor a vrátí seznam souborů, které odpovídají regulárnímu výrazu. Tento seznam se vrátí jako `Result` výstupní parametr, který je vygenerován jako položky nástroje MSBuild `MatchedFiles`.  
  
### <a name="handling-reserved-characters"></a>Zpracování vyhrazené znaky  
 Analyzátor MSBuild zpracovává vložené úlohy jako XML. Znaky, které obsahují rezervované význam ve formátu XML, třeba "\<" a ">", jsou zjištěny a zpracovávány jako by byly XML a ne zdrojový kód .NET. Zahrnout vyhrazené znaky výrazů v kódu, jako `Files.Length > 0`, zapisovat `Code` element tak, aby se jeho obsah obsažených ve výrazu CDATA následujícím způsobem:  
  
 `<Code Type="Fragment" Language="cs">`  
  
 `<![CDATA[`  
  
 `// Your code goes here.`  
  
 `]]>`  
  
 `</Code>`  
  
## <a name="see-also"></a>Viz také  
 [Vložené úlohy](../msbuild/msbuild-inline-tasks.md)   
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Cíle](../msbuild/msbuild-targets.md)




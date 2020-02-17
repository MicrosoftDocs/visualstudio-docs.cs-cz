---
title: 'Návod: Vytvoření vložené úlohy | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
- MSBuild, tasks
ms.assetid: 438194cb-668c-41a9-a7e2-c118d14c1ea7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d5c40af3e60add88948f8f1c5c36abf3b980eca
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271173"
---
# <a name="walkthrough-create-an-inline-task"></a>Návod: Vytvoření vložené úlohy
Úlohy nástroje MSBuild jsou obvykle vytvořeny kompilací třídy, která implementuje rozhraní <xref:Microsoft.Build.Framework.ITask>. Počínaje verzí .NET Framework 4 můžete vytvořit úlohy vložené do souboru projektu. Pro hostování úlohy není nutné vytvářet samostatné sestavení. Další informace najdete v tématu [vložené úkoly](../msbuild/msbuild-inline-tasks.md).

 Tento návod ukazuje, jak vytvořit a spustit tyto vložené úkoly:

- Úloha, která nemá žádné vstupní ani výstupní parametry.

- Úkol, který má jeden vstupní parametr a žádné výstupní parametry.

- Úkol, který má dva vstupní parametry a jeden výstupní parametr, který vrací vlastnost MSBuild.

- Úkol, který má dva vstupní parametry a jeden výstupní parametr, který vrací položku MSBuild.

Chcete-li vytvořit a spustit úlohy, použijte aplikaci Visual Studio a **okno příkazového řádku sady Visual Studio**následujícím způsobem:

1. Pomocí sady Visual Studio vytvořte soubor projektu MSBuild.

2. Úpravou souboru projektu v aplikaci Visual Studio vytvořte vloženou úlohu.

3. Pomocí **okna příkazového řádku** Sestavte projekt a prověřte výsledky.

## <a name="create-and-modify-an-msbuild-project"></a>Vytvoření a úprava projektu MSBuild
 Systém projektu sady Visual Studio je založen na nástroji MSBuild. Proto můžete vytvořit soubor projektu sestavení pomocí sady Visual Studio. V této části vytvoříte soubor projektu Visual C# . (Místo toho můžete vytvořit soubor projektu Visual Basic. V kontextu tohoto kurzu je rozdíl mezi dvěma soubory projektu nepatrný.)

#### <a name="to-create-and-modify-a-project-file"></a>Vytvoření a úprava souboru projektu

1. V aplikaci Visual Studio v nabídce **soubor** klikněte na položku **Nový** a poté klikněte na možnost **projekt**.

2. V dialogovém okně **Nový projekt** vyberte  **C# typ projektu a** pak vyberte šablonu **aplikace model Windows Forms** . Do pole **Název** zadejte `InlineTasks`. Zadejte **umístění** pro řešení, například *D:\\* . Ujistěte se, že je vybraná možnost **vytvořit adresář pro řešení** , je zrušené **přidání do správy zdrojového kódu** a **název řešení** je **InlineTasks**.

3. Kliknutím na tlačítko **OK** vytvořte soubor projektu.

3. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu **InlineTasks** a poté klikněte na položku **Uvolnit projekt**.

4. Znovu klikněte pravým tlačítkem myši na uzel projektu a pak klikněte na **Upravit InlineTasks. csproj**.

     Soubor projektu se zobrazí v editoru kódu.

## <a name="add-a-basic-hello-task"></a>Přidat základní úlohu Hello
 Nyní přidejte do souboru projektu základní úlohu, která zobrazí zprávu "Hello, World!" Přidejte také výchozí cíl TestBuild k vyvolání úlohy.

#### <a name="to-add-a-basic-hello-task"></a>Přidání základní úlohy Hello

1. V uzlu root `Project` změňte atribut `DefaultTargets` na `TestBuild`. Výsledný uzel `Project` by měl vypadat podobně jako v tomto příkladu:

   ```xml
   <Project ToolsVersion="4.0" DefaultTargets="TestBuild" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   ```

2. Přidejte následující vloženou úlohu a cíl do souboru projektu těsně před značku `</Project>`.

   ```xml
   <UsingTask TaskName="Hello" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup />
     <Task>
       <Code Type="Fragment" Language="cs">
         Log.LogMessage(MessageImportance.High, "Hello, world!");
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Hello />
   </Target>
   ```

3. Uložte soubor projektu.

   Tento kód vytvoří vloženou úlohu s názvem Hello a nemá žádné parametry, odkazy ani direktivy `Using`. Úloha Hello obsahuje pouze jeden řádek kódu, který zobrazuje zprávu Hello na výchozím protokolovacím zařízení, obvykle okno konzoly.

### <a name="run-the-hello-task"></a>Spustit úlohu Hello
 Spusťte nástroj MSBuild pomocí **okna příkazového řádku** k vytvoření úlohy Hello a zpracování cíle TestBuild, který ho vyvolá.

##### <a name="to-run-the-hello-task"></a>Spuštění úlohy Hello

1. Klikněte na tlačítko **Start**, klikněte na **všechny programy**a vyhledejte složku **Visual Studio Tools** a klikněte na **příkazový řádek sady Visual Studio**.

2. V **okně příkazového řádku**Najděte složku, která obsahuje soubor projektu, v tomto případě *D:\InlineTasks\InlineTasks\\* .

3. Zadejte **MSBuild** bez přepínačů příkazů a potom stiskněte klávesu **ENTER**. Ve výchozím nastavení vytvoří soubor *InlineTasks. csproj* a zpracuje výchozí cílový TestBuild, který vyvolá úlohu Hello.

4. Projděte si výstup v **okně příkazového řádku**. Měl by se zobrazit tento řádek:

    `Hello, world!`

   > [!NOTE]
   > Pokud se nezobrazí zpráva Hello, zkuste soubor projektu uložit znovu a potom spusťte úlohu Hello.

   Pomocí střídání mezi editorem kódu a **oknem příkazového řádku**můžete změnit soubor projektu a rychle zobrazit výsledky.

## <a name="define-the-echo-task"></a>Definovat úlohu s odezvou
 Vytvoří vloženou úlohu, která přijme parametr řetězce a zobrazí řetězec na výchozím protokolovacím zařízení.

#### <a name="to-define-the-echo-task"></a>Definování úlohy s odezvou

1. V editoru kódu nahraďte Task Hello a target TestBuild pomocí následujícího kódu.

   ```xml
   <UsingTask TaskName="Echo" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <Text Required="true" />
     </ParameterGroup>
     <Task>
       <Code Type="Fragment" Language="cs">
         Log.LogMessage(MessageImportance.High, Text);
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Echo Text="Greetings!" />
   </Target>
   ```

2. V **okně příkazového řádku**zadejte **MSBuild** bez přepínačů příkazů a potom stiskněte klávesu **ENTER**. Ve výchozím nastavení tato operace zpracovává výchozí cílový TestBuild, který vyvolá úlohu echo.

3. Projděte si výstup v **okně příkazového řádku**. Měl by se zobrazit tento řádek:

    `Greetings!`

   Tento kód definuje vloženou úlohu s názvem echo a má pouze jeden povinný text vstupního parametru. Ve výchozím nastavení jsou parametry typu System. String. Hodnota parametru text je nastavena, když cíl TestBuild vyvolá úlohu echo.

## <a name="define-the-adder-task"></a>Definovat úlohu přidávání
 Vytvořte vloženou úlohu, která přidá dva celočíselné parametry a vygeneruje jejich součet jako vlastnost MSBuild.

#### <a name="to-define-the-adder-task"></a>Definování úlohy přidávání

1. V editoru kódu nahraďte úlohu echo a cíl TestBuild pomocí následujícího kódu.

   ```xml
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

2. V **okně příkazového řádku**zadejte **MSBuild** bez přepínačů příkazů a potom stiskněte klávesu **ENTER**. Ve výchozím nastavení tato operace zpracovává výchozí cílový TestBuild, který vyvolá úlohu echo.

3. Projděte si výstup v **okně příkazového řádku**. Měl by se zobrazit tento řádek:

    `The sum is 9`

   Tento kód definuje vloženou úlohu s názvem "přidávání" a má dva požadované celočíselné vstupní parametry, a a B a jeden celočíselný výstupní parametr, C. Úloha přidávání přidá dva vstupní parametry a vrátí součet v parametru Output. Součet je vygenerován jako vlastnost MSBuild `Sum`. Hodnoty vstupních parametrů se nastaví, když cíl TestBuild vyvolá úlohu přidávání.

## <a name="define-the-regx-task"></a>Definování úlohy RegX
 Vytvořte vloženou úlohu, která přijímá skupinu položek a regulární výraz, a vrátí seznam všech položek, které mají obsah souboru odpovídající výrazu.

#### <a name="to-define-the-regx-task"></a>Definování úlohy RegX

1. V editoru kódu nahraďte úlohu přidávání a cíl TestBuild pomocí následujícího kódu.

   ```xml
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

2. V **okně příkazového řádku**zadejte **MSBuild** bez přepínačů příkazů a potom stiskněte klávesu **ENTER**. Ve výchozím nastavení tato operace zpracovává výchozí cílový TestBuild, který vyvolá úlohu RegX.

3. Projděte si výstup v **okně příkazového řádku**. Měli byste vidět tyto řádky:

   ```
   Input files: Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
   ```

   ```
   Matched files: Form1.cs;Form1.Designer.cs;Properties\Settings.Designer.cs
   ```

   Tento kód definuje vloženou úlohu s názvem RegX a má tyto tři parametry:

- `Expression` je povinný vstupní parametr řetězce, který má hodnotu, která je regulárním výrazem, který se má shodovat. V tomto příkladu se výraz shoduje se slovy "public" nebo "protected".

- `Files` je požadovaný vstupní parametr seznamu položek, který obsahuje hodnotu, která je seznamem souborů, ve kterých se má vyhledat shoda. V tomto příkladu je `Files` nastaveno na položku `Compile`, která obsahuje zdrojové soubory projektu.

- `Result` je výstupní parametr, jehož hodnota je seznam souborů, které mají obsah odpovídající regulárnímu výrazu.

  Hodnota vstupních parametrů je nastavena, když cíl TestBuild vyvolá úlohu RegX. Úloha RegX načte všechny soubory a vrátí seznam souborů, které odpovídají regulárnímu výrazu. Tento seznam je vrácen jako výstupní parametr `Result`, který je generován jako položka MSBuild `MatchedFiles`.

### <a name="handle-reserved-characters"></a>Zpracovat vyhrazené znaky
 Analyzátor MSBuild zpracovává vložené úkoly jako XML. Znaky, které mají rezervované významy v jazyce XML, například "\<" a ">", jsou zjišťovány a zpracovávány, jako kdyby byly XML, a nikoli zdrojový kód .NET. Chcete-li zahrnout rezervované znaky do výrazů kódu, jako je například `Files.Length > 0`, zapište `Code` element tak, aby jeho obsah byl obsažen ve výrazu CDATA následujícím způsobem:

 ```xml
<Code Type="Fragment" Language="cs">
  <![CDATA[

  // Your code goes here.

  ]]>
</Code>
```

## <a name="see-also"></a>Viz také
- [Vložené úkoly](../msbuild/msbuild-inline-tasks.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Cíle](../msbuild/msbuild-targets.md)

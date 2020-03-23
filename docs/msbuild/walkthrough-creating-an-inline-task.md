---
title: 'Návod: Vytvoření vložkového úkolu | Dokumenty společnosti Microsoft'
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
ms.openlocfilehash: 70ce19a6dcd9c61b0e14d0d88c52072f59f87fb9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631156"
---
# <a name="walkthrough-create-an-inline-task"></a>Návod: Vytvoření vřádkové úlohy

Úlohy MSBuild jsou obvykle vytvořeny kompilací třídy, která implementuje <xref:Microsoft.Build.Framework.ITask> rozhraní. Počínaje rozhraním .NET Framework verze 4 můžete vytvořit úkoly vsazené do souboru projektu. Není třeba vytvořit samostatné sestavení pro hostování úkolu. Další informace naleznete [v tématu Inline tasks](../msbuild/msbuild-inline-tasks.md).

 Tento návod ukazuje, jak vytvořit a spustit tyto vložkové úlohy:

- Úloha, která nemá žádné vstupní nebo výstupní parametry.

- Úloha, která má jeden vstupní parametr a žádné výstupní parametry.

- Úloha, která má dva vstupní parametry a jeden výstupní parametr, který vrací vlastnost MSBuild.

- Úloha, která má dva vstupní parametry a jeden výstupní parametr, který vrací položku MSBuild.

Chcete-li vytvořit a spustit úlohy, použijte Visual Studio a **okno příkazového řádku sady Visual Studio**takto:

1. Vytvořte soubor projektu MSBuild pomocí sady Visual Studio.

2. Upravte soubor projektu v sadě Visual Studio a vytvořte vázavý úkol.

3. Pomocí **okna příkazového řádku** vytvořte projekt a prozkoumejte výsledky.

## <a name="create-and-modify-an-msbuild-project"></a>Vytvoření a úprava projektu MSBuild

 Systém projektu sady Visual Studio je založen na msbuild. Proto můžete vytvořit soubor projektu sestavení pomocí sady Visual Studio. V této části vytvoříte soubor projektu Visual C#. (Místo toho můžete vytvořit soubor projektu jazyka Visual Basic. V kontextu tohoto kurzu je rozdíl mezi dvěma soubory projektu menší.)

#### <a name="to-create-and-modify-a-project-file"></a>Vytvoření a úprava souboru projektu

1. V sadě Visual Studio vytvořte nový projekt pomocí šablony aplikace C# **Windows Forms Application.** Do pole **Název** zadejte `InlineTasks`. Zadejte **umístění** řešení, například *D:\\*. Ujistěte se, že je vybraná volba **Vytvořit adresář pro řešení,** **možnost Přidat do správy zdrojového kódu** není zaškrtnuta a název **řešení** je **InlineTasks**.

3. Chcete-li vytvořit soubor projektu, klepněte na tlačítko **OK.**

3. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu **InlineTasks** a potom klepněte na příkaz **Uvolnit projekt**.

4. Znovu klikněte pravým tlačítkem myši na uzel projektu a potom klikněte na **příkaz Upravit inlineTasks.csproj**.

     Soubor projektu se zobrazí v editoru kódu.

## <a name="add-a-basic-hello-task"></a>Přidání základní úlohy Hello

 Nyní přidejte do souboru projektu základní úkol, který zobrazuje zprávu "Hello, world!" Přidejte také výchozí cíl TestBuild k vyvolání úlohy.

#### <a name="to-add-a-basic-hello-task"></a>Přidání základní úlohy Hello

1. V kořenovém `Project` uzlu `DefaultTargets` změňte `TestBuild`atribut na . Výsledný `Project` uzel by se měl podobat tomuto příkladu:

   ```xml
   <Project ToolsVersion="4.0" DefaultTargets="TestBuild" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   ```

2. Přidejte následující vktonový úkol a cíl `</Project>` do souboru projektu těsně před značku.

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

   Tento kód vytvoří vsazený úkol s názvem Hello a `Using` nemá žádné parametry, odkazy nebo direktivy. Úloha Hello obsahuje pouze jeden řádek kódu, který zobrazuje zprávu hello na výchozím zařízení protokolování, obvykle v okně konzoly.

### <a name="run-the-hello-task"></a>Spuštění úlohy Hello

 Spusťte MSBuild pomocí **okna příkazového řádku** k vytvoření úlohy Hello a ke zpracování cíle TestBuild, který jej vyvolá.

##### <a name="to-run-the-hello-task"></a>Spuštění úlohy Hello

1. Klepněte na tlačítko **Start**, klepněte na **položku Všechny programy**, vyhledejte složku Nástroje sady **Visual Studio** a klepněte na **příkazový řádek sady Visual Studio**.

2. V **okně příkazového řádku**vyhledejte složku obsahující soubor projektu, v tomto případě *\\D:\InlineTasks\InlineTasks*.

3. Zadejte **příkaz msbuild** bez přepínačů příkazů a stiskněte **klávesu Enter**. Ve výchozím nastavení se staví *soubor InlineTasks.csproj* a zpracuje výchozí cíl TestBuild, který vyvolá úlohu Hello.

4. Zkontrolujte výstup v **okně příkazového řádku**. Měli byste vidět tento řádek:

    `Hello, world!`

   > [!NOTE]
   > Pokud se zpráva Hello nezobrazí, zkuste znovu uložit soubor projektu a spusťte úlohu Hello.

   Střídáním mezi editorem kódu a **oknem příkazového řádku**můžete změnit soubor projektu a rychle zobrazit výsledky.

## <a name="define-the-echo-task"></a>Definování úlohy Ozvěna

 Vytvořte vložkou úlohu, která přijme parametr řetězce a zobrazí řetězec na výchozím zařízení pro protokolování.

#### <a name="to-define-the-echo-task"></a>Definování úlohy Echo

1. V editoru kódu nahraďte cíl úlohy Hello a TestBuild pomocí následujícího kódu.

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

2. V **okně příkazového řádku**zadejte **příkaz msbuild** bez přepínačů příkazů a stiskněte **klávesu Enter**. Ve výchozím nastavení to zpracuje výchozí cíl TestBuild, který vyvolá úlohu Echo.

3. Zkontrolujte výstup v **okně příkazového řádku**. Měli byste vidět tento řádek:

    `Greetings!`

   Tento kód definuje vložený úkol s názvem Echo a má pouze jeden požadovaný vstupní parametr Text. Ve výchozím nastavení jsou parametry typu System.String. Hodnota parametru Text je nastavena, když cíl TestBuild vyvolá úlohu Echo.

## <a name="define-the-adder-task"></a>Definování úlohy zmije

 Vytvořte vsednou úlohu, která přidá dva celé parametry a vyzařuje jejich součet jako vlastnost MSBuild.

#### <a name="to-define-the-adder-task"></a>Definování úlohy zmije

1. V editoru kódu nahraďte úlohu Echo a cíl TestBuild pomocí následujícího kódu.

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

2. V **okně příkazového řádku**zadejte **příkaz msbuild** bez přepínačů příkazů a stiskněte **klávesu Enter**. Ve výchozím nastavení to zpracuje výchozí cíl TestBuild, který vyvolá úlohu Echo.

3. Zkontrolujte výstup v **okně příkazového řádku**. Měli byste vidět tento řádek:

    `The sum is 9`

   Tento kód definuje vložený úkol s názvem Adder a má dva požadované celé číslo vstupní parametry, A a B a jeden celý výstup ový parametr C. Úloha Zmije přidá dva vstupní parametry a vrátí součet ve výstupním parametru. Součet je emitován jako `Sum`vlastnost MSBuild . Hodnoty vstupních parametrů jsou nastaveny, když cíl TestBuild vyvolá úlohu Zmije.

## <a name="define-the-regx-task"></a>Definování úlohy RegX

 Vytvořte vslanou úlohu, která přijme skupinu položek a regulární výraz, a vrátí seznam všech položek, které mají obsah souboru, který odpovídá výrazu.

#### <a name="to-define-the-regx-task"></a>Definování úlohy RegX

1. V editoru kódu nahraďte úlohu Zmije a cíl TestBuild pomocí následujícího kódu.

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

2. V **okně příkazového řádku**zadejte **příkaz msbuild** bez přepínačů příkazů a stiskněte **klávesu Enter**. Ve výchozím nastavení to zpracovává výchozí cíl TestBuild, který vyvolá úlohu RegX.

3. Zkontrolujte výstup v **okně příkazového řádku**. Měli byste vidět tyto řádky:

   ```
   Input files: Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
   ```

   ```
   Matched files: Form1.cs;Form1.Designer.cs;Properties\Settings.Designer.cs
   ```

   Tento kód definuje včleněnou úlohu s názvem RegX a má tyto tři parametry:

- `Expression`je povinný vstupní parametr řetězce, který má hodnotu, která je regulárním výrazem, který má být spárován. V tomto příkladu výraz odpovídá slovům "public" nebo "protected".

- `Files`je povinný vstupní parametr seznamu položek, který má hodnotu, která je seznamem souborů, které mají být prohledány pro shodu. V tomto `Files` příkladu je `Compile` nastavena na položku, která uvádí zdrojové soubory projektu.

- `Result`je výstupní parametr, který má hodnotu, která je seznam souborů, které mají obsah, který odpovídá regulárnímu výrazu.

  Hodnota vstupních parametrů jsou nastaveny při TestBuild cíl vyvolá úlohu RegX. Úloha RegX přečte každý soubor a vrátí seznam souborů, které odpovídají regulárnímu výrazu. Tento seznam je `Result` vrácen jako výstupní parametr, který je `MatchedFiles`emitován jako položka MSBuild .

### <a name="handle-reserved-characters"></a>Zpracování vyhrazených znaků

 Analyzátor MSBuild zpracovává vsazené úlohy jako XML. Znaky, které mají vyhrazený význam\<v jazyce XML, například " " a ">", jsou detekovány a zpracovány, jako by byly XML, a ne zdrojový kód .NET. Chcete-li zahrnout vyhrazené znaky do `Files.Length > 0`výrazů `Code` kódu, například , napište prvek tak, aby jeho obsah byl obsažen ve výrazu CDATA, a to následovně:

 ```xml
<Code Type="Fragment" Language="cs">
  <![CDATA[

  // Your code goes here.

  ]]>
</Code>
```

## <a name="see-also"></a>Viz také

- [Vsazené úkoly](../msbuild/msbuild-inline-tasks.md)
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Cíle](../msbuild/msbuild-targets.md)

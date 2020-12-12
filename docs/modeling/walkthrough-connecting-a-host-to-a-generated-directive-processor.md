---
title: Připojit hostitele k procesoru vygenerovaných direktiv
description: Zjistěte, jak můžete rozšířit vlastního hostitele tak, aby podporoval textové šablony, které volají procesory direktiv.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
dev_langs:
- CSharp
- VB
ms.openlocfilehash: a98e432c7eb9508d32f52e51acc1447035b9058b
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362493"
---
# <a name="walkthrough-connect-a-host-to-a-generated-directive-processor"></a>Návod: Připojení hostitele k procesoru vygenerovaných direktiv

Můžete napsat vlastního hostitele, který zpracovává textové šablony. Základní vlastní hostitel je znázorněn v [návodu: Vytvoření vlastního hostitele textových šablon](../modeling/walkthrough-creating-a-custom-text-template-host.md). Tohoto hostitele můžete roztáhnout tak, aby se přidaly funkce, jako je například generování více výstupních souborů.

V tomto návodu rozšíříte vlastního hostitele tak, aby podporoval textové šablony, které volají procesory direktiv. Při definování jazyka specifického pro doménu vygeneruje *procesor direktiv* pro doménový model. Procesor direktiv usnadňuje uživatelům zápis šablon, které přistupují k modelu, a snižuje nutnost psát sestavení a direktivy import v šablonách.

> [!NOTE]
> Tento návod vytvoří [Návod: Vytvoření vlastního hostitele textových šablon](../modeling/walkthrough-creating-a-custom-text-template-host.md). Nejdříve proveďte tento návod.

Tento návod zahrnuje následující úlohy:

- Pomocí [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] vygenerujte procesor direktiv založený na doménovém modelu.

- Připojení vlastního hostitele textových šablon k vygenerovanému procesoru direktiv

- Testování vlastního hostitele s vygenerovaným procesorem direktiv.

## <a name="prerequisites"></a>Předpoklady

K definování DSL musíte mít nainstalované následující součásti:

| Komponenta | Odkaz |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index) |
| Sada SDK pro vizualizaci a modelování sady Visual Studio | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Kromě toho musíte mít vytvořenou transformaci šablony vlastní text v [návodu: Vytvoření vlastního hostitele textových šablon](../modeling/walkthrough-creating-a-custom-text-template-host.md).

## <a name="use-domain-specific-language-tools-to-generate-a-directive-processor"></a>Vygenerujte procesor direktiv pomocí Domain-Specificch jazykových nástrojů.

V tomto návodu použijete Průvodce Domain-Specific Language Designer k vytvoření jazyka specifického pro doménu pro řešení DSLMinimalTest.

1. Vytvořte řešení jazyka specifického pro doménu s následujícími charakteristikami:

   - Název: DSLMinimalTest

   - Šablona řešení: minimální jazyk

   - Přípona souboru: min

   - Název společnosti: Fabrikam

   Další informace o vytváření řešení jazyka specifického pro doménu naleznete v tématu [How to: Create a Domain-Specific Language Solution](../modeling/how-to-create-a-domain-specific-language-solution.md).

2. V nabídce **Sestavení** klikněte na **Sestavit řešení**.

   > [!IMPORTANT]
   > Tento krok vygeneruje procesor direktiv a přidá k němu klíč v registru.

3. V nabídce **Ladit** klikněte na **Spustit ladění**.

    Otevře se druhá instance aplikace Visual Studio.

4. V experimentálním buildu v **Průzkumník řešení** dvakrát klikněte na soubor **Sample. min**.

    Soubor se otevře v návrháři. Všimněte si, že model má dva prvky, ExampleElement1 a ExampleElement2 a propojení mezi nimi.

5. Zavřete druhou instanci aplikace Visual Studio.

6. Uložte řešení a pak ukončete Návrháře Domain-Specific jazyka.

## <a name="connect-a-custom-text-template-host-to-a-directive-processor"></a>Připojení vlastního hostitele textových šablon k procesoru direktiv

Po vygenerování procesoru direktivy se připojíte procesor direktiv a vlastní hostitel šablony textu, který jste vytvořili v [návodu: Vytvoření vlastního hostitele textových šablon](../modeling/walkthrough-creating-a-custom-text-template-host.md).

1. Otevřete řešení CustomHost.

2. V nabídce **projekt** klikněte na příkaz **Přidat odkaz**.

     Otevře se dialogové okno **Přidat odkaz** se zobrazenou kartou **.NET** .

3. Přidejte následující odkazy:

    - Microsoft. VisualStudio. Modeling. SDK. 11.0

    - Microsoft. VisualStudio. Modeling. SDK. Diagrams. 11.0

    - Microsoft. VisualStudio. TextTemplating. 11.0

    - Microsoft. VisualStudio. TextTemplating. Interfaces. 11.0

    - Microsoft. VisualStudio. TextTemplating. Modelings. 11.0

    - Microsoft. VisualStudio. TextTemplating. VSHost. 11.0

4. V horní části Program.cs nebo Module1. vb přidejte následující řádek kódu:

    ```csharp
    using Microsoft.Win32;
    ```

    ```vb
    Imports Microsoft.Win32
    ```

5. Vyhledejte kód vlastnosti `StandardAssemblyReferences` a nahraďte ji následujícím kódem:

    > [!NOTE]
    > V tomto kroku přidáte odkazy na sestavení, která jsou požadována generovaným procesorem direktiv, který bude váš hostitel podporovat.

    ```csharp
    //the host can provide standard assembly references
    //the engine will use these references when compiling and
    //executing the generated transformation class
    //--------------------------------------------------------------
    public IList<string> StandardAssemblyReferences
    {
        get
        {
            return new string[]
            {
                //if this host searches standard paths and the GAC
                //we can specify the assembly name like this:
                //"System"
                //since this host only resolves assemblies from the
                //fully qualified path and name of the assembly
                //this is a quick way to get the code to give us the
                //fully qualified path and name of the System assembly
                //---------------------------------------------------------
                typeof(System.Uri).Assembly.Location,
                            typeof(System.Uri).Assembly.Location,
                typeof(Microsoft.VisualStudio.Modeling.ModelElement).Assembly.Location,
                typeof(Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape).Assembly.Location,
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating).Assembly.Location,
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation).Assembly.Location

            };
        }
    }
    ```

6. Vyhledejte kód pro funkci `ResolveDirectiveProcessor` a nahraďte ji následujícím kódem:

    > [!IMPORTANT]
    > Tento kód obsahuje pevně zakódované odkazy na název generovaného procesoru direktiv, ke kterému se chcete připojit. Tuto obecnější možnost si můžete snadno vytvořit. v takovém případě vyhledá všechny procesory direktiv uvedené v registru a pokusí se najít shodu. V takovém případě bude hostitel spolupracovat s jakýmkoli generovaným procesorem direktiv.

    ```csharp
    //the engine calls this method based on the directives the user has
            //specified it in the text template
            //this method can be called 0, 1, or more times
            //---------------------------------------------------------------------
            public Type ResolveDirectiveProcessor(string processorName)
            {
                //check the processor name, and if it is the name of the processor the
                //host wants to support, return the type of the processor
                //---------------------------------------------------------------------
                if (string.Compare(processorName, "DSLMinimalTestDirectiveProcessor", StringComparison.InvariantCultureIgnoreCase) == 0)
                {
                    try
                    {
                        string keyName = @"Software\Microsoft\VisualStudio\10.0Exp_Config\TextTemplating\DirectiveProcessors\DSLMinimalTestDirectiveProcessor";
                        using (RegistryKey specificKey = Registry.CurrentUser.OpenSubKey(keyName))
                        {
                            if (specificKey != null)
                            {
                                List<string> names = new List<String>(specificKey.GetValueNames());
                                string classValue = specificKey.GetValue("Class") as string;
                                if (!string.IsNullOrEmpty(classValue))
                                {
                                    string loadValue = string.Empty;
                                    System.Reflection.Assembly processorAssembly = null;
                                    if (names.Contains("Assembly"))
                                    {
                                        loadValue = specificKey.GetValue("Assembly") as string;
                                        if (!string.IsNullOrEmpty(loadValue))
                                        {
                                            //the assembly must be installed in the GAC
                                            processorAssembly = System.Reflection.Assembly.Load(loadValue);
                                        }
                                    }
                                    else if (names.Contains("CodeBase"))
                                    {
                                        loadValue = specificKey.GetValue("CodeBase") as string;
                                        if (!string.IsNullOrEmpty(loadValue))
                                        {
                                            //loading local assembly
                                            processorAssembly = System.Reflection.Assembly.LoadFrom(loadValue);
                                        }
                                    }
                                    if (processorAssembly == null)
                                    {
                                        throw new Exception("Directive Processor not found");
                                    }
                                    Type processorType = processorAssembly.GetType(classValue);
                                    if (processorType == null)
                                    {
                                        throw new Exception("Directive Processor not found");
                                    }
                                    return processorType;
                                }
                            }
                        }
                    }
                    catch (Exception e)
                    {
                        //if the directive processor can not be found, throw an error
                        throw new Exception("Directive Processor not found");
                    }
                }

                //if the directive processor is not one this host wants to support
                throw new Exception("Directive Processor not supported");
            }
    ```

7. V nabídce **File** (Soubor) klikněte na **Save All** (Uložit vše).

8. V nabídce **Sestavení** klikněte na **Sestavit řešení**.

## <a name="test-the-custom-host-with-the-directive-processor"></a>Test vlastního hostitele pomocí procesoru direktiv

Chcete-li otestovat vlastního hostitele textových šablon, musíte nejprve napsat textovou šablonu, která volá generovaný procesor direktiv. Pak spusťte vlastního hostitele, předejte mu název textové šablony a ověřte, zda je direktiva správně zpracována.

### <a name="create-a-text-template-to-test-the-custom-host"></a>Vytvoření textové šablony pro otestování vlastního hostitele

1. Vytvořte textový soubor a pojmenujte ho `TestTemplateWithDP.tt` . K vytvoření souboru můžete použít libovolný textový editor, například Poznámkový blok.

2. Do tohoto textového souboru přidejte následující text:

    > [!NOTE]
    > Programovací jazyk textové šablony nemusí odpovídat vašemu vlastnímu hostiteli.

    ```csharp
    Text Template Host Test

    <#@ template debug="true" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
    <# //this is the call to the examplemodel directive in the generated directive processor #>
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>
    <# //uncomment this line to test that the host allows the engine to set the extension #>
    <# //@ output extension=".htm" #>

    <# //uncomment this line if you want to see the generated transformation class #>
    <# //System.Diagnostics.Debugger.Break(); #>
    <# //this code uses the results of the examplemodel directive #>
    <#
        foreach ( ExampleElement box in this.ExampleModel.Elements )
        {
            WriteLine("Box: {0}", box.Name);

            foreach (ExampleElement linkedTo in box.Targets)
            {
                WriteLine("Linked to: {0}", linkedTo.Name);
            }

            foreach (ExampleElement linkedFrom in box.Sources)
            {
                WriteLine("Linked from: {0}", linkedFrom.Name);
            }

            WriteLine("");
        }
    #>
    ```

    ```vb
    Text Template Host Test

    <#@ template debug="true" language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>

    <# 'this is the call to the examplemodel directive in the generated directive processor #>
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>

    <# 'Uncomment this line to test that the host allows the engine to set the extension. #>
    <# '@ output extension=".htm" #>

    <# 'Uncomment this line if you want to see the generated transformation class. #>
    <# 'System.Diagnostics.Debugger.Break() #>

    <# 'this code uses the results of the examplemodel directive #>

    <#
       For Each box as ExampleElement In Me.ExampleModel.Elements

           WriteLine("Box: {0}", box.Name)

            For Each LinkedTo as ExampleElement In box.Targets
                WriteLine("Linked to: {0}", LinkedTo.Name)
            Next

            For Each LinkedFrom as ExampleElement In box.Sources
                WriteLine("Linked from: {0}", LinkedFrom.Name)
            Next

            WriteLine("")

       Next
    #>
    ```

3. V kódu nahraďte \<YOUR PATH> cestou k souboru Sample. min z jazyka specifického pro návrh, který jste vytvořili v prvním postupu.

4. Uložte soubor a zavřete ho.

### <a name="test-the-custom-host"></a>Test vlastního hostitele

1. Otevřete okno příkazového řádku.

2. Zadejte cestu ke spustitelnému souboru vlastního hostitele, ale zatím nemačkejte klávesu ENTER.

     Zadejte například:

     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`

    > [!NOTE]
    > Místo zadání adresy můžete vyhledat soubor CustomHost.exe v **Průzkumníkovi Windows** a pak ho přetáhnout do okna příkazového řádku.

3. Zadejte mezeru.

4. Zadejte cestu k souboru textové šablony a stiskněte klávesu ENTER.

     Zadejte například:

     `<YOUR PATH>TestTemplateWithDP.txt`

    > [!NOTE]
    > Místo zadání adresy můžete vyhledat soubor TestTemplateWithDP.txt v **Průzkumníkovi Windows** a pak ho přetáhnout do okna příkazového řádku.

     Spustí se vlastní hostitelská aplikace a spustí se proces transformace textové šablony.

5. V **Průzkumníku Windows** přejděte do složky, která obsahuje soubor TestTemplateWithDP.txt.

     Složka také obsahuje soubor TestTemplateWithDP1.txt.

6. Otevřete tento soubor a podívejte se na výsledky transformace textové šablony.

     Zobrazí se výsledky vygenerovaného textového výstupu, které by měly vypadat takto:

    ```
    Text Template Host Test

    Box: ExampleElement1
    Linked to: ExampleElement2

    Box: ExampleElement2
    Linked from: ExampleElement1
    ```

## <a name="see-also"></a>Viz také:

- [Návod: Vytvoření vlastního hostitele textových šablon](../modeling/walkthrough-creating-a-custom-text-template-host.md)

---
title: 'Návod: Připojení hostitele k procesoru vygenerovaných direktiv'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 5b5346f47d3dcb836a0e8eeef7d9b21bd55ccd07
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896234"
---
# <a name="walkthrough-connect-a-host-to-a-generated-directive-processor"></a>Návod: Připojení hostitele k procesoru vygenerovaných direktiv

Můžete napsat vlastního hostitele, který zpracovává textových šablon. Základní vlastního hostitele je ukázáno v [návod: vytvoření vlastního hostitele textových šablon](../modeling/walkthrough-creating-a-custom-text-template-host.md). Můžete rozšířit, které hostují přidat funkce, například generování víc výstupních souborů.

V tomto podrobném návodu rozbalte vlastního hostitele tak, aby podporoval textové šablony, které volají procesory direktiv. Při definování jazyka specifického pro doménu, generuje *procesor direktiv* pro doménový model. Procesor direktiv usnadňuje uživatelům zapisovat šablony, které přístup k modelu, přičemž redukuje nutnost psaní sestavení a importovat direktivy v šablonách.

> [!NOTE]
> Tento návod vychází [návod: vytvoření vlastního hostitele textových šablon](../modeling/walkthrough-creating-a-custom-text-template-host.md). Tento návod proveďte jako první.

Tento návod zahrnuje následující úlohy:

- Pomocí [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] ke generování procesoru direktiv, který je založen na modelu domény.

- Připojení vlastního hostitele textových šablon k procesoru vygenerovaných direktiv.

- Testování vlastního hostitele s procesoru vygenerovaných direktiv.

## <a name="prerequisites"></a>Požadavky

Pokud chcete definovat DSL, musíte mít nainstalovaný následující komponenty:


| | |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580) |
| Visual Studio Visualization and Modeling SDK | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Kromě toho musí mít vlastní textovou šablonu můžete vytvořit v [návod: vytvoření vlastního hostitele textových šablon](../modeling/walkthrough-creating-a-custom-text-template-host.md).

## <a name="use-domain-specific-language-tools-to-generate-a-directive-processor"></a>Nástroje jazyka specifického pro doménu k vygenerování procesoru direktiv

V tomto názorném postupu použijete k vytvoření jazyka specifického pro doménu pro řešení DSLMinimalTest Průvodce návrháře jazyka specifického pro doménu.

1. Vytváření řešení jazyka specifického pro doménu, která má následující vlastnosti:

   -   Název: DSLMinimalTest

   -   Šablona řešení: minimální jazykový

   -   Přípona souboru: min

   -   Název společnosti: Fabrikam

   Další informace o vytváření řešení jazyka specifického pro doménu, najdete v části [postupy: vytváření řešení jazyka specifického pro doménu](../modeling/how-to-create-a-domain-specific-language-solution.md).

2. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

   > [!IMPORTANT]
   > Tento krok vygeneruje procesoru direktiv a přidá klíč pro něj v registru.

3. Na **ladění** nabídky, klikněte na tlačítko **spustit ladění**.

    Otevře se druhá instance sady Visual Studio.

4. V experimentální sestavení v **Průzkumníka řešení**, poklikejte na soubor **sample.min**.

    Soubor se otevře v návrháři. Všimněte si, že model má dva prvky, ExampleElement1 a ExampleElement2 a propojení mezi nimi.

5. Zavřete druhou instanci aplikace Visual Studio.

6. Uložte řešení a pak zavřete návrháře jazyka specifického pro doménu.

## <a name="connect-a-custom-text-template-host-to-a-directive-processor"></a>Připojte se vlastního hostitele textových šablon k procesoru direktiv

Jakmile vygenerujete procesor direktiv, připojíte procesoru direktiv a vlastního hostitele textových šablon, které jste vytvořili [návod: vytvoření vlastního hostitele textových šablon](../modeling/walkthrough-creating-a-custom-text-template-host.md).

1.  Otevřete řešení CustomHost.

2.  Na **projektu** nabídky, klikněte na tlačítko **přidat odkaz**.

     **Přidat odkaz** dialogové okno s **.NET** karta zobrazí.

3.  Přidejte následující odkazy:

    -   Microsoft.VisualStudio.Modeling.Sdk.11.0

    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

    -   Microsoft.VisualStudio.TextTemplating.11.0

    -   Microsoft.VisualStudio.TextTemplating.Interfaces.11.0

    -   Microsoft.VisualStudio.TextTemplating.Modeling.11.0

    -   Microsoft.VisualStudio.TextTemplating.VSHost.11.0

4.  V horní části souboru Program.cs nebo Module1.vb přidejte následující řádek kódu:

    ```csharp
    using Microsoft.Win32;
    ```

    ```vb
    Imports Microsoft.Win32
    ```

5.  Vyhledejte kód pro vlastnost `StandardAssemblyReferences`a nahraďte ho následujícím kódem:

    > [!NOTE]
    > V tomto kroku přidáte odkazy na sestavení, které jsou vyžadované procesoru vygenerovaných direktiv, která bude podporovat hostitele.

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

6.  Vyhledejte kód pro funkci `ResolveDirectiveProcessor`a nahraďte ho následujícím kódem:

    > [!IMPORTANT]
    > Tento kód obsahuje pevně zakódovaný odkazy na název procesoru vygenerovaných direktiv, ke kterému chcete připojit. Můžete snadno provést to obecnější, v takovém případě vyhledá všechny procesory direktiv uvedený v registru a pokusí se najít shodu. V takovém případě hostitele bude pracovat se žádné procesoru vygenerovaných direktiv.

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

7.  Na **souboru** nabídky, klikněte na tlačítko **Uložit vše**.

8.  Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

## <a name="test-the-custom-host-with-the-directive-processor"></a>Testování vlastního hostitele s procesorem direktiv

K otestování vlastního hostitele textových šablon, nejprve musí napsat textovou šablonu, která volá procesoru vygenerovaných direktiv. Potom spustíte vlastního hostitele, jí předat název textové šablony a ověřte, že je správně zpracovány směrnice.

### <a name="create-a-text-template-to-test-the-custom-host"></a>Vytvoření textové šablony pro testování vlastního hostitele

1.  Vytvořte textový soubor a pojmenujte ho `TestTemplateWithDP.tt`. Libovolného textového editoru, jako je například Poznámkový blok, můžete použít k vytvoření souboru.

2.  Do tohoto textového souboru přidejte následující text:

    > [!NOTE]
    > Programovací jazyk textové šablony se nemusí shodovat s vlastního hostitele.

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

3.  V kódu, nahraďte \<vaše cesta > s cestou k souboru Sample.min z jazyka specifického pro návrh, kterou jste vytvořili v prvním postupu.

4.  Soubor uložte a zavřete.

### <a name="test-the-custom-host"></a>Testování vlastního hostitele

1.  Otevřete okno příkazového řádku.

2.  Zadejte cestu ke spustitelnému souboru vlastního hostitele, ale zatím nemačkejte klávesu ENTER.

     Zadejte například:

     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`

    > [!NOTE]
    > Místo zadání adresy můžete soubor CustomHost.exe přejděte v **Windows Explorer**a potom tento soubor přetáhnout do okna příkazového řádku.

3.  Zadejte mezeru.

4.  Zadejte cestu k souboru textové šablony a stiskněte klávesu ENTER.

     Zadejte například:

     `<YOUR PATH>TestTemplateWithDP.txt`

    > [!NOTE]
    > Místo zadání adresy můžete procházet k souboru TestTemplateWithDP.txt v **Windows Explorer**a potom tento soubor přetáhnout do okna příkazového řádku.

     Aplikace vlastního hostitele se spustí a začne proces transformace textových šablon.

5.  V **Windows Explorer**, přejděte do složky, která obsahuje soubor TestTemplateWithDP.txt.

     Složka také obsahuje soubor TestTemplateWithDP1.txt.

6.  Otevřete tento soubor a podívejte se na výsledky transformace textové šablony.

     Výsledky vygenerovaný textový výstup se zobrazí a by měl vypadat takto:

    ```
    Text Template Host Test

    Box: ExampleElement1
    Linked to: ExampleElement2

    Box: ExampleElement2
    Linked from: ExampleElement1
    ```

## <a name="see-also"></a>Viz také:

- [Návod: Vytvoření vlastního hostitele textových šablon](../modeling/walkthrough-creating-a-custom-text-template-host.md)

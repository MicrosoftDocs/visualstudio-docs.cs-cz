---
title: 'Návod: Vytvoření vlastního procesoru direktiv'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
- walkthroughs [text templates], directive processor
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
ms.openlocfilehash: c430dad62686e49d9ce07fdff9a3665b0ea519a4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930320"
---
# <a name="walkthrough-create-a-custom-directive-processor"></a>Návod: Vytvoření vlastního procesoru direktiv

*Procesory direktiv* fungují tak, že přidáte kód *vygenerované třídy transformace*. Při volání *směrnice* z *textové šablony*, zbytek kódu, který napíšete do textové šablony může záviset na funkčnosti, která poskytuje tato direktiva.

Můžete si vytvořit své vlastní procesory direktiv. To vám pak umožní textové šablony přizpůsobit. Vytvoření vlastního procesoru direktiv vytvoříte třídu, která dědí buď z <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> nebo <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

Mezi úlohy popsané v tomto návodu patří:

- Vytvoření vlastního procesoru direktiv

- Registrace procesoru direktiv

- Testování procesoru direktiv

## <a name="create-a-custom-directive-processor"></a>Vytvoření vlastního procesoru direktiv

V tomto návodu vytvoříte vlastní procesor direktiv. Přidáte vlastní direktivu, která přečte soubor XML, uloží ho <xref:System.Xml.XmlDocument> proměnnou a zpřístupní prostřednictvím vlastnosti. V části „Testování procesoru direktiv“ získáte pomocí této vlastnosti v textové šabloně přístup k tomuto souboru XML.

Volání vlastní direktivy vypadá následovně:

`<#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<Your Path>DocFile.xml" #>`

Vlastní procesor direktiv přidá proměnnou a vlastnost do vygenerované třídy transformace. Direktiva, kterou píšete <xref:System.CodeDom> třídy pro vytvoření kódu, který stroj přidá do vygenerované třídy transformace. <xref:System.CodeDom> Třídy vytvoření kódu v obou Vizuálu C# nebo Visual Basic, v závislosti na jazyce určeném `language` parametr `template` – direktiva. Jazyk procesoru direktiv a jazyk textové šablony, ke které tento procesor direktiv přistupuje, se nemusejí shodovat.

Kód, který direktiva vytvoří, vypadá takto:

```csharp
private System.Xml.XmlDocument document0Value;

public virtual System.Xml.XmlDocument Document0
{
  get
  {
    if ((this.document0Value == null))
    {
      this.document0Value = XmlReaderHelper.ReadXml(<FileNameParameterValue>);
    }
    return this.document0Value;
  }
}
```

```vb
Private document0Value As System.Xml.XmlDocument

Public Overridable ReadOnly Property Document0() As System.Xml.XmlDocument
    Get
        If (Me.document0Value Is Nothing) Then
            Me.document0Value = XmlReaderHelper.ReadXml(<FileNameParameterValue>)
        End If
        Return Me.document0Value
    End Get
End Property
```

### <a name="to-create-a-custom-directive-processor"></a>Vytvoření vlastního procesoru direktiv

1. V sadě Visual Studio vytvořte projekt knihovny tříd jazyka C# nebo Visual Basic s názvem CustomDP.

    > [!NOTE]
    > Pokud chcete procesor direktiv nainstalovat na více než jednom počítači, je vhodnější použít projekt rozšíření aplikace Visual Studio (VSIX) a zahrnout do rozšíření soubor .pkgdef. Další informace najdete v tématu [nasazení vlastního procesoru direktiv](../modeling/deploying-a-custom-directive-processor.md).

2. Přidejte odkazy na tato sestavení:

    - **Microsoft.VisualStudio.TextTemplating.\*.0**

    - **Microsoft.VisualStudio.TextTemplating.Interfaces.\*.0**

3. Nahraďte kód v **Class1** následujícím kódem. Tento kód definuje třídu CustomDirectiveProcessor, která dědí z <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> třídy a implementuje nezbytné metody.

    ```csharp
    using System;
    using System.CodeDom;
    using System.CodeDom.Compiler;
    using System.Collections.Generic;
    using System.Globalization;
    using System.IO;
    using System.Text;
    using System.Xml;
    using System.Xml.Serialization;
    using Microsoft.VisualStudio.TextTemplating;

    namespace CustomDP
    {
        public class CustomDirectiveProcessor : DirectiveProcessor
        {
            // This buffer stores the code that is added to the
            // generated transformation class after all the processing is done.
            // ---------------------------------------------------------------------
            private StringBuilder codeBuffer;

            // Using a Code Dom Provider creates code for the
            // generated transformation class in either Visual Basic or C#.
            // If you want your directive processor to support only one language, you
            // can hard code the code you add to the generated transformation class.
            // In that case, you do not need this field.
            // --------------------------------------------------------------------------
            private CodeDomProvider codeDomProvider;

            // This stores the full contents of the text template that is being processed.
            // --------------------------------------------------------------------------
            private String templateContents;

            // These are the errors that occur during processing. The engine passes
            // the errors to the host, and the host can decide how to display them,
            // for example the host can display the errors in the UI
            // or write them to a file.
            // ---------------------------------------------------------------------
            private CompilerErrorCollection errorsValue;
            public new CompilerErrorCollection Errors
            {
                get { return errorsValue; }
            }

            // Each time this directive processor is called, it creates a new property.
            // We count how many times we are called, and append "n" to each new
            // property name. The property names are therefore unique.
            // -----------------------------------------------------------------------------
            private int directiveCount = 0;

            public override void Initialize(ITextTemplatingEngineHost host)
            {
                // We do not need to do any initialization work.
            }

            public override void StartProcessingRun(CodeDomProvider languageProvider, String templateContents, CompilerErrorCollection errors)
            {
                // The engine has passed us the language of the text template
                // we will use that language to generate code later.
                // ----------------------------------------------------------
                this.codeDomProvider = languageProvider;
                this.templateContents = templateContents;
                this.errorsValue = errors;

                this.codeBuffer = new StringBuilder();
            }

            // Before calling the ProcessDirective method for a directive, the
            // engine calls this function to see whether the directive is supported.
            // Notice that one directive processor might support many directives.
            // ---------------------------------------------------------------------
            public override bool IsDirectiveSupported(string directiveName)
            {
                if (string.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) == 0)
                {
                    return true;
                }
                if (string.Compare(directiveName, "SuperCoolDirective", StringComparison.OrdinalIgnoreCase) == 0)
                {
                    return true;
                }
                return false;
            }

            public override void ProcessDirective(string directiveName, IDictionary<string, string> arguments)
            {
                if (string.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) == 0)
                {
                    string fileName;

                    if (!arguments.TryGetValue("FileName", out fileName))
                    {
                        throw new DirectiveProcessorException("Required argument 'FileName' not specified.");
                    }

                    if (string.IsNullOrEmpty(fileName))
                    {
                        throw new DirectiveProcessorException("Argument 'FileName' is null or empty.");
                    }

                    // Now we add code to the generated transformation class.
                    // This directive supports either Visual Basic or C#, so we must use the
                    // System.CodeDom to create the code.
                    // If a directive supports only one language, you can hard code the code.
                    // --------------------------------------------------------------------------

                    CodeMemberField documentField = new CodeMemberField();

                    documentField.Name = "document" + directiveCount + "Value";
                    documentField.Type = new CodeTypeReference(typeof(XmlDocument));
                    documentField.Attributes = MemberAttributes.Private;

                    CodeMemberProperty documentProperty = new CodeMemberProperty();

                    documentProperty.Name = "Document" + directiveCount;
                    documentProperty.Type = new CodeTypeReference(typeof(XmlDocument));
                    documentProperty.Attributes = MemberAttributes.Public;
                    documentProperty.HasSet = false;
                    documentProperty.HasGet = true;

                    CodeExpression fieldName = new CodeFieldReferenceExpression(new CodeThisReferenceExpression(), documentField.Name);
                    CodeExpression booleanTest = new CodeBinaryOperatorExpression(fieldName, CodeBinaryOperatorType.IdentityEquality, new CodePrimitiveExpression(null));
                    CodeExpression rightSide = new CodeMethodInvokeExpression(new CodeTypeReferenceExpression("XmlReaderHelper"), "ReadXml", new CodePrimitiveExpression(fileName));
                    CodeStatement[] thenSteps = new CodeStatement[] { new CodeAssignStatement(fieldName, rightSide) };

                    CodeConditionStatement ifThen = new CodeConditionStatement(booleanTest, thenSteps);
                    documentProperty.GetStatements.Add(ifThen);

                    CodeStatement s = new CodeMethodReturnStatement(fieldName);
                    documentProperty.GetStatements.Add(s);

                    CodeGeneratorOptions options = new CodeGeneratorOptions();
                    options.BlankLinesBetweenMembers = true;
                    options.IndentString = "    ";
                    options.VerbatimOrder = true;
                    options.BracingStyle = "C";

                    using (StringWriter writer = new StringWriter(codeBuffer, CultureInfo.InvariantCulture))
                    {
                        codeDomProvider.GenerateCodeFromMember(documentField, writer, options);
                        codeDomProvider.GenerateCodeFromMember(documentProperty, writer, options);
                    }
                }

                // One directive processor can contain many directives.
                // If you want to support more directives, the code goes here...
                // -----------------------------------------------------------------
                if (string.Compare(directiveName, "supercooldirective", StringComparison.OrdinalIgnoreCase) == 0)
                {
                    // Code for SuperCoolDirective goes here...
                }

                // Track how many times the processor has been called.
                // -----------------------------------------------------------------
                directiveCount++;

            }

            public override void FinishProcessingRun()
            {
                this.codeDomProvider = null;

                // Important: do not do this:
                // The get methods below are called after this method
                // and the get methods can access this field.
                // -----------------------------------------------------------------
                // this.codeBuffer = null;
            }

            public override string GetPreInitializationCodeForProcessingRun()
            {
                // Use this method to add code to the start of the
                // Initialize() method of the generated transformation class.
                // We do not need any pre-initialization, so we will just return "".
                // -----------------------------------------------------------------
                // GetPreInitializationCodeForProcessingRun runs before the
                // Initialize() method of the base class.
                // -----------------------------------------------------------------
                return String.Empty;
            }

            public override string GetPostInitializationCodeForProcessingRun()
            {
                // Use this method to add code to the end of the
                // Initialize() method of the generated transformation class.
                // We do not need any post-initialization, so we will just return "".
                // ------------------------------------------------------------------
                // GetPostInitializationCodeForProcessingRun runs after the
                // Initialize() method of the base class.
                // -----------------------------------------------------------------
                return String.Empty;
            }

            public override string GetClassCodeForProcessingRun()
            {
                //Return the code to add to the generated transformation class.
                // -----------------------------------------------------------------
                return codeBuffer.ToString();
            }

            public override string[] GetReferencesForProcessingRun()
            {
                // This returns the references that we want to use when
                // compiling the generated transformation class.
                // -----------------------------------------------------------------
                // We need a reference to this assembly to be able to call
                // XmlReaderHelper.ReadXml from the generated transformation class.
                // -----------------------------------------------------------------
                return new string[]
                {
                    "System.Xml",
                    this.GetType().Assembly.Location
                };
            }

            public override string[] GetImportsForProcessingRun()
            {
                //This returns the imports or using statements that we want to
                //add to the generated transformation class.
                // -----------------------------------------------------------------
                //We need CustomDP to be able to call XmlReaderHelper.ReadXml
                //from the generated transformation class.
                // -----------------------------------------------------------------
                return new string[]
                {
                    "System.Xml",
                    "CustomDP"
                };
            }
        }

        // -------------------------------------------------------------------------
        // The code that we are adding to the generated transformation class
        // will call this method.
        // -------------------------------------------------------------------------
        public static class XmlReaderHelper
        {
            public static XmlDocument ReadXml(string fileName)
            {
                XmlDocument d = new XmlDocument();

                using (XmlTextReader reader = new XmlTextReader(fileName))
                {
                    try
                    {
                        d.Load(reader);
                    }
                    catch (System.Xml.XmlException e)
                    {
                        throw new DirectiveProcessorException("Unable to read the XML file.", e);
                    }
                }
                return d;
            }
        }
    }
    ```

    ```vb
    Imports System
    Imports System.CodeDom
    Imports System.CodeDom.Compiler
    Imports System.Collections.Generic
    Imports System.Globalization
    Imports System.IO
    Imports System.Text
    Imports System.Xml
    Imports System.Xml.Serialization
    Imports Microsoft.VisualStudio.TextTemplating

    Namespace CustomDP

        Public Class CustomDirectiveProcessor
        Inherits DirectiveProcessor

            ' This buffer stores the code that is added to the
            ' generated transformation class after all the processing is done.
            ' ---------------------------------------------------------------
            Private codeBuffer As StringBuilder

            ' Using a Code Dom Provider creates code for the
            ' generated transformation class in either Visual Basic or C#.
            ' If you want your directive processor to support only one language, you
            ' can hard code the code you add to the generated transformation class.
            ' In that case, you do not need this field.
            ' --------------------------------------------------------------------------
            Private codeDomProvider As CodeDomProvider

            ' This stores the full contents of the text template that is being processed.
            ' --------------------------------------------------------------------------
            Private templateContents As String

            ' These are the errors that occur during processing. The engine passes
            ' the errors to the host, and the host can decide how to display them,
            ' for example the host can display the errors in the UI
            ' or write them to a file.
            ' ---------------------------------------------------------------------
            Private errorsValue As CompilerErrorCollection
            Public Shadows ReadOnly Property Errors() As CompilerErrorCollection
                Get
                    Return errorsValue
                End Get
            End Property

            ' Each time this directive processor is called, it creates a new property.
            ' We count how many times we are called, and append "n" to each new
            ' property name. The property names are therefore unique.
            ' --------------------------------------------------------------------------
            Private directiveCount As Integer = 0

            Public Overrides Sub Initialize(ByVal host As ITextTemplatingEngineHost)

                ' We do not need to do any initialization work.
            End Sub

            Public Overrides Sub StartProcessingRun(ByVal languageProvider As CodeDomProvider, ByVal templateContents As String, ByVal errors As CompilerErrorCollection)

                ' The engine has passed us the language of the text template
                ' we will use that language to generate code later.
                ' ----------------------------------------------------------
                Me.codeDomProvider = languageProvider
                Me.templateContents = templateContents
                Me.errorsValue = errors

                Me.codeBuffer = New StringBuilder()
            End Sub

            ' Before calling the ProcessDirective method for a directive, the
            ' engine calls this function to see whether the directive is supported.
            ' Notice that one directive processor might support many directives.
            ' ---------------------------------------------------------------------
            Public Overrides Function IsDirectiveSupported(ByVal directiveName As String) As Boolean

                If String.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) = 0 Then
                    Return True
                End If

                If String.Compare(directiveName, "SuperCoolDirective", StringComparison.OrdinalIgnoreCase) = 0 Then
                    Return True
                End If

                Return False
            End Function

            Public Overrides Sub ProcessDirective(ByVal directiveName As String, ByVal arguments As IDictionary(Of String, String))

                If String.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) = 0 Then

                    Dim fileName As String

                    If Not (arguments.TryGetValue("FileName", fileName)) Then
                        Throw New DirectiveProcessorException("Required argument 'FileName' not specified.")
                    End If

                    If String.IsNullOrEmpty(fileName) Then
                        Throw New DirectiveProcessorException("Argument 'FileName' is null or empty.")
                    End If

                    ' Now we add code to the generated transformation class.
                    ' This directive supports either Visual Basic or C#, so we must use the
                    ' System.CodeDom to create the code.
                    ' If a directive supports only one language, you can hard code the code.
                    ' --------------------------------------------------------------------------

                    Dim documentField As CodeMemberField = New CodeMemberField()

                    documentField.Name = "document" & directiveCount & "Value"
                    documentField.Type = New CodeTypeReference(GetType(XmlDocument))
                    documentField.Attributes = MemberAttributes.Private

                    Dim documentProperty As CodeMemberProperty = New CodeMemberProperty()

                    documentProperty.Name = "Document" & directiveCount
                    documentProperty.Type = New CodeTypeReference(GetType(XmlDocument))
                    documentProperty.Attributes = MemberAttributes.Public
                    documentProperty.HasSet = False
                    documentProperty.HasGet = True

                    Dim fieldName As CodeExpression = New CodeFieldReferenceExpression(New CodeThisReferenceExpression(), documentField.Name)
                    Dim booleanTest As CodeExpression = New CodeBinaryOperatorExpression(fieldName, CodeBinaryOperatorType.IdentityEquality, New CodePrimitiveExpression(Nothing))
                    Dim rightSide As CodeExpression = New CodeMethodInvokeExpression(New CodeTypeReferenceExpression("XmlReaderHelper"), "ReadXml", New CodePrimitiveExpression(fileName))
                    Dim thenSteps As CodeStatement() = New CodeStatement() {New CodeAssignStatement(fieldName, rightSide)}

                    Dim ifThen As CodeConditionStatement = New CodeConditionStatement(booleanTest, thenSteps)
                    documentProperty.GetStatements.Add(ifThen)

                    Dim s As CodeStatement = New CodeMethodReturnStatement(fieldName)
                    documentProperty.GetStatements.Add(s)

                    Dim options As CodeGeneratorOptions = New CodeGeneratorOptions()
                    options.BlankLinesBetweenMembers = True
                    options.IndentString = "    "
                    options.VerbatimOrder = True
                    options.BracingStyle = "VB"

                    Using writer As StringWriter = New StringWriter(codeBuffer, CultureInfo.InvariantCulture)

                        codeDomProvider.GenerateCodeFromMember(documentField, writer, options)
                        codeDomProvider.GenerateCodeFromMember(documentProperty, writer, options)
                    End Using

                End If

                ' One directive processor can contain many directives.
                ' If you want to support more directives, the code goes here...
                ' -----------------------------------------------------------------
                If String.Compare(directiveName, "supercooldirective", StringComparison.OrdinalIgnoreCase) = 0 Then

                    ' Code for SuperCoolDirective goes here.
                End If

                ' Track how many times the processor has been called.
                ' -----------------------------------------------------------------
                directiveCount += 1
            End Sub

            Public Overrides Sub FinishProcessingRun()

                Me.codeDomProvider = Nothing

                ' Important: do not do this:
                ' The get methods below are called after this method
                ' and the get methods can access this field.
                ' -----------------------------------------------------------------
                ' Me.codeBuffer = Nothing
            End Sub

            Public Overrides Function GetPreInitializationCodeForProcessingRun() As String

                ' Use this method to add code to the start of the
                ' Initialize() method of the generated transformation class.
                ' We do not need any pre-initialization, so we will just return "".
                ' -----------------------------------------------------------------
                ' GetPreInitializationCodeForProcessingRun runs before the
                ' Initialize() method of the base class.
                ' -----------------------------------------------------------------
                Return String.Empty
            End Function

            Public Overrides Function GetPostInitializationCodeForProcessingRun() As String

                ' Use this method to add code to the end of the
                ' Initialize() method of the generated transformation class.
                ' We do not need any post-initialization, so we will just return "".
                ' ------------------------------------------------------------------
                ' GetPostInitializationCodeForProcessingRun runs after the
                ' Initialize() method of the base class.
                ' -----------------------------------------------------------------
                Return String.Empty
            End Function

            Public Overrides Function GetClassCodeForProcessingRun() As String

                ' Return the code to add to the generated transformation class.
                ' -----------------------------------------------------------------
                Return codeBuffer.ToString()
            End Function

            Public Overrides Function GetReferencesForProcessingRun() As String()

                ' This returns the references that we want to use when
                ' compiling the generated transformation class.
                ' -----------------------------------------------------------------
                ' We need a reference to this assembly to be able to call
                ' XmlReaderHelper.ReadXml from the generated transformation class.
                ' -----------------------------------------------------------------
                Return New String() {"System.Xml", Me.GetType().Assembly.Location}
            End Function

            Public Overrides Function GetImportsForProcessingRun() As String()

                ' This returns the imports or using statements that we want to
                ' add to the generated transformation class.
                ' -----------------------------------------------------------------
                ' We need CustomDP to be able to call XmlReaderHelper.ReadXml
                ' from the generated transformation class.
                ' -----------------------------------------------------------------
                Return New String() {"System.Xml", "CustomDP"}
            End Function
        End Class

        ' --------------------------------------------------------------------------
        ' The code that we are adding to the generated transformation class
        ' will call this method.
        ' --------------------------------------------------------------------------
        Public Class XmlReaderHelper

            Public Shared Function ReadXml(ByVal fileName As String) As XmlDocument

                Dim d As XmlDocument = New XmlDocument()

                Using reader As XmlTextReader = New XmlTextReader(fileName)

                    Try
                        d.Load(reader)

                    Catch e As System.Xml.XmlException

                        Throw New DirectiveProcessorException("Unable to read the XML file.", e)
                    End Try
                End Using

                Return d
            End Function
        End Class

    End Namespace
    ```

4. Pouze v jazyce Visual Basic, otevřete **projektu** nabídky a klikněte na tlačítko **vlastnosti CustomDP**. Na **aplikace** kartě **kořenový obor názvů**, odstraňte výchozí hodnotu `CustomDP`.

5. Na **souboru** nabídky, klikněte na tlačítko **Uložit vše**.

6. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

### <a name="build-the-project"></a>Sestavení projektu

Sestavte projekt. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

## <a name="register-the-directive-processor"></a>Registrace procesoru direktiv

Než zavolat direktivu z textové šablony v sadě Visual Studio, musíte přidat klíč registru pro procesor direktiv.

> [!NOTE]
> Pokud chcete procesor direktiv nainstalovat na více než jednom počítači, je lepší definovat rozšíření aplikace Visual Studio (VSIX), která zahrnuje *.pkgdef* soubor spolu se sestavením. Další informace najdete v tématu [nasazení vlastního procesoru direktiv](../modeling/deploying-a-custom-directive-processor.md).

Klíče procesoru direktiv se v registru nacházejí na následujícím místě:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\*.0\TextTemplating\DirectiveProcessors
```

64bitové systémy používají toto místo v registru:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\*.0\TextTemplating\DirectiveProcessors
```

V tomto oddílu přidáte na stejné místo v registru klíč pro vlastní procesor direktiv.

> [!CAUTION]
> Nesprávná úprava registru může vážně poškodit systém. Před prováděním změn registru zazálohujte všechna cenná data v počítači.

### <a name="to-add-a-registry-key-for-the-directive-processor"></a>Přidání klíče registru pro procesor direktiv

1. Spustit `regedit` pomocí nabídky Start nebo příkazového řádku.

2. Přejděte do umístění **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\\*.0\TextTemplating\DirectiveProcessors**a klikněte na uzel.

   V 64bitových systémech použijte **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\\\*.0\TextTemplating\DirectiveProcessors**

3. Přidejte nový klíč s názvem CustomDirectiveProcessor.

    > [!NOTE]
    > Jedná se o název, který budete používat v poli Processor vlastních direktiv. Tento název se nemusí shodovat s názvem direktivy, názvem třídy procesoru direktiv ani s oborem názvů procesoru direktiv.

4. Přidejte novou řetězcovou hodnotu s názvem Class, která má pro název nového řetězce hodnotu CustomDP.CustomDirectiveProcessor.

5. Přidejte novou řetězcovou hodnotu s názvem CodeBase, jejíž hodnota se shoduje s cestou k souboru CustomDP.dll, který jste vytvořili dříve v tomto návodu.

     Cesta může například vypadat `C:\UserFiles\CustomDP\bin\Debug\CustomDP.dll`.

     Klíč registru by měl mít následující hodnoty:


   | Název | Typ | Data |
   |-|-|-|
   | (Výchozí) | REG_SZ | (hodnota nenastavena) |
   | Třída | REG_SZ | CustomDP.CustomDirectiveProcessor |
   | CodeBase | REG_SZ | <strong>\<Cesta k vašemu řešení ></strong>CustomDP\bin\Debug\CustomDP.dll |

     Pokud jste sestavení vložili do mezipaměti GAC, měly by tyto hodnoty vypadat takto:


   | Název | Typ | Data |
   |-|-|-|
   | (Výchozí) | REG_SZ | (hodnota nenastavena) |
   | Třída | REG_SZ | CustomDP.CustomDirectiveProcessor |
   | Assembly | REG_SZ | CustomDP.dll |


6. Restartujte sadu Visual Studio.

## <a name="test-the-directive-processor"></a>Testování procesoru direktiv

Při testování procesoru direktiv potřebujete napsat textovou šablonu, která ho zavolá.

V tomto příkladu volá textová šablona direktivu a předá název souboru XML, který obsahuje dokumentaci pro soubor třídy. Textová šablona se používá <xref:System.Xml.XmlDocument> vlastnost, kterou direktiva vytvoří, přejde na soubor XML a vytiskne komentáře k dokumentaci.

### <a name="to-create-an-xml-file-for-use-in-testing-the-directive-processor"></a>Vytvoření souboru XML pro testování procesoru direktiv

1. Vytvořte soubor s názvem *DocFile.xml* pomocí libovolného textového editoru (například Poznámkový blok).

    > [!NOTE]
    > Tento soubor můžete vytvořit na libovolném místě (například *C:\Test\DocFile.xml*).

2. Přidejte následující text do souboru XML:

    ```xml
    <?xml version="1.0"?>
    <doc>
        <assembly>
            <name>xmlsample</name>
        </assembly>
        <members>
            <member name="T:SomeClass">
                <summary>Class level summary documentation goes here.</summary>
                <remarks>Longer comments can be associated with a type or member through the remarks tag</remarks>
            </member>
            <member name="F:SomeClass.m_Name">
                <summary>Store for the name property</summary>
            </member>
            <member name="M:SomeClass.#ctor">
                <summary>The class constructor.</summary>
            </member>
            <member name="M:SomeClass.SomeMethod(System.String)">
                <summary>Description for SomeMethod.</summary>
                <param name="s">Parameter description for s goes here</param>
                <seealso cref="T:System.String">You can use the cref attribute on any tag to reference a type or member and the compiler will check that the reference exists.</seealso>
            </member>
            <member name="M:SomeClass.SomeOtherMethod">
                <summary>Some other method.</summary>
                <returns>Return results are described through the returns tag.</returns>
                <seealso cref="M:SomeClass.SomeMethod(System.String)">Notice the use of the cref attribute to reference a specific method</seealso>
            </member>
            <member name="M:SomeClass.Main(System.String[])">
                <summary>The entry point for the application.</summary>
                <param name="args">A list of command line arguments</param>
            </member>
            <member name="P:SomeClass.Name">
                <summary>Name property</summary>
                <value>A value tag is used to describe the property value</value>
            </member>
        </members>
    </doc>
    ```

3. Soubor uložte a zavřete.

### <a name="to-create-a-text-template-to-test-the-directive-processor"></a>Vytvoření textové šablony pro testování procesoru direktiv

1. V sadě Visual Studio vytvořte projekt knihovny tříd jazyka C# nebo Visual Basic s názvem TemplateTest.

2. Přidejte nový soubor textové šablony s názvem TestDP.tt.

3. Ujistěte se, že **Custom Tool** vlastnost souboru testdp.TT nastavena na `TextTemplatingFileGenerator`.

4. Změňte obsah souboru TestDP.tt na následující text.

    > [!NOTE]
    > Nahraďte řetězec `<YOUR PATH>` s cestou *DocFile.xml* souboru.

    Jazyk textové šablony se nemusí shodovat s jazykem procesoru direktiv.

    ```csharp
    <#@ assembly name="System.Xml" #>
    <#@ template debug="true" #>
    <#@ output extension=".txt" #>

    <#  // This will call the custom directive processor. #>
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>

    <#  // Uncomment this line if you want to see the generated transformation class. #>
    <#  // System.Diagnostics.Debugger.Break(); #>

    <#  // This will use the results of the directive processor. #>
    <#  // The directive processor has read the XML and stored it in Document0. #>
    <#
        XmlNode node = Document0.DocumentElement.SelectSingleNode("members");

        foreach (XmlNode member in node.ChildNodes)
        {
            XmlNode name = member.Attributes.GetNamedItem("name");
            WriteLine("{0,7}:  {1}", "Name", name.Value);

            foreach (XmlNode comment in member.ChildNodes)
            {
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText);
            }
            WriteLine("");
        }
    #>

    <# // You can call the directive processor again and pass it a different file. #>
    <# // @ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\<Your Second File>" #>

    <#  // To use the results of the second directive call, use Document1. #>
    <#
        // XmlNode node2 = Document1.DocumentElement.SelectSingleNode("members");

        // ...
    #>
    ```

    ```vb
    <#@ assembly name="System.Xml" #>
    <#@ template debug="true" language="vb" #>
    <#@ output extension=".txt" #>

    <#  ' This will call the custom directive processor. #>
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>

    <#  ' Uncomment this line if you want to see the generated transformation class. #>
    <#  ' System.Diagnostics.Debugger.Break() #>

    <#  ' This will use the results of the directive processor. #>
    <#  ' The directive processor has read the XML and stored it in Document0. #>
    <#
        Dim node as XmlNode = Document0.DocumentElement.SelectSingleNode("members")

        Dim member As XmlNode
        For Each member In node.ChildNodes

            Dim name As XmlNode = member.Attributes.GetNamedItem("name")
            WriteLine("{0,7}:  {1}", "Name", name.Value)

            Dim comment As XmlNode
            For Each comment In member.ChildNodes
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText)
            Next

            WriteLine("")
        Next
    #>

    <# ' You can call the directive processor again and pass it a different file. #>
    <# ' @ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFileTwo.xml" #>

    <#  ' To use the results of the second directive call, use Document1. #>
    <#
        ' node = Document1.DocumentElement.SelectSingleNode("members")

        ' ...
    #>
    ```

    > [!NOTE]
    > V tomto příkladu, hodnota proměnné `Processor` parametr `CustomDirectiveProcessor`. Hodnota `Processor` parametru musí odpovídat názvu klíče registru procesoru.

5. Na **souboru** nabídce zvolte **Uložit vše**.

### <a name="to-test-the-directive-processor"></a>Testování procesoru direktiv

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na souboru TestDP.tt a pak klikněte na tlačítko **spustit vlastní nástroj**.

   Pro uživatele jazyka Visual Basic, testdp.txt nemusí v **Průzkumníka řešení** ve výchozím nastavení. Chcete-li zobrazit všechny soubory přiřazené k projektu, otevřete **projektu** nabídky a klikněte na tlačítko **zobrazit všechny soubory**.

2. V **Průzkumníka řešení**, rozbalte uzel TestDP.txt a potom dvakrát klikněte na panel TestDP.txt a otevře se v editoru.

    Zobrazí se vygenerovaný textový výstup. Výstup by měl vypadat takto:

    ```text
       Name:  T:SomeClass
    summary:  Class level summary documentation goes here.
    remarks:  Longer comments can be associated with a type or member through the remarks tag

       Name:  F:SomeClass.m_Name
    summary:  Store for the name property

       Name:  M:SomeClass.#ctor
    summary:  The class constructor.

       Name:  M:SomeClass.SomeMethod(System.String)
    summary:  Description for SomeMethod.
      param:  Parameter description for s goes here
    seealso:  You can use the cref attribute on any tag to reference a type or member and the compiler will check that the reference exists.

       Name:  M:SomeClass.SomeOtherMethod
    summary:  Some other method.
    returns:  Return results are described through the returns tag.
    seealso:  Notice the use of the cref attribute to reference a specific method

       Name:  M:SomeClass.Main(System.String[])
    summary:  The entry point for the application.
      param:  A list of command line arguments

       Name:  P:SomeClass.Name
    summary:  Name property
      value:  A value tag is used to describe the property value
    ```

## <a name="add-html-to-generated-text"></a>Přidání kódu HTML k vygenerovanému textu

Po otestování vlastního procesoru direktiv můžete k vygenerovanému textu přidat kód HTML.

### <a name="to-add-html-to-the-generated-text"></a>Přidání kódu HTML k vygenerovanému textu

1. Nahraďte kód v *souboru TestDP.tt* následujícím kódem. Kód HTML je zvýrazněn. Nezapomeňte nahradit řetězec `YOUR PATH` s cestou *DocFile.xml* souboru.

    > [!NOTE]
    > Dodatečné otevírací \<# a zavírací #> značky oddělují kód příkazu od značek HTML.

    ```csharp
    <#@ assembly name="System.Xml" #>
    <#@ template debug="true" #>
    <#@ output extension=".htm" #>

    <#  // This will call the custom directive processor #>
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>

    <#  // Uncomment this line if you want to see the generated transformation class #>
    <#  // System.Diagnostics.Debugger.Break(); #>

    <html><body>

    <#  // This will use the results of the directive processor #>.
    <#  // The directive processor has read the XML and stored it in Document0#>.
    <#
        XmlNode node = Document0.DocumentElement.SelectSingleNode("members");

        foreach (XmlNode member in node.ChildNodes)
        {
    #>
    <h3>
    <#
            XmlNode name = member.Attributes.GetNamedItem("name");
            WriteLine("{0,7}:  {1}", "Name", name.Value);
    #>
    </h3>
    <#
            foreach (XmlNode comment in member.ChildNodes)
            {
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText);
    #>
    <br/>
    <#
            }
        }
    #>
    </body></html>
    ```

    ```vb
    <#@ assembly name="System.Xml" #>
    <#@ template debug="true" language="vb" #>
    <#@ output extension=".htm" #>

    <#  ' This will call the custom directive processor #>
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>

    <#  ' Uncomment this line if you want to see the generated transformation class #>
    <#  ' System.Diagnostics.Debugger.Break() #>

    <html><body>

    <#  ' This will use the results of the directive processor #>.
    <#  ' The directive processor has read the XML and stored it in Document0#>.
    <#
        Dim node as XmlNode = Document0.DocumentElement.SelectSingleNode("members")

        Dim member As XmlNode
        For Each member In node.ChildNodes
    #>
    <h3>
    <#
            Dim name As XmlNode = member.Attributes.GetNamedItem("name")
            WriteLine("{0,7}:  {1}", "Name", name.Value)
    #>
    </h3>
    <#
            Dim comment As XmlNode
            For Each comment In member.ChildNodes
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText)
    #>
    <br/>
    <#
            Next
        Next
    #>
    </body></html>
    ```

2. Na **souboru** nabídky, klikněte na tlačítko **uložit TestDP.txt**.

3. Chcete-li zobrazit ve výstupu v prohlížeči v **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor TestDP.htm a klikněte na tlačítko **zobrazit v prohlížeči**.

   Výstup by měl být stejný jako původní text, s výjimkou má formát HTML. Název každé položky se zobrazí tučným písmem.

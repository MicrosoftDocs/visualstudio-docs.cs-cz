---
title: Volání transformací textu v rozšíření VS
description: Zjistěte, jak můžete pomocí služby šablon textu transformovat textové šablony. Zjistěte také, jak získat službu STextTemplating a přetypovat ji na ITextTemplating.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 71f376cbe0ffd6c2716802977f1570aa5036fcdb
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386771"
---
# <a name="invoke-text-transformation-in-a-visual-studio-extension"></a>Vyvolání transformace textu v Visual Studio rozšíření

Pokud píšete rozšíření Visual Studio, jako je příkaz nabídky nebo jazyk specifický pro [doménu,](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)můžete k transformaci textových šablon použít službu šablon textu. Získejte [službu STextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932394(v=vs.110)) a přetypování na [ITextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110)).

## <a name="get-the-text-templating-service"></a>Získání služby šablonování textu

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = ...; // An instance of EnvDTE, for example

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;

// Process a text template:
string result = t4.ProcessTemplate(filePath, System.IO.File.ReadAllText(filePath));
```

## <a name="pass-parameters-to-the-template"></a>Předání parametrů šabloně

 Do šablony můžete předávat parametry. Uvnitř šablony můžete získat hodnoty parametrů pomocí `<#@parameter#>` direktivy .

 Jako typ parametru je nutné použít typ, který lze serializovat nebo zařadit. To znamená, že typ musí být deklarován pomocí <xref:System.SerializableAttribute> , nebo musí být odvozen z <xref:System.MarshalByRefObject> . Toto omezení je nezbytné, protože textová šablona se vykonává v samostatné doméně AppDomain. Všechny předdefinované typy, například **System.String** a **System.Int32,** jsou serializovatelné.

 Pro předání hodnot parametrů může volající kód umístit hodnoty buď do `Session` slovníku, nebo do objektu <xref:System.Runtime.Remoting.Messaging.CallContext> .

 Následující příklad používá obě metody k transformaci krátké testovací šablony:

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = dte;

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost sessionHost = t4 as ITextTemplatingSessionHost;

// Create a Session in which to pass parameters:
sessionHost.Session = sessionHost.CreateSession();
sessionHost.Session["parameter1"] = "Hello";
sessionHost.Session["parameter2"] = DateTime.Now;

// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("parameter3", 42);

// Process a text template:
string result = t4.ProcessTemplate("",
   // This is the test template:
   "<#@parameter type=\"System.String\" name=\"parameter1\"#>"
 + "<#@parameter type=\"System.DateTime\" name=\"parameter2\"#>"
 + "<#@parameter type=\"System.Int32\" name=\"parameter3\"#>"
 + "Test: <#=parameter1#>    <#=parameter2#>    <#=parameter3#>");

// This test code yields a result similar to the following line:
//     Test: Hello    07/06/2010 12:37:45    42
```

## <a name="error-reporting-and-the-output-directive"></a>Hlášení chyb a direktiva output

Všechny chyby, ke které během zpracování dojde, se zobrazí v Visual Studio chybovém okně. Kromě toho můžete být upozorněni na chyby zadáním zpětného volání, které implementuje [ITextTemplatingCallback](/previous-versions/visualstudio/visual-studio-2012/bb932397(v=vs.110)).

Pokud chcete výsledný řetězec zapsat do souboru, můžete chtít vědět, jaká přípona souboru a kódování byla zadána v `<#@output#>` direktivě v šabloně. Tyto informace budou do zpětného volání rovněž předány. Další informace najdete v tématu [T4 Output – direktiva](../modeling/t4-output-directive.md).

```csharp
void ProcessMyTemplate(string MyTemplateFile)
{
  string templateContent = File.ReadAllText(MyTemplateFile);
  T4Callback cb = new T4Callback();
  // Process a text template:
  string result = t4.ProcessTemplate(MyTemplateFile, templateContent, cb);
  // If there was an output directive in the MyTemplateFile,
  // then cb.SetFileExtension() will have been called.
  // Determine the output file name:
  string resultFileName =
    Path.Combine(Path.GetDirectoryName(MyTemplateFile),
        Path.GetFileNameWithoutExtension(MyTemplateFile))
      + cb.fileExtension;
  // Write the processed output to file:
  File.WriteAllText(resultFileName, result, cb.outputEncoding);
  // Append any error messages:
  if (cb.errorMessages.Count > 0)
  {
    File.AppendAllLines(resultFileName, cb.errorMessages);
  }
}

class T4Callback : ITextTemplatingCallback
{
  public List<string> errorMessages = new List<string>();
  public string fileExtension = ".txt";
  public Encoding outputEncoding = Encoding.UTF8;

  public void ErrorCallback(bool warning, string message, int line, int column)
  { errorMessages.Add(message); }

  public void SetFileExtension(string extension)
  { fileExtension = extension; }

  public void SetOutputEncoding(Encoding encoding, bool fromOutputDirective)
  { outputEncoding = encoding; }
}
```

Kód lze testovat pomocí souboru šablony, který je podobný následujícímu:

```
<#@output extension=".htm" encoding="ASCII"#>
<# int unused;  // Compiler warning "unused variable"
#>
Sample text.
```

Upozornění kompilátoru se zobrazí v Visual Studio chybových oken a také vygeneruje volání `ErrorCallback` .

## <a name="reference-parameters"></a>Parametry odkazu

Hodnoty můžete předat z textové šablony pomocí třídy parametrů, která je odvozena z <xref:System.MarshalByRefObject> .

## <a name="related-articles"></a>Související články

Vygenerování textu z předzpracované textové šablony: Zavolejte `TransformText()` metodu vygenerované třídy. Další informace najdete v tématu Generování textu za běhu pomocí [textových šablon T4.](../modeling/run-time-text-generation-with-t4-text-templates.md)

Generování textu mimo příponu Visual Studio: Definujte vlastního hostitele. Další informace najdete v tématu [Zpracování textových šablon pomocí vlastního hostitele](../modeling/processing-text-templates-by-using-a-custom-host.md).

Pokud chcete vygenerovat zdrojový kód, který lze později zkompilovat a spustit: Zavolejte metodu [PreprocessTemplate](/previous-versions/visualstudio/visual-studio-2012/ee844321(v=vs.110)) třídy [ITextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110)).

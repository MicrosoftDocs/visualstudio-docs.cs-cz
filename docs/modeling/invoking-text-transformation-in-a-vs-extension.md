---
title: Volání transformací textu v rozšíření VS
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 01a2b4863736b22e08cf2075e6402d836e9cc671
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926797"
---
# <a name="invoking-text-transformation-in-a-vs-extension"></a>Volání transformací textu v rozšíření VS
Pokud píšete rozšíření sady Visual Studio, například příkaz nabídky nebo [jazyka specifického pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md), můžete použít službu šablonování textu k transformaci šablon textu. Získejte <xref:Microsoft.VisualStudio.TextTemplating.VSHost.STextTemplating> služby a přetypovat ji na <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>.

## <a name="getting-the-text-templating-service"></a>Získání služby šablonování textu

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

## <a name="passing-parameters-to-the-template"></a>Předání parametrů do šablony
 Do šablony můžete předávat parametry. Uvnitř šablony lze hodnoty parametrů získat pomocí `<#@parameter#>` směrnice.

 Jako typ parametru je nutné použít typ, který lze serializovat nebo zařadit. To znamená, typ musí být deklarován s <xref:System.SerializableAttribute>, nebo musí být odvozen od <xref:System.MarshalByRefObject>. Toto omezení je nezbytné, protože textová šablona se vykonává v samostatné doméně AppDomain. Všechny vestavěné typy, jako **System.String** a **System.Int32** jsou serializovatelné.

 K předání hodnot parametru volající kód umístit hodnoty buď v `Session` slovníku, nebo <xref:System.Runtime.Remoting.Messaging.CallContext>.

 Následující příklad používá obě metody k transformaci krátké testovací šablony:

```
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

## <a name="error-reporting-and-the-output-directive"></a>Hlášení chyb a direktiva output
 Všechny chyby, které vznikají při zpracování se zobrazí v okně chyb sady Visual Studio. Kromě toho můžete být upozorněni určením zpětného volání, která implementuje chyb <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplatingCallback>.

 Pokud chcete výsledný řetězec zapisovat do souboru, můžete chtít vědět, jaké přípony souboru a kódování byly zadané v `<#@output#>` direktiv v šabloně. Tyto informace budou do zpětného volání rovněž předány. Další informace najdete v tématu [T4 – direktiva Output](../modeling/t4-output-directive.md).

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

 V okně chyb sady Visual Studio se zobrazí upozornění kompilátoru, a také vygeneruje volání `ErrorCallback`.

## <a name="reference-parameters"></a>Parametry odkazu
 Můžete předat hodnoty ven z textové šablony pomocí třídy parametru, který je odvozen z <xref:System.MarshalByRefObject>.

## <a name="related-topics"></a>Související témata
 Vygenerování textu z Předzpracované textové šablony: volání `TransformText()` metody generované třídy. Další informace najdete v tématu [generování textu za běhu pomocí textových šablon T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Vygenerování textu mimo rozšíření sady Visual Studio: Definujte vlastního hostitele. Další informace najdete v tématu [zpracování textových šablon pomocí vlastního hostitele](../modeling/processing-text-templates-by-using-a-custom-host.md).

 Vygenerování zdrojového kódu, který lze později zkompilovat a spustit: volání `t4.PreprocessTemplate()` metoda <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>.

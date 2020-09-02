---
title: Vyvolání transformace textu v rozšíření VS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 64674976-841f-43cb-8e61-0645c8a89eec
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a87f84a945d9d79f6d481f7bcc9e656f7ec7bcbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646152"
---
# <a name="invoking-text-transformation-in-a-vs-extension"></a>Volání transformací textu v rozšíření VS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud píšete [rozšíření sady Visual Studio](https://msdn.microsoft.com/library/5b1b5db3-6005-44cf-83b0-e608d7764d14) , například příkaz nabídky nebo [jazyk specifický pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md), můžete k transformaci textových šablon použít službu šablonování textu. Získat službu [STextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932394(v=vs.110)) a přetypovat ji na [ITextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110)).

## <a name="getting-the-text-templating-service"></a>Získání služby šablonování textu

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider – how you do this depends on the context:
IServiceProvider serviceProvider = ...; // An instance of EnvDTE, for example

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;

// Process a text template:
string result = t4.ProcessTemplate(filePath, System.IO.File.ReadAllText(filePath));

```

## <a name="passing-parameters-to-the-template"></a>Předání parametrů do šablony
 Do šablony můžete předávat parametry. V šabloně můžete získat hodnoty parametrů pomocí `<#@parameter#>` direktivy.

 Jako typ parametru je nutné použít typ, který lze serializovat nebo zařadit. To znamená, že typ musí být deklarován s <xref:System.SerializableAttribute> , nebo musí být odvozen od <xref:System.MarshalByRefObject> . Toto omezení je nezbytné, protože textová šablona se vykonává v samostatné doméně AppDomain. Všechny předdefinované typy, jako je **System. String** a **System. Int32** , jsou serializovatelné.

 Pro předání hodnot parametrů může volající kód umístit hodnoty buď do `Session` slovníku, nebo do <xref:System.Runtime.Remoting.Messaging.CallContext> .

 Následující příklad používá obě metody k transformaci krátké testovací šablony:

```
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider – how you do this depends on the context:
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
 Všechny chyby, které vznikají při zpracování, se zobrazí v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okně chyb. Kromě toho můžete být upozorněni na chyby zadáním zpětného volání, které implementuje [ITextTemplatingCallback](/previous-versions/visualstudio/visual-studio-2012/bb932397(v=vs.110)).

 Pokud chcete výsledný řetězec zapsat do souboru, možná budete chtít zjistit, jaké přípony souborů a kódování byly zadány v `<#@output#>` direktivě v šabloně. Tyto informace budou do zpětného volání rovněž předány. Další informace najdete v tématu [direktiva výstupu T4](../modeling/t4-output-directive.md).

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

 V okně chyb se zobrazí upozornění kompilátoru [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a také se vygeneruje volání `ErrorCallback` .

## <a name="reference-parameters"></a>Parametry odkazu
 Můžete předat hodnoty z textové šablony pomocí třídy parametru, která je odvozena z <xref:System.MarshalByRefObject> .

## <a name="related-topics"></a>Související témata
 Pro vygenerování textu z předzpracované textové šablony: volejte `TransformText()` metodu generované třídy. Další informace najdete v tématu [generování textu v době běhu s textovými šablonami T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Vygenerování textu mimo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření: Definujte vlastního hostitele. Další informace najdete v tématu [zpracování textových šablon pomocí vlastního hostitele](../modeling/processing-text-templates-by-using-a-custom-host.md).

 Pro generování zdrojového kódu, který lze později zkompilovat a spustit: zavolejte metodu [PreprocessTemplate](/previous-versions/visualstudio/visual-studio-2012/ee844321(v=vs.110)) [ITextTemplating](/previous-versions/visualstudio/visual-studio-2012/bb932392(v=vs.110)).

---
title: Volání transformací textu v rozšíření VS | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64674976-841f-43cb-8e61-0645c8a89eec
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0751229e778e13375698f591d789edfd318b3ffc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298620"
---
# <a name="invoking-text-transformation-in-a-vs-extension"></a>Volání transformací textu v rozšíření VS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud píšete [rozšíření sady Visual Studio](http://msdn.microsoft.com/library/5b1b5db3-6005-44cf-83b0-e608d7764d14) například příkaz nabídky nebo [jazyka specifického pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md), můžete použít službu šablonování textu k transformaci šablon textu. Získejte <xref:Microsoft.VisualStudio.TextTemplating.VSHost.STextTemplating> služby a přetypovat ji na <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>.  
  
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
 Do šablony můžete předávat parametry. Uvnitř šablony lze hodnoty parametrů získat pomocí `<#@parameter#>` směrnice.  
  
 Jako typ parametru je nutné použít typ, který lze serializovat nebo zařadit. To znamená, typ musí být deklarován s <xref:System.SerializableAttribute>, nebo musí být odvozen od <xref:System.MarshalByRefObject>. Toto omezení je nezbytné, protože textová šablona se vykonává v samostatné doméně AppDomain. Všechny vestavěné typy, jako **System.String** a **System.Int32** jsou serializovatelné.  
  
 K předání hodnot parametru volající kód umístit hodnoty buď v `Session` slovníku, nebo <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
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
 Zobrazí se všechny chyby, které vznikají při zpracování v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okno chyb. Kromě toho můžete být upozorněni určením zpětného volání, která implementuje chyb <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplatingCallback>.  
  
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
  
 Zobrazí se upozornění kompilátoru v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okno chyb a také vygeneruje volání `ErrorCallback`.  
  
## <a name="reference-parameters"></a>Parametry odkazu  
 Můžete předat hodnoty ven z textové šablony pomocí třídy parametru, který je odvozen z <xref:System.MarshalByRefObject>.  
  
## <a name="related-topics"></a>Související témata  
 Vygenerování textu z předzpracované textové šablony:  
 Volání `TransformText()` metody generované třídy. Další informace najdete v tématu [generování textu za běhu pomocí textových šablon T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Vygenerování textu mimo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření:  
 Definujte vlastního hostitele. Další informace najdete v tématu [zpracování textových šablon pomocí vlastního hostitele](../modeling/processing-text-templates-by-using-a-custom-host.md).  
  
 Vygenerování zdrojového kódu, který lze později zkompilovat a spustit:  
 Volání `t4.PreprocessTemplate()` metoda <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>.




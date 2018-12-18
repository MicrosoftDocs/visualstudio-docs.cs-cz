---
title: T4 – Direktiva Parameter | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d590387-1d9d-40a5-a72c-65fae7a8bdf3
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 87e493667af1626cd97e575ddb614e7fd12c21d3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294551"
---
# <a name="t4-parameter-directive"></a>T4 – direktiva Parameter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] textové šablony `parameter` – direktiva deklaruje vlastnosti ve vašem kódu šablony, které jsou inicializovány z hodnoty předané z externí kontextu. Tyto hodnoty můžete nastavit, pokud píšete kód, který vyvolá transformace textu.  
  
## <a name="using-the-parameter-directive"></a>Pomocí – direktiva Parameter  
  
```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 `parameter` – Direktiva deklaruje vlastnosti ve vašem kódu šablony, které jsou inicializovány z hodnoty předané z externí kontextu. Tyto hodnoty můžete nastavit, pokud píšete kód, který vyvolá transformace textu. Hodnoty mohou být předány buď `Session` slovníku, nebo v <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 Je možné deklarovat parametry typu lze používat vzdáleně. To znamená, typ musí být deklarován s <xref:System.SerializableAttribute>, nebo musí být odvozen od <xref:System.MarshalByRefObject>. Díky tomu hodnoty parametrů, které mají být předány do domény aplikace 00Z zpracování šablony.  
  
 Můžete například napsat textové šablony s následujícím obsahem:  
  
```  
<#@ template language="C#" #>  
  
<#@ parameter type="System.Int32" name="TimesToRepeat" #>  
  
<# for (int i = 0; i < TimesToRepeat; i++) { #>  
Line <#= i #>  
<# } #>  
  
```  
  
## <a name="passing-parameter-values-to-a-template"></a>Předávání hodnot parametrů do šablony  
 Pokud píšete [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření například příkaz nabídky nebo obslužnou rutinu události, může zpracovat šablonu použít službu šablonování textu:  
  
```csharp  
// Get a service provider – how you do this depends on the context:  
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example   
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;  
// Create a Session in which to pass parameters:  
host.Session = host.CreateSession();  
// Add parameter values to the Session:  
session["TimesToRepeat"] = 5;  
// Process a text template:  
string result = t4.ProcessTemplate("MyTemplateFile.t4",  
  System.IO.File.ReadAllText("MyTemplateFile.t4"));  
  
```  
  
## <a name="passing-values-in-the-call-context"></a>Předávání hodnot v rámci volání  
 Můžete také předat hodnoty jako logické data v <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 Následující příklad předává hodnoty oběma způsoby:  
  
```csharp  
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;  
host.Session = host.CreateSession();  
// Pass a value in Session:  
host.Session["p1"] = 32;  
// Pass another value in CallContext:  
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");  
  
// Process a small template inline:  
string result = t4.ProcessTemplate("",   
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"  
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"  
 + "Test <#=p1#> <#=p2#>");  
  
// Result value is:  
//     Test 32 test  
  
```  
  
## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Předávání hodnot textová šablona běhu (Předzpracovaný)  
 Není obvykle nutné použít `<#@parameter#>` direktiv s využitím šablon textu za běhu (Předzpracované). Místo toho můžete definovat další konstruktor nebo nastavitelnou vlastnost pro vygenerovaný kód, pomocí kterého předání hodnot parametrů. Další informace najdete v tématu [generování textu za běhu pomocí textových šablon T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Nicméně pokud chcete použít `<#@parameter>` v šabloně za běhu, můžete předat hodnoty do něj pomocí slovníku relací. Jako příklad předpokládejme, že jste vytvořili soubor jako předzpracovaná šablona volá `PreTextTemplate1`. Šablony ve svém programu lze vyvolat pomocí následujícího kódu.  
  
```csharp  
PreTextTemplate1 t = new PreTextTemplate1();  
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();  
t.Session["TimesToRepeat"] = 5;  
// Add other parameter values to t.Session here.  
t.Initialize(); // Must call this to transfer values.  
string resultText = t.TransformText();  
  
```  
  
## <a name="obtaining-arguments-from-texttemplateexe"></a>Získání argumenty z TextTemplate.exe  
  
> [!IMPORTANT]
>  `parameter` Směrnice nenačte hodnoty nastavené v `–a` parametr `TextTransform.exe` nástroj. K získání těchto hodnot, nastavte `hostSpecific="true"` v `template` směrnice a použití `this.Host.ResolveParameterValue("","","argName")`.




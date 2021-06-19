---
title: T4 – direktiva Parameter
description: V tomto Visual Studio deklaruje direktiva parameter vlastnosti v kódu šablony, které jsou inicializovány z hodnot předáovaných z externího kontextu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8ef80179d43996669b9d883fd2ca9163208d18d7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386095"
---
# <a name="t4-parameter-directive"></a>T4 – direktiva Parameter

V Visual Studio šablony deklaruje direktiva vlastnosti v kódu šablony, které jsou inicializovány z hodnot předáovaných `parameter` z externího kontextu. Tyto hodnoty můžete nastavit, pokud napíšete kód, který vyvolá transformaci textu.

## <a name="using-the-parameter-directive"></a>Použití direktivy Parameter

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 Direktiva `parameter` deklaruje vlastnosti v kódu šablony, které jsou inicializovány z hodnot předáovaných z externího kontextu. Tyto hodnoty můžete nastavit, pokud napíšete kód, který vyvolá transformaci textu. Hodnoty lze předat buď ve `Session` slovníku, nebo v <xref:System.Runtime.Remoting.Messaging.CallContext> .

 Můžete deklarovat parametry libovolného spustitelného typu. To znamená, že typ musí být deklarován pomocí <xref:System.SerializableAttribute> nebo musí být odvozen z <xref:System.MarshalByRefObject> . To umožňuje předat hodnoty parametrů do domény AppDomain, ve které je šablona zpracována.

 Můžete například napsat textovou šablonu s následujícím obsahem:

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>
```

## <a name="passing-parameter-values-to-a-template"></a>Předávání hodnot parametrů šabloně
 Pokud píšete rozšíření Visual Studio, jako je příkaz nabídky nebo obslužná rutina události, můžete šablonu zpracovat pomocí služby šablonování textu:

```csharp
// Get a service provider - how you do this depends on the context:
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

## <a name="passing-values-in-the-call-context"></a>Předávání hodnot v kontextu volání
 Alternativně můžete předat hodnoty jako logická data v <xref:System.Runtime.Remoting.Messaging.CallContext> .

 Následující příklad předává hodnoty pomocí obou metod:

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

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Předávání hodnot do Run-Time (předzpracované) textové šablony
 Obvykle není nutné používat direktivu s textovou šablonou `<#@parameter#>` za běhu (předzpracované). Místo toho můžete definovat další konstruktor nebo nastavitelné vlastnosti pro vygenerovaný kód, jehož prostřednictvím předáte hodnoty parametrů. Další informace najdete v tématu Generování textu za běhu pomocí [textových šablon T4.](../modeling/run-time-text-generation-with-t4-text-templates.md)

 Pokud však chcete použít v šabloně za běhu, můžete do ní předat hodnoty `<#@parameter>` pomocí slovníku Relace. Předpokládejme například, že jste soubor vytvořili jako předzpracovanou šablonu s názvem `PreTextTemplate1` . Šablonu v programu můžete vyvolat pomocí následujícího kódu.

```csharp
PreTextTemplate1 t = new PreTextTemplate1();
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();
t.Session["TimesToRepeat"] = 5;
// Add other parameter values to t.Session here.
t.Initialize(); // Must call this to transfer values.
string resultText = t.TransformText();
```

## <a name="obtaining-arguments-from-texttemplateexe"></a>Získání argumentů z TextTemplate.exe

> [!IMPORTANT]
> Direktiva `parameter` nenačítá hodnoty nastavené `-a` v parametru `TextTransform.exe` nástroje. Pokud chcete tyto hodnoty získat, `hostSpecific="true"` nastavte v direktivě a `template` použijte `this.Host.ResolveParameterValue("","","argName")` .

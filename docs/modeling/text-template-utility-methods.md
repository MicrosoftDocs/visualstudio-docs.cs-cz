---
title: Pomocné metody textových šablon
description: Seznamte se s různými metodami nástrojů textových šablon, které jsou k dispozici při psaní kódu v Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b45bf6418562da5315c986a64a1295c137e982d6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388682"
---
# <a name="text-template-utility-methods"></a>Pomocné metody textových šablon

Existuje několik metod, které jsou vždy k dispozici při psaní kódu v Visual Studio textové šabloně. Tyto metody jsou definovány v <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> souboru .

> [!TIP]
> Můžete také použít jiné metody a služby poskytované hostitelským prostředím v běžné (nezpracované) textové šabloně. Můžete například vyřešit cesty k souborům, protokolovat chyby a získat služby poskytované Visual Studio a všechny načtené balíčky. Další informace najdete v tématu [Přístup Visual Studio z textové šablony](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\)).

## <a name="write-methods"></a>Metody zápisu

Místo použití bloku kódu výrazu můžete k připojení textu uvnitř standardního bloku kódu použít metody `Write()` `WriteLine()` a . Následující dva bloky kódu jsou funkčně ekvivalentní.

### <a name="code-block-with-an-expression-block"></a>Blok kódu s blokem výrazu

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

### <a name="code-block-using-writeline"></a>Blok kódu využívající WriteLine()

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

Může být užitečné použít jednu z těchto užitkových metod místo bloku výrazů uvnitř dlouhého bloku kódu s vnořenými řídicími strukturami.

Metody a mají dvě přetížení, jedno, které přebírá jeden řetězcový parametr, a jedno, které přebírá složený formátovací řetězec a pole objektů, které se mají zahrnout do řetězce `Write()` `WriteLine()` (jako `Console.WriteLine()` metoda ). Následující dvě použití jsou `WriteLine()` funkčně ekvivalentní:

```
<#
    string msg = "Say: {0}, {1}, {2}";
    string s1 = "hello";
    string s2 = "goodbye";
    string s3 = "farewell";

    WriteLine(msg, s1, s2, s3);
    WriteLine("Say: hello, goodbye, farewell");
#>
```

## <a name="indentation-methods"></a>Metody odsazení

K formátování výstupu textové šablony můžete použít metody odsazení. Třída <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> má řetězcovou vlastnost, která zobrazuje aktuální odsazení v textové šabloně, a pole, které je seznamem přidaných `CurrentIndent` `indentLengths` odsazení. Pomocí metody můžete přidat odsazení a odečíst `PushIndent()` odsazení pomocí `PopIndent()` metody . Pokud chcete odebrat všechna odsazení, použijte `ClearIndent()` metodu . Následující blok kódu ukazuje použití těchto metod:

```
<#
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    ClearIndent();
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
#>
```

Tento blok kódu vytvoří následující výstup:

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>Metody chyb a upozornění

K přidání zpráv do aplikace můžete použít chybové a varovné Visual Studio Seznam chyb. Následující kód například přidá chybovou zprávu do Seznam chyb.

```
<#
  try
  {
    string str = null;
    Write(str.Length.ToString());
  }
  catch (Exception e)
  {
    Error(e.Message);
  }
#>
```

## <a name="access-to-host-and-service-provider"></a>Přístup k hostiteli a poskytovateli služeb

Vlastnost může `this.Host` poskytnout přístup k vlastnostem vystaveným hostitelem, který spouští šablonu. Pokud chcete `this.Host` použít , musíte nastavit atribut v `hostspecific` `<@template#>` direktivě :

`<#@template ... hostspecific="true" #>`

Typ závisí `this.Host` na typu hostitele, ve kterém je šablona spuštěná. V šabloně, která běží v Visual Studio, můžete přetypovat na , abyste získali přístup ke `this.Host` službám, jako je integrované vývojové prostředí `IServiceProvider` (IDE). Příklad:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Použití jiné sady užitkových metod

V rámci procesu generování textu se soubor šablony transformuje do třídy, která je vždy pojmenována a `GeneratedTextTransformation` dědí z <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> . Pokud chcete místo toho použít jinou sadu metod, můžete napsat vlastní třídu a zadat ji do direktivy šablony. Vaše třída musí dědit z <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

```
<#@ template inherits="MyUtilityClass" #>
```

Direktiva `assembly` slouží k odkazování na sestavení, kde lze najít zkompilované třídy.

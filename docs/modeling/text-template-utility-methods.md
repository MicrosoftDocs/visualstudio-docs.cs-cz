---
title: Pomocné metody textových šablon
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c55da4d58b717bc4d42b6fafdd084067b7e21a31
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591759"
---
# <a name="text-template-utility-methods"></a>Pomocné metody textových šablon

Existuje několik metod, které jsou vždy k dispozici při psaní kódu v textové šabloně sady Visual Studio. Tyto metody jsou definovány v <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

> [!TIP]
> Můžete také použít jiné metody a služby poskytované hostitelským prostředím v běžné (nezpracované) textové šabloně. Můžete například vyřešit cesty k souborům, protokolovat chyby a získávat služby, které poskytuje Visual Studio a všechny načtené balíčky. Další informace naleznete v tématu [přístup k aplikaci Visual Studio z textové šablony](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\)).

## <a name="write-methods"></a>Metody zápisu

Můžete použít `Write()` `WriteLine()` metody a k připojení textu uvnitř bloku standardního kódu namísto použití bloku kódu výrazu. Následující dva bloky kódu jsou funkčně ekvivalentní.

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

### <a name="code-block-using-writeline"></a>Blok kódu pomocí metody WriteLine ()

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

Může být užitečné použít jednu z těchto pomocných metod namísto bloku výrazu uvnitř dlouhého bloku kódu s vnořenými řídicími strukturami.

`Write()`Metody a `WriteLine()` mají dvě přetížení, jednu, která přijímá jeden řetězcový parametr a jednu, která má složený řetězec formátu a pole objektů, které mají být zahrnuty do řetězce (například `Console.WriteLine()` metody). Následující dvě použití `WriteLine()` jsou funkčně ekvivalentní:

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

## <a name="indentation-methods"></a>Metody odsazování

Můžete použít metody odsazení k formátování výstupu šablony textu. <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>Třída má `CurrentIndent` řetězcovou vlastnost, která zobrazuje aktuální odsazení v textové šabloně a `indentLengths` pole, které je seznam odsazení, která byla přidána. Můžete přidat odsazení s `PushIndent()` metodou a odečíst odsazení `PopIndent()` metodou. Chcete-li odebrat všechna odsazení, použijte `ClearIndent()` metodu. Následující blok kódu ukazuje použití těchto metod:

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

Tento blok kódu generuje následující výstup:

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>Metody chyb a upozornění

Chcete-li přidat zprávy do Seznam chyb sady Visual Studio, můžete použít metody nástroje Error a Warning. Například následující kód přidá chybovou zprávu do Seznam chyb.

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

Vlastnost `this.Host` může poskytovat přístup k vlastnostem vystaveným hostitelem, který spouští šablonu. Chcete-li použít `this.Host` , musíte nastavit `hostspecific` atribut v `<@template#>` direktivě:

`<#@template ... hostspecific="true" #>`

Typ `this.Host` závisí na typu hostitele, ve kterém je šablona spuštěna. V šabloně, která je spuštěna v aplikaci Visual Studio, můžete přetypovat `this.Host` na, `IServiceProvider` abyste získali přístup ke službám, jako je IDE. Příklad:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Použití jiné sady pomocných metod

V rámci procesu generování textu je soubor šablony transformován na třídu, která je vždy pojmenována `GeneratedTextTransformation` a dědí z <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> . Pokud místo toho chcete použít jinou sadu metod, můžete napsat vlastní třídu a zadat ji v direktivě šablony. Vaše třída musí dědit z <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

```
<#@ template inherits="MyUtilityClass" #>
```

Použijte `assembly` direktivu pro odkaz na sestavení, kde lze nalézt zkompilovanou třídu.

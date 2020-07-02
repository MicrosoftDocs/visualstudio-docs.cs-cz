---
title: Způsoby ladění kódu XSLT
ms.date: 03/05/2019
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: d8e3885aa895cec5ed080b7a8b4d22522d2e9edf
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815614"
---
# <a name="debugging-xslt"></a>Ladění XSLT

V aplikaci Visual Studio můžete ladit kód XSLT. Ladicí program XSLT podporuje nastavení zarážek, zobrazení stavů spuštění XSLT atd. Ladicí program XSLT lze použít k ladění šablon stylů XSLT nebo aplikací XSLT.

Můžete spustit kód po jednotlivých řádcích, a to pomocí krokování do, krokování nad nebo rozkrokování z kódu. Příkazy pro použití funkce pro krokování kódu v ladicím programu XSLT jsou stejné jako u ostatních ladicích programů sady Visual Studio.

Jakmile začnete s laděním, otevře se v ladicím programu XSLT okna, ve kterém se zobrazí vstupní dokument a výstup XSLT.

> [!NOTE]
> Ladicí program XSLT je k dispozici pouze v edicích Professional a Enterprise sady Visual Studio.

## <a name="debug-from-the-xml-editor"></a>Ladění z editoru XML

Můžete spustit ladicí program, pokud máte šablonu stylů nebo vstupní soubor XML otevřený v editoru. To vám umožní ladit při navrhování šablon stylů.

1. Otevřete šablonu stylů nebo soubor XML v aplikaci Visual Studio.

1. V nabídce **XML** vyberte **Spustit ladění XSLT** nebo stiskněte klávesu **ALT** + **F5**.

## <a name="debug-from-an-app-that-uses-xslt"></a>Ladění z aplikace, která používá XSLT

Při ladění aplikace můžete krokovat s XSLT. Po stisknutí klávesy **F11** na <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> volání může ladicí program krokovat kód XSLT.

> [!NOTE]
> Krokování na transformaci XSLT z <xref:System.Xml.Xsl.XslTransform> třídy není podporováno. <xref:System.Xml.Xsl.XslCompiledTransform>Třída je jediný procesor XSLT, který podporuje krokování do XSLT při ladění.

### <a name="to-start-debugging-an-xslt-application"></a>Spuštění ladění aplikace XSLT

1. Při vytváření instance <xref:System.Xml.Xsl.XslCompiledTransform> objektu nastavte `enableDebug` parametr na hodnotu `true` ve vašem kódu. To oznamuje procesoru XSLT k vytváření ladicích informací při kompilování kódu.

1. Stisknutím klávesy **F11** se můžete do kódu XSLT krokovat.

   Šablona stylů XSLT je načtena v novém okně dokumentu a spustí se ladicí program XSLT.

   Alternativně můžete přidat bod přerušení do seznamu stylů a spustit aplikaci.

### <a name="example"></a>Příklad

Následuje příklad programu C# XSLT. Ukazuje, jak povolit ladění XSLT.

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Xsl;

namespace ConsoleApplication
{
  class Program
  {
    private const string sourceFile = @"c:\data\xsl_files\books.xml";
    private const string stylesheet = @"c:\data\xsl_files\below-average.xsl";
    private const string outputFile = @"c:\data\xsl_files\output.xml";

    static void Main(string[] args)
    {
      // Enable XSLT debugging.
      XslCompiledTransform xslt = new XslCompiledTransform(true);

      // Compile the style sheet.
      xslt.Load(stylesheet);

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="xslt-profiler"></a>Profiler XSLT

[Profiler XSLT](../xml-tools/xslt-profiler.md) je nástroj, který umožňuje vývojářům měřit, vyhodnocovat a cílit na problémy související s výkonem v kódu XSLT vytvořením podrobných sestav o výkonu XSLT. Další informace najdete v tématu [Profiler XSLT](../xml-tools/xslt-profiler.md).

## <a name="see-also"></a>Viz také:

- [Návod: ladění šablony stylů XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [První pohled na ladicí program sady Visual Studio](../debugger/debugger-feature-tour.md)
- [Základy ladění: zarážky](../debugger/using-breakpoints.md)

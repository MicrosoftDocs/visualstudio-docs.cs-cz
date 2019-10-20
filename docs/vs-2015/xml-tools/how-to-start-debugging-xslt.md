---
title: 'Postupy: spuštění ladění XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 8358335a-fcb0-45e0-a37e-45b43e49ec0a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 09471b9e62b758e4e02e054494ed108532bbd301
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656333"
---
# <a name="how-to-start-debugging-xslt"></a>Postupy: spuštění ladění XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ladicí program XSLT lze použít k ladění šablony stylů XSLT nebo aplikace XSLT. Při ladění můžete spustit kód po jednom řádku pomocí krokování do, krokování nad nebo rozkrokování z kódu. Příkazy pro použití funkce pro krokování kódu jsou u ladicího programu XSLT stejné jako pro ostatní ladicí programy sady Visual Studio. Jakmile začnete s laděním, otevře se v ladicím programu XSLT okna, ve kterém se zobrazí vstupní dokument a výstup XSLT.

## <a name="xml-editor"></a>Editor XML
 Ladicí program lze spustit z editoru XML. To vám umožní ladit při navrhování šablon stylů.

#### <a name="to-start-debugging-from-a-style-sheet"></a>Spuštění ladění ze seznamu stylů

1. Otevřete šablonu stylů v editoru XML.

2. V nabídce **XML** vyberte **ladit XSL** .

#### <a name="to-start-debugging-from-an-xml-input-document"></a>Spuštění ladění ze vstupního dokumentu XML

1. Otevřete dokument XML v editoru XML.

2. V nabídce **XML** vyberte **ladit XSL** .

## <a name="xslt-from-other-languages"></a>XSLT z jiných jazyků
 Při ladění aplikace můžete také Krokovat s transformací XSLT. Při stisknutí klávesy F11 ve <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> volání může ladicí program krokovat kód XSLT.

> [!NOTE]
> Krokování na transformaci XSLT z <xref:System.Xml.Xsl.XslTransform> třídy není podporováno. Třída <xref:System.Xml.Xsl.XslCompiledTransform> je jediným procesorem XSLT, který podporuje krokování do XSLT při ladění.

#### <a name="to-start-debugging-an-xslt-application"></a>Spuštění ladění aplikace XSLT

1. Při vytváření instance objektu <xref:System.Xml.Xsl.XslCompiledTransform> nastavte parametr `enableDebug` na `true` ve vašem kódu.

     To oznamuje procesoru XSLT k vytváření ladicích informací při kompilování kódu.

2. Stisknutím klávesy F11 se můžete do kódu XSLT krokovat.

     Šablona stylů XSLT je načtena v novém okně dokumentu a je spuštěn ladicí program XSLT.

     Alternativně můžete přidat bod přerušení do seznamu stylů a spustit aplikaci.

### <a name="example"></a>Příklad
 Následuje příklad programu C# XSLT. Ukazuje, jak povolit ladění XSLT.

```
using System;
using System.IO;
using System.Xml;
using System.Xml.Xsl;

namespace ConsoleApplication
{
  class Program
  {
    private const string sourceFile = @"c:\data\xsl_files\books.xml";
    private const string stylesheet = @"c:\data\xsl_files\belowAvg.xsl";
    private const string outputFile = @"c:\data\xsl_files\output.xml";

    static void Main(string[] args)
    {
      // Enable XSLT debugging.
      XslCompiledTransform xslt = new XslCompiledTransform(true);

      // Compile the style sheet.
      xslt.Load(stylesheet)

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="see-also"></a>Viz také
 [Návod: ladění šablony stylů XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) [Přehled krokování kódu](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9)

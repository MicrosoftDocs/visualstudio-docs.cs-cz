---
title: 'CA3077: Nezabezpečené zpracování v návrhu rozhraní API, dokumentu XML a čtečce textu XML | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0e75f86b958d0f2602a3f32830e8c6f18c185584
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925073"
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077: Nezabezpečené zpracování v návrhu rozhraní API, dokumentu XML a čtečce textu XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InsecureDTDProcessingInAPIDesign|
|CheckId|CA3077|
|Kategorie|Microsoft.Security|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina
 Při navrhování rozhraní API odvozený od XMLDocument a XMLTextReader, mějte na paměti z <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>.  Použití nezabezpečené DTDProcessing instancí, při odkazování na řešení externí entity zdroje nebo nastavení nezabezpečené hodnot v souboru XML může způsobit zpřístupnění informací.

## <a name="rule-description"></a>Popis pravidla
 A [dokumentu typ definice (DTD)](https://msdn.microsoft.com/library/aa468547.aspx) je jedním ze dvou způsobů analyzátor jazyka XML můžete určit platnosti dokumentu, podle definice [World Wide Web Consortium (W3C) značky XML (Extensible Language) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Toto pravidlo vyhledá vlastnosti a instance, kde je nedůvěryhodná data přijat upozornit vývojáře o potenciál [informacím](http://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c) hrozeb, které mohou vést k [útok na dostupnost služby (DoS)](http://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600) útoky. Toto pravidlo aktivuje, když:

-   <xref:System.Xml.XmlDocument> nebo <xref:System.Xml.XmlTextReader> třídy použijte výchozí překladač hodnoty pro zpracování deklarace DTD.

-   Žádný konstruktor je definován pro dokument XML nebo odvozené třídy XmlTextReader nebo bez zabezpečeného hodnota se používá pro <xref:System.Xml.XmlResolver>.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

-   Zachytit a zpracovat všechny výjimky XmlTextReader správně, aby se zabránilo zpřístupnění informací cestu.

-   Použití <xref:System.Xml.XmlSecureResolver>místo objekt XmlResolver omezit prostředky XmlTextReader přístup.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud si nejste jisti, že vstup je znám jako z důvěryhodného zdroje, nepotlačujte pravidlo z tohoto upozornění.

## <a name="pseudo-code-examples"></a>Příklady pseudo kódu

### <a name="violation"></a>Porušení

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass () {} // warn
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2() // warn
        {
        }
    }
}
```

### <a name="solution"></a>Řešení

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass ()
        {
            XmlResolver = null;
        }
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2()
        {
               XmlResolver = null;
        }
    }
}
```




---
title: 'CA3077: nezabezpečené zpracování v návrhu rozhraní API, dokumentu XML a čtečce textu XML | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c0d6a6f6ab42d69d4503741f6625627c46d4ef77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545103"
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077: Nezabezpečené zpracování v návrhu rozhraní API, dokumentu XML a čtečce textu XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|InsecureDTDProcessingInAPIDesign|
|CheckId|CA3077|
|Kategorie|Microsoft.Security|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Při navrhování rozhraní API odvozeného z XMLDocument a XMLTextReader si zavědomi <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> .  Použití nezabezpečených instancí DTDProcessing při odkazování na zdroje externích entit nebo jejich překládání na nezabezpečené hodnoty v XML může vést k odhalení informací.

## <a name="rule-description"></a>Popis pravidla
 [Definice typu dokumentu (DTD)](https://msdn.microsoft.com/library/aa468547.aspx) je jedním ze dvou způsobů, jak může analyzátor XML určit platnost dokumentu, jak je definováno v [konsorcium World Wide Web (W3C) jazyk XML (Extensible Markup Language) (XML) 1,0](https://www.w3.org/TR/2008/REC-xml-20081126/). Toto pravidlo vyhledává vlastnosti a instance, kde jsou přijímána nedůvěryhodná data, aby upozornila vývojáře na potenciální hrozby [zpřístupnění informací](https://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c) , což může vést k útokům DOS [(Denial of Service)](https://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600) . Toto pravidlo se aktivuje v těchto případech:

- <xref:System.Xml.XmlDocument><xref:System.Xml.XmlTextReader>třídy nebo používají výchozí hodnoty překladače pro zpracování DTD.

- Pro odvozené třídy XmlDocument nebo XmlTextReader není definován žádný konstruktor nebo není použita žádná bezpečná hodnota pro <xref:System.Xml.XmlResolver> .

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

- Zachyťte a zpracujte všechny výjimky XmlTextReader správně, aby nedocházelo k odhalení informací o cestách.

- Použijte  <xref:System.Xml.XmlSecureResolver> místo objekt XmlResolver k omezení prostředků, ke kterým má přístup XmlTextReader přístup.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud si nejste jistí, že je vstup z důvěryhodného zdroje známý, nedoporučujeme z tohoto upozornění pravidlo potlačit.

## <a name="pseudo-code-examples"></a>Příklady kódu pseudo

### <a name="violation"></a>Selhání

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

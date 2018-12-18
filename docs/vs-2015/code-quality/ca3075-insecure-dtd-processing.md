---
title: 'CA3075: Zpracování nezabezpečené specifikace DTD | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8284f065a829ac7ecc29330fb8a9dad74e92690e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850169"
---
# <a name="ca3075-insecure-dtd-processing"></a>CA3075: Zpracování nezabezpečené specifikace DTD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InsecureDTDProcessing|
|CheckId|CA3075|
|Kategorie|Microsoft.Security|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina
 Pokud používáte nezabezpečené <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instance nebo odkaz na externí entity zdroje, analyzátor může přijmout nedůvěryhodné vstupní tak zveřejnit citlivé informace, které útočníci.

## <a name="rule-description"></a>Popis pravidla
 A [dokumentu typ definice (DTD)](https://msdn.microsoft.com/library/aa468547.aspx) je jedním ze dvou způsobů analyzátor jazyka XML můžete určit platnosti dokumentu, podle definice [World Wide Web Consortium (W3C) značky XML (Extensible Language) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Toto pravidlo vyhledá vlastnosti a instance, kde je nedůvěryhodná data přijat upozornit vývojáře o potenciál [informacím](http://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c) hrozeb, které mohou vést k [útok na dostupnost služby (DoS)](http://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600) útoky. Toto pravidlo aktivuje, když:

- Je zapnutá DtdProcessing <xref:System.Xml.XmlReader> instanci, která přeloží externí entity XML pomocí <xref:System.Xml.XmlUrlResolver>.

- <xref:System.Xml.XmlNode.InnerXml%2A> Nastavenou v souboru XML.

- <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> je nastavena na analýzy.

- Nedůvěryhodný vstup zpracována pomocí <xref:System.Xml.XmlResolver> místo <xref:System.Xml.XmlSecureResolver> .

- Objekt XmlReader.<xref:System.Xml.XmlReader.Create%2A> Metoda je volána s nezabezpečené <xref:System.Xml.XmlReaderSettings> instance nebo vůbec žádné instance.

- <xref:System.Xml.XmlReader> je vytvořen s nezabezpečené výchozí nastavení nebo hodnoty.

  Ve všech těchto případech je výsledek stejný: obsah buď soubor systému nebo síťových sdílených složek z počítače, kde je zpracování souboru XML se zveřejní pro útočníka, který pak mohou být použity jako vektor DoS.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

- Zachytit a zpracovat všechny výjimky XmlTextReader správně, aby se zabránilo zpřístupnění informací cestu.

- Použití <xref:System.Xml.XmlSecureResolver> omezit prostředky, ke kterým přístup XmlTextReader.

- Nejsou povoleny <xref:System.Xml.XmlReader> otevřete všem externím prostředkům tak, že nastavíte <xref:System.Xml.XmlResolver> vlastnost **null**.

- Ujistěte se, že <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A> vlastnost <xref:System.Data.DataViewManager> přiřazena z důvěryhodného zdroje.

  Rozhraní .NET 3.5 a starší

- Zakázat zpracování DTD, pokud pracujete se sekvenčním nedůvěryhodných zdrojů tak, že nastavíte <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A> vlastnost **true** .

- Pomocí třídy XmlTextReader má vyžádané dědičnosti úplný vztah důvěryhodnosti. Zobrazit [požadavky na dědičnost](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9) Další informace.

  Rozhraní .NET 4 a novější

- Nedoporučujeme povolovat DtdProcessing, pokud pracujete s nedůvěryhodných zdrojů tak, že nastavíte vlastnost DtdProcessing [zakázat nebo ignorovat](https://msdn.microsoft.com/library/system.xml.dtdprocessing.aspx)

- Zajistěte, aby metoda Load() XmlReader instance ve všech případech InnerXml.

> [!NOTE]
>  Toto pravidlo může vykazovat některé platné instance XmlSecureResolver počet falešně pozitivních výsledků. Pracujeme na řešení tohoto problému mid 2016.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud si nejste jisti, že vstup je znám jako z důvěryhodného zdroje, nepotlačujte pravidlo z tohoto upozornění.

## <a name="pseudo-code-examples"></a>Příklady pseudo kódu

### <a name="violation"></a>Porušení

```csharp
using System.IO;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlSchema schema = XmlSchema.Read(tr, null); // warn
            return schema;
        }
    }
}
```

### <a name="solution"></a>Řešení

```csharp
using System.IO;
using System.Xml;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlTextReader reader = new XmlTextReader(tr) { DtdProcessing = DtdProcessing.Prohibit };
            XmlSchema schema = XmlSchema.Read(reader , null);
            return schema;
        }
    }
}
```

### <a name="violation"></a>Porušení

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings();
        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);  // warn
        }
    }
}
```

### <a name="solution"></a>Řešení

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings()
        {
            DtdProcessing = DtdProcessing.Prohibit
        };

        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);
        }
    }
}
```

### <a name="violations"></a>Porušení

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseSetInnerXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument() { XmlResolver = null };
            doc.InnerXml = xml; // warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseLoadXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument(){ XmlResolver = null };
            doc.LoadXml(xml); // warn
        }
    }
}
```

### <a name="solution"></a>Řešení

```csharp
using System.Xml;

public static void TestMethod(string xml)
{
    XmlDocument doc = new XmlDocument() { XmlResolver = null };
    System.IO.StringReader sreader = new System.IO.StringReader(xml);
    XmlTextReader reader = new XmlTextReader(sreader) { DtdProcessing = DtdProcessing.Prohibit };
    doc.Load(reader);
}
```

### <a name="violation"></a>Porušení

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            serializer.Deserialize(stream); // warn
        }
    }
}
```

### <a name="solution"></a>Řešení

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            XmlTextReader reader = new XmlTextReader(stream) { DtdProcessing = DtdProcessing.Prohibit } ;
            serializer.Deserialize(reader );
        }
    }
}
```

### <a name="violation"></a>Porušení

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XPathDocument doc = new XPathDocument(path); // warn
        }
    }
}
```

### <a name="solution"></a>Řešení

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XmlTextReader reader = new XmlTextReader(path) { DtdProcessing = DtdProcessing.Prohibit };
            XPathDocument doc = new XPathDocument(reader);
        }
    }
}
```

### <a name="violation"></a>Porušení

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = new XmlUrlResolver() };
    }
}
```

### <a name="solution"></a>Řešení

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = null }; // or set to a XmlSecureResolver instance
    }
}
```

### <a name="violations"></a>Porušení

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Parse };
            XmlReader reader = XmlReader.Create(path, settings); // warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod()
        {
            var reader = XmlTextReader.Create(""doc.xml""); //warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            try {
                XmlTextReader reader = new XmlTextReader(path); // warn
            }
            catch { throw ; }
            finally {}
        }
    }
}
```

### <a name="solution"></a>Řešení

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Prohibit };
            XmlReader reader = XmlReader.Create(path, settings);
        }
    }
}
```




---
title: 'CA3075: nezabezpečené zpracování DTD | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2ce5390ce8d649ab2c57eccde34506d6831b8193
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300969"
---
# <a name="ca3075-insecure-dtd-processing"></a>CA3075: Zpracování nezabezpečené specifikace DTD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InsecureDTDProcessing|
|CheckId|CA3075|
|Kategorie|Microsoft.Security|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Pokud používáte nezabezpečené <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instance nebo odkazujete na zdroje externích entit, může analyzátor přijmout nedůvěryhodné vstupní a únik citlivých informací útočníkům.

## <a name="rule-description"></a>Popis pravidla
 [Definice typu dokumentu (DTD)](https://msdn.microsoft.com/library/aa468547.aspx) je jedním ze dvou způsobů, jak může analyzátor XML určit platnost dokumentu, jak je definováno v [konsorcium World Wide Web (W3C) jazyk XML (Extensible Markup Language) (XML) 1,0](https://www.w3.org/TR/2008/REC-xml-20081126/). Toto pravidlo vyhledává vlastnosti a instance, kde jsou přijímána nedůvěryhodná data, aby upozornila vývojáře na potenciální hrozby [zpřístupnění informací](https://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c) , což může vést k útokům DOS [(Denial of Service)](https://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600) . Toto pravidlo se aktivuje v těchto případech:

- DtdProcessing je povolena na instanci <xref:System.Xml.XmlReader>, která řeší externí entity XML pomocí <xref:System.Xml.XmlUrlResolver>.

- Vlastnost <xref:System.Xml.XmlNode.InnerXml%2A> v kódu XML je nastavena.

- vlastnost <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> je nastavena na hodnotu analyzovat.

- Nedůvěryhodný vstup se zpracovává pomocí <xref:System.Xml.XmlResolver> místo <xref:System.Xml.XmlSecureResolver>.

- Objekt XmlReader.<xref:System.Xml.XmlReader.Create%2A> Metoda je vyvolána s nezabezpečenou <xref:System.Xml.XmlReaderSettings> instancí nebo vůbec žádnou instancí.

- Vytvoří se <xref:System.Xml.XmlReader> s nezabezpečenými výchozími nastaveními nebo hodnotami.

  V každém z těchto případů je výsledek stejný: obsah buď ze systému souborů, nebo síťových sdílených složek z počítače, ve kterém je soubor XML zpracován, bude vystaven útočníkovi, který se pak může použít jako vektor DoS.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

- Zachyťte a zpracujte všechny výjimky XmlTextReader správně, aby nedocházelo k odhalení informací o cestách.

- Použijte <xref:System.Xml.XmlSecureResolver> k omezení prostředků, ke kterým má aplikace XmlTextReader přístup.

- Nepovolujte <xref:System.Xml.XmlReader> otevírat žádné externí prostředky nastavením vlastnosti <xref:System.Xml.XmlResolver> na **hodnotu null**.

- Zajistěte, aby byla vlastnost <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A> <xref:System.Data.DataViewManager> přiřazena z důvěryhodného zdroje.

  .NET 3,5 a starší

- Pokud pracujete s nedůvěryhodnými zdroji, zakažte zpracování DTD nastavením vlastnosti <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A> na **hodnotu true** .

- Třída XmlTextReader má úplný požadavek dědičnosti vztahu důvěryhodnosti. Další informace najdete v tématu [požadavky dědičnosti](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) .

  .NET 4 a novější

- Pokud pracujete s nedůvěryhodnými zdroji, vyhněte se povolení DtdProcessing nastavením vlastnosti DtdProcessing na [zakázat nebo ignorovat](https://msdn.microsoft.com/library/system.xml.dtdprocessing.aspx)

- Zajistěte, aby metoda Load () přebírá instanci XmlReader ve všech případech InnerXml.

> [!NOTE]
> Toto pravidlo může v některých platných instancích XmlSecureResolver hlásit falešně pozitivní výsledky. Pracujeme na řešení tohoto problému od Mid 2016.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud si nejste jistí, že je vstup z důvěryhodného zdroje známý, nedoporučujeme z tohoto upozornění pravidlo potlačit.

## <a name="pseudo-code-examples"></a>Příklady kódu pseudo

### <a name="violation"></a>Selhání

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

### <a name="violation"></a>Selhání

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

### <a name="violation"></a>Selhání

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

### <a name="violation"></a>Selhání

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

### <a name="violation"></a>Selhání

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

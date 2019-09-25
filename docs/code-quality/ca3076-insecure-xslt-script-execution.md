---
title: 'CA3076: Spuštění nezabezpečeného skriptu XSLT'
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c6c5df0109a8cff3cefcc308ea27077ef0fbe03
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237080"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Spuštění nezabezpečeného skriptu XSLT

|||
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|Kategorie|Microsoft.Security|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Pokud v aplikacích .NET nezabezpečeně vyplníte Extensible Stylesheet Language Transformers (XSLT), může procesor vyřešit nedůvěryhodné odkazy identifikátorů URI, které by mohly zveřejnit citlivé informace pro útočníky, což by způsobilo odepření služby a vzájemného pracoviště. ohrožující. Další informace najdete v tématu věnovaném [bezpečnostním hlediskům XSLT (. NET Guide)](/dotnet/standard/data/xml/xslt-security-considerations).

## <a name="rule-description"></a>Popis pravidla

**XSLT** je standard konsorcium World Wide Web (W3C) pro transformaci dat XML. XSLT se obvykle používá pro zápis šablon stylů pro transformaci dat XML do jiných formátů, jako je HTML, text s pevnou délkou, textový soubor s oddělovači nebo jiný formát XML. I když je ve výchozím nastavení zakázaná, můžete ji povolit pro svůj projekt.

Aby se zajistilo, že nezveřejňujete plochu pro útok, toto pravidlo se aktivuje při každém XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> přijímá nezabezpečené instance <xref:System.Xml.Xsl.XsltSettings> kombinace a <xref:System.Xml.XmlResolver>, což umožňuje škodlivé zpracování skriptů.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

- Nahraďte nezabezpečený argument XsltSettings pomocí XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> nebo s instancí, která má zakázanou funkci dokumentu a provádění skriptu.

- <xref:System.Xml.XmlSecureResolver> Nahraďte <xref:System.Xml.XmlResolver> argument hodnotou null nebo instancí.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Pokud si nejste jistí, že je vstup z důvěryhodného zdroje známý, nedoporučujeme z tohoto upozornění pravidlo potlačit.

## <a name="pseudo-code-examples"></a>Příklady kódu pseudo

### <a name="violation-that-uses-xsltsettingstrustedxslt"></a>Porušení, které používá XsltSettings. TrustedXslt

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
         void TestMethod()
        {
             XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
             var settings = XsltSettings.TrustedXslt;
             var resolver = new XmlUrlResolver();
             xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
        }
    }
}
```

### <a name="solution-that-uses-xsltsettingsdefault"></a>Řešení, které používá XsltSettings. Default

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        void TestMethod()
        {
            XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
            var settings = XsltSettings.Default;
            var resolver = new XmlUrlResolver();
            xslCompiledTransform.Load("testStylesheet", settings, resolver);
        }
    }
}
```

### <a name="violationmdashdocument-function-and-script-execution-not-disabled"></a>Funkce&mdash;dokumentu porušení a provádění skriptu není zakázané.

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
            }
            catch { throw; }
            finally { }
        }
    }
}
```

### <a name="solutionmdashdisable-document-function-and-script-execution"></a>Řešení&mdash;– zakázat funkci dokumentu a provádění skriptu

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                settings.EnableDocumentFunction = false;
                settings.EnableScript = false;
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver);
            }
            catch { throw; }
            finally { }
        }
    }
}
```

## <a name="see-also"></a>Viz také:

- [Požadavky na zabezpečení XSLT (. Průvodce NET)](/dotnet/standard/data/xml/xslt-security-considerations)
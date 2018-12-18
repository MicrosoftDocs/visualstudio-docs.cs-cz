---
title: 'CA3076: Spuštění nezabezpečeného skriptu XSLT'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 74fe556d775e60dec5dde4528a1924e55ab4c2ed
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546389"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Spuštění nezabezpečeného skriptu XSLT

|||
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|Kategorie|Microsoft.Security|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina

Pokud spuštění šablony stylů transformace XSLT (Extensible Language) v aplikacích .NET nezabezpečeným způsobem, procesor může vyřešit nedůvěryhodné identifikátor URI odkazy, které může odhalit citlivé informace, které útočníci, což vede k Denial of Service a webů útoky. Další informace najdete v tématu [Considerations(.NET Guide) zabezpečení XSLT](/dotnet/standard/data/xml/xslt-security-considerations).

## <a name="rule-description"></a>Popis pravidla

**XSLT** je standard pro transformaci dat XML World Wide Web Consortium (W3C). XSLT se obvykle používá k zápisu šablony stylů k transformaci dat XML do jiných formátů, jako jsou HTML, text pevné délky, text oddělený čárkami nebo jiný formát XML. I když zakázané ve výchozím nastavení, můžete ji povolit pro váš projekt.

Aby bylo zajištěno nevystavujete rovinu útoku, toto pravidlo aktivuje vždy, když XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> přijímá nezabezpečené kombinaci instance <xref:System.Xml.Xsl.XsltSettings> a <xref:System.Xml.XmlResolver>, která umožňuje zpracování škodlivým skriptem.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

- Nahraďte XsltSettings nezabezpečené XsltSettings argument.<xref:System.Xml.Xsl.XsltSettings.Default%2A> nebo s instancí, který byl zakázán spuštění funkce a skriptu dokumentu.

- Nahradit <xref:System.Xml.XmlResolver> argument s hodnotou null nebo <xref:System.Xml.XmlSecureResolver> instance.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Pokud si nejste jisti, že vstup je znám jako z důvěryhodného zdroje, nepotlačujte pravidlo z tohoto upozornění.

## <a name="pseudo-code-examples"></a>Příklady pseudo kódu

### <a name="violation-that-uses-xsltsettingstrustedxslt"></a>Narušení, který používá XsltSettings.TrustedXslt

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

### <a name="solution-that-uses-xsltsettingsdefault"></a>Řešení, které využívá XsltSettings.Default

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

### <a name="violationmdashdocument-function-and-script-execution-not-disabled"></a>Porušení&mdash;dokumentu spuštění funkce a skript nejsou zakázané

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

### <a name="solutionmdashdisable-document-function-and-script-execution"></a>Řešení&mdash;zakázat spuštění funkce a skriptu dokumentu

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

- [Aspekty zabezpečení XSLT (Průvodce technologií .NET)](/dotnet/standard/data/xml/xslt-security-considerations)
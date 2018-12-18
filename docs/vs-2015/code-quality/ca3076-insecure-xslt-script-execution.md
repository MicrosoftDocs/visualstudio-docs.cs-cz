---
title: 'CA3076: Spuštění nezabezpečeného skriptu XSLT | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53cb7a46-c564-488f-bc51-0e210a7853c9
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 39aebc0e7681b139e021c48c12a87d4b060cc7af
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911470"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Spuštění nezabezpečeného skriptu XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|Kategorie|Microsoft.Security|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina
 Pokud spustíte [šablony stylů transformace XSLT (Extensible Language)](https://support.microsoft.com/en-us/kb/313997) v aplikacích .NET nezabezpečeným způsobem, procesor může [nedůvěryhodné identifikátor URI odkazy](http://msdn.microsoft.com/en-us/ba3e4d4f-1ee7-4226-a51a-78a1f1b5bd8a) , který může zveřejnit citlivé informace, které útočníci, což vede k útokům DOS a webů.

## <a name="rule-description"></a>Popis pravidla
 [XSLT](http://msdn.microsoft.com/en-us/6377ce5f-3c45-42a6-b7a9-ec8da588b60c) je standard pro transformaci dat XML World Wide Web Consortium (W3C). XSLT se obvykle používá k zápisu šablony stylů k transformaci dat XML do jiných formátů, jako jsou HTML, pevné délky textu, text oddělený čárkami nebo jiný formát XML. I když zakázané ve výchozím nastavení, můžete ji povolit pro váš projekt.

 Aby bylo zajištěno nevystavujete rovinu útoku, toto pravidlo aktivuje vždy, když XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> přijímá nezabezpečené kombinaci instance <xref:System.Xml.Xsl.XsltSettings> a <xref:System.Xml.XmlResolver>, která umožňuje zpracování škodlivým skriptem.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

-   Nahraďte XsltSettings nezabezpečené XsltSettings argument.<xref:System.Xml.Xsl.XsltSettings.Default%2A> nebo s instancí, který byl zakázán spuštění funkce a skriptu dokumentu.

-   Nahradit <xref:System.Xml.XmlResolver> argument s hodnotou null nebo <xref:System.Xml.XmlSecureResolver> instance.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud si nejste jisti, že vstup je znám jako z důvěryhodného zdroje, nepotlačujte pravidlo z tohoto upozornění.

## <a name="pseudo-code-examples"></a>Příklady pseudo kódu

### <a name="violation"></a>Porušení

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

### <a name="solution"></a>Řešení

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

### <a name="violation"></a>Porušení

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

### <a name="solution"></a>Řešení

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




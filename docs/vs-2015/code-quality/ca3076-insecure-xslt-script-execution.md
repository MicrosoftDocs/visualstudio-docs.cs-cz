---
title: 'CA3076: nezabezpečené spuštění skriptu XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 53cb7a46-c564-488f-bc51-0e210a7853c9
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2b3e06bb7a150c4bb07eefc0571818f1127fe460
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545116"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Spuštění nezabezpečeného skriptu XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|Kategorie|Microsoft.Security|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Pokud v aplikacích .NET nezabezpečeně vyplníte [Extensible Stylesheet Language Transformers (XSLT)](https://support.microsoft.com/kb/313997) , může procesor [vyřešit nedůvěryhodné odkazy identifikátorů URI](https://msdn.microsoft.com/ba3e4d4f-1ee7-4226-a51a-78a1f1b5bd8a) , které by mohly zveřejnit citlivé informace pro útočníky, což vede k odepření útoků služby a mezi weby.

## <a name="rule-description"></a>Popis pravidla
 [XSLT](https://msdn.microsoft.com/6377ce5f-3c45-42a6-b7a9-ec8da588b60c) je standard konsorcium World Wide Web (W3C) pro transformaci dat XML. XSLT se obvykle používá k psaní šablon stylů pro transformaci dat XML do jiných formátů, jako je například HTML, text s pevnou délkou, text oddělený čárkami nebo jiný formát XML. I když je ve výchozím nastavení zakázaná, můžete ji povolit pro svůj projekt.

 Aby se zajistilo, že nezveřejňujete plochu pro útok, toto pravidlo se aktivuje při každém XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> přijímá nezabezpečené instance kombinace <xref:System.Xml.Xsl.XsltSettings> a <xref:System.Xml.XmlResolver> , což umožňuje škodlivé zpracování skriptů.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

- Nahraďte nezabezpečený argument XsltSettings pomocí XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> nebo s instancí, která má zakázanou funkci dokumentu a provádění skriptu.

- Nahraďte <xref:System.Xml.XmlResolver> argument hodnotou null nebo <xref:System.Xml.XmlSecureResolver> instancí.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pokud si nejste jistí, že je vstup z důvěryhodného zdroje známý, nedoporučujeme z tohoto upozornění pravidlo potlačit.

## <a name="pseudo-code-examples"></a>Příklady kódu pseudo

### <a name="violation"></a>Selhání

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

### <a name="violation"></a>Selhání

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

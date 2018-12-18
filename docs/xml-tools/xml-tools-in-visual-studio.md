---
title: Nástroje XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET Framework classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f87c06e2bfc3885c0f52230e927933ff3cb0d87c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53054995"
---
# <a name="xml-tools-in-visual-studio"></a>Nástroje XML v sadě Visual Studio

*Kód XML (Extensible Language)* je značkovací jazyk, který poskytuje formátu pro popis data. To usnadňuje přesnější deklarace výsledků hledání obsahu a lépe vystihuje napříč různými platformami. XML navíc umožňuje oddělení prezentaci z data. Například ve formátu HTML použijete značky na prohlížeč pro zobrazení dat jako tučný nebo kurzívu; v XML použijete pouze pro popis dat, jako je například název města, teploty a tlaku barometrický značky. Ve formátu XML použijte šablony stylů, jako je šablona stylů XSL (Extensible Language) a šablony stylů CSS (CSS) data můžete prezentovat tak v prohlížeči. XML data odděluje od prezentaci a procesu. To umožňuje zobrazení a zpracování dat, jak chcete, s použitím různých stylů a aplikace.

XML je podmnožinou SGML, která je optimalizována pro doručení prostřednictvím webu. Je určené World Wide Web Consortium (W3C). Jazykem zaručuje, že jsou strukturovaná data jednotné a nezávislá aplikace nebo dodavatele.

XML je založen na řadu funkcí sady Visual Studio a rozhraní .NET Framework. Následující seznam článků názvy nástroje a funkce související s XML, které nabízí Visual Studio a rozhraní .NET Framework.

Další informace najdete v tématu <xref:System.Xml?displayProperty=fullName> dokumentaci.

## <a name="reference"></a>Odkaz

[Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699) zpřístupňuje [editoru XML](http://go.microsoft.com/fwlink/?LinkId=228249) strom prostřednictvím analýzy [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) pro všechny dokumenty XML.

[Reference na standardy XML](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) poskytuje informace o XML technologií, včetně XML, dokumentu typ definice (DTD), schéma XML definice jazyk (XSD) a XSLT.

<xref:System.Xml?displayProperty=fullName> Popisuje třídy a další prvky, které tvoří <xref:System.Xml> obor názvů a obsahuje odkazy na podrobnější informace o každé položky.

<xref:System.Xml.Serialization?displayProperty=fullName> Popisuje třídy a další prvky, které tvoří <xref:System.Xml.Serialization> obor názvů a nabízí odkazy k podrobnějším informacím o jednotlivých položkách.

## <a name="related-sections"></a>Související oddíly

[XML Document Object Model (DOM)](/dotnet/standard/data/xml/xml-document-object-model-dom) popisuje jak <xref:System.Xml.XmlDocument> a jeho přidružených tříd v souladu s modelu objektu dokumentu W3C (Core) úrovně 1 a 2 úroveň oboru názvů podporu specifikace.

[Zpracování dat XML pomocí objektu XmlReader a XmlWriter](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc189001\(v\=vs.95\))

[Transformace XSLT](/dotnet/standard/data/xml/xslt-transformations) popisuje jak <xref:System.Xml.Xsl.XslCompiledTransform> třída implementuje XSLT 1.0 doporučení.

[Zpracování dat XML pomocí modelu dat XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model) popisuje jak <xref:System.Xml.XPath.XPathNavigator> třída může zpracovat XML dat uložených v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu. <xref:System.Xml.XPath.XPathNavigator> Třídy je založena na výraz XQuery 1.0 a modelu dat XPath 2.0 a můžete použít k procházení a úpravy dat XML.

[Schéma objektu modelu (SOM) XML](/dotnet/standard/data/xml/xml-schema-object-model-som) popisuje třídy používané pro vytváření prostředků a manipulace s schémat XML, tím, že poskytuje <xref:System.Xml.Schema.XmlSchema> třídy pro načtení a upravit schéma.
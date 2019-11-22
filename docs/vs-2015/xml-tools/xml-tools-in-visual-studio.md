---
title: Nástroje XML
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ee0cf61f8ec2787894c6f67b8ac75424246c507
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297444"
---
# <a name="xml-tools-in-visual-studio"></a>Nástroje XML v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kód XML (Extensible Language) * je značkovací jazyk, který poskytuje formátu pro popis data. To usnadňuje přesnější deklarace výsledků hledání obsahu a lépe vystihuje napříč různými platformami. XML navíc umožňuje oddělení prezentaci z data. Například ve formátu HTML použijete značky na prohlížeč pro zobrazení dat jako tučný nebo kurzívu; v XML použijete pouze pro popis dat, jako je například název města, teploty a tlaku barometrický značky. V XML pomocí stylů CSS jako je šablona stylů XSL (Extensible Language) a šablony stylů CSS (CSS) data můžete prezentovat tak v prohlížeči. XML data odděluje od prezentaci a procesu. To umožňuje zobrazení a zpracování dat, jak chcete, s použitím různých stylů a aplikace.

 XML je podmnožinou SGML, která je optimalizována pro doručení prostřednictvím webu. Je určené World Wide Web Consortium (W3C). Jazykem zaručuje, že strukturovaných dat bude jednotné a nezávislá aplikace nebo dodavatele.

 XML je základem mnoho funkcí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Následující téma seznam názvů nástrojů a funkcí týkajících se kód XML, který nabízí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

 Další informace najdete v tématu [středisko pro vývojáře XML](https://go.microsoft.com/fwlink/?LinkID=100176), která obsahuje nejnovější dokumentaci, technických informací, soubory ke stažení, diskusní skupiny a další prostředky pro vývojáře v XML.

## <a name="in-this-section"></a>V tomto oddílu
 [Práce s daty XML](../xml-tools/working-with-xml-data.md) popisuje role XML v datech způsob, jak je zpracována v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 [Ladění XSLT](../xml-tools/debugging-xslt.md) obsahuje odkazy na témata týkající se použití ladicího programu sady Visual Studio k ladění XSLT.

## <a name="reference"></a>Odkaz
 [Microsoft.VisualStudio.XmlEditor](https://go.microsoft.com/fwlink/?LinkID=165699) zpřístupňuje [editoru XML](https://go.microsoft.com/fwlink/?LinkId=228249) strom prostřednictvím analýzy [System.Xml.Linq](https://go.microsoft.com/fwlink/?LinkId=228250) pro všechny dokumenty XML.

 [Reference na standardy XML](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) poskytuje informace o XML technologií, včetně XML, dokumentu typ definice (DTD), schéma XML definice jazyk (XSD) a XSLT.

 <xref:System.Xml?displayProperty=fullName> Popisuje třídy a další prvky, které tvoří <xref:System.Xml> obor názvů a obsahuje odkazy na podrobnější informace o každé položky.

 <xref:System.Xml.Serialization?displayProperty=fullName> Popisuje třídy a další prvky, které tvoří <xref:System.Xml.Serialization> obor názvů a nabízí odkazy k podrobnějším informacím o jednotlivých položkách.

## <a name="related-sections"></a>Související oddíly
 [XML Document Object Model (DOM)](https://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) popisuje jak <xref:System.Xml.XmlDocument> a jeho přidružených tříd v souladu s modelu objektu dokumentu W3C (Core) úrovně 1 a 2 úroveň oboru názvů podporu specifikace.

 [Čtení XML s objekt XmlReader](https://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) popisuje jak <xref:System.Xml.XmlReader> poskytuje mapovaný, přesměrování pouze, jen pro čtení přístup k datům XML datový proud XML.

 [Zápis XML pomocí funkce XmlWriter](https://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) popisuje jak <xref:System.Xml.XmlWriter> poskytuje mapovaný, předávat pouze způsob, jak generovat datové proudy XML a pomáhá vytvářet dokumenty XML, které jsou v souladu se standardem W3C.

 [Transformace XSLT](https://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) popisuje jak <xref:System.Xml.Xsl.XslCompiledTransform> třída implementuje XSLT 1.0 doporučení.

 [Zpracování dat XML pomocí modelu dat XPath](https://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) popisuje jak <xref:System.Xml.XPath.XPathNavigator> třída může zpracovat XML dat uložených v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu. <xref:System.Xml.XPath.XPathNavigator> Třídy je založena na výraz XQuery 1.0 a modelu dat XPath 2.0 a můžete použít k procházení a úpravy dat XML.

 [Schéma objektu modelu (SOM) XML](https://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) popisuje třídy používané pro vytváření prostředků a manipulace s schémat XML, tím, že poskytuje <xref:System.Xml.Schema.XmlSchema> třídy pro načtení a upravit schéma.

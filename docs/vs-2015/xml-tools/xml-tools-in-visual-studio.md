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
ms.openlocfilehash: b9a46523c4c856367e77c345c7e44d0dbc87508f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845975"
---
# <a name="xml-tools-in-visual-studio"></a>Nástroje XML v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jazyk XML (eXtensible Markup Language) (XML) * je značkovací jazyk, který poskytuje formát pro popisovaná data. To usnadňuje přesnější deklarace obsahu a smysluplnější výsledky hledání napříč různými platformami. Kromě toho umožňuje XML oddělení prezentace od dat. Například ve formátu HTML používáte značky k oznámení, že prohlížeč zobrazuje data tučně nebo kurzívou. v jazyce XML použijete značky pouze k popisu dat, jako je například název města, teplota a barometricový tlak. V jazyce XML používáte šablony stylů, jako je XSL (Extensible Stylesheet Language) a kaskádové šablony stylů (CSS) k prezentaci dat v prohlížeči. XML odděluje data z prezentace a procesu. Díky tomu můžete zobrazit a zpracovat data podle potřeby, a to použitím různých šablon stylů a aplikací.

 XML je podmnožina jazyka SGML, která je optimalizována pro doručování přes web. Je definován konsorcium World Wide Web (W3C). Tato standardizace zaručuje, že strukturovaná data budou jednotná a nezávisle na aplikacích nebo dodavatelích.

 XML je základem mnoha funkcí nástroje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Následující seznam témat obsahuje názvy nástrojů a funkcí souvisejících s XML, které jsou nabízeny v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

 Další informace najdete v centru pro [vývojáře XML](https://msdn.microsoft.com/data/bb190600.aspx), které poskytuje nejnovější dokumentaci, technické informace, soubory ke stažení, diskusní skupiny a další materiály pro vývojáře XML.

## <a name="in-this-section"></a>V tomto oddílu
 [Práce s daty XML](../xml-tools/working-with-xml-data.md) Popisuje roli XML v způsobu zpracování dat v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 [Ladění XSLT](../xml-tools/debugging-xslt.md) Obsahuje odkazy na témata o používání ladicího programu sady Visual Studio k ladění XSLT.

## <a name="reference"></a>Referenční informace
 [ EditorMicrosoft.VisualStudio.Xml](https://msdn.microsoft.com/library/microsoft.visualstudio.xmleditor.aspx) Zpřístupňuje strom analýzy [editoru XML](https://msdn.microsoft.com/library/ms255810.aspx) prostřednictvím [System.Xml. LINQ](https://msdn.microsoft.com/library/system.xml.linq.aspx) pro všechny dokumenty XML.

 [Reference standardů XML](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) Poskytuje informace o technologiích XML, včetně XML, definice typu dokumentu (DTD), XML Schema Definition Language (XSD) a XSLT.

 <xref:System.Xml?displayProperty=fullName> Popisuje třídy a další prvky, které tvoří <xref:System.Xml> obor názvů a obsahuje odkazy na podrobnější informace o každé položce.

 <xref:System.Xml.Serialization?displayProperty=fullName> Popisuje třídy a další prvky, které tvoří <xref:System.Xml.Serialization> obor názvů a obsahuje odkazy na podrobnější informace o každé položce.

## <a name="related-sections"></a>Související oddíly
 [XML model DOM (Document Object Model) (DOM)](https://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) Popisuje, jak <xref:System.Xml.XmlDocument> a jeho přidružené třídy jsou v rozporu s specifikacemi podpory W3C model DOM (Document Object Model) (Core) na úrovni 1 a 2.

 [Čtení XML pomocí objektu XmlReader](https://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) Popisuje, jak <xref:System.Xml.XmlReader> poskytuje neukládatelné do mezipaměti, jen pro čtení a přístup k datům XML přes datový proud XML.

 [Zápis XML pomocí funkce XmlWriter](https://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) Popisuje, jak <xref:System.Xml.XmlWriter> poskytuje neukládatelné do mezipaměti, pouze před generováním datových proudů XML a pomáhá vytvářet dokumenty XML, které vyhovují standardu W3C.

 [Transformace XSLT](https://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) Popisuje, jak <xref:System.Xml.Xsl.XslCompiledTransform> Třída implementuje doporučení XSLT 1,0.

 [Zpracování dat XML pomocí datového modelu XPath](https://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) Popisuje, jak <xref:System.Xml.XPath.XPathNavigator> Třída dokáže zpracovat data XML uložená v <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> objektu nebo. <xref:System.Xml.XPath.XPathNavigator>Třída je založena na datovém modelu XQuery 1,0 a XPath 2,0 a lze jej použít k procházení a úpravám dat XML.

 [Model objektu XML schématu (SOM)](https://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) Popisuje třídy používané pro vytváření a manipulaci se schématy XML tím, že poskytuje <xref:System.Xml.Schema.XmlSchema> třídu pro načtení a úpravu schématu.

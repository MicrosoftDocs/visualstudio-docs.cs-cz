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

 XML je základem mnoha funkcí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Následující seznam témat obsahuje názvy nástrojů a funkcí souvisejících s XML, které jsou nabízeny v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

 Další informace najdete v centru pro [vývojáře XML](https://go.microsoft.com/fwlink/?LinkID=100176), které poskytuje nejnovější dokumentaci, technické informace, soubory ke stažení, diskusní skupiny a další materiály pro vývojáře XML.

## <a name="in-this-section"></a>V tomto oddílu
 [Práce s daty XML](../xml-tools/working-with-xml-data.md) Popisuje roli XML v způsobu, jakým jsou data zpracovávána v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 [Ladění XSLT](../xml-tools/debugging-xslt.md) Obsahuje odkazy na témata o používání ladicího programu sady Visual Studio k ladění XSLT.

## <a name="reference"></a>Odkaz
 [Microsoft. VisualStudio. XmlEditor](https://go.microsoft.com/fwlink/?LinkID=165699) zpřístupňuje strom analýzy [editoru XML](https://go.microsoft.com/fwlink/?LinkId=228249) prostřednictvím [System. XML. Linq](https://go.microsoft.com/fwlink/?LinkId=228250) pro všechny dokumenty XML.

 [Reference standardů XML](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) Poskytuje informace o technologiích XML, včetně XML, definice typu dokumentu (DTD), XML Schema Definition Language (XSD) a XSLT.

 <xref:System.Xml?displayProperty=fullName> popisuje třídy a další prvky, které tvoří obor názvů <xref:System.Xml> a obsahuje odkazy na podrobnější informace o každé položce.

 <xref:System.Xml.Serialization?displayProperty=fullName> popisuje třídy a další prvky, které tvoří obor názvů <xref:System.Xml.Serialization> a obsahuje odkazy na podrobnější informace o každé položce.

## <a name="related-sections"></a>Související oddíly
 [XML model DOM (Document Object Model) (DOM)](https://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) Popisuje, jak <xref:System.Xml.XmlDocument> a jeho přidružených tříd vyhovují specifikacím podpory W3C model DOM (Document Object Model) (Core) Level 1 a Level 2 obory názvů.

 [Čtení XML pomocí objektu XmlReader](https://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) Popisuje, jak <xref:System.Xml.XmlReader> poskytuje neukládatelné do mezipaměti, jen pro čtení a přístup k datům XML přes datový proud XML.

 [Zápis XML pomocí funkce XmlWriter](https://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) Popisuje způsob, jakým <xref:System.Xml.XmlWriter> poskytuje neukládatelné do mezipaměti, pouze před generováním datových proudů XML a pomáhá vytvářet dokumenty XML, které vyhovují standardu W3C.

 [Transformace XSLT](https://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) Popisuje, jak třída <xref:System.Xml.Xsl.XslCompiledTransform> implementuje doporučení XSLT 1,0.

 [Zpracování dat XML pomocí datového modelu XPath](https://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) Popisuje, jak třída <xref:System.Xml.XPath.XPathNavigator> může zpracovávat data XML uložená v <xref:System.Xml.XPath.XPathDocument> nebo objektu <xref:System.Xml.XmlDocument>. Třída <xref:System.Xml.XPath.XPathNavigator> je založena na datovém modelu XQuery 1,0 a XPath 2,0 a lze jej použít k procházení a úpravám dat XML.

 [Model objektu XML schématu (SOM)](https://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) Popisuje třídy, které slouží k vytváření a manipulaci se schématy XML, poskytnutím <xref:System.Xml.Schema.XmlSchema> třídy pro načtení a úpravu schématu.

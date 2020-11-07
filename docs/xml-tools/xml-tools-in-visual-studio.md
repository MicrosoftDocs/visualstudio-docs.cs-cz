---
title: Editor XML a Návrhář schémat
description: Seznamte se s nástroji v aplikaci Visual Studio pro práci s XML, XSLT a schématy XML, včetně editoru XML, návrháře schémat XML a ladicího programu XSLT.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
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
- XML [Visual Studio], .NET classes
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc8cac3e16e06c23d0d51ee4483bcf5fb8abfb05
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351281"
---
# <a name="overview-of-xml-tools-in-visual-studio"></a>Přehled nástrojů XML v aplikaci Visual Studio

*Jazyk XML (Extensible Markup Language) (XML)* je jazyk značek, který poskytuje formát pro popisovaná data. XML odděluje data a její prezentaci pomocí přidružených šablon stylů, jako je XSL (Extensible Stylesheet Language) a kaskádové šablony stylů (CSS). Visual Studio obsahuje nástroje a funkce, které usnadňují práci s XML, XSLT a schématy XML.

## <a name="xml-editor"></a>Editor XML

[Editor XML](xml-editor.md) slouží k úpravám dokumentů XML. Poskytuje úplnou kontrolu syntaxe XML, ověřování schématu při psaní, barevném kódování a IntelliSense. Pokud je k dispozici definice typu schématu nebo dokumentu, používá technologie IntelliSense k vypsání přípustných prvků a atributů.

Mezi další funkce patří:

- Podpora fragmentů kódu XML, včetně fragmentů generovaných schématem

- Osnova dokumentu, aby bylo možné prvky rozbalit a sbalit

- Možnost spouštět transformace XSLT a zobrazovat výsledky jako text, XML nebo HTML

- Možnost generování schémat XML Schema Definition Language (XSD) z dokumentu instance XML

- Podpora úprav šablon stylů XSLT, včetně podpory technologie IntelliSense

- Průzkumník schémat XML

## <a name="xml-schema-designer"></a>Návrhář schématu XML

[Návrhář schématu XML](xml-schema-designer.md) je integrován se sadou Visual Studio a EDITORem XML, který vám umožní pracovat s schématy XML Schema Definition Language (XSD).

## <a name="xslt-debugging"></a>Ladění XSLT

Visual Studio podporuje [ladění šablon stylů XSLT](../xml-tools/debugging-xslt.md). Pomocí ladicího programu můžete nastavit body přerušení v šabloně stylů XSLT, krokovat na šablonu stylů XSLT z kódu a tak dále.

> [!NOTE]
> Ladicí program XSLT je k dispozici pouze v edici Enterprise sady Visual Studio.

## <a name="see-also"></a>Viz také

- <xref:System.Xml?displayProperty=fullName>
- [Transformace XSLT](/dotnet/standard/data/xml/xslt-transformations)
- [Zpracování dat XML pomocí datového modelu XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [model DOM (Document Object Model) dokumentu XML](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [Model objektu schématu (SOM) XML](/dotnet/standard/data/xml/xml-schema-object-model-som)

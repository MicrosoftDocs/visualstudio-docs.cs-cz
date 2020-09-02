---
title: LINQ to XML dynamické vlastnosti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6ff0b31512711b8888b05fcfde191c8cb5c47d99
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664266"
---
# <a name="linq-to-xml-dynamic-properties"></a>Dynamické vlastnosti LINQ to XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V této části najdete referenční informace o dynamických vlastnostech v LINQ to XML. Konkrétně tyto vlastnosti jsou zpřístupněny <xref:System.Xml.Linq.XAttribute> <xref:System.Xml.Linq.XElement> třídami a, které jsou v <xref:System.Xml.Linq> oboru názvů.

 Jak je vysvětleno v tématu [Přehled datové vazby WPF s LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), každá z dynamických vlastností je ekvivalentní standardní veřejné vlastnosti nebo metody ve stejné třídě. Tyto standardní členy by se měly používat pro většinu účelů; dynamické vlastnosti jsou určené speciálně pro LINQ to XML scénáře datových vazeb. Další informace o standardních členech těchto tříd naleznete v <xref:System.Xml.Linq.XAttribute> <xref:System.Xml.Linq.XElement> tématech a referenční témata.

 V souvislosti s jejich vyřešenými hodnotami jsou dynamické vlastnosti v této části rozdělené do dvou kategorií:

- Jednoduché, například `Value` vlastnosti v <xref:System.Xml.Linq.XAttribute> <xref:System.Xml.Linq.XElement> třídách a, které jsou přeloženy na jedinou hodnotu.

- Indexované hodnoty, jako jsou vlastnosti [prvků](../designers/elements-xelement-dynamic-property.md) a [následníků](../designers/descendants-xelement-dynamic-property.md) <xref:System.Xml.Linq.XElement> , které jsou přeloženy na typ indexeru. Aby byly typy indexerů přeloženy na požadovanou hodnotu nebo kolekci, je nutné předat rozšířený parametr názvu.

  Všechny dynamické vlastnosti, které vracejí indexovanou hodnotu typu, <xref:System.Collections.Generic.IEnumerable%601> používají provádění Deffered. Další informace o odloženém spuštění naleznete v tématu [Úvod do dotazů LINQ (C#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).

## <a name="in-this-section"></a>V tomto oddílu

|Téma|Popis|
|-----------|-----------------|
|[Dynamické vlastnosti třídy XAttribute](../designers/xattribute-class-dynamic-properties.md)|Poskytuje podrobnosti o dynamických vlastnostech vystavených <xref:System.Xml.Linq.XAttribute> třídou.|
|[Dynamické vlastnosti třídy XElement](../designers/xelement-class-dynamic-properties.md)|Poskytuje podrobnosti o dynamických vlastnostech vystavených <xref:System.Xml.Linq.XElement> třídou.|

## <a name="reference"></a>Referenční informace
 <xref:System.Xml.Linq>

 <xref:System.Xml.Linq.XElement?displayProperty=fullName>

 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a>Viz také
 [Datová vazba WPF s LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md) [datovou vazbou WPF s LINQ to XML přehled](../designers/wpf-data-binding-with-linq-to-xml-overview.md) [Úvod do dotazů LINQ (C#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)

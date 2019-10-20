---
title: Dynamické vlastnosti LINQ to XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5993639a1bd6db1b814615bc75c1a57b64212185
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72635267"
---
# <a name="linq-to-xml-dynamic-properties"></a>Dynamické vlastnosti LINQ to XML

V této části najdete referenční informace o dynamických vlastnostech v LINQ to XML. Konkrétně tyto vlastnosti jsou zpřístupněny <xref:System.Xml.Linq.XAttribute> a <xref:System.Xml.Linq.XElement> třídy, které jsou v oboru názvů <xref:System.Xml.Linq>.

Jak je vysvětleno v tématu [Přehled datové vazby WPF s LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), každá z dynamických vlastností je ekvivalentní standardní veřejné vlastnosti nebo metody ve stejné třídě. Tyto standardní členy by se měly používat pro většinu účelů; dynamické vlastnosti jsou určené speciálně pro LINQ to XML scénáře datových vazeb. Další informace o standardních členech těchto tříd naleznete v tématu <xref:System.Xml.Linq.XAttribute> a <xref:System.Xml.Linq.XElement> referenční témata.

V souvislosti s jejich vyřešenými hodnotami jsou dynamické vlastnosti v této části rozdělené do dvou kategorií:

- Jednoduché, například vlastnosti `Value` v třídách <xref:System.Xml.Linq.XAttribute> a <xref:System.Xml.Linq.XElement>, které se překládají na jedinou hodnotu.

- Indexované hodnoty, jako jsou vlastnosti [prvků](../designers/elements-xelement-dynamic-property.md) a [následníků](../designers/descendants-xelement-dynamic-property.md) <xref:System.Xml.Linq.XElement>, které se překládají na typ indexeru. Aby byly typy indexerů přeloženy na požadovanou hodnotu nebo kolekci, je nutné předat rozšířený parametr názvu.

Všechny dynamické vlastnosti, které vracejí indexovanou hodnotu typu <xref:System.Collections.Generic.IEnumerable%601> použít odložené provádění. Další informace o odloženém spuštění najdete v tématu [Úvod do dotazů LINQC#()](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="reference"></a>Odkaz

- <xref:System.Xml.Linq>
- <xref:System.Xml.Linq.XElement?displayProperty=fullName>
- <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a>Viz také:

- [Datová vazba WPF s LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)
- [Datová vazba WPF s LINQ to XML – přehled](../designers/wpf-data-binding-with-linq-to-xml-overview.md)
- [Úvod do dotazů LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)

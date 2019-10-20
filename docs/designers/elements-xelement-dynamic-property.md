---
title: Elementy (dynamická vlastnost XElement)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Elements
apitype: Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d92e9ebd1e5be9f3535dcac136bb46ba33975f0c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637311"
---
# <a name="elements-xelement-dynamic-property"></a>Elementy (dynamická vlastnost XElement)

Získá indexer použitý k načtení podřízených prvků aktuálního prvku, které odpovídají zadanému rozbalenému názvu.

## <a name="syntax"></a>Syntaxe

```xaml
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota

Indexer typu `IEnumerable<XElement> Item(String expandedName)`. Tento indexer Získá rozšířený název požadovaných podřízených prvků a vrátí odpovídající podřízené prvky ve <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` Collection.

## <a name="remarks"></a>Poznámky

Tato vlastnost je ekvivalentní metodě <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> třídy <xref:System.Xml.Linq.XContainer>.

Prvky ve vrácené kolekci jsou v pořadí zdrojového dokumentu XML.

Tato vlastnost používá odložené provádění.

## <a name="see-also"></a>Viz také:

- [Dynamické vlastnosti třídy XElement](../designers/attribute-xelement-dynamic-property.md)
- [Element](../designers/element-xelement-dynamic-property.md)
- [Potomci](../designers/descendants-xelement-dynamic-property.md)
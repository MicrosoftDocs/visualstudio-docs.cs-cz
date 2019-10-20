---
title: – Element (dynamická vlastnost XElement)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 08b2f7f008c1522c5f65b5ee7a58c3ed98e8a845
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637326"
---
# <a name="element-xelement-dynamic-property"></a>– Element (dynamická vlastnost XElement)

Získá indexer použitý k načtení instance podřízeného elementu, který odpovídá zadanému rozšířenému názvu.

## <a name="syntax"></a>Syntaxe

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota

Indexer typu `XElement Item(String expandedName)`. Tento indexer Získá rozšířený parametr názvu a vrátí odpovídající <xref:System.Xml.Linq.XElement>, nebo `null`, pokud neexistuje žádný element se zadaným názvem.

## <a name="remarks"></a>Poznámky

Tato vlastnost je ekvivalentní <xref:System.Xml.Linq.XContainer.Element%2A> metodě <xref:System.Xml.Linq.XContainer?displayProperty=fullName> třídy.

## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [Dynamické vlastnosti třídy XElement](../designers/attribute-xelement-dynamic-property.md)
- [Elements](../designers/elements-xelement-dynamic-property.md)
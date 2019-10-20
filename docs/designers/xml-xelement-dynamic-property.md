---
title: XML (dynamická vlastnost XElement)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c93aaf3b43a930fe88020738460ec131972a205a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72633523"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (dynamická vlastnost XElement)

Získá neformátovaný obsah XML elementu.

## <a name="syntax"></a>Syntaxe

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>Hodnota nebo návratová hodnota vlastnosti

@No__t_0, která představuje neformátovaný obsah XML elementu.

## <a name="remarks"></a>Poznámky

Tato vlastnost je ekvivalentní metodě <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> <xref:System.Xml.Linq.XNode?displayProperty=fullName> třídy s parametrem `SaveOptions` nastaveným na <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>Viz také:

- [Dynamické vlastnosti třídy XElement](../designers/attribute-xelement-dynamic-property.md)
- [Hodnota](../designers/value-xelement-dynamic-property.md)
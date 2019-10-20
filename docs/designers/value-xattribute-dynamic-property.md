---
title: Value (dynamická vlastnost XAttribute)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fefa3d13f1a38b5d1c329fa9df9220e13e769b1c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72634521"
---
# <a name="value-xattribute-dynamic-property"></a>Value (dynamická vlastnost XAttribute)

Získá nebo nastaví hodnotu atributu XML.

## <a name="syntax"></a>Syntaxe

```xaml
attrib.Value
```

## <a name="property-valuereturn-value"></a>Hodnota nebo návratová hodnota vlastnosti

@No__t_0 obsahující hodnotu tohoto atributu.

## <a name="exceptions"></a>Výjimky

|Typ výjimky|Podmínka|
| - |---------------|
|<xref:System.ArgumentNullException>|Při nastavování je `value` `null`.|

## <a name="remarks"></a>Poznámky

Tato vlastnost je ekvivalentní vlastnosti <xref:System.Xml.Linq.XAttribute.Value%2A> třídy <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, ale tato dynamická vlastnost také podporuje oznamování změn.

## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>
- [Dynamické vlastnosti třídy XAttribute](../designers/value-xattribute-dynamic-property.md)
- [Atribut](../designers/attribute-xelement-dynamic-property.md)
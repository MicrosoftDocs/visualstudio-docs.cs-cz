---
title: XML (dynamická vlastnost XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8a69245a875d0c1df1942af12afaacc5a9ffc34b
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080834"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (dynamická vlastnost XElement)

Získá neformátovaném tvaru XML obsahu elementu.

## <a name="syntax"></a>Syntaxe

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>Vlastnost hodnota nebo návratová hodnota

A <xref:System.String> , která představuje neformátovaný obsah XML daného elementu.

## <a name="remarks"></a>Poznámky

Tato vlastnost je ekvivalentní k <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> metodu <xref:System.Xml.Linq.XNode?displayProperty=fullName> třídy, se `SaveOptions` parametr nastaven na <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>Viz také:

- [Dynamické vlastnosti třídy XElement](../designers/xelement-class-dynamic-properties.md)
- [Hodnota](../designers/value-xelement-dynamic-property.md)
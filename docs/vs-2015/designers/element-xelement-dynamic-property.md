---
title: – Element (dynamická vlastnost XElement) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Element
api_type:
- Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c6171a5dedfd6985a6f54e748011bf86e03f4d3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664655"
---
# <a name="element-xelement-dynamic-property"></a>– Element (dynamická vlastnost XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Získá indexer použitý k načtení instance podřízeného elementu, který odpovídá zadanému rozšířenému názvu.

## <a name="syntax"></a>Syntaxe

```
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota
 Indexer typu `XElement Item(String expandedName)`. Tento indexer Získá rozšířený parametr názvu a vrátí odpovídající <xref:System.Xml.Linq.XElement>, nebo `null`, pokud neexistuje žádný element se zadaným názvem.

## <a name="remarks"></a>Poznámky
 Tato vlastnost je ekvivalentní <xref:System.Xml.Linq.XContainer.Element%2A> metodě <xref:System.Xml.Linq.XContainer?displayProperty=fullName> třídy.

## <a name="see-also"></a>Viz také
 elementy [dynamických vlastností třídy <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName> XElement](../designers/xelement-class-dynamic-properties.md) [](../designers/elements-xelement-dynamic-property.md)

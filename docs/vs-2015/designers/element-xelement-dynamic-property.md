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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664655"
---
# <a name="element-xelement-dynamic-property"></a>– Element (dynamická vlastnost XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Získá indexer použitý k načtení instance podřízeného elementu, který odpovídá zadanému rozšířenému názvu.

## <a name="syntax"></a>Syntax

```
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota
 Indexer `XElement Item(String expandedName)` typu Tento indexer převezme rozbalený parametr názvu a vrátí odpovídající <xref:System.Xml.Linq.XElement> , nebo `null` Pokud neexistuje žádný element se zadaným názvem.

## <a name="remarks"></a>Poznámky
 Tato vlastnost je ekvivalentní <xref:System.Xml.Linq.XContainer.Element%2A> metodě <xref:System.Xml.Linq.XContainer?displayProperty=fullName> třídy.

## <a name="see-also"></a>Viz také
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>[Elementy](../designers/elements-xelement-dynamic-property.md) [dynamických vlastností třídy XElement](../designers/xelement-class-dynamic-properties.md)

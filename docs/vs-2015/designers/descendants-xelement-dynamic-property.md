---
title: Descendants (dynamická vlastnost XElement) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b0496a04219c88573b3b555ef879a046d90faa3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664774"
---
# <a name="descendants-xelement-dynamic-property"></a>Descendants (dynamická vlastnost XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Získá indexer použitý k načtení všech následníků aktuálního prvku, který se shoduje se zadaným rozbaleným názvem.

## <a name="syntax"></a>Syntaxe

```
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota
 Indexer typu `IEnumerable<XElement> Item(String expandedName)`. Tento indexer získá rozbalený název zadaných potomkových prvků a vrátí vyhovující podřízené elementy ve <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` Collection.

## <a name="remarks"></a>Poznámky
 Tato vlastnost je ekvivalentní metodě <xref:System.Xml.Linq.XContainer.Descendants%28System.Xml.Linq.XName%29?displayProperty=fullName> třídy <xref:System.Xml.Linq.XContainer>.

 Prvky ve vrácené kolekci jsou v pořadí zdrojového dokumentu XML.

 Tato vlastnost používá odložené provádění.

## <a name="see-also"></a>Viz také
 [Elementy](../designers/elements-xelement-dynamic-property.md) [dynamických vlastností třídy XElement](../designers/xelement-class-dynamic-properties.md)

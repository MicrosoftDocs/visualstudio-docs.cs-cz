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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664774"
---
# <a name="descendants-xelement-dynamic-property"></a>Descendants (dynamická vlastnost XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Získá indexer použitý k načtení všech následníků aktuálního prvku, který se shoduje se zadaným rozbaleným názvem.

## <a name="syntax"></a>Syntax

```
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota
 Indexer `IEnumerable<XElement> Item(String expandedName)` typu Tento indexer získá rozbalený název zadaných potomkových prvků a vrátí vyhovující podřízené prvky v <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` kolekci.

## <a name="remarks"></a>Poznámky
 Tato vlastnost je ekvivalentní <xref:System.Xml.Linq.XContainer.Descendants%28System.Xml.Linq.XName%29?displayProperty=fullName> metodě <xref:System.Xml.Linq.XContainer> třídy.

 Prvky ve vrácené kolekci jsou v pořadí zdrojového dokumentu XML.

 Tato vlastnost používá odložené provádění.

## <a name="see-also"></a>Viz také
 [Elementy](../designers/elements-xelement-dynamic-property.md) [dynamických vlastností třídy XElement](../designers/xelement-class-dynamic-properties.md)

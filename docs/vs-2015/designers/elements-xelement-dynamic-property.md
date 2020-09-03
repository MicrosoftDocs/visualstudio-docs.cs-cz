---
title: Elementy (dynamická vlastnost XElement) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Elements
api_type:
- Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 383101679827f19b9a85d36f0f5a39eb772c68ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664683"
---
# <a name="elements-xelement-dynamic-property"></a>Elementy (dynamická vlastnost XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Získá indexer použitý k načtení podřízených prvků aktuálního prvku, které odpovídají zadanému rozbalenému názvu.

## <a name="syntax"></a>Syntax

```
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota
 Indexer `IEnumerable<XElement> Item(String expandedName)` typu Tento indexer Získá rozšířený název požadovaných podřízených elementů a vrátí odpovídající podřízené prvky v <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` kolekci.

## <a name="remarks"></a>Poznámky
 Tato vlastnost je ekvivalentní <xref:System.Xml.Linq.XContainer.Elements%28System.Xml.Linq.XName%29?displayProperty=fullName> metodě <xref:System.Xml.Linq.XContainer> třídy.

 Prvky ve vrácené kolekci jsou v pořadí zdrojového dokumentu XML.

 Tato vlastnost používá odložené provádění.

## <a name="see-also"></a>Viz také
 [XElement třídy dynamické vlastnosti](../designers/xelement-class-dynamic-properties.md) [Element](../designers/element-xelement-dynamic-property.md) [následovníci](../designers/descendants-xelement-dynamic-property.md) elementu

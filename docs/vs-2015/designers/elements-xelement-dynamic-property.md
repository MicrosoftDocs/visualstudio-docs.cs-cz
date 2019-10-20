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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664683"
---
# <a name="elements-xelement-dynamic-property"></a>Elementy (dynamická vlastnost XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Získá indexer použitý k načtení podřízených prvků aktuálního prvku, které odpovídají zadanému rozbalenému názvu.

## <a name="syntax"></a>Syntaxe

```
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota
 Indexer typu `IEnumerable<XElement> Item(String expandedName)`. Tento indexer Získá rozšířený název požadovaných podřízených prvků a vrátí odpovídající podřízené prvky ve <xref:System.Collections.IEnumerable> `<` <xref:System.Xml.Linq.XElement> `>` Collection.

## <a name="remarks"></a>Poznámky
 Tato vlastnost je ekvivalentní metodě <xref:System.Xml.Linq.XContainer.Elements%28System.Xml.Linq.XName%29?displayProperty=fullName> třídy <xref:System.Xml.Linq.XContainer>.

 Prvky ve vrácené kolekci jsou v pořadí zdrojového dokumentu XML.

 Tato vlastnost používá odložené provádění.

## <a name="see-also"></a>Viz také
 [XElement třídy dynamické vlastnosti](../designers/xelement-class-dynamic-properties.md) [](../designers/element-xelement-dynamic-property.md) [následovníci](../designers/descendants-xelement-dynamic-property.md) elementu

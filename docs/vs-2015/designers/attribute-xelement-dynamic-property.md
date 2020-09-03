---
title: Atribut (dynamická vlastnost XElement) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 551e072b05e7a88ff9624c5d16e4aa199a6afd66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657985"
---
# <a name="attribute-xelement-dynamic-property"></a>Atribut (dynamická vlastnost XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Získá indexer použitý k načtení instance atributu, který odpovídá zadanému rozšířenému názvu.

## <a name="syntax"></a>Syntax

```
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota
 Indexer `XAttribute Item(String expandedName)` typu Tento indexer Získá rozšířený název zadaného atributu a vrátí odpovídající <xref:System.Xml.Linq.XAttribute> , nebo `null` Pokud neexistuje žádný atribut se zadaným názvem.

## <a name="remarks"></a>Poznámky
 Tato vlastnost je ekvivalentní <xref:System.Xml.Linq.XElement.Attribute%2A> metodě <xref:System.Xml.Linq.XElement?displayProperty=fullName> třídy.

## <a name="see-also"></a>Viz také
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>[Hodnota](../designers/value-xattribute-dynamic-property.md) [dynamických vlastností třídy XElement](../designers/xelement-class-dynamic-properties.md)

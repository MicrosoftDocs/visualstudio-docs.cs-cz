---
title: XML (dynamická vlastnost XElement) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c794d79d62fc580001efc5cf16993d4ac5fef48b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663849"
---
# <a name="xml-xelement-dynamic-property"></a>XML (dynamická vlastnost XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Získá neformátovaný obsah XML elementu.

## <a name="syntax"></a>Syntax

```
elem.Xml
```

## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota
 <xref:System.String>Který představuje neformátovaný obsah XML elementu.

## <a name="remarks"></a>Poznámky
 Tato vlastnost je ekvivalentní <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> metodě <xref:System.Xml.Linq.XNode?displayProperty=fullName> třídy s `SaveOptions` parametrem nastaveným na <xref:System.Xml.Linq.SaveOptions> .

## <a name="see-also"></a>Viz také
 [Hodnota](../designers/value-xelement-dynamic-property.md) [dynamických vlastností třídy XElement](../designers/xelement-class-dynamic-properties.md)

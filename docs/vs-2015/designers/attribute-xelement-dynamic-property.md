---
title: Atribut (dynamická vlastnost XElement) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b6be72f0b40382ca8c7e9986c2d5a56e03344221
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49194834"
---
# <a name="attribute-xelement-dynamic-property"></a>Atribut (dynamická vlastnost XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Získá se používá k načtení instance atributu, který odpovídá zadané rozbalený název indexeru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
elem.Attribute[{namespaceName}attribName]  
```  
  
## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota  
 Indexer typu `XAttribute Item(String expandedName)`. Indexer vezme rozbalený název zadaného atributu a vrátí odpovídající <xref:System.Xml.Linq.XAttribute>, nebo `null` Pokud neexistuje žádný atribut se zadaným názvem.  
  
## <a name="remarks"></a>Poznámky  
 Tato vlastnost je ekvivalentní <xref:System.Xml.Linq.XElement.Attribute%2A> metodu <xref:System.Xml.Linq.XElement?displayProperty=fullName> třídy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>   
 [Dynamické vlastnosti třídy XElement](../designers/xelement-class-dynamic-properties.md)   
 [Hodnota](../designers/value-xattribute-dynamic-property.md)




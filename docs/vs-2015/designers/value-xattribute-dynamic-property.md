---
title: Value (dynamická vlastnost XAttribute) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XAttribute.Value
api_type:
- Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9a31b4c4182ed67a3e67d3c25c2c5ccf50e083f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664053"
---
# <a name="value-xattribute-dynamic-property"></a>Value (dynamická vlastnost XAttribute)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Získá nebo nastaví hodnotu atributu XML.

## <a name="syntax"></a>Syntax

```
attrib.Value
```

## <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota
 <xref:System.String>Obsahující hodnotu tohoto atributu.

## <a name="exceptions"></a>Výjimky

|Typ výjimky|Stav|
|--------------------|---------------|
|<xref:System.ArgumentNullException>|Při nastavování `value` je `null` .|

## <a name="remarks"></a>Poznámky
 Tato vlastnost je ekvivalentní <xref:System.Xml.Linq.XAttribute.Value%2A> vlastnosti <xref:System.Xml.Linq.XAttribute?displayProperty=fullName> třídy, ale tato dynamická vlastnost také podporuje oznamování změn.

## <a name="see-also"></a>Viz také
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>[Atribut](../designers/attribute-xelement-dynamic-property.md) [dynamické vlastnosti třídy XAttribute](../designers/xattribute-class-dynamic-properties.md)

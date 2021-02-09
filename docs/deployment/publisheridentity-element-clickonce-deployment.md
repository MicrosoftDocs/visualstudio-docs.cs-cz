---
title: '&lt;publisherIdentity – – &gt; element (nasazení ClickOnce) | Microsoft Docs'
description: Element publisherIdentity – obsahuje informace o vydavateli, který podepsal manifest nasazení. Element je vyžadován pro podepsané manifesty.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65f225f8e3dd3f6d2b3afb2d2a5284d172d4fab1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891290"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity – – &gt; element (nasazení ClickOnce)
Obsahuje informace o vydavateli, který podepsal tento manifest nasazení.

## <a name="syntax"></a>Syntax

```xml
<publisherIdentity
   name
   issuerKeyHash
/>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `publisherIdentity`Element je vyžadován pro podepsané manifesty. V následující tabulce jsou uvedeny atributy, které `publisherIdentity` prvek podporuje.

|Atribut|Popis|
|---------------|-----------------|
|`name`|Povinná hodnota. Popisuje identitu strany, která publikovala tuto aplikaci.|
|`issuerKeyHash`|Povinná hodnota. Obsahuje hodnotu hash SHA-1 veřejného klíče vystavitele certifikátu.|

#### <a name="parameters"></a>Parametry

## <a name="property-valuereturn-value"></a>Hodnota nebo návratová hodnota vlastnosti

## <a name="exceptions"></a>Výjimky

## <a name="remarks"></a>Poznámky

## <a name="requirements"></a>Požadavky

## <a name="subhead"></a>Dílčí Head
---
title: '&lt;Assembly – &gt; element (nasazení ClickOnce) | Microsoft Docs'
description: Element Assembly je kořenový prvek a je vyžadován v nasazení ClickOnce. Jeho první obsažený prvek musí být element assemblyIdentity.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b7838e0a212bbc1e743783255106bb44561fbe62
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837759"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;Assembly – &gt; element (nasazení ClickOnce)
Element nejvyšší úrovně pro manifest nasazení.

## <a name="syntax"></a>Syntax

```xml

      <assembly  
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `assembly`Element je kořenový prvek a je povinný. Jeho první obsažený prvek musí být `assemblyIdentity` element. Prvky manifestu musí být v následujících oborech názvů: `urn:schemas-microsoft-com:asm.v1` , `urn:schemas-microsoft-com:asm.v2` a `http://www.w3.org/2000/09/xmldsig#` . Podřízené elementy sestavení musí být také v těchto oborech názvů, dědění nebo označením.

 `assembly`Element má následující atribut.

|Atribut|Popis|
|---------------|-----------------|
|`manifestVersion`|Povinná hodnota. Tento atribut musí být nastaven na hodnotu `1.0` .|

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje `assembly` prvek v manifestu nasazení pro aplikaci nasazenou pomocí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Tento příklad kódu je součástí většího příkladu, který je k dispozici v tématu [manifestu nasazení ClickOnce](../deployment/clickonce-deployment-manifest.md) .

```xml
<asmv1:assembly
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
```

## <a name="see-also"></a>Viz také
- [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)
- [\<assembly> objekt](../deployment/assembly-element-clickonce-application.md)
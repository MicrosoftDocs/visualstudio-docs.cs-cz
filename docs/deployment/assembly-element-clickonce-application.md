---
title: '&lt;Assembly – &gt; element (aplikace ClickOnce) | Microsoft Docs'
description: Element Assembly je kořenový prvek a je vyžadován v aplikaci ClickOnce. Jeho první obsažený prvek musí být element assemblyIdentity.
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
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c3614cd2d4fc0e6a5eebfb8dc6911e6eb183c01
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383219"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;Assembly – &gt; element (aplikace ClickOnce)
Element nejvyšší úrovně pro manifest aplikace

## <a name="syntax"></a>Syntax

```xml

      <assembly
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `assembly`Element je kořenový prvek a je povinný. Jeho první obsažený prvek musí být `assemblyIdentity` element. Prvky manifestu musí být v jednom z následujících oborů názvů:

 `urn:schemas-microsoft-com:asm.v1`

 `urn:schemas-microsoft-com:asm.v2`

 `http://www.w3.org/2000/09/xmldsig#`

 Podřízené elementy sestavení musí být také v těchto oborech názvů, dědění nebo označením.

 `assembly`Element má následující atribut.

|Atribut|Popis|
|---------------|-----------------|
|`manifestVersion`|Povinná hodnota. `manifestVersion`Atribut musí být nastaven na hodnotu `1.0` .|

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje `assembly` prvek v manifestu aplikace pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci. Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestu aplikace ClickOnce](../deployment/clickonce-application-manifest.md).

```xml
<asmv1:assembly
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">
```

## <a name="see-also"></a>Viz také
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<assembly> objekt](../deployment/assembly-element-clickonce-deployment.md)

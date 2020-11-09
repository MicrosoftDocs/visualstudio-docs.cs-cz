---
title: '&lt;assemblyIdentity – &gt; element (aplikace ClickOnce) | Microsoft Docs'
description: V aplikaci ClickOnce je požadován element assemblyIdentity. Neobsahuje žádné podřízené elementy a má atributy popsané v tomto článku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c86d5d1fd1e25b498405197b68efd9553ed64f16
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383206"
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;assemblyIdentity – &gt; element (aplikace ClickOnce)
Identifikuje aplikaci nasazenou v [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení.

## <a name="syntax"></a>Syntax

```xml

      <assemblyIdentity
   name
   version
   publicKeyToken
   processorArchitecture
   language
/>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `assemblyIdentity`Element je povinný. Neobsahuje žádné podřízené elementy a má následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`Name`|Povinná hodnota. Určuje název aplikace.<br /><br /> Pokud `Name` obsahuje speciální znaky, jako například jednoduché nebo dvojité uvozovky, aplikace může selhat při aktivaci.|
|`Version`|Povinná hodnota. Určuje číslo verze aplikace v následujícím formátu: `major.minor.build.revision`|
|`publicKeyToken`|Nepovinný parametr. Určuje 16 znaků šestnáctkový řetězec, který představuje posledních 8 bajtů `SHA-1` hodnoty hash veřejného klíče, pod nímž je aplikace nebo sestavení podepsáno. Veřejný klíč, který se používá k podepsání katalogu, musí být 2048 bitů nebo větší.<br /><br /> I když podepisování sestavení je doporučeno, ale nepovinné, tento atribut je povinný. Pokud je sestavení bez znaménka, měli byste zkopírovat hodnotu z sestavení podepsaného svým držitelem nebo použít "fiktivní" hodnotu všech nul.|
|`processorArchitecture`|Povinná hodnota. Určuje procesor. Platné hodnoty jsou `msil` pro všechny procesory, `x86` pro 32 Windows, `IA64` pro 64-bit Windows a `Itanium` 64 pro procesory Itanium s procesorem Itanium.|
|`language`|Povinná hodnota. Identifikuje kódy jazyků dvou částí (například `en-US` ) sestavení. Tento prvek je v `asmv2` oboru názvů. Je-li tento parametr zadán, je použita výchozí hodnota `neutral` .|

## <a name="examples"></a>Příklady

### <a name="description"></a>Popis
 Následující příklad kódu ukazuje `assemblyIdentity` prvek v [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu aplikace. Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestu aplikace ClickOnce](../deployment/clickonce-application-manifest.md).

### <a name="code"></a>Kód

```xml
<asmv1:assemblyIdentity
  name="My Application Deployment.exe"
  version="1.0.0.0"
  publicKeyToken="43cb1e8e7a352766"
  language="neutral"
  processorArchitecture="x86"
  type="win32" />
```

## <a name="see-also"></a>Viz také
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<assemblyIdentity> objekt](../deployment/assemblyidentity-element-clickonce-deployment.md)
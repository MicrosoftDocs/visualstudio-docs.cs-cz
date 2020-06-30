---
title: '&lt;vstoRuntime – &gt; element (vývoj pro Office v sadě Visual Studio)'
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 985afe50d7c6edcfdb34e2ca046f59c5f7b664a0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541879"
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;vstoRuntime – &gt; element (vývoj pro Office v sadě Visual Studio)
  `vstoRuntime`Element `vstav3` oboru názvů obsahuje podporovanou verzi Visual Studio Tools for Office runtime pro konkrétní řešení Office.

## <a name="syntax"></a>Syntax

```xml
<vstoRuntime
    release
    version
    supportUrl />
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `vstoRuntime`Element je povinný a je v `vstav3` oboru názvů. Pokud řešení pro systém Office podporuje dvě verze Visual Studio Tools for Office runtime, existují dva `vstoRuntime` prvky v manifestu aplikace.

 `vstoRuntime`Element má následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`release`|Povinná hodnota. Vydaná verze modulu runtime Visual Studio Tools for Office.|
|`version`|Povinná hodnota. Číslo verze modulu runtime Visual Studio Tools for Office.|
|`supportUrl`|Nepovinný parametr. Odkaz na umístění instalace modulu runtime Visual Studio Tools for Office.|

 `vstoRuntime`neobsahuje žádné elementy.

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje `vstoRuntime` prvek v manifestu aplikace pro řešení Office nasazené pomocí [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestech aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<vstav3:vstoRuntime
    release="VSTOR40Beta1"
    version="10.0.20303"
    supportUrl="http://www.microsoft.com" />
```

## <a name="see-also"></a>Viz také

- [Manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)

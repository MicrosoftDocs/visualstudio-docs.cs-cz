---
title: '&lt;Update – &gt; element (vývoj pro Office v sadě Visual Studio)'
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 241bddb8c79a01bb1ba6921486a4dc46d99940cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537381"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;Update – &gt; element (vývoj pro Office v sadě Visual Studio)
  `update`Prvek určuje interval, ve kterém bude řešení vyhledávat aktualizace.

## <a name="syntax"></a>Syntax

```xml
<update
  enabled>
  <expiration
    maximumAge
    unit
  />
</update>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `update`Element je povinný a je v `vstav3` oboru názvů.

 `update`Element má následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`enabled`|Povinná hodnota. Nastavte povoleno na jednu z následujících hodnot:<br /><br /> -   **true** pro kontrolu aktualizací.<br />-   **false** , pokud chcete zabránit kontrole aktualizací.|

 `update`Element má následující podřízené prvky.

### <a name="expiration"></a>vypršení platnosti
 `expiration`Element je povinný a je v `vstav3` oboru názvů. Tento prvek určuje interval, ve kterém řešení vyhledává aktualizace.

 `expiration`Element má následující atributy.

|Atribut|Popis|
|---------------|-----------------|
|`maximumAge`| Povinná hodnota. Nastavte tuto hodnotu jako celé číslo.|
|`unit`|Povinná hodnota. Nastavte `unit` na jednu z následujících hodnot:<br /><br /> -   **hodin**<br />-   **denní**<br />-   **Week**|

## <a name="example-of-always-checking-for-updates"></a>Příklad vždycky se zjišťováním aktualizací

### <a name="description"></a>Popis
 Následující příklad kódu ukazuje `update` prvek, který je nastaven tak, aby vždy kontroloval aktualizace v řešeních pro systém Office.

### <a name="code"></a>Kód

```xml
<vstav3:update enabled="true" />
```

## <a name="example-of-setting-a-default-update-interval"></a>Příklad nastavení výchozího intervalu aktualizace

### <a name="description"></a>Popis
 Následující příklad kódu ukazuje `update` prvek v manifestu aplikace pro řešení Office. Tento příklad kódu je součástí většího příkladu, který je k dispozici v [manifestech aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kód

```xml
<vstav3:update enabled="true">
    <vstav3:expiration maximumAge="7" unit="days" />
</vstav3:update>
```

## <a name="see-also"></a>Viz také

- [Nasazení řešení Office pomocí technologie ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)

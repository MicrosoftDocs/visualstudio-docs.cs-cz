---
title: '&lt;Schedules – &gt; element (zaváděcí nástroj) | Microsoft Docs'
description: Element Schedules obsahuje prvky plánu, které definují konkrétní časy, ve kterých by měly být spuštěny příkazy definované elementem Command.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0154816985076373c3ced4981aa714971a9ded29
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949646"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Schedules – &gt; element (zaváděcí nástroj)
`Schedules`Element obsahuje `Schedule` prvky, které definují konkrétní časy, ve kterých `Command` by měly být spuštěny příkazy definované elementem.

## <a name="syntax"></a>Syntax

```xml
<Schedules>
    <Schedule
        Name
    >
        <BuildList />
        <BeforePackage />
        <AfterPackage />
    </Schedule>
</Schedules>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `Schedules`Prvek je podřízeným prvkem `Product` elementu. Každý `Product` prvek může mít maximálně jeden `Schedules` element. `Schedules`Element nemá žádné atributy.

## <a name="schedule"></a>Plán
 `Schedule`Prvek je podřízeným prvkem `Schedules` elementu. `Schedules`Element musí mít alespoň jeden `Schedule` element.

 `Schedule` má následující atribut.

|Atribut|Popis|
|---------------|-----------------|
|`Name`|Povinná hodnota. Název položky plánu To odpovídá `ScheduleName` vlastnosti `Command` elementu. Když `Command` odkazuje na pojmenovaný plán, bude proveden pouze v čase stanoveném tímto `Schedule` prvkem. Plány mohou být také přidruženy k `FailIf` `BypassIf` prvkům a, které omezují tyto podmíněné testy, aby byly spuštěny podle zadaného plánu. Další informace naleznete v tématu [ \<Commands> element](../deployment/commands-element-bootstrapper.md).|

 Daný `Schedule` element může mít přesně jednu z následujících podřízených objektů.

## <a name="buildlist"></a>BuildList
 `BuildList`Element instruuje instalační program, aby spustil příkaz hned po spuštění spouštěcí aplikace.

## <a name="beforepackage"></a>BeforePackage
 `BeforePackage`Element instruuje instalační program, aby před instalací zadaného balíčku spustil příkaz.

## <a name="afterpackage"></a>AfterPackage
 `AfterPackage`Element dá instalačnímu programu pokyn, aby po instalaci zadaného balíčku spustil příkaz.

## <a name="see-also"></a>Viz také
- [\<Product> objekt](../deployment/product-element-bootstrapper.md)
- [Odkaz na schéma produktu a balíčku](../deployment/product-and-package-schema-reference.md)
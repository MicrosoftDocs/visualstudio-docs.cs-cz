---
title: Rozhraní API grafiky a statistiky paměti | Microsoft Docs
description: Projděte si Přehled statistik rozhraní API grafiky a statistiky paměti, které zobrazují informace o využití rozhraní Direct3D API a spotřebě paměti GPU u různých prostředků.
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 08c9f518f6d56f2ec211ef494da3890a56bf1369
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882294"
---
# <a name="graphics-api-and-memory-statistics"></a>Grafické rozhraní API a statistika paměti
<!-- VERSIONLESS -->
Visual Studio 2017 a vyšší podporují statistiku rozhraní API grafiky a nástroje statistiky paměti.  Tyto dva nástroje vám umožňují zobrazit různé bity informací o využití rozhraní Direct3D API a také spotřebu paměti GPU různých prostředků.

## <a name="graphics-api-statistics"></a>Statistika rozhraní API grafiky
Statistika rozhraní API grafiky v aplikaci Visual Studio Diagnostika grafiky umožňuje zobrazit všechna volání Direct3D, která byla provedena, a počet jednotlivých volání.  Chcete-li zobrazit okno, vyberte položku nabídky **statistiky zobrazení > rozhraní API** .

![Statistika rozhraní API](media/gfx_diag_api_statistics.png)

Tento nástroj může být užitečný při zjišťování volání rozhraní DirectX, které nemůžete dělat, nebo volání, která provádíte příliš často.

Kliknutím pravým tlačítkem myši v okně můžete zkopírovat všechna data ve formátu CSV, který je možné vložit do aplikace, jako je Excel, pro další analýzu.

## <a name="memory-statistics"></a>Statistiky paměti
Tento nástroj zobrazí velikost paměti, kterou ovladač grafiky přiděluje pro prostředky, které vytvoříte v rámci snímku.  Chcete-li zobrazit toto okno, vyberte položku nabídky **statistiky zobrazení > paměti** .

![Statistiky paměti](media/gfx_diag_memory_statistics.png)

Sloupec **alokace GPU** zobrazuje množství paměti využívané událostí zobrazenými ve sloupci **událost** .  Můžete také vybrat ikonu kukátka ![ kukátka ](media/gfx_watch.png) a zobrazit [historii prostředků](graphics-event-list.md#resource-history) pro vybranou událost.

Stejně jako u nástroje statistiky rozhraní API můžete kliknout pravým tlačítkem myši v okně a zkopírovat všechna data ve formátu CSV, který je možné vložit do aplikace Excel pro další analýzu.

## <a name="see-also"></a>Viz také
- [Diagnostika grafiky (Ladění grafiky DirectX)](visual-studio-graphics-diagnostics.md)
- [Historie prostředků](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->
---
title: Popisy událostí | Microsoft Docs
description: Seznamte se s typy událostí a důvody jejich použití. Každý typ události má určitý účel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a2d4ee971e2c53c9431982ef33483471a50c54bc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851306"
---
# <a name="event-descriptions"></a>Popisy událostí
Každý typ události má určitý účel.

## <a name="events-and-the-reasons-for-their-use"></a>Události a důvody jejich použití

|Událost|Description|
|-----------|-----------------|
|Aktivovat události dokumentu|Nastane, pokud ladicí stroj (DE) chce IDE otevřít nebo převést dokument do popředí.|
|Události zarážek nebo chyb zarážek|Odesílá se, když je navázána zarážka, nebo když se zarážka nemůže svázat a vrátí se chyba.|
|Nevázané události zarážky|Nastane, pokud se zruší vazba vázané zarážky z kódu.|
|Může zastavit události.|Odesílá se do integrovaného vývojového prostředí (IDE), aby se určilo, jestli se uživatel může zastavit v zadaném bodě kódu.|
|Události zarážek|Nastane, pokud je dosaženo kódu nebo datové zarážky.|
|Události textu dokumentu|Nastane, pokud se změní text v dokumentu. Tyto události nejsou odesílány `IDebugEventCallBack2::Event` metodou.|
|Modul vytvořit události|Odesílá se při prvním vytvoření motoru.|
|Události vstupního bodu|Odesílá se, když se ladicí program spustí, a dostal svůj první vstupní bod uživatele.|
|Události výjimky|Odesílá se, když běžící program narazí na výjimku.|
|Události dokončení vyhodnocení výrazu|Odesílá se po dokončení vyhodnocení asynchronního výrazu.|
|Najít události symbolů|Odesílá se vždy, když DE potřebuje požádat uživatele o vyhledání symbolů pro modul.|
|Načíst dokončené události|Odesílá se pouze v případě, že je dokončeno počáteční zatížení programu a první kód bude spuštěn v programu.|
|Události zpráv|Odesílá se při posílání zpráv uživatelům.|
|Události načtení modulu|Odesílá se při načtení nebo uvolnění nového modulu.|
|Události výstupních řetězců|Odesílá se, když program zapíše výstup ladění.|
|Vytváření a zničení událostí|Odesílá se k oznámení vytvoření nebo zničení procesů, programů, vlastností, relací a vláken, takže IDE sady Visual Studio může sledovat stav laděných programů.|
|Události dokončení kroku|Odesílá se po dokončení kroku.|
|Události změny názvu vlákna|Odesílá se, když uživatel změní název vlákna.|
|Události změny názvu programu|Odesílá se, když uživatel změní název programu.|

## <a name="see-also"></a>Viz také
- [Odesílání událostí](../../extensibility/debugger/sending-events.md)

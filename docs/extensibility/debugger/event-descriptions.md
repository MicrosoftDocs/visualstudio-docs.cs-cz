---
title: Popisy událostí | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3c2582717fd4da3b833da90a951f9b8f72a59f71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738784"
---
# <a name="event-descriptions"></a>Popisy událostí
Každý typ události má určitý účel.

## <a name="events-and-the-reasons-for-their-use"></a>Události a důvody jejich použití

|Událost|Popis|
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

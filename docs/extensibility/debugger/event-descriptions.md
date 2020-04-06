---
title: Popisy událostí | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738784"
---
# <a name="event-descriptions"></a>Popisy událostí
Každý typ události má specifický účel.

## <a name="events-and-the-reasons-for-their-use"></a>Události a důvody jejich použití

|Událost|Popis|
|-----------|-----------------|
|Aktivace událostí dokumentu|Dojít, když ladicí modul (DE) chce ide otevřít nebo přenést dokument do popředí.|
|Události chyby vázané na zarážky nebo zarážky|Odesláno, pokud je zarážka vázána nebo pokud se zarážka nemůže vázat a je vrácena chyba.|
|Nevázané události zarážky|Dojít při vázané zarážky unbinds z kódu.|
|Může zastavit události|Odesláno do rozhraní IDE k určení, zda uživatel chce zastavit v zadaném bodě v kódu.|
|Události zarážky|Dojít při zásahu kódu nebo zarážky dat.|
|Události textu dokumentu|Vyvolá se při změně textu v dokumentu. Tyto události nejsou odesílány `IDebugEventCallBack2::Event` prostřednictvím metody.|
|Engine vytvořit události|Odesláno při prvním vytvoření motoru.|
|Události vstupního bodu|Odesláno, když je laděný program spuštěn jeho inicializační kód a dosáhl svého prvního vstupního bodu uživatele.|
|Události výjimek|Odesláno, když spuštěný program narazí na výjimku.|
|Události vyhodnocení výrazu dokončení události|Odesláno po dokončení vyhodnocení asynchronního výrazu.|
|Najít události symbolu|Odesláno vždy, když DE potřebuje požádat uživatele o nalezení symbolů pro modul.|
|Načíst úplné události|Odesláno pouze v případě, že počáteční načtení programu je dokončena a první kód se chystá spustit v programu.|
|Události zprávy|Odesláno při odeslání zpráv uživatelům.|
|Události načítání modulu|Odesláno při načtení nebo uvolnění nového modulu.|
|Události výstupního řetězce|Odesláno při programu zapíše ladicí výstup.|
|Vytváření a ničení událostí|Odesláno oznámit vytvoření nebo zničení procesů, programů, vlastností, relací a vláken, aby rozhraní IDE sady Visual Studio bylo možné sledovat stav laděných programů.|
|Události dokončení kroku|Odesláno po dokončení kroku.|
|Události změny názvu vlákna|Odesláno, když uživatel změní název vlákna.|
|Události změny názvu programu|Odesláno, když uživatel změní název programu.|

## <a name="see-also"></a>Viz také
- [Odesílání událostí](../../extensibility/debugger/sending-events.md)

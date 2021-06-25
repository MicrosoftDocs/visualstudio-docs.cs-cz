---
title: Popisy | Microsoft Docs
description: Seznamte se s typy událostí a důvody jejich použití. Každý typ události má určitý účel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ee2eedac924b3bbd58fac6980da9151a88da9196
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902641"
---
# <a name="event-descriptions"></a>Popisy událostí
Každý typ události má určitý účel.

## <a name="events-and-the-reasons-for-their-use"></a>Události a důvody jejich použití

|Událost|Description|
|-----------|-----------------|
|Aktivace událostí dokumentu|K tomu dochází v případě, že ladicí modul (DE) chce, aby se integrované vývojové prostředí otevřel nebo přeneslo dokument do popředí.|
|Chybové události vázané na zarážku nebo zarážku|Odesílá se, když je zarážka svázaná nebo když zarážka nemůže vytvořit vazbu a vrátí se chyba.|
|Události nevázané na zarážku|K tomu dochází v případě, že vázané zarážky odruší binování od kódu.|
|Může zastavit události.|Odesláno do integrovaného vývojového prostředí za účelem určení, zda by uživatel chtěl zastavit v zadaném bodě v kódu.|
|Události zarážky|K tomu dojde, když dojde k chybě kódu nebo datové zarážky.|
|Dokumentovat textové události|K této chybě dochází při změně textu v dokumentu. Tyto události nejsou odesílány prostřednictvím `IDebugEventCallBack2::Event` metody .|
|Události vytvoření modulu|Odesílá se při prvním vytvoření modulu.|
|Události vstupního bodu|Odesílá se, když laděné programy spouštěly svůj inicializační kód a dosáhly svého prvního uživatelského vstupního bodu.|
|Události výjimky|Odesílá se, když spuštěný program narazí na výjimku.|
|Události dokončení vyhodnocení výrazu|Odesílá se po dokončení vyhodnocení asynchronního výrazu.|
|Vyhledání událostí symbolu|Odesílá se vždy, když destrukce potřebuje požádat uživatele o vyhledání symbolů pro modul.|
|Načtení událostí dokončení|Odesláno pouze v případě, že se počáteční načtení programu dokončí a první kód se v programu spustí.|
|Události zpráv|Odesílá se při odesílání zpráv uživatelům.|
|Události načítání modulů|Odesílá se při načtení nebo uvolnění nového modulu.|
|Události výstupního řetězce|Odesílá se, když program zapisuje výstup ladění.|
|Vytváření a ničení událostí|Odesláno, aby oznamoval vytvoření nebo zničení procesů, programů, vlastností, relací a vláken, aby integrované vývojové prostředí Visual Studio IDE sledovalo stav laděného programu.|
|Události dokončení kroku|Odesílá se po dokončení kroku.|
|Události změny názvu vlákna|Odesláno, když uživatel změní název vlákna.|
|Události změny názvu programu|Odesílá se, když uživatel změní název programu.|

## <a name="see-also"></a>Viz také
- [Odesílání událostí](../../extensibility/debugger/sending-events.md)

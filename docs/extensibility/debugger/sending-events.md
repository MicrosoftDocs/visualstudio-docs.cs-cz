---
title: Odesílání událostí | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ec0d3aa29da562147b71b8efde49baf07d8ae0b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713031"
---
# <a name="send-events"></a>Odesílání událostí
Mechanismus komunikace mezi ladicím programem a ladicím strojem (DE) je model událostí založený na modelu DCOM. Události jsou odesílány jako objekty MODELU COM a každá událost má parametry, které určují:

- De, který volal událost.

- Popis toho, co se stalo.

- Informace o procesu, programu a vlákně, které identifikují kontext, kde k události došlo. Proces není odeslán pro události odeslané z DE.

- Typ události, který označuje, zda je událost synchronní nebo asynchronní.

  Všechny události ladění jsou odesílány pomocí metody [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="in-this-section"></a>V tomto oddílu
 [Zdroje událostí](../../extensibility/debugger/event-sources-visual-studio-sdk.md) Vysvětluje dva zdroje událostí: ladicí modul (DE) a správce ladění relace (SDM).

 [Podporované typy událostí](../../extensibility/debugger/supported-event-types.md) Popisuje aktuálně podporované typy událostí: asynchronní a synchronní.

 [Popisy událostí](../../extensibility/debugger/event-descriptions.md) Definuje události a důvody pro jejich použití.

## <a name="related-sections"></a>Související oddíly
 [Vytvoření vlastního ladicího modulu](../../extensibility/debugger/creating-a-custom-debug-engine.md) Popisuje, jak DE pracuje s interpretu nebo operačního systému poskytovat služby ladění.

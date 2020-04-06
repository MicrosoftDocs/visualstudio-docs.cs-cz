---
title: Odeslání požadovaných událostí | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc83b47e53607fe1111ececbbf892c96f7bbb639
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712999"
---
# <a name="send-the-required-events"></a>Odeslat požadované události
Tento postup použijte pro odesílání požadovaných událostí.

## <a name="process-for-sending-required-events"></a>Proces odesílání požadovaných událostí
 Následující události jsou vyžadovány v tomto pořadí při vytváření ladicího modulu (DE) a jeho připojení k programu:

1. Odeslat objekt události [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do správce ladění relace (SDM) při de je inicializován pro ladění jednoho nebo více programů v procesu.

2. Pokud je k programu, který má být laděn, připojen, odešlete objektu události [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) do objektu SDM. Tato událost může být zastavení událost, v závislosti na návrhu motoru.

3. Pokud je program připojen k při spuštění procesu, odešlete objekt události [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) do objektu SDM, abyste upozornili ide nového vlákna. Tato událost může být zastavení událost, v závislosti na návrhu motoru.

4. Odeslat objekt události [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) do sdm při dokončení načítání programu nebo při připojení k programu. Tato událost musí být zastavení události.

5. Pokud je spuštěna aplikace, která má být laděna, odešlete objekt události [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) do objektu SDM při spuštění první instrukce kódu v architektuře za běhu. Tato událost je vždy zastavení události. Při krokování do relace ladění ide zastaví na této události.

> [!NOTE]
> Mnoho jazyků používá globální inicializátory nebo externí, předkompilované funkce (z knihovny CRT nebo _Main) na začátku jejich kódu. Pokud jazyk programu, který ladíte, obsahuje některý z těchto typů prvků před počátečním vstupním bodem, je tento kód spuštěn **main** a `WinMain`událost vstupního bodu je odeslána, když je dosaženo vstupního bodu uživatele, například main nebo , .

## <a name="see-also"></a>Viz také
- [Povolení odlazení programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)

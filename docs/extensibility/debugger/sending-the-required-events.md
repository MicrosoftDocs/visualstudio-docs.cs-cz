---
title: Odesílání požadovaných událostí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2512dc35d77263c5237dff12b7a5f07060458e1c
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251420"
---
# <a name="send-the-required-events"></a>Odesílání požadovaných událostí
Pomocí tohoto postupu pro odesílání požadovaných událostí.  
  
## <a name="process-for-sending-required-events"></a>Proces odesílání požadovaných událostí  
 Tyto události jsou povinné, v tomto pořadí, při vytváření ladicího stroje (DE) a připojení k programu:  
  
1.  Odeslání [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) objektu události do Správce ladění relace (SDM), když je DE je inicializován pro ladění jednoho nebo více programů v procesu.  
  
2.  Při ladění programu přiřazen, odeslat [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) objekt SDM události. Tato událost může být událostí ukončení, v závislosti na návrhu modulu.  
  
3.  Pokud program je připojen k při spuštění procesu, pošlete [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) události objektu SDM oznámit integrovaného vývojového prostředí nového vlákna. Tato událost může být událostí ukončení, v závislosti na návrhu modulu.  
  
4.  Odeslání [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) události objektu SDM po dokončení načítání nebo dokončení připojení k programu program, který se právě ladí. Tato událost musí být událostí ukončení.  
  
5.  Pokud je aplikace k ladění, odesílat [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) události objektu SDM po první instrukce kódu za běhu architektury se pokračovalo. Tato událost je vždy událostí ukončení. Při krokování s vnořením do relace ladění, rozhraní IDE přestane na této události.  
  
> [!NOTE]
>  Řadu jiných jazyků použití globálních inicializátorů nebo externí, předkompilované funkcí (z knihovny CRT nebo _Main) na začátku svůj kód. Pokud jazyk ladíte program obsahuje některý z těchto typů prvků před počáteční vstupní bod, je tento kód spuštěný a vstupního bodu událost je odeslána při vstupu uživatele bodu, jako například **hlavní** nebo `WinMain`, je byl dosažen.  
  
## <a name="see-also"></a>Viz také:  
 [Povolení ladění programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
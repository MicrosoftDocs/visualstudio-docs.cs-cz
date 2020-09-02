---
title: Odeslání požadovaných událostí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 457e2daf3e52c23ba9733d09d3aeb94750b5fab9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64831365"
---
# <a name="sending-the-required-events"></a>Odesílání požadovaných událostí
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tento postup slouží k odeslání požadovaných událostí.  
  
## <a name="process-for-sending-required-events"></a>Proces odeslání požadovaných událostí  
 V tomto pořadí jsou vyžadovány následující události při vytváření ladicího stroje (DE) a jeho připojení k programu:  
  
1. Pokud je DE initializeed pro ladění jednoho nebo více programů v procesu, odešlete objekt události [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do Správce ladění relace (SDM).  
  
2. Když je program, který se má ladit, připojený k, odešlete objekt události [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) do SDM. Tato událost může být událost zastavení v závislosti na návrhu modulu.  
  
3. Pokud je program připojen ke spuštění procesu, odešle objekt události [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) do modelu SDM pro oznamování integrovaného vývojového prostředí (IDE) nového vlákna. Tato událost může být událost zastavení v závislosti na návrhu modulu.  
  
4. Odešle objekt události [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) do SDM, když je dokončeno načítání programu nebo když se dokončí připojení k programu. Tato událost musí být událost zastavení.  
  
5. Pokud se spustí aplikace, která se má ladit, odešle objekt události [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) do modelu SDM, pokud se chystá spuštění první instrukce kódu v architektuře run-time. Tato událost je vždy událost zastavení. Při krokování do relace ladění se rozhraní IDE zastaví v této události.  
  
> [!NOTE]
> Mnoho jazyků používá globální inicializátory nebo externí, předkompilované funkce (z knihovny CRT nebo _Main) na začátku kódu. Pokud jazyk programu, který ladíte, obsahuje jeden z těchto typů prvků před počátečním vstupním bodem, pak se tento kód spustí a událost vstupního bodu je odeslána, když je dosaženo vstupního bodu uživatele, jako je například **Main** nebo `WinMain` .  
  
## <a name="see-also"></a>Viz také  
 [Povolení ladění programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)

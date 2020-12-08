---
title: Odeslání požadovaných událostí | Microsoft Docs
description: Přečtěte si o seřazených událostech, které jsou požadovány při vytváření ladicího stroje a jeho připojení k programu v ladění aplikace Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 49c85e3d371bfd729d55e9d17a6c8de61924e35f
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845307"
---
# <a name="send-the-required-events"></a>Odeslat požadované události
Tento postup slouží k odeslání požadovaných událostí.

## <a name="process-for-sending-required-events"></a>Proces odeslání požadovaných událostí
 V tomto pořadí jsou vyžadovány následující události při vytváření ladicího stroje (DE) a jeho připojení k programu:

1. Pokud je DE initializeed pro ladění jednoho nebo více programů v procesu, odešlete objekt události [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) do Správce ladění relace (SDM).

2. Když je program, který se má ladit, připojený k, odešlete objekt události [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) do SDM. Tato událost může být událost zastavení v závislosti na návrhu modulu.

3. Pokud je program připojen ke spuštění procesu, odešle objekt události [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) do modelu SDM pro oznamování integrovaného vývojového prostředí (IDE) nového vlákna. Tato událost může být událost zastavení v závislosti na návrhu modulu.

4. Odešle objekt události [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) do SDM, když je dokončeno načítání programu nebo když se dokončí připojení k programu. Tato událost musí být událost zastavení.

5. Pokud se spustí aplikace, která se má ladit, odešle objekt události [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) do modelu SDM, pokud se chystá spuštění první instrukce kódu v architektuře run-time. Tato událost je vždy událost zastavení. Při krokování do relace ladění se rozhraní IDE zastaví v této události.

> [!NOTE]
> Mnoho jazyků používá globální inicializátory nebo externí, předkompilované funkce (z knihovny CRT nebo _Main) na začátku kódu. Pokud jazyk programu, který ladíte, obsahuje jeden z těchto typů prvků před počátečním vstupním bodem, je tento kód spuštěn a událost vstupního bodu je odeslána při dosažení vstupního bodu uživatele, jako je například **Main** nebo `WinMain` .

## <a name="see-also"></a>Viz také
- [Povolení ladění programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)

---
title: Povolení programu k debuggedu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17c6218cd0b25c0cf0134351fd5efd7490b6a1f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738890"
---
# <a name="enable-a-program-to-be-debugged"></a>Povolení odlažení programu
Před ladění motoru (DE) můžete ladit program, musíte nejprve spustit DE nebo jej připojit k existujícímu programu.

## <a name="in-this-section"></a>V tomto oddílu
 [Získání portu](../../extensibility/debugger/getting-a-port.md) Popisuje, jak získat port jako první krok k povolení programu ladit.

 [Registrace programu](../../extensibility/debugger/registering-the-program.md) Vysvětluje další krok v povolení programu ladit: registrace s portem. Po registraci může být program laděn buď procesem připojování nebo ladění just-in-time (JIT).

 [Připojení k programu](../../extensibility/debugger/attaching-to-the-program.md) Vysvětluje další krok: připojení ladicího programu k programu.

 [Připojení založené na spuštění](../../extensibility/debugger/launch-based-attachment.md) Popisuje přílohu programu založenou na spuštění, která je automaticky při spuštění pomocí nástroje SDM.

 [Odeslat požadované události](../../extensibility/debugger/sending-the-required-events.md) Provede vás požadované události při vytváření ladicí modul (DE) a připojení k programu.

## <a name="related-sections"></a>Související oddíly
 [Vytvoření vlastního ladicího modulu](../../extensibility/debugger/creating-a-custom-debug-engine.md) Definuje ladicí modul (DE) a popisuje služby implementované prostřednictvím rozhraní DE a jak mohou způsobit přechod ladicího programu mezi různými provozními režimy.

---
title: Připojení po spuštění | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a4ce0a7465891035b43bbb8f6f22f0c064d104c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739280"
---
# <a name="attach-after-a-launch"></a>Připojit po spuštění
Po spuštění programu je relace ladění připravena k připojení ladicího modulu (DE) k uvedenému programu.

## <a name="design-decisions"></a>Rozhodnutí o návrhu
 Vzhledem k tomu, že komunikace je jednodušší v rámci sdíleného adresního prostoru, musíte si vybrat mezi dvěma návrhovými přístupy: nastavením komunikace mezi ladicí relací a DE. Nebo nastavte komunikaci mezi DE a programem. Vyberte si mezi následujícími možnostmi:

- Pokud má větší smysl nastavit komunikaci mezi ladicí relace a DE, relace ladění co-vytvoří DE a požádá DE připojit k programu. Tento návrh ponechá ladicí relaci a DE společně v jednom adresním prostoru a prostředí za běhu a program společně v jiném.

- Pokud má větší smysl nastavit komunikaci mezi DE a programem, prostředí za běhu spoluvytvoří DE. Tento návrh ponechá SDM v jednom adresním prostoru a DE, run-time prostředí a program společně v jiném. Tento návrh je typický pro DE, který je implementován s interpretem pro spuštění skriptovaných jazyků.

    > [!NOTE]
    > Jak DE připojí k programu je závislá na implementaci. Komunikace mezi DE a programem je také závislá na implementaci.

## <a name="implementation"></a>Implementace
 Programově, když správce ladění relace (SDM) nejprve obdrží objekt [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) který představuje program, který má být spuštěn, volá metodu [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) a předá mu objekt [IDebugCallbackback2,](../../extensibility/debugger/reference/idebugeventcallback2.md) který se později používá k předání ladicích událostí zpět do sdm. Metoda `IDebugProgram2::Attach` pak volá [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metoda. Další informace o tom, jak modul `IDebugProgram2` SDM přijímá rozhraní, naleznete v [tématu Upozornění na port](../../extensibility/debugger/notifying-the-port.md).

 Pokud de potřebuje spustit ve stejném adresním prostoru jako program, který ladíte: protože DE je obvykle součástí interpretu, který je spuštěn skript, `IDebugProgramNodeAttach2::OnAttach` metoda vrátí `S_FALSE`. Vrácení `S_FALSE` označuje, že dokončil proces připojení.

 Pokud však DE spustí v `IDebugProgramNodeAttach2::OnAttach` adresním prostoru SDM: `S_OK`metoda vrátí , nebo [Rozhraní IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) není implementována vůbec na [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) objekt přidružený k programu, který ladíte. V tomto případě [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) metoda je nakonec volána k dokončení operace připojit.

 V druhém případě musíte volat [Metodu GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) `IDebugProgram2` na objekt, `IDebugEngine2::Attach` který byl `GUID` předán metodě, uložit `GUID` objekt `IDebugProgram2::GetProgramId` v místním programu a vrátit to, když je metoda následně volána na tento objekt. Používá `GUID` se k identifikaci programu jedinečně napříč různými součástmi ladění.

 V případě `IDebugProgramNodeAttach2::OnAttach` vrácené `S_FALSE`metody je `GUID` této metodě předáno `IDebugProgramNodeAttach2::OnAttach` použití pro program a je `GUID` to metoda, která nastaví objekt místního programu.

 De je nyní připojen k programu a je připraven k odeslání všech událostí při spuštění.

## <a name="see-also"></a>Viz také
- [Připojení přímo k programu](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [Upozornění na port](../../extensibility/debugger/notifying-the-port.md)
- [Ladění úkolů](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [Připojit](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Připojit](../../extensibility/debugger/reference/idebugengine2-attach.md)

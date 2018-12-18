---
title: Připojení po spuštění | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b767ef1aeed691255a62a9cb5c1e264034acf24e
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152907"
---
# <a name="attach-after-a-launch"></a>Připojit po spuštění
Po spuštění programu, relace ladění je připraven k připojení ladicího stroje (DE) do uvedeného programu.  
  
## <a name="design-decisions"></a>Rozhodnutí o návrhu  
 Protože komunikace je snazší v rámci sdílené adresní prostor, musíte zvolit mezi dva přístupy návrhu: nastavit komunikaci mezi ladicí relaci a DE. Nebo můžete nastavit komunikaci mezi DE a program. Zvolte z následujících možností:  
  
-   Pokud to dává větší smysl nastavení komunikace mezi ladicí relaci a DE, relace ladění společně vytvoří DE a dotaz, DE se připojit k programu. Tento návrh ponechá ladicí relaci a DE společně v jeden adresní prostor a běhového prostředí a program společně v jiném.  
  
-   Pokud to dává větší smysl nastavení komunikace mezi DE a program, vytvoří prostředí run-time společně DE. Tento návrh opustí SDM v jeden adresní prostor DE, běhové prostředí a program společně v jiném. Tento návrh je typický pro Zavedenými, které je implementováno s interpretu pro spuštění skriptovací jazyky.  
  
    > [!NOTE]
    >  Jak DE připojí k programu je závislý na implementaci. Komunikace mezi DE a program je také závislý na implementaci.  
  
## <a name="implementation"></a>Implementace  
 Prostřednictvím kódu programu, když správce ladění relace (SDM) nejprve obdrží [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) objektu, který představuje program spustit, volá [připojit](../../extensibility/debugger/reference/idebugprogram2-attach.md) metodu předáním [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) objektu, který je pozdější sloužící k předávání výjimky ladění zpět do SDM. `IDebugProgram2::Attach` Pak zavolá metodu [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metody. Další informace o způsobu SDM přijímá `IDebugProgram2` rozhraní najdete v tématu [upozornění portu](../../extensibility/debugger/notifying-the-port.md).  
  
 Pokud vaše DE je potřeba spustit ve stejném adresním prostoru jako program ladění: protože DE je obvykle součástí interpret, který je spuštěný skript, `IDebugProgramNodeAttach2::OnAttach` vrátí metoda `S_FALSE`. `S_FALSE` Vrátit označuje, že dokončení procesu připojování.  
  
 Pokud však DE běží v adresním prostoru SDM: `IDebugProgramNodeAttach2::OnAttach` vrátí metoda `S_OK`, nebo [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) rozhraní není implementováno vůbec na [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) objekt přidružený k programu, kterou ladíte. V takovém případě [připojit](../../extensibility/debugger/reference/idebugengine2-attach.md) nakonec je volána metoda k dokončení operace připojení.  
  
 V druhém případě je nutné volat [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metodu na `IDebugProgram2` objekt, který byl předán `IDebugEngine2::Attach` metody, úložiště `GUID` v místní aplikaci objekt a vraťte se tím `GUID` při `IDebugProgram2::GetProgramId` u tohoto objektu je následně volána metoda. `GUID` Slouží k identifikaci program jednoznačně mezi různými komponentami ladění.  
  
 V případě třídy `IDebugProgramNodeAttach2::OnAttach` metody vracející `S_FALSE`, `GUID` pro program je předán do metody a je `IDebugProgramNodeAttach2::OnAttach` metodu, která nastaví `GUID` na objekt místní program.  
  
 DE je teď připojený k programu a připravena k odeslání události při spuštění.  
  
## <a name="see-also"></a>Viz také:  
 [Připojení přímo k programu](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Upozornění portu](../../extensibility/debugger/notifying-the-port.md)   
 [Ladění úloh](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Připojení](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
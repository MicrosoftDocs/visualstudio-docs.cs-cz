---
title: Připojení po spuštění | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 416c05a7592d9f036a76a5d96537b4be917a0651
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774702"
---
# <a name="attaching-after-a-launch"></a>Připojení po spuštění
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Poté, co byl spuštěn program, relace ladění je připraven k připojit ladicí stroj (DE) do uvedeného programu.  
  
## <a name="design-decisions"></a>Rozhodnutí o návrhu  
 Protože komunikace je snazší v rámci sdílené adresní prostor, musíte se rozhodnout, jestli je vhodnější k umožnění komunikace mezi ladicí relaci a DE nebo mezi DE a program. Zvolte z následujících možností:  
  
-   Pokud to dává větší smysl pro usnadnění komunikace mezi ladicí relaci a DE, relace ladění společně vytvoří DE a požádá DE se připojit k programu. To opustí ladicí relaci a DE společně v jeden adresní prostor a běhového prostředí a program společně v jiném.  
  
-   Pokud to dává větší smysl pro usnadnění komunikace mezi DE a program, běhové prostředí společně vytvoří DE. Kvůli tomu SDM v jeden adresní prostor a DE, běhové prostředí a program v jiném společně. Toto je typická Zavedenými, které je implementováno s interpretu pro spuštění skriptovací jazyky.  
  
    > [!NOTE]
    >  Jak DE připojí k programu je závislý na implementaci. Komunikace mezi DE a program je také závislý na implementaci.  
  
## <a name="implementation"></a>Implementace  
 Prostřednictvím kódu programu, když správce ladění relace (SDM) nejprve obdrží [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) objektu, který představuje program spustit, volá [připojit](../../extensibility/debugger/reference/idebugprogram2-attach.md) metodu předáním [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) objektu, který je pozdější sloužící k předávání výjimky ladění zpět do SDM. `IDebugProgram2::Attach` Pak zavolá metodu [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metody. Další informace o způsobu SDM přijímá `IDebugProgram2` rozhraní najdete v tématu [upozornění portu](../../extensibility/debugger/notifying-the-port.md).  
  
 Pokud vaše DE je potřeba spustit ve stejném adresním prostoru jako laděného programu, obvykle vzhledem k tomu, že je DE je součástí interpretu spuštění skriptu, `IDebugProgramNodeAttach2::OnAttach` vrátí metoda `S_FALSE`, označující, že dokončení procesu připojování.  
  
 Pokud na druhé straně DE běží v adresním prostoru SDM, `IDebugProgramNodeAttach2::OnAttach` metoda vrátí hodnotu `S_OK` nebo [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) rozhraní není implementováno vůbec na [IDebugProgramNode2 ](../../extensibility/debugger/reference/idebugprogramnode2.md) objekt přidružený k laděnému programu. V takovém případě [připojit](../../extensibility/debugger/reference/idebugengine2-attach.md) nakonec je volána metoda k dokončení operace připojení.  
  
 V druhém případě je nutné volat [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metodu na `IDebugProgram2` objekt, který byl předán `IDebugEngine2::Attach` metody, úložiště `GUID` v místní aplikaci objekt a vraťte se tím `GUID` při `IDebugProgram2::GetProgramId` u tohoto objektu je následně volána metoda. `GUID` Slouží k identifikaci program jednoznačně mezi různými komponentami ladění.  
  
 Všimněte si, že v případě třídy `IDebugProgramNodeAttach2::OnAttach` metody vracející `S_FALSE`, `GUID` pro program je předán do metody a je `IDebugProgramNodeAttach2::OnAttach` metodu, která nastaví `GUID` na objekt místní program.  
  
 DE je teď připojený k programu a připravena k odeslání události při spuštění.  
  
## <a name="see-also"></a>Viz také  
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


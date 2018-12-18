---
title: Připojení k programu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c87aa879009ef0cd68a83d8ad7affdf0be58f796
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903644"
---
# <a name="attach-to-the-program"></a>Připojit k programu
Po registraci svých programů s příslušný port je nutné připojit ladicí program k program, který chcete ladit.  
  
## <a name="choose-how-to-attach"></a>Zvolte, jak připojit  
 Existují tři způsoby, ve kterých pokusí připojit k laděnému programu Správce ladění relace (SDM). 
  
1. Pro programy, které se spustí modul ladění [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) získá SDM – metoda (Typická interpretovaný jazyků, například), [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) rozhraní z [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) objekt přidružený k přímého připojení k programu. Pokud SDM můžete získat `IDebugProgramNodeAttach2` rozhraní, SDM pak zavolá [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metody. `IDebugProgramNodeAttach2::OnAttach` Vrátí metoda `S_OK` označíte nepřipojili k programu a další pokusy lze připojit k programu.  
  
2. Pokud SDM můžete získat [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) rozhraní z programu připojovaný ke SDM volání [připojit](../../extensibility/debugger/reference/idebugprogramex2-attach.md) metody. Tento přístup je typické pro programy, které byly spuštěny vzdáleně dodavatele portu.  
  
3. Pokud program nelze připojit prostřednictvím `IDebugProgramNodeAttach2::OnAttach` nebo `IDebugProgramEx2::Attach` metody SDM načte ladicího stroje (pokud ještě není načtena) pomocí volání `CoCreateInstance` funkce a pak zavolá [připojit](../../extensibility/debugger/reference/idebugengine2-attach.md) metody. Tento přístup je typické pro programy spustí místně dodavatele portu.  
  
    Je také možné pro dodavatele port. Tento vlastní port pro volání `IDebugEngine2::Attach` metoda implementace dodavatele port. Tento vlastní port `IDebugProgramEx2::Attach` metody. Obvykle v tomto případě dodavatele port. Tento vlastní port spustí modul ladění na vzdáleném počítači.  
  
   Přílohy se dosáhne, když správce ladění relace (SDM) volá [připojit](../../extensibility/debugger/reference/idebugengine2-attach.md) metody.  
  
   Pokud spuštění vašeho DE ve stejném procesu jako aplikace k ladění, pak musíte implementovat tyto metody [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):  
  
- [Gethostname –](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
  Po `IDebugEngine2::Attach` metoda je volána, postupujte podle těchto kroků ve vaší implementaci `IDebugEngine2::Attach` metody:  
  
1.  Odeslání [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) objekt SDM události. Další informace najdete v tématu [odesílání událostí](../../extensibility/debugger/sending-events.md).  
  
2.  Volání [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metodu [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) objekt, který byl předán `IDebugEngine2::Attach` metoda.  
  
     Tím se vrátí `GUID` , který se používá k identifikaci program. `GUID` Musí být uložen v objektu, že představuje místní program určený k DE, a to je vrácena, pokud `IDebugProgram2::GetProgramId` metoda je volána na `IDebugProgram2` rozhraní.  
  
    > [!NOTE]
    >  Pokud se rozhodnete implementovat `IDebugProgramNodeAttach2` rozhraní programu `GUID` je předán `IDebugProgramNodeAttach2::OnAttach` metoda. To `GUID` se používá v programu `GUID` vrácených `IDebugProgram2::GetProgramId` metody.  
  
3.  Odeslání [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) události objektu oznámit SDM, místní `IDebugProgram2` byl vytvořen objekt představující program DE. Podrobnosti najdete v tématu [odesílání událostí](../../extensibility/debugger/sending-events.md).  
  
    > [!NOTE]
    >  To není stejné `IDebugProgram2` objekt, který byl předán `IDebugEngine2::Attach` metody. Dříve předaný `IDebugProgram2` objekt rozezná pouze port a je samostatný objekt.  
  
## <a name="see-also"></a>Viz také:  
 [Příloha založená na spuštění](../../extensibility/debugger/launch-based-attachment.md)   
 [Odesílání událostí](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Připojení](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
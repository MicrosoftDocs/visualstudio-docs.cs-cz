---
title: Připojení po spuštění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 693cf6d746f51862415f2f30e46d48a998047f14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64835345"
---
# <a name="attaching-after-a-launch"></a>Připojení po spuštění
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Po spuštění programu je relace ladění připravena připojit ladicí stroj (DE) k uvedenému programu.  
  
## <a name="design-decisions"></a>Rozhodnutí o návrhu  
 Vzhledem k tomu, že komunikace je snazší v rámci sdíleného adresního prostoru, je nutné se rozhodnout, zda je vhodnější, aby bylo možné zjednodušit komunikaci mezi ladicí relací a DE nebo mezi programem DE a. Vyberte si z těchto možností:  
  
- Pokud je smysluplnější zjednodušit komunikaci mezi ladicí relací a DE, pak relace ladění společně vytvoří příkaz DE a požádá o připojení k programu. Tím se relace ladění a odpojí v jednom adresním prostoru a prostředí modulu runtime a program dohromady v jiném.  
  
- Pokud je smysluplnější zjednodušit komunikaci mezi DE a programem, pak prostředí za běhu společně vytvoří rutinu DE. To znamená, že se SDM bude nabývat v jednom adresním prostoru a v prostředí DE, běhového prostředí a programu společně v jiném. To je typický z výrazu DE, který je implementován s překladačem pro spouštění skriptovacích jazyků.  
  
    > [!NOTE]
    > Způsob, jakým je příkaz DE připojen k programu, je závislý na implementaci. Komunikace mezi DE a programem je také závislá na implementaci.  
  
## <a name="implementation"></a>Implementace  
 Programově, když správce ladění relace (SDM) nejprve přijme objekt [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , který představuje program, který má být spuštěn, volá metodu [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) a předá jí objekt [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) , který je později použit k předání událostí ladění zpět do SDM. `IDebugProgram2::Attach`Metoda pak zavolá metodu [Attach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . Další informace o tom, jak model SDM obdrží `IDebugProgram2` rozhraní, najdete v tématu [informování portu](../../extensibility/debugger/notifying-the-port.md).  
  
 Pokud DE potřebuje běžet ve stejném adresním prostoru jako program, který je právě laděný, obvykle proto, že je DE součástí překladače, který spouští skript, `IDebugProgramNodeAttach2::OnAttach` vrátí metoda `S_FALSE` , která indikuje, že dokončila proces připojení.  
  
 Pokud je na druhé straně rutina DE spuštěna v adresním prostoru SDM, `IDebugProgramNodeAttach2::OnAttach` Metoda vrátí `S_OK` nebo rozhraní [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) není implementováno vůbec u objektu [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) přidruženého k laděnému programu. V tomto případě je metoda [připojení](../../extensibility/debugger/reference/idebugengine2-attach.md) nakonec volána k dokončení operace připojení.  
  
 V druhém případě je třeba zavolat metodu [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) na `IDebugProgram2` objekt, který byl předán `IDebugEngine2::Attach` metodě, uložit `GUID` do objektu lokálního programu a vrátit tuto hodnotu, `GUID` Pokud `IDebugProgram2::GetProgramId` je metoda následně volána na tomto objektu. `GUID`Slouží k jednoznačné identifikaci programu v různých ladicích součástech.  
  
 Všimněte si, že v případě, že se `IDebugProgramNodeAttach2::OnAttach` vrátí metoda `S_FALSE` , která `GUID` má být použita pro program, je předána této metodě a jedná se o `IDebugProgramNodeAttach2::OnAttach` metodu, která nastaví `GUID` objekt místní program.  
  
 DE je nyní připojen k programu a je připraven k odeslání jakékoli události po spuštění.  
  
## <a name="see-also"></a>Viz také  
 [Připojení přímo k programu](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Oznamování portu](../../extensibility/debugger/notifying-the-port.md)   
 [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Pojovat](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Připojit](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Připojit](../../extensibility/debugger/reference/idebugengine2-attach.md)

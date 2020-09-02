---
title: Připojení po spuštění | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739280"
---
# <a name="attach-after-a-launch"></a>Připojit po spuštění
Po spuštění programu je relace ladění připravena připojit ladicí modul (DE) k uvedenému programu.

## <a name="design-decisions"></a>Rozhodnutí o návrhu
 Vzhledem k tomu, že komunikace je snazší v rámci sdíleného adresního prostoru, je nutné zvolit mezi dvěma přístupy k návrhu: nastavte komunikaci mezi ladicí relací a DE. Nebo nastavte komunikaci mezi DE a programem. Vyberte si z těchto možností:

- Pokud je vhodnější nastavit komunikaci mezi ladicí relací a DE, relace ladění společně vytvoří příkaz DE a požádá o připojení k programu. Tento návrh opustí relaci ladění a odpojí se v jednom adresním prostoru a prostředí run-time a program společně v jiném.

- Pokud je vhodnější nastavit komunikaci mezi DE a programem, prostředí za běhu společně vytvoří rutinu DE. Tento návrh opouští model SDM v jednom adresním prostoru a prostředí run-time a program dohromady v jiném. Tento návrh je typický z DE, který je implementován s překladačem pro spouštění skriptovacích jazyků.

    > [!NOTE]
    > Způsob, jakým je příkaz DE připojen k programu, je závislý na implementaci. Komunikace mezi DE a programem je také závislá na implementaci.

## <a name="implementation"></a>Implementace
 Programově, když správce ladění relace (SDM) nejprve přijme objekt [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , který představuje program, který má být spuštěn, volá metodu [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) a předá jí objekt [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) , který je později použit k předání událostí ladění zpět do SDM. `IDebugProgram2::Attach`Metoda pak zavolá metodu [Attach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . Další informace o tom, jak model SDM obdrží `IDebugProgram2` rozhraní, najdete v tématu [informování portu](../../extensibility/debugger/notifying-the-port.md).

 Pokud DE potřebuje běžet ve stejném adresním prostoru jako program, který ladíte: vzhledem k tomu, že DE je obvykle součástí překladače, který spouští skript, `IDebugProgramNodeAttach2::OnAttach` Metoda vrátí `S_FALSE` . Tato `S_FALSE` operace vrátí, že dokončila proces připojení.

 Pokud se ale DE spustí v adresním prostoru SDM: `IDebugProgramNodeAttach2::OnAttach` Metoda `S_OK` se vrátí nebo není rozhraní [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) implementované na objekt [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) přidružený k programu, který ladíte. V tomto případě je metoda [připojení](../../extensibility/debugger/reference/idebugengine2-attach.md) nakonec volána k dokončení operace připojení.

 V druhém případě je třeba zavolat metodu [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) na `IDebugProgram2` objekt, který byl předán `IDebugEngine2::Attach` metodě, uložit `GUID` do objektu lokálního programu a vrátit tuto hodnotu, `GUID` Pokud `IDebugProgram2::GetProgramId` je metoda následně volána na tomto objektu. `GUID`Slouží k jednoznačné identifikaci programu v různých ladicích součástech.

 V případě `IDebugProgramNodeAttach2::OnAttach` , že metoda vrací `S_FALSE` hodnotu, `GUID` která je použita pro program, je předána této metodě a jedná se o `IDebugProgramNodeAttach2::OnAttach` metodu, která nastaví `GUID` objekt místní program.

 DE je nyní připojen k programu a je připraven k odeslání jakékoli události po spuštění.

## <a name="see-also"></a>Viz také
- [Připojení přímo k programu](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [Oznamování portu](../../extensibility/debugger/notifying-the-port.md)
- [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [Připojit](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Připojit](../../extensibility/debugger/reference/idebugengine2-attach.md)

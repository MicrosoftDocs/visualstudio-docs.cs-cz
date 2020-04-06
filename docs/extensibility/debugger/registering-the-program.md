---
title: Registrace programu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b68fa67f784d155288482ad724b632ed5ba5fa41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713161"
---
# <a name="register-the-program"></a>Registrace programu
Po ladění motoru získal port, reprezentované [rozhraní IDebugPort2,](../../extensibility/debugger/reference/idebugport2.md) dalším krokem v povolení programu ladit je zaregistrovat s portem. Po registraci je program k dispozici pro ladění jedním z následujících způsobů:

- Proces připojení, který umožňuje ladicí program získat úplné ladění řízení spuštěné aplikace.

- Just-in-time (JIT) ladění, které umožňuje ladění po faktu programu, který běží nezávisle na ladicím programu. Když architektura za běhu zachytí chybu, ladicí program je upozorněn před operační systém nebo prostředí runtime uvolní paměť a prostředky chybující program.

## <a name="registering-procedure"></a>Postup registrace

### <a name="to-register-your-program"></a>Registrace programu

1. Volání metody [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) implementované portem.

     `IDebugPortNotify2::AddProgramNode`vyžaduje ukazatel na rozhraní [IDebugProgramNode2.](../../extensibility/debugger/reference/idebugprogramnode2.md)

     Obvykle při načtení programu operačního systému nebo prostředí run-time vytvoří uzel programu. Pokud ladicí modul (DE) je vyzván k načtení programu, DE vytvoří a zaregistruje uzel programu.

     Následující příklad ukazuje ladicí modul, který spouští program a registruje jej pomocí portu.

    > [!NOTE]
    > Tato ukázka kódu není jediný způsob, jak spustit a obnovit proces; tento kód je především příkladem registrace programu s portem.

    ```cpp
    // This is an IDebugEngineLaunch2 method.
    HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,
                                          IDebugPort2 *pPort,
                                          /* omitted parameters */,
                                          IDebugProcess2**ppDebugProcess)
    {
        // do stuff here to set up for a launch (such as handling the other parameters)
        ...

        // Now get the IPortNotify2 interface so we can register a program node
        // in CDebugEngine::ResumeProcess.
        CComPtr<IDebugDefaultPort2> spDefaultPort;
        HRESULT hr = pPort->QueryInterface(&spDefaultPort);
        if (SUCCEEDED(hr))
        {
            CComPtr<IDebugPortNotify2> spPortNotify;
            hr = spDefaultPort->GetPortNotify(&spPortNotify);
            if (SUCCEEDED(hr))
            {
                // Remember the port notify so we can use it in ResumeProcess.
                m_spPortNotify = spPortNotify;

                // Now launch the process in a suspended state and return the
                // IDebugProcess2 interface
                CComPtr<IDebugPortEx2> spPortEx;
                hr = pPort->QueryInterface(&spPortEx);
                if (SUCCEEDED(hr))
                {
                    // pass on the parameters we were given (omitted here)
                    hr = spPortEx->LaunchSuspended(/* omitted parameters */,ppDebugProcess)
                }
            }
        }
        return(hr);
    }

    HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)
    {
        // Make a program node for this process
        HRESULT hr;
        CComPtr<IDebugProgramNode2> spProgramNode;
        hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);
        if (SUCCEEDED(hr))
        {
            hr = m_spPortNotify->AddProgramNode(spProgramNode);
            if (SUCCEEDED(hr))
            {
                // resume execution of the process using the port given to us earlier.
               // (Querying for the IDebugPortEx2 interface is valid here since
               // that's how we got the IDebugPortNotify2 interface in the first place.)
                CComPtr<IDebugPortEx2> spPortEx;
                hr = m_spPortNotify->QueryInterface(&spPortEx);
                if (SUCCEEDED(hr))
                {
                    hr  = spPortEx->ResumeProcess(pDebugProcess);
                }
            }
        }
        return(hr);
    }

    ```

## <a name="see-also"></a>Viz také
- [Získání portu](../../extensibility/debugger/getting-a-port.md)
- [Povolení odlazení programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)

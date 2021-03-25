---
title: Registrace programu | Microsoft Docs
description: Přečtěte si, jak se program, který se má ladit, zaregistruje na portu poté, co ladicí modul získá port.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4fda27bd0572713e16311e6feae8ff74870cb006
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070632"
---
# <a name="register-the-program"></a>Zaregistrovat program
Poté, co ladicí stroj získá port, který je reprezentován rozhraním [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , je dalším krokem k tomu, abyste mohli ladit program, zaregistrovat ho v portu. Po registraci je program k dispozici pro ladění jedním z následujících způsobů:

- Proces připojení, který umožňuje ladicímu programu získat kompletní řízení ladění spuštěné aplikace.

- Ladění JIT (just-in-time), které umožňuje ladění programu po určité skutečnosti, který běží nezávisle na ladicím programu. Když architektura za běhu zachytí chybu, ladicí program je upozorněn před tím, než operační systém nebo běhové prostředí uvolní paměť a prostředky pro chybový program.

## <a name="registering-procedure"></a>Postup registrace

### <a name="to-register-your-program"></a>Registrace programu

1. Zavolejte metodu [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) implementovanou portem.

     `IDebugPortNotify2::AddProgramNode` vyžaduje ukazatel na rozhraní [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) .

     V případě, že operační systém nebo prostředí run-time načte program, vytvoří uzel programu. Pokud je k načtení programu požádán ladicí modul (DE), nástroj DE vytvoří a zaregistruje uzel programu.

     Následující příklad ukazuje modul ladění, který spouští program a registruje ho pomocí portu.

    > [!NOTE]
    > Tato ukázka kódu není jediným způsobem, jak spustit a obnovit proces; Tento kód je hlavně příkladem registrace programu s portem.

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
- [Povolení ladění programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)

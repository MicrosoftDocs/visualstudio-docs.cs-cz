---
title: Získání port | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7bf4948e7cb2590136774eab76fbafec91dbfa40
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738631"
---
# <a name="get-a-port"></a>Získání portu
Port představuje připojení k počítači, na kterém jsou spuštěny procesy. Tento počítač může být místní počítač nebo vzdálený počítač (který by mohl být spuštěn operační systém, který není založen na systému Windows; další informace naleznete v [tématu Porty).](../../extensibility/debugger/ports.md)

Port je reprezentován rozhraním [IDebugPort2.](../../extensibility/debugger/reference/idebugport2.md) Používá se k získání informací o procesech spuštěných v počítači, ke které je port připojen.

Ladicí modul potřebuje přístup k portu, aby mohl zaregistrovat uzly programů s portem a uspokojit požadavky na informace o procesu. Například pokud ladicí modul implementuje rozhraní [IDebugProgramProvider2,](../../extensibility/debugger/reference/idebugprogramprovider2.md) implementace metody [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) může požádat port o vrácení nezbytných informací o procesu.

Visual Studio dodává potřebný port do ladicího modulu a získá tento port od dodavatele portu. Pokud je připojen program (buď z v rámci ladicího programu nebo z důvodu byla vyvolána výjimka, která aktivuje dialogové okno Just-in-Time [JIT], uživatel je uveden výběr přenosu (jiný název pro dodavatele portu) k použití. V opačném případě, pokud uživatel spustí program z ladicího programu, systém projektu určuje dodavatele portu, který má být používán. V obou těchto případě Visual Studio instancee dodavatele portu, reprezentované [rozhraní IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) a požádá o nový port voláním [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) s [rozhraním IDebugPortRequest2.](../../extensibility/debugger/reference/idebugportrequest2.md) Tento port je pak předán ladicí mu motoru v jednom nebo druhém formuláři.

## <a name="example"></a>Příklad
Tento fragment kódu ukazuje, jak použít port dodaný [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) k registraci uzlu programu v [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Parametry, které přímo nesouvisejí s tímto konceptem, byly pro přehlednost vynechány.

> [!NOTE]
> Tento příklad používá port ke spuštění a obnovení procesu a předpokládá, že rozhraní [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) je implementováno na portu. To není v žádném případě jediný způsob, jak provádět tyto úkoly, a je možné, že port nemusí být ani zapojeny jiné než mít programu [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) uvedeny na to.

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
                hr = spPortEx->ResumeProcess(pDebugProcess);
            }
        }
    }
    return(hr);
}
```

## <a name="see-also"></a>Viz také
- [Registrace programu](../../extensibility/debugger/registering-the-program.md)
- [Povolení odlazení programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [Dodavatelé přístavů](../../extensibility/debugger/port-suppliers.md)
- [Porty](../../extensibility/debugger/ports.md)

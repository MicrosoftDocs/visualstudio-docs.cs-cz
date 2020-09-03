---
title: Načítá se port | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738631"
---
# <a name="get-a-port"></a>Získat port
Port představuje připojení k počítači, na kterém běží procesy. Tento počítač může být místní počítač nebo vzdálený počítač (což může být spuštěný operační systém, který není založený na Windows). Další informace najdete v tématu [porty](../../extensibility/debugger/ports.md) .

Port je reprezentován rozhraním [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) . Slouží k získání informací o procesech spuštěných na počítači, ke kterému je připojen port.

Ladicí stroj potřebuje přístup k portu, aby mohla registrovat uzly programu s portem a splňovat požadavky na informace o procesu. Například pokud ladicí stroj implementuje rozhraní [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) , implementace metody [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) by mohla požádat o potřebné informace o procesu, aby mohl být vrácen.

Visual Studio poskytuje potřebný port pro ladicí stroj a získá tento port od dodavatele portu. Pokud je program připojen k (buď z ladicího programu, nebo z důvodu vyvolání výjimky, která spustí dialogové okno just-in-time [JIT]), uživateli je dána volba přenosu (další název dodavatele portu), který se má použít. V opačném případě, pokud uživatel spustí program v rámci ladicího programu, projektový systém určí dodavatele portu, který se má použít. V obou událostech Visual Studio vytvoří instanci dodavatele portu reprezentovanou rozhraním [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) a požádá o nový port voláním [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) s rozhraním [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) . Tento port je pak předán do ladicího modulu v jednom nebo jiném formuláři.

## <a name="example"></a>Příklad
Tento fragment kódu ukazuje, jak použít port dodaný do [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) k registraci uzlu programu v [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Parametry, které přímo nesouvisejí s tímto konceptem, byly pro přehlednost vynechány.

> [!NOTE]
> V tomto příkladu se používá port ke spuštění a obnovení procesu a předpokládá, že je na portu implementováno rozhraní [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) . To znamená, že jediný způsob, jak tyto úlohy provádět, a je možné, že port není ani v případě, že by k tomu měl [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) programu.

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
- [Povolení ladění programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [Dodavatelé portů](../../extensibility/debugger/port-suppliers.md)
- [Porty](../../extensibility/debugger/ports.md)

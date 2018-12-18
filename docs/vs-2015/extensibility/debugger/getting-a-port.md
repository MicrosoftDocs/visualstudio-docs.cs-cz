---
title: Získání portu | Dokumentace Microsoftu
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
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 660ead58af40f85b4da4d68d7172866f5fe1fd0c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789899"
---
# <a name="getting-a-port"></a>Získání portu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Port představuje připojení k počítači, na kterém běží procesů. Tento počítač může být v místním počítači nebo vzdáleného počítače (který může potenciálně být bez Windows-based operační systém, najdete v článku [porty](../../extensibility/debugger/ports.md) Další informace).  
  
 Port je reprezentována [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) rozhraní. Používá se k získání informací o procesy spuštěné na počítači, který port, který je připojen k.  
  
 Ladicí stroj potřebuje přístup k portu, pokud chcete zaregistrovat program uzly s portem a požadavky na informace o procesu. Například, pokud ladicí stroj implementuje [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) implementace pro rozhraní [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) metoda může požádat o nezbytný proces port informace se mají vrátit.  
  
 Visual Studio poskytuje nezbytné port ladicího stroje a získá tento port od jiného dodavatele portu. Pokud program je připojen k (buď v rámci ladicího programu nebo z důvodu výjimky byla vyvolána, která se aktivuje dialogové okno Just-in-Time [JIT]), uživatel dostane volba přenosu (jiný název pro dodavatele portu) používat. V opačném případě, pokud uživatel spustí program z v rámci ladicího programu, systém projektu určuje dodavatele portu používat. V obou případech sady Visual Studio vytvoří instanci dodavatele portu, reprezentovaný [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) rozhraní a požádá o nový port voláním [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) s [ IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) rozhraní. Tento port je pak předán ladicí stroj v podobě jednoho nebo druhého.  
  
## <a name="example"></a>Příklad  
 Tento fragment kódu ukazuje, jak používat port zadaný pro [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) k registraci uzlu aplikace v [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Pro přehlednost byly vynechány parametry nemají přímou souvislost tento koncept.  
  
> [!NOTE]
>  Tento příklad používá port, který můžete spustit a pokračovat v procesu a předpokládá, že [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) rozhraní je implementováno na portu. Toto je v žádném smyslu jediný způsob, jak provádět tyto úlohy a je možné, že port nemusí i možné zahrnutí jiné než a program [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) k němu.  
  
```cpp#  
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
 [Registrace programu](../../extensibility/debugger/registering-the-program.md)   
 [Povolení ladění programu](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [Dodavatelé portů](../../extensibility/debugger/port-suppliers.md)   
 [Porty](../../extensibility/debugger/ports.md)


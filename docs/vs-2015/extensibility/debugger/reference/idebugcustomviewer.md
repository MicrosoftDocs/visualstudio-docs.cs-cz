---
title: IDebugCustomViewer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f94fe0301777a615fa6dc567311c493ff55a90a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196302"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní umožňuje vyhodnocovacímu filtru výrazů (EE) zobrazit hodnotu vlastnosti v jakémkoli formátu.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 EE implementuje toto rozhraní k zobrazení hodnoty vlastnosti ve vlastním formátu.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Volání funkce modelu COM `CoCreateInstance` vytvoří instanci tohoto rozhraní. `CLSID`Předaná `CoCreateInstance` aplikace je získána z registru. Volání [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Získá umístění v registru. Podrobnosti a příklad najdete v části poznámky.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 Toto rozhraní implementuje následující metodu:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Bez ohledu na to, co je potřeba k zobrazení dané hodnoty.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní se používá v případě, že hodnota vlastnosti nemůže být zobrazena běžným způsobem – například s datovou tabulkou nebo jiným komplexním typem vlastnosti. Vlastní prohlížeč, reprezentovaný `IDebugCustomViewer` rozhraním, se liší od Vizualizér typu, což je externí program pro zobrazení dat určitého typu bez ohledu na EE. EE implementuje vlastní prohlížeč, který je specifický pro tyto EE. Uživatel vybere typ vizualizér, který se má použít, to je Vizualizér typu nebo vlastní prohlížeč. Podrobnosti o tomto procesu najdete v tématu [vizualizace a zobrazení dat](../../../extensibility/debugger/visualizing-and-viewing-data.md) .  
  
 Vlastní prohlížeč je zaregistrován stejným způsobem jako EE a proto vyžaduje identifikátor GUID jazyka a identifikátor GUID dodavatele. Přesnou metriku (nebo název položky registru) je známo pouze pro EE. Tato metrika se vrátí ve struktuře [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) , která se zase vrátí voláním metody [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). Hodnota uložená v metrikě je ta `CLSID` , která je předána funkci modelu COM `CoCreateInstance` (viz příklad).  
  
 K registraci vlastního prohlížeče lze použít [pomocníka sady SDK pro funkci ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetEEMetric` . `Debugging SDK Helpers`Konkrétní klíče registru, které vlastní prohlížeč potřebuje, najdete v části Registry hodnotitelé výrazů v tématu. Všimněte si, že vlastní prohlížeč potřebuje jenom jednu metriku (která je definovaná implementátorem EE), zatímco vyhodnocovací filtr výrazů vyžaduje několik předdefinovaných metrik.  
  
 V normálním případě vlastní prohlížeč poskytuje zobrazení dat jen pro čtení, protože rozhraní [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) dodávané [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) nemá žádné metody pro změnu hodnoty vlastnosti s výjimkou řetězce. Aby bylo možné podporovat změnu libovolných bloků dat, rozhraní EE implementuje vlastní rozhraní na stejný objekt, který implementuje `IDebugProperty3` rozhraní. Toto vlastní rozhraní potom poskytne metody potřebné ke změně libovolného bloku dat.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak získat první vlastní prohlížeč z vlastnosti, pokud tato vlastnost má nějaké vlastní prohlížeče.  
  
```cpp#  
IDebugCustomViewer *GetFirstCustomViewer(IDebugProperty2 *pProperty)  
{  
    // This string is typically defined globally.  For this example, it  
    // is defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugCustomViewer *pViewer = NULL;  
    if (pProperty != NULL) {  
        CComQIPtr<IDebugProperty3> pProperty3(pProperty);  
        if (pProperty3 != NULL) {  
            HRESULT hr;  
            ULONG viewerCount = 0;  
            hr = pProperty3->GetCustomViewerCount(&viewerCount);  
            if (viewerCount > 0) {  
                ULONG viewersFetched = 0;  
                DEBUG_CUSTOM_VIEWER viewerInfo = { 0 };  
                hr = pProperty3->GetCustomViewerList(0,  
                                                     1,  
                                                     &viewerInfo,  
                                                     &viewersFetched);  
                if (viewersFetched == 1) {  
                    CLSID clsidViewer = { 0 };  
                    CComPtr<IDebugCustomViewer> spCustomViewer;  
                    // Get the viewer's CLSID from the registry.  
                    ::GetEEMetric(viewerInfo.guidLang,  
                                  viewerInfo.guidVendor,  
                                  viewerInfo.bstrMetric,  
                                  &clsidViewer,  
                                  strRegistrationRoot);  
                    if (!IsEqualGUID(clsidViewer,GUID_NULL)) {  
                        // Instantiate the custom viewer.  
                        spCustomViewer.CoCreateInstance(clsidViewer);  
                        if (spCustomViewer != NULL) {  
                            pViewer = spCustomViewer.Detach();  
                        }  
                    }  
                }  
            }  
        }  
    }  
    return(pViewer);  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [Pomocníka sady SDK pro ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)

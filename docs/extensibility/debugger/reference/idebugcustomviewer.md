---
title: IDebugCustomViewer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3fb70365304883abe99a87cfec5e78bbed89f2dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107537"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Toto rozhraní umožňuje (EE) zobrazíte vlastnosti na hodnotu v jakémkoli formát je nezbytné vyhodnocovací filtr výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 EE implementuje toto rozhraní zobrazíte vlastnosti na hodnotu ve vlastním formátu.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Volání do modelu COM na `CoCreateInstance` funkce vytvoří instanci tohoto rozhraní. `CLSID` Předaný `CoCreateInstance` se získávají z registru. Volání [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) získá umístění v registru. V části poznámky pro podrobnosti a také v příkladu.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Toto rozhraní implementuje následující metodu:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Položky DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Nepodporuje, vše, co je nezbytné k zobrazení dané hodnoty.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní se používá při normálním způsobem nelze zobrazit vlastnosti na hodnotu – například s tabulkou dat nebo jiný typ komplexní vlastnost. Vlastní prohlížeč, jako je znázorněn `IDebugCustomViewer` rozhraní, se liší od vizualizéru typ, který je pro zobrazení dat určitého typu bez ohledu EE vnějšímu programu. EE implementuje vlastní prohlížeč, který je specifická pro tuto EE. Uživatel vybere typu vizualizér chcete použít, je-li jej vizualizéru typu nebo vlastní prohlížeč. V tématu [Visualizing a zobrazení Data](../../../extensibility/debugger/visualizing-and-viewing-data.md) podrobnosti o tomto procesu.  
  
 Vlastní prohlížeč je zaregistrován stejným způsobem jako EE a proto vyžaduje jazyk GUID a dodavatele identifikátor GUID. Přesný metrika (nebo název položky registru) je zná pouze EE. Tato metrika je vrácený v [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) strukturu, která zase vrátí volání [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). Hodnota uložená v metrika je `CLSID` předá do modelu COM na `CoCreateInstance` funkce (podívejte se na příklad).  
  
 [SDK pomocníci pro ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) funkce, `SetEEMetric`, je možné zaregistrovat vlastní prohlížeč. Najdete v části "Vyhodnocovače výrazů" registru `Debugging SDK Helpers` pro konkrétní registru klíče, který potřebuje vlastní prohlížeč. Všimněte si, že vlastní prohlížeč potřebuje pouze jedna metrika (který je definovaný EE implementátor), zatímco vyhodnocení výrazu vyžaduje několik předdefinované metriky.  
  
 Za normálních okolností vlastní prohlížeč poskytuje zobrazení jen pro čtení dat, protože [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) rozhraní zadané [položky DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) nemá žádné metody pro změnu hodnotu vlastnosti s výjimkou jako řetězec. Aby bylo možné podporovat změnu libovolný bloků dat, EE implementuje vlastní rozhraní pro stejný objekt, který implementuje `IDebugProperty3` rozhraní. Toto vlastní rozhraní by pak poskytují metody potřeby změnit bloku libovolný data.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak získat z vlastnosti první vlastní prohlížeč, pokud tato vlastnost neobsahuje žádné vlastní prohlížeče.  
  
```cpp  
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
 [Pomocníci SDK pro ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
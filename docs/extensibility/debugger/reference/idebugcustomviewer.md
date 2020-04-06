---
title: IDebugCustomViewer | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c44d2289180ece35725b9258e9d20abeb3a4cac3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732419"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Toto rozhraní umožňuje vyhodnocení výrazu (EE) zobrazit hodnotu vlastnosti v jakémkoli formátu je nezbytné.

## <a name="syntax"></a>Syntaxe

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
EE implementuje toto rozhraní k zobrazení hodnoty vlastnosti ve vlastním formátu.

## <a name="notes-for-callers"></a>Poznámky pro volající
Volání `CoCreateInstance` funkce COM konkretizovat toto rozhraní. Předáno `CLSID` `CoCreateInstance` do je získán z registru. Volání [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) získá umístění v registru. Podrobnosti a příklad najdete v části Poznámky.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
Toto rozhraní implementuje následující metodu:

|Metoda|Popis|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Provádí vše, co je nezbytné k zobrazení dané hodnoty.|

## <a name="remarks"></a>Poznámky
Toto rozhraní se používá v případě, že hodnotu vlastnosti nelze zobrazit běžnými prostředky – například s datovou tabulkou nebo jiným komplexním typem vlastnosti. Vlastní prohlížeč, reprezentované `IDebugCustomViewer` rozhraním, se liší od vizualizéru typu, což je externí program pro zobrazení dat určitého typu bez ohledu na EE. EE implementuje vlastní prohlížeč, který je specifický pro tento EE. Uživatel vybere typ vizualizéru, který má použít, ať už se jedná o vizualizér typu nebo vlastní prohlížeč. Podrobnosti o tomto procesu naleznete v tématu [Vizualizace a zobrazení dat.](../../../extensibility/debugger/visualizing-and-viewing-data.md)

Vlastní prohlížeč je registrován stejným způsobem jako EE, a proto vyžaduje identifikátor GUID jazyka a identifikátor GUID dodavatele. Přesná metrika (nebo název položky registru) je známa pouze EE. Tato metrika je vrácena ve [struktuře DEBUG_CUSTOM_VIEWER,](../../../extensibility/debugger/reference/debug-custom-viewer.md) která je vrácena voláním [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). Hodnota uložená v metrice `CLSID` je, která `CoCreateInstance` je předána funkci COM (viz příklad).

[Pomocné spoje sady SDK](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetEEMetric`pro funkci ladění lze použít k registraci vlastního prohlížeče. Naleznete v části registru Vyhodnocení výrazů `Debugging SDK Helpers` pro konkrétní klíče registru, které vlastní prohlížeč potřebuje. Všimněte si, že vlastní prohlížeč potřebuje pouze jednu metriku (která je definována implementátorem EE) zatímco vyhodnocení výrazu vyžaduje několik předdefinovaných metrik.

Za normálních okolností vlastní prohlížeč poskytuje zobrazení dat jen pro čtení, protože rozhraní [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) dodávané do [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) nemá žádné metody pro změnu hodnoty vlastnosti s výjimkou jako řetězec. Za účelem podpory změny libovolných bloků dat, EE implementuje vlastní rozhraní `IDebugProperty3` na stejný objekt, který implementuje rozhraní. Toto vlastní rozhraní by pak poskytnout metody potřebné ke změně libovolného bloku dat.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg.h

Obor názvů: Microsoft.VisualStudio.Debugger.Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Příklad
Tento příklad ukazuje, jak získat první vlastní prohlížeč z vlastnosti, pokud tato vlastnost má nějaké vlastní prohlížeče.

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
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [Pomocníci sad SDK pro ladění](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)

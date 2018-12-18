---
title: IDebugProperty3::GetCustomViewerList | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty3::GetCustomViewerList
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerList
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 646483fd27f59dab538aee2be888a45114ce44a3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795437"
---
# <a name="idebugproperty3getcustomviewerlist"></a>IDebugProperty3::GetCustomViewerList
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Získá seznam vlastních prohlížečů, které jsou přidružené k této vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```csharp  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celtSkip`  
 [in] Počet prohlížečů mají přeskočit.  
  
 `celtRequested`  
 [in] Počet prohlížeče k načtení (také určuje velikost `rgViewers` pole).  
  
 `rgViewers`  
 [out v] Pole [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) struktury být vyplněna.  
  
 `pceltFetched`  
 [out] Vrátí skutečný počet prohlížeče.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Pro podporu vizualizérů typů, tato metoda předává volání [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) metody. Pokud vyhodnocovací filtr výrazů také podporuje vlastních prohlížečů pro typ této vlastnosti, tuto metodu můžete připojit příslušné vlastních prohlížečů do seznamu.  
  
 Zobrazit [vizualizér typů a vlastní prohlížeč](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) podrobnosti o rozdílech mezi vizualizérů typů a vlastních prohlížečů.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pro tuto metodu implementovat **CProperty** objekt, který zveřejňuje [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) rozhraní.  
  
```cpp#  
STDMETHODIMP CProperty::GetCustomViewerList(ULONG celtSkip, ULONG celtRequested, DEBUG_CUSTOM_VIEWER* prgViewers, ULONG* pceltFetched)  
{  
    if (NULL == prgViewers)  
    {  
        return E_POINTER;  
    }  
  
    if (GetVisualizerService())  
    {  
        return m_pIEEVisualizerService->GetCustomViewerList(celtSkip, celtRequested, prgViewers, pceltFetched);  
    }  
    else  
    {  
        return E_NOTIMPL;  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)   
 [Vizualizér typů a vlastní prohlížeč](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)


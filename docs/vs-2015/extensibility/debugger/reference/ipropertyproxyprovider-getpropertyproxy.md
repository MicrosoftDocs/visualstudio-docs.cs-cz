---
title: 'IPropertyProxyProvider:: GetPropertyProxy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider::GetPropertyProxy
helpviewer_keywords:
- IPropertyProxyProvider::GetPropertyProxy
ms.assetid: 3ebb7515-5bfe-48f4-9b8d-721b8f664eb6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cc505799a0ea7571ccff41057ba9852018ddbb3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199463"
---
# <a name="ipropertyproxyprovidergetpropertyproxy"></a>IPropertyProxyProvider::GetPropertyProxy
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Načte proxy rozhraní vlastnosti pro zadané ID proxy serveru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetPropertyProxy(  
   DWORD                  dwID,  
   IPropertyProxyEESide** proxy  
);  
```  
  
```csharp  
int GetPropertyProxy(  
   uint                     dwID,  
   out IPropertyProxyEESide proxy  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwID`  
 pro ID požadovaného proxy serveru vlastnosti  
  
 `proxy`  
 mimo Vrátí objekt [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) .  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Aby bylo možné podporovat vizualizace externího typu, tato metoda obvykle předává volání metodě [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md) . Podrobnosti o tom, jak se IEEVisualizerService získává, najdete v tématu [vizualizace a zobrazení dat](../../../extensibility/debugger/visualizing-and-viewing-data.md) .  
  
## <a name="see-also"></a>Viz také  
 [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Vizualizace a zobrazení dat](../../../extensibility/debugger/visualizing-and-viewing-data.md)

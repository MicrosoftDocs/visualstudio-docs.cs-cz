---
title: 'IDebugPortPicker:: SetSite | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6cd0b91491be365a4686265bd698717219df0afb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188397"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Nastaví poskytovatele služby.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT SetSite(  
   IServiceProvider * pSP  
);  
```  
  
```csharp  
public int SetSite(  
   IServiceProvider pSP  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pSP`  
 pro Odkaz na rozhraní poskytovatele služeb  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda bude volána před voláním jakékoli jiné metody.  
  
## <a name="see-also"></a>Viz také  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)

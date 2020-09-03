---
title: 'IDebugMethodField:: GetGlobalContainer | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 63912b75435de503dec677b715d1914b419ba07a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162563"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Získá globální kontejner metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetGlobalContainer(  
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetGlobalContainer(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppClass`  
 mimo Vrátí [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) představující modul, ve kterém je tato metoda definována.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Vrácený objekt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) představuje celý modul a je umělým objektem, tedy samotný modul nemá skutečnou třídu, ale může být reprezentován `IDebugClassField` objektem, což umožňuje, aby byly různé prvky modulu vyčísleny a zjištěny.  
  
## <a name="see-also"></a>Viz také  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)

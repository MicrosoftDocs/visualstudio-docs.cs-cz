---
title: 'IDebugEnumField:: GetUnderlyingSymbol | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetUnderlyingSymbol
helpviewer_keywords:
- IDebugEnumField::GetUnderlyingSymbol method
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1841ca2bf9bd5a43ec5a16a515a03769db64ea15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188964"
---
# <a name="idebugenumfieldgetunderlyingsymbol"></a>IDebugEnumField::GetUnderlyingSymbol
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato metoda vrací [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , který představuje název výčtu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetUnderlyingSymbol(  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetUnderlyingSymbol(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppField`  
 mimo Vrátí [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) popisující název tohoto výčtu.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Název výčtu také obsahuje typ výčtu, který je vázán na umístění v paměti pomocí [BIND](../../../extensibility/debugger/reference/idebugbinder-bind.md).  
  
## <a name="see-also"></a>Viz také  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [Zapisovat](../../../extensibility/debugger/reference/idebugbinder-bind.md)

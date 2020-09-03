---
title: 'IDebugPointerField:: GetDereferencedField | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 02197f660189d4caf374fc5927f349fd5fc6b8b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201010"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato metoda vrací typ objektu, na který odkazuje tento objekt ukazatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetDereferencedField(  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetDereferencedField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppField`  
 mimo Vrátí [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) popisující typ cílového objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Pokud například objekt [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) odkazuje na celé číslo, typ [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) vrácený touto metodou popisuje tento typ Integer.  
  
## <a name="see-also"></a>Viz také  
 [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

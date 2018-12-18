---
title: IDebugObject2::GetBackingFieldForProperty | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d788d048fc428825cbc667b18424b32c68ddc5c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49840230"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Získá pole nebo proměnné (pokud existuje), který může být zálohování vlastnost reprezentovaný tímto objektem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppObject`  
 [out] [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) objekt popisující pole zálohování.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí hodnotu S_OK; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) objekt představuje vlastnost třídy spravovaného kódu, to znamená, že metoda get a/nebo nastavení přístupového objektu. Tyto vlastnosti se obecně vyžadují proměnná obsahuje hodnotu manipulovat vlastnost. Tato proměnná je označována jako pole zálohování. Pokud tam není žádné pole zálohování pro objekt, ujistěte se, vrátí hodnotu null: některé volající nemusí věnovat pozornost návratovou hodnotu, ale místo toho bude vypadat zobrazíte, pokud byla vrácena hodnota null v `ppObject`.  
  
## <a name="see-also"></a>Viz také  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
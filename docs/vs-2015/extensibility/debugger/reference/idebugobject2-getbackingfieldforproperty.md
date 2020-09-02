---
title: 'IDebugObject2:: GetBackingFieldForProperty | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5eadbed61638ff1442c4ed7033426e245abf930a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62536383"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Získá pole nebo proměnnou (pokud existuje), která může zálohovat vlastnost reprezentovanou tímto objektem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppObject`  
 mimo Objekt [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) popisující pole zálohování.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Objekt [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) reprezentuje vlastnost třídy spravovaného kódu, to znamená metodu s přístupovým objektem Get nebo set. Tyto vlastnosti obecně vyžadují, aby proměnná obsahovala hodnotu, která je zpracována vlastností. Tato proměnná je označována jako pole pro zálohování. Pokud není k dispozici žádné pole pro daný objekt, je nutné vrátit hodnotu null: někteří volající nemůžou věnovat pozornost návratové hodnotě, ale místo toho budou chtít zjistit, jestli se v nevrátila hodnota null `ppObject` .  
  
## <a name="see-also"></a>Viz také  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)

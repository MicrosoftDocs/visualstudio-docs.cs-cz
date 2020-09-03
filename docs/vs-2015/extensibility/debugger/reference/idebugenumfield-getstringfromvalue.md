---
title: 'IDebugEnumField:: GetStringFromValue | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecdd60c363e30afbe4c61e8e18660a17a06a5ce8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188999"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato metoda získá název konstanty výčtu dané hodnoty.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetStringFromValue(  
   ULONGLONG value,  
   BSTR*     pbstrValue  
);  
```  
  
```csharp  
int GetStringFromValue(  
   ulong      value,  
   out string pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `value`  
 pro Hodnota, pro kterou má být získán název konstanty výčtu.  
  
 `pbstrValue`  
 mimo Vrátí název konstanty výčtu.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí hodnotu `S_OK` ; jinak vrátí, `S_FALSE` zda nemá žádná přidružená název, nebo vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je k stejné hodnotě přidruženo více než jeden název, bude vráceno křestní jméno definované ve výčtu.  
  
## <a name="see-also"></a>Viz také  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)

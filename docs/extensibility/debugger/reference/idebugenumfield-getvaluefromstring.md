---
title: IDebugEnumField::GetValueFromString | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 86cf8b1421769ac9a4b302e0da3676d826b9bea6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942228"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
Tato metoda vrátí hodnotu přidruženou k názvu konstanta výčtu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetValueFromString(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromString(  
   string    pszValue,  
   out ulong pValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszValue`  
 [in] Řetězec určující název, který má být získána hodnota. Všimněte si, že pro C++, toto je řetězec širokých znaků.  
  
 `pValue`  
 [out] Vrátí související číselnou hodnotu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí `S_FALSE`, pokud název není součástí výčtu nebo kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je velká a malá písmena. Hledat bez tohoto rozlišování potřeby (například v jazyce jako například Visual Basic, kde názvy nejsou malá a velká písmena) a použít [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).  
  
## <a name="see-also"></a>Viz také  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
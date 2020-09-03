---
title: 'IDebugEnumField:: GetValueFromStringCaseInsensitive | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: efe94a721c432cb1284df299ca267271ab5bef4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188934"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato metoda používá hledání bez rozlišování velkých a malých písmen k vrácení hodnoty přidružené k názvu konstanty výčtu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetValueFromStringCaseInsensitive(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromStringCaseInsensitive(  
   string    pszValue,   
   out ulong pValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszValue`  
 pro Řetězec určující název, pro který má být získána hodnota. Všimněte si, že pro C++ je to řetězec s velkým znakem.  
  
 `pValue`  
 mimo Vrátí přidruženou číselnou hodnotu.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` , pokud název není součástí výčtu nebo kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 V této metodě se nerozlišují malá a velká písmena. Pokud je potřeba vyhledávání citlivé na velká a malá písmena (například v jazyce C++, kde se v názvech rozlišují malá a velká písmena), použijte [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).  
  
## <a name="see-also"></a>Viz také  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)

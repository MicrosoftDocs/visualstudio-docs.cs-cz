---
title: 'IDebugProperty2:: SetValueAsReference | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a94e3767ee05e39e847af27dc5999fa8bbbe2d44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193450"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Nastaví hodnotu této vlastnosti na hodnotu daného odkazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```csharp  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `rgpArgs`  
 pro Pole argumentů předávaných metodě setter vlastnosti spravovaného kódu. Pokud metoda setter vlastnosti nepřijímá argumenty nebo pokud tento objekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) neodkazuje na takové setter vlastnosti, `rgpArgs` měla by být hodnota null. Tento parametr je obvykle hodnota null.  
  
 `dwArgCount`  
 pro Počet argumentů v `rgpArgs` poli.  
  
 `pValue`  
 pro Odkaz ve formě objektu [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) na hodnotu, která má být použita k nastavení této vlastnosti.  
  
 `dwTimeout`  
 pro Doba, která se má provést při nastavování hodnoty (v milisekundách) Typickou hodnotou je `INFINITE` . To má vliv na dobu, po kterou může jakékoli možné vyhodnocení trvat.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí `S_OK` . v opačném případě vrátí kód chyby, obvykle jeden z následujících:  
  
|Chyba|Popis|  
|-----------|-----------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Nastavení hodnoty z odkazu není podporováno.|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Hodnotu nelze nastavit, protože tato vlastnost odkazuje na metodu.|  
|`E_SETVALUE_VALUE_IS_READONLY`|Hodnota je jen pro čtení a nelze ji nastavit.|  
|`E_NOTIMPL`|Metoda není implementována.|  
  
## <a name="see-also"></a>Viz také  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

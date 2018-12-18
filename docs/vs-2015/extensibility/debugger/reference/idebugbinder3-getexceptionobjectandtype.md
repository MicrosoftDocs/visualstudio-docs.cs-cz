---
title: IDebugBinder3::GetExceptionObjectAndType | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d43cf051b90e8a5c0cece3acaf8e1e6ed45b37a0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781358"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato metoda načte výjimky přidružené k objektu, pokud existuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```csharp  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppException`  
 [out] Vrátí objekt představující výjimku.  
  
 `ppField`  
 [out] Vrátí objekt představující konkrétní pole, které mohou způsobit výjimku (to může mít hodnotu null).  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
> [!NOTE]
>  Pokud chcete ověřit, zda dojde k výjimce, zkontrolujte hodnoty vrácené `ppException`: Pokud je hodnota null, pak tento objekt přidružen žádná výjimka.  
  
## <a name="see-also"></a>Viz také  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)


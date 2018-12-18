---
title: IEnumDebugCustomAttributes::Reset | Dokumentace Microsoftu
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
- IEnumCustomAttributes::Reset
helpviewer_keywords:
- IEnumDebugCustomAttributes::Reset
ms.assetid: e0db6518-5a71-4adb-a407-4d2ac7a3e369
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: df775b8464249a5c6d8db8e7a71a50dcb989b7c4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791719"
---
# <a name="ienumdebugcustomattributesreset"></a>IEnumDebugCustomAttributes::Reset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Návrat na začátek pořadí výčtu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Až tato metoda je volána, další volání [Další](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) metoda vrátí první prvek výčtu.  
  
## <a name="see-also"></a>Viz také  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [Next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)


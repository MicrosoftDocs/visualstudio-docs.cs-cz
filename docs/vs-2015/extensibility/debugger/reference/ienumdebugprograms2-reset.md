---
title: 'IEnumDebugPrograms2:: resetovat | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Reset
helpviewer_keywords:
- IEnumDebugPrograms2::Reset
ms.assetid: b289242b-24ea-4df3-a811-20b0c8a903d6
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4ef5174ec476a242ec215eac5fcaf140cdec67c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62562898"
---
# <a name="ienumdebugprograms2reset"></a>IEnumDebugPrograms2::Reset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obnoví výčet na první prvek.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Po volání této metody vrátí další volání metody [Next](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md) první prvek výčtu.  
  
## <a name="see-also"></a>Viz také  
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)

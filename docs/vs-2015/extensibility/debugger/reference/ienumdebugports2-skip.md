---
title: 'IEnumDebugPorts2:: Skip | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::Skip
helpviewer_keywords:
- IEnumDebugPorts2::Skip
ms.assetid: a837383f-7b39-4e06-b336-f1715b073dbe
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 96bf6bd5277e6683bf793de17e608802c6c01034
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155050"
---
# <a name="ienumdebugports2skip"></a>IEnumDebugPorts2::Skip
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Přeskočí na zadaný počet prvků.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 pro Počet prvků, které se mají přeskočit  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí `S_OK` . Vrátí, `S_FALSE` Pokud `celt` je větší než počet zbývajících prvků. v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `celt` Určuje hodnotu větší než počet zbývajících prvků, je výčet nastaven na konec a `S_FALSE` je vrácen.  
  
## <a name="see-also"></a>Viz také  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)

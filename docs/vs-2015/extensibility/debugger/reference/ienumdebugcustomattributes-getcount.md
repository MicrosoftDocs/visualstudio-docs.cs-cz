---
title: 'IEnumDebugCustomAttributes:: GetCount | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::GetCount
helpviewer_keywords:
- IEnumDebugCustomAttributes::GetCount
ms.assetid: fafe826f-4ebf-4572-b2a3-d5dd2916c12f
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9c175297bf0f80c74e0c3409843164e0b08589ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62551488"
---
# <a name="ienumdebugcustomattributesgetcount"></a>IEnumDebugCustomAttributes::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Získá počet vlastních atributů v enumerátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetCount(   
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcelt`  
 mimo Vrátí počet prvků ve výčtu.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda není součástí vlastního rozhraní výčtu modelu COM, které určuje, že `Next` `Clone` `Skip` je nutné implementovat pouze,, a `Reset` .  
  
## <a name="see-also"></a>Viz také  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)

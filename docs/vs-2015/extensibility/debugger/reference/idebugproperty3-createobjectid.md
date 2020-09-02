---
title: 'IDebugProperty3:: CreateObjectID | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0035faad9078acd70886d597f039c0d8de5ee12f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64788321"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vytvoří jedinečné ID pro tuto vlastnost, aby bylo zajištěno, že je mezi všemi ostatními vlastnostmi jedinečné.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```csharp  
int CreateObjectID();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je volána, když správce ladění relace chce ověřit, zda je tato vlastnost jednoznačně identifikována mezi všemi ostatními vlastnostmi. Ladicí stroj (DE) tuto metodu podporuje, pokud nejsou vlastnosti, se kterými pracuje, již jednoznačně identifikovány. Pokud DE nepodporuje tuto metodu, vrátí `E_NOTIMPL` .  
  
 Jakékoli jedinečné ID, které bylo vytvořeno pomocí, `CreateObjectID` je zničeno při volání metody [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) ; to také signalizuje nutnost jednoznačně identifikovat tuto vlastnost.  
  
> [!NOTE]
> Neexistuje žádná metoda pro načtení tohoto jedinečného ID, takže metoda DE může v případě volání metody dělat jakékoli jedinečné identifikátory `CreateObjectID` .  
  
## <a name="see-also"></a>Viz také  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)

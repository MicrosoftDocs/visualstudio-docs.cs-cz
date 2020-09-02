---
title: 'IDebugPortSupplier3:: CanPersistPorts | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: edc989771b41cc4a5cc5b4710de4cbb5632873e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188181"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato metoda určuje, zda dodavatel portu může zachovat porty (jejich zápisem na disk) mezi voláními ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```csharp  
int CanPersistPorts();  
```  
  
#### <a name="parameters"></a>Parametry  
 Žádné  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` Pokud je možné porty zachovat nebo je `S_FALSE` Označit, že porty nelze zachovat.  
  
## <a name="remarks"></a>Poznámky  
 Pokud dodavatel portu může zachovat porty, měl by tak učinit, když je zničený, a po opětovném vytvoření instance ho znovu načítat.  
  
## <a name="see-also"></a>Viz také  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)

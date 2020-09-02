---
title: 'IPropertyProxyEESide:: funkce CreateReplacementObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c3a21e640d6661f8066609bdc344299ccbd63d52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147507"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vytvoří kopii datového objektu specifickou pro vyhodnocení výrazu (EE).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dataIn`  
 pro Objekt [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) , který uchovává data ke zkopírování.  
  
 `dataOut`  
 mimo Vrátí nový `IEEDataStorage` objekt.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Této metodě je udělen objekt [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) představující pole bajtů. Tento příchozí datový objekt není obvykle implementován pomocí et. Objekt vrácený touto metodou je však vždy implementován pomocí et, což umožňuje, aby rozhraní EE implementovalo `IEEDataStorage` rozhraní pro jakoukoliv třídu.  
  
 Všimněte si, že data zadaná příchozím `IEEDataStorage` objektem musí být stejná data v odchozím `IEEDataStorage` objektu.  
  
## <a name="see-also"></a>Viz také  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)

---
title: IEEDataStorage::GetData | Dokumentace Microsoftu
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
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0d23ecbc348d4aab4fdbbb83abaaba54fdad345
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751090"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Načte zadaný počet bajtů z objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetData(  
   ULONG  dataSize,  
   ULONG* sizeGotten,  
   BYTE*  data  
);  
```  
  
```csharp  
int GetData(  
   uint     dataSize,  
   out uint sizeGotten,  
   byte[]   data  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dataSize`  
 [in] Počet bajtů k načtení ( `data` pole musí obsahovat nejméně tento počet bajtů).  
  
 `sizeGotten`  
 [out] Vrátí počet bajtů ve skutečnosti načíst.  
  
 `data`  
 [out v] Pole se vyplní požadovaná data.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Doporučené použití této metody je pro načtení všech bajtů dat do místního pole, protože neexistuje žádný způsob, jak přeskočit bajtů v procesu načítání. V tomto případě parametr `dataSize` by měla být hodnota vrácené [getsize –](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) metody.  
  
## <a name="see-also"></a>Viz také  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)


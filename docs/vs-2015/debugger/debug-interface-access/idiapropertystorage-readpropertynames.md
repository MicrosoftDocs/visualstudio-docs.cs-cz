---
title: 'IDiaPropertyStorage:: ReadPropertyNames | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3f6d3ac520a396b5207767a3fec0913c801c287
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537352"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte odpovídající názvy řetězců pro dané identifikátory vlastností.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cpropid`  
 pro Počet ID vlastností v `rgpropid` .  
  
 `rgpropid`  
 pro Pole ID vlastností, pro které se mají získat názvy ( `PROPID` je definováno v WTypes. h jako `ULONG` ).  
  
 `rglpwstrName`  
 [in, out] Pole názvů vlastností pro zadaná ID vlastností Pole musí být předem přiděleno pro uchování požadovaného počtu názvů vlastností a musí být schopno uchovávat nejméně `cpropid``BSTR` řetězce.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí `S_OK` . v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Názvy vrácených vlastností musí být uvolněny (voláním `SysFreeString` funkce), pokud už je nepotřebujete.  
  
## <a name="see-also"></a>Viz také  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)

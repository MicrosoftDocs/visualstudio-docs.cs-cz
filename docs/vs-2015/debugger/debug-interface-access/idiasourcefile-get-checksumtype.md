---
title: 'IDiaSourceFile:: get_checksumType | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f859bce63e2976b23ab613e249dad41b2bc63486
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190700"
---
# <a name="idiasourcefileget_checksumtype"></a>IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte typ kontrolního součtu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 mimo Vrátí typ kontrolního součtu.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Typ kontrolního součtu je hodnota, kterou lze namapovat na algoritmus kontrolního součtu. Například standardní formát souboru PDB může mít obvykle jednu z následujících hodnot:  
  
|Typ kontrolního součtu|Popisek CryptoAPI|Popis|  
|-------------------|---------------------|-----------------|  
|0|\<none>|K dispozici není žádný kontrolní součet.|  
|1|`CALG_MD5`|byl vygenerován kontrolní součet algoritmu hash MD5.|  
|2|`CALG_SHA1`|byl vygenerován kontrolní součet algoritmu hash SHA1.|  
  
 `CryptoAPI`Popisky jsou z `ALG_ID` výčtu. Další informace o algoritmech hash najdete v `CryptoAPI` části Microsoft [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)] .  
  
 Chcete-li získat skutečné bajty kontrolního součtu pro zdrojový soubor, zavolejte metodu [IDiaSourceFile:: get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) .  
  
## <a name="see-also"></a>Viz také  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)

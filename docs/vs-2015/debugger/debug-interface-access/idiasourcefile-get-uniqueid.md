---
title: Idiasourcefile::get_uniqueid – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_uniqueId method
ms.assetid: e0b8dbc0-6061-4f31-bead-2cd72be44e41
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adfd0bbdd7b6fd29261541f71f718862b96f7f5f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739802"
---
# <a name="idiasourcefilegetuniqueid"></a>IDiaSourceFile::get_uniqueId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte hodnotu klíče jednoduché celé číslo, které jsou jedinečné pro tuto bitovou kopii.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_uniqueId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Vrátí hodnotu klíče jednoduché celé číslo, které jsou jedinečné pro tuto bitovou kopii.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Porovnání klíčů, nikoli řetězce může zrychlit zpracování čísla řádku.  
  
## <a name="see-also"></a>Viz také  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)




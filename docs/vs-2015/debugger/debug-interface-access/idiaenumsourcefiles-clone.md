---
title: Idiaenumsourcefiles::clone – | Dokumentace Microsoftu
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
- IDiaEnumSourceFiles::Clone method
ms.assetid: 87a9a9b6-3927-4131-927c-ad95f8f098b9
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 131bd0f9c4feac8f6e879c7a2b50c4d350971130
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788092"
---
# <a name="idiaenumsourcefilesclone"></a>IDiaEnumSourceFiles::Clone
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vytvoří čítač, který obsahuje stejného stavu jako aktuální enumerátor výčtu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumSourceFiles** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 ppenum  
 [out] Vrátí [idiaenumsourcefiles –](../../debugger/debug-interface-access/idiaenumsourcefiles.md) objekt, který obsahuje duplicitní čítače výčtu. Zdrojový soubory nejsou duplicitní pouze enumerátor.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)




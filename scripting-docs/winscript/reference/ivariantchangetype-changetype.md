---
title: IVariantChangeType::ChangeType | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IVariantChangeType.ChangeType
apilocation:
- scrobj.dll
helpviewer_keywords:
- IVariantChangeType::ChangeType
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d742d1bd57c85aa75c9ccd60479d08c1a559fb37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796413"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Přebírá hodnotu typu variant a vytvoří nový typ variant pomocí zadaného typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pvarDst`  
 [ve out] Hodnotu typu variant tak, aby obsahovala hodnota reprezentována `pvarSrc`, ale v typu zadaném pomocí `vtNew`.  
  
 `pvarSrc`  
 [v] Chcete-li změnit na nový typ hodnotu variant.  
  
 `lcid`  
 [v] Kontext národního prostředí, který se má použít při převodu argumenty do nebo z řetězce.  
  
 `vtNew`  
 [v] Určuje typ `pvarDst` se.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 `pvarDst` a `pvarSrc` argumenty může být stejná, v takovém případě se přepíše původní hodnotu. Tato metoda předá `pvarDst` k `VariantClear` funkce a proto `pvarDst` se musí inicializovat na platnou hodnotu.  
  
## <a name="see-also"></a>Viz také  
 [Ivariantchangetype – rozhraní](../../winscript/reference/ivariantchangetype-interface.md)
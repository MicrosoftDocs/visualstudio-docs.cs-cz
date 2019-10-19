---
title: 'Ivariantchangetype –:: ChangeType | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 406d5d8486b3016f0105b7bd8bf231db0e1e9613
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571782"
---
# <a name="ivariantchangetypechangetype"></a>IVariantChangeType::ChangeType
Použije hodnotu typu variant a vytvoří novou variantu se zadaným typem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pvarDst`  
 [in, out] Typ variant, který má obsahovat hodnotu reprezentovanou `pvarSrc`, ale s typem určeným parametrem `vtNew`.  
  
 `pvarSrc`  
 pro Hodnota typu variant, která se má změnit na nový typ.  
  
 `lcid`  
 pro Kontext národního prostředí, který se má použít při převodu argumentů na nebo z řetězců.  
  
 `vtNew`  
 pro Určuje typ `pvarDst`, který se má stát.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Argumenty `pvarDst` a `pvarSrc` mohou být stejné. v takovém případě je původní hodnota přepsána. Tato metoda předává `pvarDst` do funkce `VariantClear` a v důsledku toho by `pvarDst` měla být inicializována na platnou hodnotu.  
  
## <a name="see-also"></a>Viz také:  
 [IVariantChangeType – rozhraní](../../winscript/reference/ivariantchangetype-interface.md)
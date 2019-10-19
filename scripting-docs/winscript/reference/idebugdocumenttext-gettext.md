---
title: 'IDebugDocumentText –:: GetText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetText
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6472c40802fff4dad6e5ecc8f2729c95459e09f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572079"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Načte znaky nebo atributy znaků přidružené k rozsahu pozice znaků.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cCharacterPosition`  
 pro Počáteční umístění rozsahu pozice znaku  
  
 `pcharText`  
 [in, out] Znaková vyrovnávací paměť textu. Velikost vyrovnávací paměti musí být dostatečně velká, aby mohla pojmout `cMaxChars`é znaky. Pokud má tento parametr hodnotu NULL, metoda nevrátí znaky.  
  
 `pstaTextAttr`  
 [in, out] Vyrovnávací paměť atributu znaku. Velikost vyrovnávací paměti musí být dostatečně velká, aby mohla pojmout `cMaxChars`é znaky. Pokud má tento parametr hodnotu NULL, metoda nevrátí atributy.  
  
 `pcNumChars`  
 [in, out] Počet vrácených znaků nebo atributů. Před voláním této metody musí být tento parametr nastaven na hodnotu nula.  
  
 `cMaxChars`  
 pro Počet znaků v rozsahu pozice znaku. Určuje také maximální počet znaků, které se mají vrátit.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda načte znaky nebo atributy znaků přidružené k rozsahu pozice znaků. Rozsah pozice znaku je určen znakovou polohou a počtem znaků.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní IDebugDocumentText –](../../winscript/reference/idebugdocumenttext-interface.md)  
 [SOURCE_TEXT_ATTR – výčet](../../winscript/reference/source-text-attr-enumeration.md)
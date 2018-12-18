---
title: IDebugDocumentText::GetText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 5a1006304974fab4959ad6313ffdc26793cdd345
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794577"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Načte znaky nebo znak atributy přidružené rozsah pozice znaku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [v] Spusťte umístění pozice rozsahu znaků.  
  
 `pcharText`  
 [ve out] Textová vyrovnávací paměť znak. Vyrovnávací paměti musí být dostatečně velký pro uložení `cMaxChars` znaků. Pokud tento parametr hodnotu NULL, metoda nevrátí znaků.  
  
 `pstaTextAttr`  
 [ve out] Vyrovnávací paměť atribut znak. Vyrovnávací paměti musí být dostatečně velký pro uložení `cMaxChars` znaků. Pokud tento parametr hodnotu NULL, metoda nevrátí atributy.  
  
 `pcNumChars`  
 [ve out] Vrátí počet znaků nebo atributů. Tento parametr musí být nastaven na hodnotu nula před voláním této metody.  
  
 `cMaxChars`  
 [v] Počet znaků od pozice znaku. Také určuje maximální počet znaků, který má vrátit.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda načte znaky nebo znak atributy přidružené rozsah pozice znaku. Pozice znaku a počet znaků je zadán rozsahu pozice znaků.  
  
## <a name="see-also"></a>Viz také  
 [Idebugdocumenttext – rozhraní](../../winscript/reference/idebugdocumenttext-interface.md)   
 [SOURCE_TEXT_ATTR – výčet](../../winscript/reference/source-text-attr-enumeration.md)
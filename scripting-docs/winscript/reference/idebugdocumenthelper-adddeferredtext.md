---
title: 'Idebugdocumenthelper –:: AddDeferredText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDeferredText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDeferredText
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1aae73e44059b1f07fa4cb54f40cdcd12e564a8f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577043"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Upozorní pomocníka, že je daný text k dispozici, ale neposkytuje tyto znaky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cChars`  
 pro Počet znaků, které se mají přidat (Unicode)  
  
 `dwTextStartCookie`  
 pro Soubor cookie definovaný hostitelem, který představuje počáteční pozici textu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_FAIL`|Metoda se nezdařila.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda umožňuje hostiteli odložit znaky pro přidání do doby, než jsou potřeba, a umožnit pomáhajícímu generovat přesná oznámení a informace o velikosti. Parametr `dwTextStartCookie` je soubor cookie definovaný hostitelem, který představuje počáteční pozici textu. Tento soubor cookie musí poskytovat další volání `IDebugDocumentText::GetText`. Například v hostiteli, který představuje text ve znakové sadě DBCS, může být soubor cookie posun bajtů.  
  
 Předpokládá se, že jedno volání `IDebugDocumentText::GetText` může získat znaky z více volání `AddDeferredText`. Pomocné třídy se také mohou zeptat na stejný rozsah odložených znaků více než jednou.  
  
> [!NOTE]
> Volání `AddDeferredText` by se neměla kombinovat s voláními `AddUnicodeText` nebo `AddDBCSText`. Pokud k tomu dojde, `E_FAIL` se vrátí.  
  
## <a name="see-also"></a>Viz také:  
   [rozhraní idebugdocumenthelper –](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [Idebugdocumenthelper –:: AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [Idebugdocumenthelper –:: AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)
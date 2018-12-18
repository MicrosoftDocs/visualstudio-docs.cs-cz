---
title: IDebugDocumentHelper::AddDeferredText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: c92909874429075bebc6a1f0a252573d049584e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794715"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Pomocné rutiny upozorní, že zadaný text je k dispozici, ale neposkytuje znaky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cChars`  
 [v] Počet znaků (Unicode) Chcete-li přidat.  
  
 `dwTextStartCookie`  
 [v] Definované hostitele souboru cookie, který představuje počáteční pozici textu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_FAIL`|Metoda se nezdařilo.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda umožňuje hostiteli odložení poskytování znaků, které chcete přidat, dokud není potřeba, zatímco pomocné rutiny pro generování přesné oznámení a informace o velikosti. `dwTextStartCookie` Parametr je soubor cookie definované hostitele, který představuje počáteční pozici textu. Následující volání `IDebugDocumentText::GetText` musíte zadat Tento soubor cookie. V hostiteli, který reprezentuje text v DBCS, soubor cookie může být například posun bajtů.  
  
 Předpokládá se, který jediné volání `IDebugDocumentText::GetText` můžete získat znaky z více volání `AddDeferredText`. Pomocné třídy může také požádat o stejný rozsah odložené znaků více než jednou.  
  
> [!NOTE]
>  Volání `AddDeferredText` by neměl být ve smíšeném pomocí volání `AddUnicodeText` nebo `AddDBCSText`. Pokud k tomu dojde, `E_FAIL` je vrácen.  
  
## <a name="see-also"></a>Viz také  
 [Idebugdocumenthelper – rozhraní](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)
---
title: IDebugDocumentHelper::DefineScriptBlock | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.DefineScriptBlock
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b6ec86dacc2e3a8f3d9e28a6db744b778ff01eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794253"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Signalizuje do pomocné rutiny konkrétní rozsah znaků blok skriptu, který zpracovává daný skriptovací stroj.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ulCharOffset`  
 [v] Umístění začátku bloku skriptu.  
  
 `cChars`  
 [v] Počet znaků v bloku skriptu.  
  
 `pas`  
 [v] Skriptovací stroj pro daný blok skriptu.  
  
 `fScriptlet`  
 [v] Příznak, který označuje, zda blok skriptu skriptletu.  
  
 `pdwSourceContext`  
 [out] Kontext zdroje v bloku skriptu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Tuto metodu můžete použít inteligentního hostitele, když jeho dokumenty obsahují bloky vloženého skriptu. Tuto metodu můžete použít modul jazyka, když jeho kód obsahuje vložené skripty pro jiné jazyky.  
  
 Skriptovací stroj je zodpovědná za všechny syntaxe barevné zvýrazňování a kód kontextu vyhledávání v bloku skriptu.  
  
 `DefineScriptBlock` Metoda by měla být volána po přidání text (například pomocí `IDebugDocumentHelper::AddDBCSText` metoda), ale před skript bloku analýze (například pomocí `IActiveScriptParse ::ParseScriptText` metoda).  
  
## <a name="see-also"></a>Viz také  
 [Idebugdocumenthelper – rozhraní](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)
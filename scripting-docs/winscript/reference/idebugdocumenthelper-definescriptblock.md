---
title: Idebugdocumenthelper –::D efineScriptBlock | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 6a2418b18e80ac86b672b3847f24ef9084ed1252
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576977"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Určuje pomoc, že konkrétní rozsah znaků je blok skriptu, který je zpracováván daným skriptovacím modulem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
 pro Umístění začátku bloku skriptu.  
  
 `cChars`  
 pro Počet znaků v bloku skriptu.  
  
 `pas`  
 pro Skriptovací modul pro tento blok skriptu.  
  
 `fScriptlet`  
 pro Příznak, který označuje, zda je blok skriptu skriptletu.  
  
 `pdwSourceContext`  
 mimo Zdrojový kontext pro blok skriptu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Inteligentní hostitel může tuto metodu použít, pokud její dokumenty obsahují vložené bloky skriptu. Jazykový modul může tuto metodu použít, pokud její kód obsahuje vložené skripty pro jiné jazyky.  
  
 Skriptovací stroj zodpovídá za všechny barvy syntaxe a vyhledávání kontextu kódu v bloku skriptu.  
  
 Metoda `DefineScriptBlock` by měla být volána po přidání textu (například pomocí metody `IDebugDocumentHelper::AddDBCSText`), ale před analýzou bloku skriptu (například pomocí metody `IActiveScriptParse ::ParseScriptText`).  
  
## <a name="see-also"></a>Viz také:  
   [rozhraní idebugdocumenthelper –](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [Idebugdocumenthelper –:: AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)
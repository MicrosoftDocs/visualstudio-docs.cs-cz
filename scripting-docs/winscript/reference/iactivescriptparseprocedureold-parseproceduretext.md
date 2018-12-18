---
title: IActiveScriptParseProcedureOld::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld.ParseProcedureText
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld::ParseProcedureText
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cab546deb390535fa8ff71e116a0ad42d33cc104
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793608"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Analyzuje postup daného kódu a přidá anonymní postup obor názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrCode`  
 [v] Postup text k vyhodnocení. Výklad tento řetězec závisí na skriptovací jazyk.  
  
 `pstrFormalParams`  
 [v] Názvy formální parametr pro proceduru. Názvy parametrů musí být odděleny s odpovídající oddělovače pro skriptovacího stroje. Názvy nesmí být uzavřena v závorkách.  
  
 `pstrItemName`  
 [v] Název pojmenovanou položku, která poskytuje kontext, ve kterém se má vyhodnotit postup. Pokud tento parametr je `NULL`, vyhodnotí kód v globálním kontextu skriptovacího stroje.  
  
 `punkContext`  
 [v] Objekt kontextu. Tento objekt je vyhrazený pro použití v prostředí ladění, kde může poskytovat takový kontext ladicí program k reprezentaci active kontextu spuštění. Pokud tento parametr je `NULL`, modul používá `pstrItemName` k identifikaci kontextu.  
  
 `pstrDelimiter`  
 [v] Oddělovač end postupu. Když `pstrCode` je analyzována z datového proudu textu, hostitel se většinou používá oddělovač, například dvě jednoduché uvozovky ("), ke zjištění ukončení režimu. Tento parametr určuje oddělovač, který se používá hostitele, která umožňuje skriptovací stroj zajistit některé podmíněného primitivní předběžného zpracování (například dvě jednoduchých uvozovek pro použití jako oddělovač nahraďte jednoduché uvozovky [']). Přesně jak (a pokud) skriptovací stroj používá tyto informace závisí na skriptovacího stroje. Tento parametr nastavte na `NULL` Pokud hostitel nepoužili oddělovač konec procedury.  
  
 `dwSourceContextCookie`  
 [v] Hodnota definované aplikací, který se používá pro účely ladění.  
  
 `ulStartingLineNumber`  
 [v] Hodnoty s nulovým základem, který určuje, kdy řádek analýza ve vyrovnaném bude zahájena.  
  
 `dwFlags`  
 [v] Příznaky přidružený postup. Může být kombinací těchto hodnot.  
  
|Konstanta|Hodnota|Význam|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|Určuje, že kód v `pstrCode` je výraz, který reprezentuje návratovou hodnotu procedury.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|Určuje, že `this` ukazatel je součástí oboru procedury.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|Určuje, že nadřazených položek `this` ukazatel jsou zahrnuty v oboru procedury.|  
  
 `ppdisp`  
 [out] Vrátí obálku odesílání, kde je výchozí metodou postup analyzovat touto metodou.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`E_INVALIDARG`|Argument byl neplatný.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_NOTIMPL`|Tato metoda není podporována. Skriptovací stroj nepodporuje přidání běhu postupy pro obor názvů.|  
|`E_UNEXPECTED`|Nebyl očekáván volání (například skriptovací stroj je ve stavu Neinicializovaný nebo uzavřený).|  
|`OLESCRIPT_E_SYNTAX`|Syntaxe neurčené chybě v postupu.|  
|`S_FALSE`|Skriptovací stroj nepodporuje objekt odesílání; `ppdisp`parametr je nastaven na `NULL`.|  
  
## <a name="remarks"></a>Poznámky  
 Žádný kód skriptu se vyhodnotí během toto volání; Místo toho postup zkompilován metodu na `ppdisp` kde může být volána skriptem později.  
  
 Toto rozhraní je zastaralé pro `IActiveScriptParseProcedure` rozhraní. `IActiveScriptParseProcedure::ParseProcedureText` Metoda se podobá této metodě, ale umožňuje zadat název postupu. Za všech okolností `IActiveScriptParseProcedure::ParseProcedureText` by měl být použit.  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptparseprocedureold – rozhraní](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)
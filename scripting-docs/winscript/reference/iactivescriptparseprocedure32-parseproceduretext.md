---
title: IActiveScriptParseProcedure32::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ede37171-2f1e-4467-a358-17bd4a4f1869
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 2f36160ab9dca3ccc99aed1068b7e94fe1b7675d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793536"
---
# <a name="iactivescriptparseprocedure32parseproceduretext"></a>IActiveScriptParseProcedure32::ParseProcedureText
Analyzuje postup daného kódu a postup přidá do oboru názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrCode`  
 [v] Adresa text postup k vyhodnocení. Výklad tento řetězec závisí na skriptovací jazyk.  
  
 `pstrFormalParams`  
 [v] Adresa názvy formální parametr pro proceduru. Názvy parametrů musí být odděleny s odpovídající oddělovače pro skriptovacího stroje. Názvy nesmí být uzavřena v závorkách.  
  
 `pstrProcedureName`  
 [v] Adresa název procedury ho proto analyzovat.  
  
 `pstrItemName`  
 [v] Adresa položky název, který poskytuje kontext, ve kterém se má vyhodnotit postupu. Pokud tento parametr je `NULL`, vyhodnotí kód v globálním kontextu skriptovacího stroje.  
  
 `punkContext`  
 [v] Adresa objektu kontextu. Tento objekt je vyhrazený pro použití v prostředí ladění, kde může poskytovat takový kontext ladicí program k reprezentaci active kontextu spuštění. Pokud tento parametr je `NULL`, modul používá `pstrItemName` k identifikaci kontextu.  
  
 `pstrDelimiter`  
 [v] Adresa koncového postup oddělovače. Když `pstrCode` je analyzována z datového proudu textu, hostitel se většinou používá oddělovač, například dvě jednoduché uvozovky ("), ke zjištění ukončení režimu. Tento parametr určuje oddělovač, který se používá hostitele, která umožňuje skriptovací stroj zajistit některé podmíněného primitivní předběžného zpracování (například nahrazení jednoduché uvozovky ['] dvě jednoduchých uvozovek pro použití jako oddělovač). Přesně jak (a pokud) skriptovací stroj díky použití těchto informací závisí na skriptovacího stroje. Tento parametr nastavte na `NULL` Pokud hostitel nepoužili oddělovač konec procedury.  
  
 `dwSourceContextCookie`  
 [v] Hodnota definované aplikací, který se používá pro účely ladění.  
  
 `ulStartingLineNumber`  
 [v] Počítaný od nuly hodnota, která určuje, které řádku analýza ve vyrovnaném bude zahájena v.  
  
 `dwFlags`  
 [v] Příznaky přidružený postup. Může být kombinací těchto hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Určuje, že kód v `pstrCode` je výraz, který reprezentuje návratovou hodnotu procedury. Ve výchozím nastavení může obsahovat kód výrazu, seznam příkazů nebo něco jinak povolenou v postupu skriptovací jazyk.|  
|SCRIPTPROC_IMPLICIT_THIS|Určuje, že `this` ukazatel je součástí oboru procedury.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Určuje, že nadřazených položek `this` ukazatel jsou zahrnuty v oboru procedury.|  
  
 `ppdisp`  
 [out] Adresa pro objekt obsahující v skriptu globální metody a vlastnosti ukazatel. Pokud skriptovací stroj nepodporuje takového objektu `NULL` je vrácen.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Úspěch.|  
|`E_INVALIDARG`|Argument byl neplatný.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_NOTIMPL`|Tato metoda není podporována. Skriptovací stroj nepodporuje přidání běhu postupy pro obor názvů.|  
|`E_UNEXPECTED`|Nebyl očekáván volání (například skriptovací stroj je ve stavu Neinicializovaný nebo uzavřený).|  
|`OLESCRIPT_E_SYNTAX`|Syntaxe neurčené chybě v postupu.|  
|`S_FALSE`|Skriptovací stroj nepodporuje objekt odesílání; `ppdisp` parametr je nastaven na `NULL`.|  
  
## <a name="remarks"></a>Poznámky  
 Žádný kód skriptu se vyhodnotí během toto volání; Místo toho postup zkompilován stavů skriptu, kde může být volána skriptem později.  
  
## <a name="see-also"></a>Viz také  
 [IActiveScriptParseProcedure32](../../winscript/reference/iactivescriptparseprocedure32.md)
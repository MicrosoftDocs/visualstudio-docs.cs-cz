---
title: IActiveScriptStringCompare::StrComp | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStringCompare.StrComp
apilocation:
- scrobj.dll
helpviewer_keywords:
- StrComp method, IActiveScriptStringCompare interface
ms.assetid: 124d1281-8037-4766-a2a1-61244ac1f114
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b92b29f4e40f5e8de567337957aabbcb3c057fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793638"
---
# <a name="iactivescriptstringcomparestrcomp"></a>IActiveScriptStringCompare::StrComp
Definuje metodu porovnání řetězce skriptovacího stroje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StrComp(  
// The first string:  
    [in] BSTR bszStr1,    
// The second string:   
    [in] BSTR bszStr2,    
// The result of the comparison:  
    [out, retval] LONG* iRet   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bszStr1`  
 První řetězec.  
  
 `bszStr2`  
 K druhému řetězci.  
  
 `iRet`  
 Výsledek porovnání. 0, pokud `bszStr1` a `bszStr2`jsou identické; -1, pokud `bszStr1`  <  `bszStr2`; 1 v případě `bszStr1`  >  `bszStr2`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Úspěch.|  
|`E_INVALIDARG`|Argument není platný.|  
|`E_UNEXPECTED`|Nebyl očekáván volání (například skriptovací stroj ještě byla načtena nebo inicializovat).|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je volána pokaždé, když se spustí porovnání řetězců.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přetížení funkce porovnání řetězce. Přetížení je povoleno, pokud používáte [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) nastavit SCRIPTPROP_STRINGCOMPAREINSTANCE.  
  
```cpp#  
cpp_quote("// {58562769-ED52-42f7-8403-4963514E1F11}")  
cpp_quote("DEFINE_GUID(IID_IActiveScriptStringCompare, 0x58562769,   
    0xED52, 0x42f7, 0x84, 0x03, 0x49, 0x63, 0x51, 0x4E, 0x1F, 0x11);")  
cpp_quote("")  
  
cpp_quote("#define SCRIPTPROP_INTEGERMODE              0x00003000")  
cpp_quote("#define SCRIPTPROP_STRINGCOMPAREINSTANCE    0x00003001")  
cpp_quote("")  
interface IActiveScriptStringCompare;  
[  
         object,  
         uuid(58562769-ED52-42f7-8403-4963514E1F11),  
         pointer_default(unique)  
]  
interface IActiveScriptStringCompare : IUnknown  
{  
        // StrComp  
        //     bszStr1: first string  
        //     bszStr2: second string  
        //     iRet: 0 if identical, -1 if bszStr1 < bszStr2, 1 if   
        //         bszStr1 > bszStr2  
        //            
        //     Return values:  
        //         S_OK: Success  
        //         E_NOTIMPL: Not implemented  
        //  
        HRESULT StrComp(  
                [in] BSTR bszStr1,  
                [in] BSTR bszStr2,  
                [out, retval] LONG* iRet  
        );  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptstringcompare – rozhraní](../../winscript/reference/iactivescriptstringcompare-interface.md)
---
title: IDebugModule3::GetSymbolInfo | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e121434f5db1edc1e4c13df3e832cba5be7d471
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876123"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Načte seznam cest, které budou vyhledány pro symboly, stejně jako výsledky hledání jednotlivé cesty.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSymbolInfo(  
   SYMBOL_SEARCH_INFO_FIELDS  dwFields,  
   MODULE_SYMBOL_SEARCH_INFO* pInfo  
);  
```  
  
```csharp  
int GetSymbolInfo(  
   enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,   
   MODULE_SYMBOL_SEARCH_INFO[]    pinfo  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFields`  
 [in] Kombinace příznaků z [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) výčet určující, které pole `pInfo` mají být vyplněna.  
  
 `pInfo`  
 [out] A [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) strukturu, jejíž členové jsou pro vyplnění pomocí zadaných informací. Pokud je tato hodnota null, vrátí tato metoda `E_INVALIDARG`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
> [!NOTE]
>  Vrácený řetězec (v `MODULE_SYMBOL_SEARCH_INFO` struktura) může být prázdný i v případě `S_OK` je vrácena. V takovém případě se žádné informace o hledání vrátit.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `bstrVerboseSearchInfo` pole `MODULE_SYMBOL_SEARCH_INFO` struktura není prázdný a obsahuje seznam cest prohledávat a výsledky hledání. V seznamu je formátováno s cestou, následované třemi tečkami ("..."), za nímž následuje výsledek. Pokud existuje více než jednu dvojici výsledek cestu, každý pár oddělený pár "\r\n" (návrat na začátek řádku return nebo odřádkování). Vzor vypadá takto:  
  
 \<cesta >... \<výsledku > \r\n\<cesta >... \<výsledku > \r\n\<cesta >... \<výsledku >  
  
 Všimněte si, že poslední položka nemá \r\n pořadí.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu vrátí tato metoda tři cesty s tři různé výsledky hledání. Každý řádek je přerušen skrze pár návrat na začátek řádku return nebo odřádkování. Příklad výstupu právě zobrazí výsledky hledání jako jeden řetězec.  
  
> [!NOTE]
>  Stav výsledek je všechno, co hned za "..." až do konce řádku.  
  
```cpp  
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)  
{  
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };  
    HRESULT hr;  
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);  
    if (SUCCEEDED(hr)) {  
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;  
        if (searchInfo.Length() != 0) {  
            std::wcout << (wchar_t *)(BSTR)searchInfo;  
            std::wcout << std::endl;  
        }  
    }  
}  
```  
  
 **c:\symbols\user32.pdb... Soubor nebyl nalezen.**  
**c:\winnt\symbols\user32.pdb... Verze neodpovídá.**  
**\\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Načíst symboly.**   
## <a name="see-also"></a>Viz také  
 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
---
title: 'IDebugModule3:: GetSymbolInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63803b84e3d00bddef2238a627300522a4e7c294
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929781"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Načte seznam cest, které hledají symboly, i výsledky hledání jednotlivých cest.

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

## <a name="parameters"></a>Parametry
`dwFields`\
pro Kombinace příznaků z výčtu [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) určující, která pole mají `pInfo` být vyplněna.

`pInfo`\
mimo [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) strukturu, jejíž členové se mají vyplnit zadanými informacemi. Pokud je tato hodnota null, vrátí tato metoda `E_INVALIDARG` .

## <a name="return-value"></a>Návratová hodnota
Pokud je metoda úspěšná, vrátí se. `S_OK` v opačném případě vrátí kód chyby.

> [!NOTE]
> Vrácený řetězec (ve `MODULE_SYMBOL_SEARCH_INFO` struktuře) může být prázdný, i když `S_OK` je vrácen. V tomto případě nebyly k dispozici žádné vyhledávací informace, které by bylo možné vrátit.

## <a name="remarks"></a>Poznámky
Pokud `bstrVerboseSearchInfo` pole `MODULE_SYMBOL_SEARCH_INFO` struktury není prázdné, obsahuje seznam prohledávaných cest a výsledky tohoto hledání. Seznam je formátován s cestou, následovanou třemi tečkami ("...") následovaným výsledkem. Pokud existuje více než jedna dvojice výsledků cesty, pak je každý pár oddělený dvojicí "\r\n" (přeprava za sekundu). Vzor vypadá takto:

\<path>...\<result> \r\n \<path> ... \<result> \r\n \<path> ...\<result>

Všimněte si, že poslední položka nemá sekvenci \r\n.

## <a name="example"></a>Příklad
V tomto příkladu Tato metoda vrátí tři cesty se třemi různými výsledky hledání. Každý řádek je ukončen dvojicí pro návrat vozíku a odřádkování. Ukázkový výstup pouze vytiskne výsledky hledání jako jeden řetězec.

> [!NOTE]
> Výsledkem stavu je vše hned za "..." až do konce řádku.

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

**c:\symbols\user32.pdb... Soubor se nenašel.** 
 **c:\winnt\symbols\user32.pdb... Verze se neshoduje.** 
 **\\\symbols\symbols\user32.dll \0a8sd0ad8ad\user32.pdb... Symboly byly načteny.**

## <a name="see-also"></a>Viz také

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)

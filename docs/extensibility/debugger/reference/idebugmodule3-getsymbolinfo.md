---
title: IDebugModule3::GetSymbolInfo | Dokumenty společnosti Microsoft
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3aafb28715f58eaba4499b47a2e1dee15b82ed14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726901"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Načte seznam cest, které jsou vyhledávány pro symboly, stejně jako výsledky hledání každé cesty.

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
[v] Kombinace příznaků z [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) výčtu určující, `pInfo` která pole mají být vyplněna.

`pInfo`\
[out] Struktura [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) jejíž členy mají být vyplněny zadanými informacemi. Pokud se jedná o hodnotu `E_INVALIDARG`null, vrátí tato metoda .

## <a name="return-value"></a>Návratová hodnota
Pokud je metoda úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.

> [!NOTE]
> Vrácený řetězec (ve `MODULE_SYMBOL_SEARCH_INFO` struktuře) může `S_OK` být prázdný i v případě, že je vrácena. V tomto případě nebyly k dispozici žádné vyhledávací informace, které by bylo možné vrátit.

## <a name="remarks"></a>Poznámky
Pokud `bstrVerboseSearchInfo` pole `MODULE_SYMBOL_SEARCH_INFO` struktury není prázdné, obsahuje seznam prohledávaných cest a výsledky tohoto hledání. Seznam je formátován s cestou, následuje tři tečky ("..."), následuje výsledek. Pokud existuje více než jeden pár výsledků cesty, pak je každá dvojice oddělena dvojicí "\r\n" (carriage-return/linefeed). Vzor vypadá takto:

\<cesta>... \<výsledek>\r\n\<> cesty... \<výsledek>\r\n\<> cesty... \<výsledek>

Všimněte si, že poslední položka nemá \r\n sekvenci.

## <a name="example"></a>Příklad
V tomto příkladu tato metoda vrátí tři cesty se třemi různými výsledky hledání. Každý řádek je ukončen dvojicí carriage-return/linefeed. Ukázkový výstup pouze vytiskne výsledky hledání jako jeden řetězec.

> [!NOTE]
> Výsledek stavu je vše bezprostředně následující po "..." až na konec řádku.

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
 **c:\winnt\symbols\user32.pdb... Verze se neshoduje.** 
 ** \\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symboly načteny.**

## <a name="see-also"></a>Viz také

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)

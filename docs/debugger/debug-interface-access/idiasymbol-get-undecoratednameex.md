---
title: Idiasymbol::get_undecoratednameex – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de8eb57e8b1e31be835163e67fa12e3cd6556892
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930658"
---
# <a name="idiasymbolgetundecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
Načte část nebo všechny nedekorovaný název pro C++ dekorovaného názvu (propojení).  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `undecoratedOptions`  
 [in] Určuje kombinaci příznaků je vráceno ovládacího prvku. V části poznámky pro konkrétní hodnoty a co dělají.  
  
 `pRetVal`  
 [out] Vrátí že nedekorovaný název pro C++ dekorovaného názvu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí `S_FALSE` nebo kód chyby.  
  
> [!NOTE]
>  Vrácená hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.  
  
## <a name="remarks"></a>Poznámky  
 `undecorateOptions` Může obsahovat kombinaci následující příznaky.  
  
> [!NOTE]
>  Příznak názvy nejsou definované v sadě DIA SDK, budete muset přidat deklarace do kódu nebo používat nezpracované hodnoty.  
  
|Příznak|Hodnota|Popis|  
|----------|-----------|-----------------|  
|UNDNAME_COMPLETE|0x0000|Povolí úplnou undecoration.|  
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Odebere úvodní podtržítka od Microsoftu Rozšířená klíčová slova.|  
|UNDNAME_NO_MS_KEYWORDS|0x0002|Zakáže rozšíření Rozšířená klíčová slova společnosti Microsoft.|  
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Zakáže rozšíření návratový typ pro primární deklarace.|  
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Zakáže rozšíření modelu deklarace.|  
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Zakáže rozšíření jazyka Specifikátor deklarace.|  
|UNDNAME_RESERVED1|0x0020|VYHRAZENÁ.|  
|UNDNAME_RESERVED2|0x0040|VYHRAZENÁ.|  
|UNDNAME_NO_THISTYPE|0x0060|Zakáže všechny modifikátory na `this` typu.|  
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|Zakáže přístup ke specifikátorům pro členy rozšíření.|  
|UNDNAME_NO_THROW_SIGNATURES|0x0100|Zakáže rozšíření "throw podpisy" pro funkce a ukazatelů na funkce.|  
|UNDNAME_NO_MEMBER_TYPE|0x0200|Zakazuje rozbalení `static` nebo `virtual` členy.|  
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|Zakáže rozšíření model od Microsoftu pro UDT vrátí.|  
|UNDNAME_32_BIT_DECODE|0x0800|Undecorates 32-bit dekorované názvy.|  
|UNDNAME_NAME_ONLY|0x1000|Získá název pro primární deklarace; Vrátí pouze [oboru::] název.  Rozbalí parametry šablony.|  
|UNDNAME_TYPE_ONLY|0x2000|Vstup je pouze typ kódování; lze kombinovat abstraktní deklarátor.|  
|UNDNAME_HAVE_PARAMETERS|0x4000|Parametry šablony skutečné jsou k dispozici.|  
|UNDNAME_NO_ECSU|0x8000|Potlačí zobrazení výčtu/třídu/strukturu/sjednocení.|  
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|Potlačí kontrolu znaků platný identifikátor.|  
|UNDNAME_NO_PTR64|0x20000|Nezahrnuje ptr64 ve výstupu.|  
  
## <a name="see-also"></a>Viz také  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
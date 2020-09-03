---
title: 'IDiaSymbol:: get_undecoratedNameEx | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25942c76d8e568d6354c9a6a2b2c69c806cde352
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85461600"
---
# <a name="idiasymbolget_undecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
Načte část nebo celý nedekorovaný název pro název dekorované (vazby) v jazyce C++.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_undecoratedNameEx( 
   DWORD undecorateOptions,
   BSTR* pRetval
);
```

#### <a name="parameters"></a>Parametry
 `undecoratedOptions`

pro Určuje kombinaci příznaků, které řídí, co je vráceno. Konkrétní hodnoty a to, co dělají, najdete v části s poznámkami.

 `pRetVal`

mimo Vrátí nedekorovaný název pro dekorované názvy v jazyce C++.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky
 `undecorateOptions`Může se jednat o kombinaci následujících příznaků.

> [!NOTE]
> Názvy příznaků nejsou definovány v DIA SDK, takže je nutné přidat deklarace do kódu nebo použít nezpracované hodnoty.

|Příznak|Hodnota|Popis|
|----------|-----------|-----------------|
|UNDNAME_COMPLETE|0x0000|Povoluje úplné oddekorace.|
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Odstraní úvodní podtržítka od společnosti Microsoft rozšířená klíčová slova.|
|UNDNAME_NO_MS_KEYWORDS|0x0002|Zakáže rozšiřování rozšířených klíčových slov společnosti Microsoft.|
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Zakáže rozšíření návratového typu pro primární deklaraci.|
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Zakáže rozšíření modelu deklarace.|
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Zakáže rozšíření specifikátoru jazyka deklarace.|
|UNDNAME_RESERVED1|0x0020|Rezervovaný.|
|UNDNAME_RESERVED2|0x0040|Rezervovaný.|
|UNDNAME_NO_THISTYPE|0x0060|Zakáže všechny modifikátory `this` typu.|
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|Zakáže rozšíření specifikátorů přístupu pro členy.|
|UNDNAME_NO_THROW_SIGNATURES|0x0100|Zakáže rozšíření throw-signaturs pro funkce a ukazatele na funkce.|
|UNDNAME_NO_MEMBER_TYPE|0x0200|Zakáže rozšíření `static` nebo `virtual` členů.|
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|Zakáže rozšíření modelu Microsoft pro funkce UDT.|
|UNDNAME_32_BIT_DECODE|0x0800|Neupraví 32-bit dekorované názvy.|
|UNDNAME_NAME_ONLY|0x1000|Získá pouze název primární deklarace; Vrátí pouze název [Scope::].  Rozbalí parametry šablony.|
|UNDNAME_TYPE_ONLY|0x2000|Vstup je pouze kódování typu; Vytvoří abstraktní deklarátor.|
|UNDNAME_HAVE_PARAMETERS|0x4000|Reálné parametry šablony jsou k dispozici.|
|UNDNAME_NO_ECSU|0x8000|Potlačí výčet/třídu/strukturu/sjednocení.|
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|Potlačí kontrolu platných znaků identifikátoru.|
|UNDNAME_NO_PTR64|0x20000|Nezahrnuje ptr64 do výstupu.|

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
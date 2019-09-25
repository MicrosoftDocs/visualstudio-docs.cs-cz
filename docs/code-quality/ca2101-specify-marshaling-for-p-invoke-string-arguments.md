---
title: 'CA2101: Určete zařazování pro argumenty řetězce volání nespravovaného kódu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f49c9dfdac1d8d8aec8ec32df7374b5ae0a28e92
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233027"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: Určete zařazování pro argumenty řetězce volání nespravovaného kódu

|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|Kategorie|Microsoft.Globalization|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Člen vyvolání platformy umožňuje částečně důvěryhodných volajících, má řetězcový parametr a explicitně nezařazuje řetězec.

## <a name="rule-description"></a>Popis pravidla
Pokud převedete z kódování Unicode na ANSI, je možné, že ne všechny znaky Unicode mohou být reprezentovány v konkrétní znakové stránce ANSI. *Mapování podle nejlepšího hlediska* se pokusí vyřešit tento problém nahrazením znaku pro znak, který nelze reprezentovat. Použití této funkce může způsobit potenciální ohrožení zabezpečení, protože nemůžete ovládat vybraný znak. Škodlivý kód by například mohl úmyslně vytvořit řetězec v kódování Unicode, který obsahuje znaky, které se nenašly na konkrétní kódové stránce, které jsou převedeny na speciální znaky systému souborů, jako je například '.. ' nebo '/'. Všimněte si také, že kontroly zabezpečení pro speciální znaky často proběhne před převodem řetězce na ANSI.

Mapování nejlepšího umístění je výchozí pro nespravovaný převod, WChar na megabajt. Pokud explicitně nezakážete mapování nejlepšího obsahu, může váš kód obsahovat zneužití ohrožení zabezpečení z důvodu tohoto problému.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, explicitně zařaďte řetězcové datové typy.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Následující příklad ukazuje metodu, která porušuje toto pravidlo a pak ukazuje, jak toto porušení opravit.

[!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]
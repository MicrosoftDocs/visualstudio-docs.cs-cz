---
title: 'CA2101: Určete zařazování pro argumenty řetězce P-Invoke | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 57b7214058baf63ffa5e3ee2c9a982bf411b60e7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652187"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: Určete kódování pro argumenty řetězce volání nespravovaného kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|Kategorie|Microsoft. Globalization|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Člen vyvolání platformy umožňuje částečně důvěryhodných volajících, má řetězcový parametr a explicitně nezařazuje řetězec.

## <a name="rule-description"></a>Popis pravidla
 Pokud převedete z kódování Unicode na ANSI, je možné, že ne všechny znaky Unicode mohou být reprezentovány v konkrétní znakové stránce ANSI. *Mapování podle nejlepšího hlediska* se pokusí vyřešit tento problém nahrazením znaku pro znak, který nelze reprezentovat. Použití této funkce může způsobit potenciální ohrožení zabezpečení, protože nemůžete ovládat vybraný znak. Škodlivý kód by například mohl úmyslně vytvořit řetězec v kódování Unicode, který obsahuje znaky, které se nenašly na konkrétní kódové stránce, které jsou převedeny na speciální znaky systému souborů, jako je například '.. ' nebo '/'. Všimněte si také, že kontroly zabezpečení pro speciální znaky často proběhne před převodem řetězce na ANSI.

 Mapování nejlepšího umístění je výchozí pro nespravovaný převod, WChar na megabajt. Pokud explicitně nezakážete mapování nejlepšího obsahu, může váš kód obsahovat zneužití ohrožení zabezpečení z důvodu tohoto problému.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, explicitně zařaďte řetězcové datové typy.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, která porušuje toto pravidlo a pak ukazuje, jak toto porušení opravit.

 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PinvokeAnsiUnicode/cs/FxCop.Security.PinvokeAnsiUnicode.cs#1)]

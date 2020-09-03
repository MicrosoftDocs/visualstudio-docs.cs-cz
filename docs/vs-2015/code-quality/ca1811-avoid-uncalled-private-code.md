---
title: 'CA1811: Vyhněte se nevolanému soukromému kódu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 223b2ff9aa25ddd94a3c62eb9e641127a1cace4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543816"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: Vyhněte se nevolanému privátnímu kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Kategorie|Microsoft. Performance|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Soukromý nebo interní člen (na úrovni sestavení) nemá volající v sestavení, není vyvolán modulem CLR (Common Language Runtime) a není vyvolán delegátem. Následující členové nejsou kontrolováni tímto pravidlem:

- Explicitní členy rozhraní.

- Statické konstruktory.

- Konstruktory serializace.

- Metody označené <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> nebo <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> .

- Členy, které jsou popsány.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo může hlásit falešně pozitivní hodnoty, pokud se vstupní body, které nejsou aktuálně identifikovány logikou pravidla. Kompilátor může také generovat nevolající kód do sestavení.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odeberte nevolající kód nebo přidejte kód, který ho volá.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Z tohoto pravidla je bezpečné potlačit upozornění.

## <a name="related-rules"></a>Související pravidla
 [CA1812: Vyhněte se nevytvořeným instancím interních tříd](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Zkontrolujte nepoužité parametry](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Odeberte nepoužívané lokální hodnoty](../code-quality/ca1804-remove-unused-locals.md)

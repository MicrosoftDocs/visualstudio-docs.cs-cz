---
title: 'CA1031: Nezachycujte výjimky obecného typu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c1dc1e5ed18ddcd42d42c96f3f853808c58ade48
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236068"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Nezachycujte výjimky obecného typu

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Kategorie|Microsoft.Design|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
<xref:System.Exception?displayProperty=fullName> Obecná výjimka <xref:System.SystemException?displayProperty=fullName> ,jako`catch` je například nebo, zachycena v příkazu nebo obecná klauzule catch, jako jenapříklad.`catch()`

## <a name="rule-description"></a>Popis pravidla
Obecné výjimky by neměly být zachycovány.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, Zachyťte konkrétnější výjimku nebo znovu vyvolejte obecnou výjimku jako poslední příkaz v `catch` bloku.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo. Zachycení obecných typů výjimek může skrývat problémy za běhu od uživatele knihovny a může zjednodušit ladění.

> [!NOTE]
> Počínaje .NET Framework 4 modul CLR (Common Language Runtime) již neposkytuje poškozené výjimky stavu, ke kterým dochází v operačním systému a spravovaném kódu, jako je například narušení přístupu v [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]systému, aby je bylo možné zpracovat spravovaným kódem. Pokud chcete zkompilovat aplikaci v .NET Framework 4 nebo novějších verzích a zachovat zpracování poškozených výjimek stavu, můžete použít <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atribut na metodu, která zpracovává výjimku poškozeného stavu.

## <a name="example"></a>Příklad
Následující příklad ukazuje typ, který porušuje toto pravidlo a typ, který tento `catch` blok správně implementuje.

[!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
[!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
[!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>Související pravidla
[CA2200: Znovu vyvolat pro zachování podrobností zásobníku](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)
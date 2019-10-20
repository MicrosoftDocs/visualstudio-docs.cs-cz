---
title: 'CA1031: Nezachycujte obecné typy výjimek | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2696446ee2b257b78559909c0cba672cded39943
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661899"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Nezachycujte výjimky obecného typu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Kategorie|Microsoft. Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Obecná výjimka, jako je například <xref:System.Exception?displayProperty=fullName> nebo <xref:System.SystemException?displayProperty=fullName>, je zachycena v příkazu `catch`, nebo je použita klauzule General catch, jako je například `catch()`.

## <a name="rule-description"></a>Popis pravidla
 Obecné výjimky by neměly být zachycovány.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, Zachyťte konkrétnější výjimku nebo znovu vyvolejte obecnou výjimku jako poslední příkaz v bloku `catch`.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. Zachycení obecných typů výjimek může skrývat problémy za běhu od uživatele knihovny a může zjednodušit ladění.

> [!NOTE]
> Počínaje [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] modul CLR (Common Language Runtime) již neposkytuje poškozené výjimky stavu, ke kterým dochází v operačním systému a spravovaném kódu, jako je například narušení přístupu v [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)], aby je bylo možné zpracovat spravovaným kódem. Pokud chcete zkompilovat aplikaci v [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] nebo novějších verzích a zachovat zpracování poškozených výjimek stavu, můžete použít atribut <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> na metodu, která zpracovává výjimku poškozeného stavu.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který porušuje toto pravidlo a typ, který správně implementuje blok `catch`.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA2200: Znovu vyvolejte pro zachování podrobností zásobníku](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)

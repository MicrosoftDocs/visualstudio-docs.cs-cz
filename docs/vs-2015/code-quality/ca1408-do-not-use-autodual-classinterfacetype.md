---
title: 'CA1408: Nepoužívejte AutoDual ClassInterfaceType | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3ccd8f9fa201e2cdfabfb7f6354d6df4718c572e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652758"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: Nepoužívejte AutoDual ClassInterfaceType
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Kategorie|Microsoft. interoperabilita|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Viditelný typ objektu součásti modelu COM je označen atributem <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> nastaveným na hodnotu `AutoDual` <xref:System.Runtime.InteropServices.ClassInterfaceType>.

## <a name="rule-description"></a>Popis pravidla
 Typy, které používají duální rozhraní, umožňují klientům navázat se na určité rozložení rozhraní. Změny v budoucí verzi rozložení typu nebo jakéhokoli základního typu přeruší klienty modulu COM, kteří jsou navázáni na toto rozhraní. Ve výchozím nastavení, pokud není zadán atribut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>, je použito pouze odesílající rozhraní.

 Pokud není určeno jinak, všechny veřejné neobecné typy jsou viditelné pro COM; všechny NonPublic a obecné typy jsou neviditelné v modelu COM.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte hodnotu atributu <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> na hodnotu `None` <xref:System.Runtime.InteropServices.ClassInterfaceType> a explicitně definujte rozhraní.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačí upozornění z tohoto pravidla, pokud není jisté, že rozložení typu a jeho základní typy se v budoucí verzi nezmění.

## <a name="example"></a>Příklad
 Následující příklad ukazuje třídu, která porušuje pravidlo a opětovnou deklaraci třídy pro použití explicitního rozhraní.

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/cs/FxCop.Interoperability.AutoDual.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/vb/FxCop.Interoperability.AutoDual.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1403: Typy automatického rozložení by neměly být viditelné modelu COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412: Označte rozhraní ComSource jako IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Viz také
 [Představujeme rozhraní třídy](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [opravňující typy .NET pro](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) spolupráci [s nespravovaným kódem](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)

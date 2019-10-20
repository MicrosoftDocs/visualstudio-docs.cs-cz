---
title: 'CA1412: označte ComSource rozhraní jako IDispatch | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 86dc7042a48faa200ef9c360829b1756bc261ab0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652730"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: Označte rozhraní ComSource jako IDispatch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Kategorie|Microsoft. interoperabilita|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Typ je označen atributem <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> a alespoň jedno zadané rozhraní není označeno atributem <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> nastaveným na hodnotu `InterfaceIsDispatch`.

## <a name="rule-description"></a>Popis pravidla
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> slouží k identifikaci rozhraní události, které třída zveřejňuje klientům modelu COM (Component Object Model). Tato rozhraní musí být vystavena jako `InterfaceIsIDispatch` a povolit tak Visual Basic 6 klientů modelu COM pro příjem oznámení události. Ve výchozím nastavení, pokud rozhraní není označeno atributem <xref:System.Runtime.InteropServices.InterfaceTypeAttribute>, je vystaveno jako duální rozhraní.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte nebo upravte atribut <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> tak, aby byla jeho hodnota nastavena na InterfaceIsIDispatch pro všechna rozhraní, která jsou zadána s atributem <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje třídu, kde jedno z rozhraní je v rozporu s pravidlem.

 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/cs/FxCop.Interoperability.MarkIDispatch.cs#1)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/vb/FxCop.Interoperability.MarkIDispatch.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1408: Nepoužívejte AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Viz také
 [Postupy: vyvolávání událostí zpracovávaných v rámci jímky modelu COM, které](https://msdn.microsoft.com/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd) [spolupracuje s nespravovaným kódem](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)

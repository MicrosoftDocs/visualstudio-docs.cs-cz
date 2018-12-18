---
title: 'CA1816: Volání uvolňování paměti. SuppressFinalize správně | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d859f8fe38d4b6efecb83b117f35cbf483467b6f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913875"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: Volejte správně GC.SuppressFinalize
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Kategorie|Společnosti Microsoft. Použití|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina

-   Metoda, která je implementací <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> nevolá <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

-   Metoda, která není implementací <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> volání <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

-   Volá metodu <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> a předává něco jiného (Me v jazyce Visual Basic).

## <a name="rule-description"></a>Popis pravidla
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> Metoda umožňuje uživatelům uvolnění prostředků kdykoli před objektu poté jsou dostupné pro uvolnění paměti. Pokud <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> metoda je volána, uvolnění prostředků objektu. Díky tomu finalizace zbytečné. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> by měly volat <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> tak systému uvolňování paměti volat finalizační metodu objektu.

 Chcete-li zabránit odvozené typy s finalizační metody by bylo nutné znovu implementovat [System.IDisposable] (<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->) a pro její zavolání, měla by volat stále nezapečetěné typy bez finalizačních metod <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla:

 Pokud metoda je implementací <xref:System.IDisposable.Dispose%2A>, přidejte volání do <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 Pokud metoda není implementace <xref:System.IDisposable.Dispose%2A>, buď odeberte volání <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> nebo ji přesunout do tohoto typu <xref:System.IDisposable.Dispose%2A> implementace.

 Změna všechna volání <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> předat (Me v jazyce Visual Basic).

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Pouze potlačit upozornění tohoto pravidla, pokud jsou deliberating pomocí <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> řídit dobu života jiné objekty. Nepotlačujte upozornění tohoto pravidla, pokud implementace <xref:System.IDisposable.Dispose%2A> nevolá <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>. V takovém případě služeb při selhání pro potlačení dokončení snižuje výkon a poskytují žádné výhody.

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, která nesprávně volání <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>Příklad
 Následující příklad ukazuje metodu, která správně volá <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA2215: Metody Dispose by měly volat uvolnění třídy Base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216: Uvolnitelné typy by měly deklarovat finalizační metodu](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Viz také
 [Vzor pro metodu Dispose](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)




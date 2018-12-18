---
title: 'CA1001: Typy, které vlastní uvolnitelné pole by měly být uvolnitelné | Dokumentace Microsoftu'
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
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a4bde7f20d1e7c93aec7a4a1a3abf44c21659b6e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176446"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Typy, které vlastní uvolnitelné pole by měly být uvolnitelné
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|  
|CheckId|CA1001|  
|Kategorie|Microsoft.Design|  
|Narušující změna|Bez konce – Pokud typ není viditelný mimo sestavení.<br /><br /> Rozdělení – typ je viditelný mimo sestavení.|  
  
## <a name="cause"></a>příčina  
 Třída deklaruje a implementuje pole instance, která je <xref:System.IDisposable?displayProperty=fullName> typ a třída neimplementuje <xref:System.IDisposable>.  
  
## <a name="rule-description"></a>Popis pravidla  
 Třída implementuje <xref:System.IDisposable> rozhraní k uvolnění nespravovaných prostředků, které vlastní. Pole instance, která je <xref:System.IDisposable> označuje, že pole vlastní nespravovaný zdroj. Třída, která deklaruje <xref:System.IDisposable> pole nepřímo vlastní nespravovaný zdroj a měla by implementovat <xref:System.IDisposable> rozhraní. Pokud třída není přímo vlastníkem jakýchkoliv nespravovaných prostředků, neměly by implementovat finalizační metodu.  
  
## <a name="how-to-fix-violations"></a>Jak vyřešit porušení  
 Chcete-li opravit porušení tohoto pravidla, implementovat <xref:System.IDisposable> z a <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> volání metody <xref:System.IDisposable.Dispose%2A> metoda pole.  
  
## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění  
 Nepotlačujte upozornění na toto pravidlo.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje třídu, která porušuje pravidlo a třídy, která splňuje pravidlo implementací <xref:System.IDisposable>. Třída neimplementuje finalizační metodu, protože třída není přímo vlastníkem jakýchkoliv nespravovaných prostředků.  
  
 [!code-csharp[FxCop.Design.DisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/cs/FxCop.Design.DisposableFields.cs#1)]
 [!code-vb[FxCop.Design.DisposableFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/vb/FxCop.Design.DisposableFields.vb#1)]  
  
## <a name="related-rules"></a>Související pravidla  
 [CA2213: Uvolnitelné pole by mělo být uvolněno](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2216: Uvolnitelné typy by měly deklarovat finalizační metodu](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA2215: Metody Dispose by měly volat uvolnění třídy Base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA1049: Typy, které vlastní nativní prostředky by měly být uvolnitelné](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)


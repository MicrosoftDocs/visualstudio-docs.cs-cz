---
title: 'CA2215: metody Dispose by měly volat Dispose základní třídy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4197c2faaf4aa23db930a9019538592326a84116
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534378"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Metody Dispose by měly volat uvolnění základní třídy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Typ, který implementuje <xref:System.IDisposable?displayProperty=fullName> dědí z typu, který také implementuje <xref:System.IDisposable> . <xref:System.IDisposable.Dispose%2A>Metoda dědění typu nevolá <xref:System.IDisposable.Dispose%2A> metodu nadřazeného typu.

## <a name="rule-description"></a>Popis pravidla
 Pokud typ dědí z typu na jedno použití, musí volat <xref:System.IDisposable.Dispose%2A> metodu základního typu v rámci své vlastní <xref:System.IDisposable.Dispose%2A> metody. Volání metody Dispose základní typ zajistí, že budou uvolněny všechny prostředky vytvořené základním typem.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zavolejte `base` .<xref:System.IDisposable.Dispose%2A> v <xref:System.IDisposable.Dispose%2A> metodě.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 V případě volání metody je bezpečné potlačit upozornění od tohoto pravidla `base` .<xref:System.IDisposable.Dispose%2A> nastane na hlubší úrovni volání než kontroly pravidla.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ `TypeA` , který implementuje <xref:System.IDisposable> .

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ `TypeB` , který dědí z typu `TypeA` a správně volá jeho <xref:System.IDisposable.Dispose%2A> metodu.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Viz také
 <xref:System.IDisposable?displayProperty=fullName>[Vzor Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)

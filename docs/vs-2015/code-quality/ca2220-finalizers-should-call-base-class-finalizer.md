---
title: 'CA2220: finalizační metody by měly volat finalizační metodu základní třídy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1a4538c66d351956da8168d4f84c1895190ab453
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663580"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Finalizační metody by měly volat finalizační metodu třídy Base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina
 Typ, který Přepisuje <xref:System.Object.Finalize%2A?displayProperty=fullName>, nevolá metodu <xref:System.Object.Finalize%2A> v její základní třídě.

## <a name="rule-description"></a>Popis pravidla
 Finalizační metoda musí být šířena přes hierarchii dědičnosti. Aby bylo zajištěno, typy musí volat svou základní třídu <xref:System.Object.Finalize%2A> metody z vlastní <xref:System.Object.Finalize%2A> metody. C# Kompilátor automaticky přidá volání k finalizační metodě základní třídy.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zavolejte metodu <xref:System.Object.Finalize%2A> základního typu z vaší metody <xref:System.Object.Finalize%2A>.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. Některé kompilátory, které cílí na modul CLR (Common Language Runtime), vkládají volání finalizační metody základního typu do jazyka MSIL (Microsoft Intermediate Language). Pokud je oznámeno upozornění z tohoto pravidla, kompilátor nevloží volání a je nutné jej přidat do kódu.

## <a name="example"></a>Příklad
 Následující Visual Basic příklad ukazuje typ `TypeB`, který správně volá metodu <xref:System.Object.Finalize%2A> ve své základní třídě.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Viz také
 [Vzor pro metodu Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)

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
ms.openlocfilehash: 5d9139314d52c4c50de84a45f227e6df5715bf02
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540657"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Finalizační metody by měly volat finalizační metodu základní třídy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Typ, který Přepisuje, <xref:System.Object.Finalize%2A?displayProperty=fullName> nevolá <xref:System.Object.Finalize%2A> metodu v její základní třídě.

## <a name="rule-description"></a>Popis pravidla
 Finalizační metoda musí být šířena přes hierarchii dědičnosti. Aby bylo zajištěno, typy musí volat svou metodu základní třídy <xref:System.Object.Finalize%2A> v rámci své vlastní <xref:System.Object.Finalize%2A> metody. Kompilátor jazyka C# přidá volání finalizační metody základní třídy automaticky.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zavolejte metodu základního typu <xref:System.Object.Finalize%2A> z vaší <xref:System.Object.Finalize%2A> metody.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. Některé kompilátory, které cílí na modul CLR (Common Language Runtime), vkládají volání finalizační metody základního typu do jazyka MSIL (Microsoft Intermediate Language). Pokud je oznámeno upozornění z tohoto pravidla, kompilátor nevloží volání a je nutné jej přidat do kódu.

## <a name="example"></a>Příklad
 Následující příklad Visual Basic ukazuje typ `TypeB` , který správně volá <xref:System.Object.Finalize%2A> metodu v její základní třídě.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Viz také
 [Vzor pro metodu Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)

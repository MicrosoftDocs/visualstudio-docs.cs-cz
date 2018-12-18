---
title: 'CA2220: Finalizační metody by měly volat finalizační metodu třídy Base'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c814324ac21017acf6a0182f7807b0a0878c8aca
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551204"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Finalizační metody by měly volat finalizační metodu třídy Base

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Kategorie|Microsoft.Usage|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina

Typ, který přepíše <xref:System.Object.Finalize%2A?displayProperty=fullName> nevolá <xref:System.Object.Finalize%2A> metoda v její základní třídě.

## <a name="rule-description"></a>Popis pravidla

Finalizační metoda musí být šířena přes hierarchii dědičnosti. Aby toto bylo zajištěno, musí typy zavolat své základní třídy <xref:System.Object.Finalize%2A> metodu z v rámci své vlastní <xref:System.Object.Finalize%2A> metody. Kompilátor jazyka C# automaticky přidá volání finalizační metodu třídy base.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Chcete-li opravit porušení tohoto pravidla, zavolejte základní typ <xref:System.Object.Finalize%2A> metodu z vašeho <xref:System.Object.Finalize%2A> metody.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo. Některé kompilátory, které se zaměřují na modul common language runtime vložit volání do finalizační metodu základního typu do Microsoft intermediate language (MSIL). Pokud upozornění toto pravidlo se použije v hlášení, kompilátor nevkládá volání a je třeba přidat ji do vašeho kódu.

## <a name="example"></a>Příklad

Následující příklad jazyka Visual Basic ukazuje typ `TypeB` , která správně volá <xref:System.Object.Finalize%2A> metoda v její základní třídě.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>Viz také:

- [Vzor pro metodu Dispose](/dotnet/standard/design-guidelines/dispose-pattern)
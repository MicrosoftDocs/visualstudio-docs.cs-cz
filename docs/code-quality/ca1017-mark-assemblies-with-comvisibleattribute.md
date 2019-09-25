---
title: 'CA1017: Označte sestavení pomocí ComVisibleAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 073332738a01cb299b2b185c6fca20131222f981
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236259"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: Označte sestavení pomocí ComVisibleAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|Kategorie|Microsoft.Design|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Pro sestavení není <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> použit atribut.

## <a name="rule-description"></a>Popis pravidla
Atribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> určuje, jak klienti modelu COM přistupují ke spravovanému kódu. Dobrý návrh přikazuje, aby sestavení explicitně uvedla viditelnost modelu COM. Viditelnost modelu COM lze nastavit pro celé sestavení a následně přepsat pro jednotlivé typy a členy typu. Pokud atribut není přítomen, obsah sestavení je viditelný pro klienty modelu COM.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, přidejte atribut do sestavení. Pokud nechcete, aby bylo sestavení viditelné pro klienty modelu COM, použijte atribut a nastavte jeho hodnotu na `false`.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo. Chcete-li, aby bylo sestavení viditelné, použijte atribut a nastavte jeho hodnotu na `true`.

## <a name="example"></a>Příklad
Následující příklad ukazuje sestavení, které má <xref:System.Runtime.InteropServices.ComVisibleAttribute> atribut použit, aby se zabránilo jeho viditelnému klientům modelu COM.

[!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
[!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
[!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]

## <a name="see-also"></a>Viz také:

- [Spolupráce s nespravovaným kódem](/dotnet/framework/interop/index)
- [Kvalifikace typů .NET pro spolupráci](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
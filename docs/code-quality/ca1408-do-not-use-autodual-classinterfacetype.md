---
title: 'CA1408: Nepoužívejte typ AutoDual ClassInterface'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b26d92ca63a94cac7e293a688b1c7b3331586877
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234796"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: Nepoužívejte typ AutoDual ClassInterface

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Kategorie|Microsoft. interoperabilita|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Viditelný typ modelu COM (Component Object Model) je označen <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributem nastaveným `AutoDual` na hodnotu <xref:System.Runtime.InteropServices.ClassInterfaceType>.

## <a name="rule-description"></a>Popis pravidla
Typy, které používají duální rozhraní, umožňují klientům navázat se na určité rozložení rozhraní. Změny v budoucí verzi rozložení typu nebo jakéhokoli základního typu přeruší klienty modulu COM, kteří jsou navázáni na toto rozhraní. Ve výchozím nastavení platí, <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> že pokud atribut není zadán, je použita pouze odesílající rozhraní.

Pokud není určeno jinak, všechny veřejné neobecné typy jsou viditelné pro COM; všechny NonPublic a obecné typy jsou neviditelné v modelu COM.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, změňte hodnotu <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributu `None` na hodnotu <xref:System.Runtime.InteropServices.ClassInterfaceType> a explicitně definujte rozhraní.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Potlačí upozornění z tohoto pravidla, pokud není jisté, že rozložení typu a jeho základní typy se v budoucí verzi nezmění.

## <a name="example"></a>Příklad
Následující příklad ukazuje třídu, která porušuje pravidlo a opětovnou deklaraci třídy pro použití explicitního rozhraní.

[!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
[!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]

## <a name="related-rules"></a>Související pravidla
[CA1403: Typy automatického rozložení by neměly být viditelné modelu COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

[CA1412: Označte rozhraní ComSource jako IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Viz také:

- [Kvalifikace typů .NET pro spolupráci](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Spolupráce s nespravovaným kódem](/dotnet/framework/interop/index)
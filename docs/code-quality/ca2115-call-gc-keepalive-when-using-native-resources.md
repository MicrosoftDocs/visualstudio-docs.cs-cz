---
title: 'CA2115: Volejte GC.KeepAlive při použití nativních prostředků'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: eb6d28e15870907034479e698ba8e7464f4f5159
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232727"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: Volejte GC.KeepAlive při použití nativních prostředků

|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|Kategorie|Microsoft.Security|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Metoda deklarovaná v typu s finalizační metodou odkazuje na <xref:System.IntPtr?displayProperty=fullName> pole nebo <xref:System.UIntPtr?displayProperty=fullName> , ale nevolá <xref:System.GC.KeepAlive%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla

Uvolňování paměti dokončí objekt, pokud na něj nejsou žádné další odkazy ve spravovaném kódu. Nespravované odkazy na objekty nebrání uvolňování paměti. Toto pravidlo zjistí chyby, které mohou nastat, protože nespravovaný prostředek je finalizován v době, kdy je stále používán nespravovaným kódem.

Toto pravidlo předpokládá, <xref:System.IntPtr> že <xref:System.UIntPtr> a pole ukládají ukazatele na nespravované prostředky. Vzhledem k tomu, že účelem finalizační metody je uvolnit nespravované prostředky, pravidlo předpokládá, že finalizační metoda uvolní nespravovaný prostředek, na který odkazuje pole ukazatelů. Toto pravidlo také předpokládá, že metoda odkazuje na pole ukazatele na předání nespravovaného prostředku do nespravovaného kódu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, přidejte <xref:System.GC.KeepAlive%2A> volání do metody a předejte aktuální instanci (`this` v C# a C++) jako argument. Umístěte volání za poslední řádek kódu, kde musí být objekt chráněn z uvolňování paměti. Ihned po volání na <xref:System.GC.KeepAlive%2A>je objekt znovu považován za připravený pro uvolňování paměti za předpokladu, že na něj nejsou žádné spravované odkazy.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Toto pravidlo vytváří některé předpoklady, které mohou vést k falešně pozitivním hodnotám. Upozornění můžete v tomto pravidle bezpečně potlačit, pokud:

- Finalizační metoda neuvolní obsah <xref:System.IntPtr> pole nebo <xref:System.UIntPtr> odkazované metodou.

- Metoda nepředá <xref:System.IntPtr> pole nebo <xref:System.UIntPtr> do nespravovaného kódu.

Pečlivě zkontrolujte další zprávy, než je vyloučíte. Toto pravidlo detekuje chyby, které je obtížné rekládat a ladit.

## <a name="example"></a>Příklad

V následujícím příkladu `BadMethod` nezahrnuje `GC.KeepAlive` volání a proto porušuje pravidlo. `GoodMethod`obsahuje opravený kód.

> [!NOTE]
> V tomto příkladu je to pseudo code. I když se kód zkompiluje a spustí, upozornění se neaktivuje, protože nespravovaný prostředek není vytvořen nebo je uvolněn.

[!code-csharp[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]

## <a name="see-also"></a>Viz také:

- <xref:System.GC.KeepAlive%2A?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- [Vzor pro metodu Dispose](/dotnet/standard/design-guidelines/dispose-pattern)
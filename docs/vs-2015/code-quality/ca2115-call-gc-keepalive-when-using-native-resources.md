---
title: 'CA2115: volání GC. Udržení naživu při použití nativních prostředků | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c668172ca318000068fb4e90f4848e456c32208d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543621"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: Volejte GC.KeepAlive při použití nativních prostředků
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|Kategorie|Microsoft.Security|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Metoda deklarovaná v typu s finalizační metodou odkazuje na <xref:System.IntPtr?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName> pole nebo, ale nevolá <xref:System.GC.KeepAlive%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Popis pravidla
 Uvolňování paměti dokončí objekt, pokud na něj nejsou žádné další odkazy ve spravovaném kódu. Nespravované odkazy na objekty nebrání uvolňování paměti. Toto pravidlo zjistí chyby, které mohou nastat, protože nespravovaný prostředek je finalizován v době, kdy je stále používán nespravovaným kódem.

 Toto pravidlo předpokládá, že <xref:System.IntPtr> a <xref:System.UIntPtr> pole ukládají ukazatele na nespravované prostředky. Vzhledem k tomu, že účelem finalizační metody je uvolnit nespravované prostředky, pravidlo předpokládá, že finalizační metoda uvolní nespravovaný prostředek, na který odkazuje pole ukazatelů. Toto pravidlo také předpokládá, že metoda odkazuje na pole ukazatele na předání nespravovaného prostředku do nespravovaného kódu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte volání do <xref:System.GC.KeepAlive%2A> metody a předejte aktuální instanci ( `this` v jazyce C# a C++) jako argument. Umístěte volání za poslední řádek kódu, kde musí být objekt chráněn z uvolňování paměti. Ihned po volání na je <xref:System.GC.KeepAlive%2A> objekt znovu považován za připravený pro uvolňování paměti za předpokladu, že na něj nejsou žádné spravované odkazy.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Toto pravidlo vytváří některé předpoklady, které mohou vést k falešně pozitivním hodnotám. Upozornění můžete v tomto pravidle bezpečně potlačit, pokud:

- Finalizační metoda neuvolní obsah <xref:System.IntPtr> <xref:System.UIntPtr> pole nebo odkazované metodou.

- Metoda nepředá <xref:System.IntPtr> <xref:System.UIntPtr> pole nebo do nespravovaného kódu.

  Pečlivě zkontrolujte další zprávy, než je vyloučíte. Toto pravidlo detekuje chyby, které je obtížné rekládat a ladit.

## <a name="example"></a>Příklad
 V následujícím příkladu `BadMethod` nezahrnuje volání `GC.KeepAlive` a proto porušuje pravidlo. `GoodMethod`obsahuje opravený kód.

> [!NOTE]
> Tento příklad je pseudo kód, i když se kód zkompiluje a spustí, upozornění není aktivováno, protože nespravovaný prostředek není vytvořen nebo je uvolněn.

 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.IntptrAndFinalize/cs/FxCop.Security.IntptrAndFinalize.cs#1)]

## <a name="see-also"></a>Viz také
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 [Vzor pro metodu Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)

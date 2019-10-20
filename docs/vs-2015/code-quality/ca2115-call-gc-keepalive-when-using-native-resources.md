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
ms.openlocfilehash: e0aa10cc453919a2a79ee6d3d46db95c19d8756e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658702"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: Volejte GC.KeepAlive při použití nativních zdrojů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|Kategorie|Microsoft.Security|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina
 Metoda deklarovaná v typu s finalizační metodou odkazuje na <xref:System.IntPtr?displayProperty=fullName> nebo <xref:System.UIntPtr?displayProperty=fullName> pole, ale nevolá <xref:System.GC.KeepAlive%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla
 Uvolňování paměti dokončí objekt, pokud na něj nejsou žádné další odkazy ve spravovaném kódu. Nespravované odkazy na objekty nebrání uvolňování paměti. Toto pravidlo zjistí chyby, které mohou nastat, protože nespravovaný prostředek je finalizován v době, kdy je stále používán nespravovaným kódem.

 Toto pravidlo předpokládá, že pole <xref:System.IntPtr> a <xref:System.UIntPtr> ukládají ukazatele na nespravované prostředky. Vzhledem k tomu, že účelem finalizační metody je uvolnit nespravované prostředky, pravidlo předpokládá, že finalizační metoda uvolní nespravovaný prostředek, na který odkazuje pole ukazatelů. Toto pravidlo také předpokládá, že metoda odkazuje na pole ukazatele na předání nespravovaného prostředku do nespravovaného kódu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte do metody volání <xref:System.GC.KeepAlive%2A> a předejte aktuální instanci (`this` v C# a C++) jako argument. Umístěte volání za poslední řádek kódu, kde musí být objekt chráněn z uvolňování paměti. Ihned po volání <xref:System.GC.KeepAlive%2A> je objekt znovu považován za připravený pro uvolňování paměti za předpokladu, že na něj nejsou žádné spravované odkazy.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Toto pravidlo vytváří některé předpoklady, které mohou vést k falešně pozitivním hodnotám. Upozornění můžete v tomto pravidle bezpečně potlačit, pokud:

- Finalizační metoda neuvolní obsah pole <xref:System.IntPtr> nebo <xref:System.UIntPtr>, na které odkazuje metoda.

- Metoda nepředá pole <xref:System.IntPtr> nebo <xref:System.UIntPtr> do nespravovaného kódu.

  Pečlivě zkontrolujte další zprávy, než je vyloučíte. Toto pravidlo detekuje chyby, které je obtížné rekládat a ladit.

## <a name="example"></a>Příklad
 V následujícím příkladu `BadMethod` neobsahuje volání `GC.KeepAlive`, a proto porušuje pravidlo. `GoodMethod` obsahuje opravený kód.

> [!NOTE]
> Tento příklad je pseudo kód, i když se kód zkompiluje a spustí, upozornění není aktivováno, protože nespravovaný prostředek není vytvořen nebo je uvolněn.

 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.IntptrAndFinalize/cs/FxCop.Security.IntptrAndFinalize.cs#1)]

## <a name="see-also"></a>Viz také
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName><xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 [Vzor pro metodu Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)

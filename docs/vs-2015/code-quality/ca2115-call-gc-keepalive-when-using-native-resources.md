---
title: 'CA2115: Volejte uvolňování paměti. KeepAlive při použití nativních zdrojů | Dokumentace Microsoftu'
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
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e8f45b188945febcd3c81fc4be6a9427d8fe94ba
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948743"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: Volejte GC.KeepAlive při použití nativních zdrojů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|Kategorie|Microsoft.Security|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina
 Metoda deklarovaného v typu s finalizační metoda odkazuje <xref:System.IntPtr?displayProperty=fullName> nebo <xref:System.UIntPtr?displayProperty=fullName> pole, ale nevolá <xref:System.GC.KeepAlive%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla
 Uvolňování paměti dokončí objektu, pokud neexistují žádné další odkazy na ni ve spravovaném kódu. Nespravované odkazy na objekty nebrání uvolňování paměti. Toto pravidlo zjistí chyby, které mohou nastat, protože nespravovaný prostředek je finalizován v době, kdy je stále používán nespravovaným kódem.

 Toto pravidlo předpokládá, že <xref:System.IntPtr> a <xref:System.UIntPtr> ukládání pole ukazatelů na nespravované prostředky. Protože účel finalizační metodu pro uvolnění nespravovaných prostředků, pravidlo předpokládá, že finalizační metoda uvolní nespravovaný prostředek, který ukazuje ukazatel pole. Toto pravidlo předpokládá také, že metoda odkazuje na pole ukazatel k předání tohoto nespravovaného prostředku do nespravovaného kódu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte volání <xref:System.GC.KeepAlive%2A> metody, předejte aktuální instanci (`this` v C# a C++) jako argument. Umístěte volání za posledním řádkem kódu, kde musí být chráněné objekt z kolekce uvolnění paměti. Ihned po volání <xref:System.GC.KeepAlive%2A>, objekt je znovu považovat za připravené pro uvolnění paměti za předpokladu, že neexistují žádné spravované odkazy na ni.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Toto pravidlo do určité míry vyhodnotit, které můžou vést k počet falešně pozitivních výsledků. Můžete bezpečně potlačit upozornění tohoto pravidla, pokud:

- Finalizační metoda neuvolní obsah <xref:System.IntPtr> nebo <xref:System.UIntPtr> pole odkazuje metodu.

- Metoda nepředává <xref:System.IntPtr> nebo <xref:System.UIntPtr> pole do nespravovaného kódu.

  Pečlivě si prostudujte ostatní zprávy před jejich vyloučení. Toto pravidlo zjistí chyby, které je obtížné reprodukovat a ladění.

## <a name="example"></a>Příklad
 V následujícím příkladu `BadMethod` nezahrnuje volání `GC.KeepAlive` a proto porušuje pravidlo. `GoodMethod` obsahuje opraveným kódem.

> [!NOTE]
>  V tomto příkladu je pseudo kód, i když kód zkompiluje a spustí, upozornění není aktivováno, protože nespravovaný prostředek není vytvoření nebo uvolnění.

 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.IntptrAndFinalize/cs/FxCop.Security.IntptrAndFinalize.cs#1)]

## <a name="see-also"></a>Viz také
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName><xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 [Vzor pro metodu Dispose](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)




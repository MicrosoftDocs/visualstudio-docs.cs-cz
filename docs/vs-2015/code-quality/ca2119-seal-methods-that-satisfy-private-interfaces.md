---
title: 'CA2119: metody zapečetit, které odpovídají privátním rozhraním | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0afa6950a6ad876cdcfdcc1a56dd143422b9d44f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544349"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: Zapečeťte metody, které vyhovují privátním rozhraním
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Dědičný veřejný typ poskytuje implementaci přepsatelné metody `internal` `Friend` rozhraní (v Visual Basic).

## <a name="rule-description"></a>Popis pravidla
 Metody rozhraní mají veřejné přístupnost, které nelze změnit implementací typu. Interní rozhraní vytvoří kontrakt, který není určen pro implementaci mimo sestavení, které definuje rozhraní. Veřejný typ, který implementuje metodu interního rozhraní pomocí `virtual` `Overridable` modifikátoru (in Visual Basic), umožňuje metodu přepsat odvozeným typem, který je mimo sestavení. Pokud druhý typ v definičním sestavení volá metodu a očekává pouze interní kontrakt, chování může být ohroženo, když místo toho je provedena přepsaná metoda v externím sestavení. Tím se vytvoří chyba zabezpečení.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zabráníte přepsání metody mimo sestavení pomocí jedné z následujících akcí:

- Proveďte deklaraci typu `sealed` ( `NotInheritable` v Visual Basic).

- Změňte přístupnost deklarace typu na `internal` ( `Friend` v Visual Basic).

- Odebere všechny veřejné konstruktory z deklarující typ.

- Implementujte metodu bez použití `virtual` modifikátoru.

- Explicitně Implementujte metodu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění od tohoto pravidla, pokud po pečlivém přezkoumání neexistují žádné problémy se zabezpečením, které by mohly být zneužity, pokud je metoda přepsána mimo sestavení.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, `BaseImplementation` , který porušuje toto pravidlo.

 [!code-cpp[FxCop.Security.SealMethods1#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cpp/FxCop.Security.SealMethods1.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cs/FxCop.Security.SealMethods1.cs#1)]
 [!code-vb[FxCop.Security.SealMethods1#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/vb/FxCop.Security.SealMethods1.vb#1)]

## <a name="example"></a>Příklad
 Následující příklad zneužije implementaci virtuální metody předchozího příkladu.

 [!code-cpp[FxCop.Security.SealMethods2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cpp/FxCop.Security.SealMethods2.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cs/FxCop.Security.SealMethods2.cs#1)]
 [!code-vb[FxCop.Security.SealMethods2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/vb/FxCop.Security.SealMethods2.vb#1)]

## <a name="see-also"></a>Viz také
 [Interfaces](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37) [Rozhraní](https://msdn.microsoft.com/library/61b06674-12c9-430b-be68-cc67ecee1f5b) rozhraní

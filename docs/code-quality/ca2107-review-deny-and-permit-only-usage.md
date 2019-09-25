---
title: 'CA2107: Zkontrolujte použití čistého odepření a povolení'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fdb2bab3231613772b1eda1895d925f8dd40ee93
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232846"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Zkontrolujte použití čistého odepření a povolení

|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Kategorie|Microsoft.Security|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Metoda obsahuje kontrolu zabezpečení, která určuje akci zabezpečení PermitOnly nebo Deny.

## <a name="rule-description"></a>Popis pravidla

Akce <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> zabezpečení by se měla používat jenom pro ty, kteří mají pokročilé znalosti zabezpečení .NET. Kód používající tyto bezpečnostní akce by měl být podroben revizi zabezpečení.

Deny změní výchozí chování procházení zásobníku, ke kterému dochází v reakci na požadavek zabezpečení. Umožňuje zadat oprávnění, která nesmí být udělena po dobu trvání metody odepření, bez ohledu na skutečná oprávnění volajícího v zásobníku volání. Pokud procházení zásobníku detekuje metodu, která je zabezpečená metodou Deny, a pokud je požadované oprávnění zahrnuté do odepřených oprávnění, procházení zásobníku se nepovede. PermitOnly také mění výchozí chování procházení zásobníku. Umožňuje kódu určit pouze ta oprávnění, která lze udělit, bez ohledu na oprávnění volajících. Pokud procházení zásobníku detekuje metodu, která je zabezpečena pomocí metody PermitOnly, a pokud požadované oprávnění není zahrnuto v oprávněních, která jsou určena parametrem PermitOnly, procházení zásobníku se nezdařilo.

Kód, který závisí na těchto akcích, by měl být pečlivě vyhodnocován z důvodu slabých chyb zabezpečení z důvodu jejich omezené využitelnosti a jemného chování. Zvažte použití těchto zdrojů:

- [Požadavky na propojení](/dotnet/framework/misc/link-demands) nejsou ovlivněny pomocí metody Deny nebo PermitOnly.

- Pokud se Deny nebo PermitOnly vyskytne ve stejném bloku zásobníku jako poptávka, která způsobuje procházení zásobníku, akce zabezpečení nemají žádný vliv.

- Hodnoty, které se používají k vytvoření oprávnění založeného na cestách, je obvykle možné zadat několika způsoby. Odepření přístupu k jedné z těchto cest neodepře přístup všem formulářům. Pokud je například sdílená složka \\\Server\Share namapovaná na síťovou jednotku X:, abyste odepřeli přístup k souboru ve sdílené složce, musíte zamítnout \\\Server\Share\File, X:\file a všechny další cesty, které přistupují k souboru.

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> Může ukončit procházení zásobníku před dosažením zamítnutí nebo PermitOnly.

- Pokud má zamítnutí nějaký účinek, konkrétně v případě, že volající má oprávnění, které je blokováno odepřením, volající má přímý přístup k chráněnému prostředku a obcházení zamítnutí. Podobně pokud volající nemá oprávnění Odepřít, procházení zásobníku selže bez odmítnutí.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Jakékoli použití těchto akcí zabezpečení způsobí porušení. Chcete-li opravit porušení, nepoužívejte tyto akce zabezpečení.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Potlačí upozornění od tohoto pravidla až po dokončení kontroly zabezpečení.

## <a name="example-1"></a>Příklad 1

Následující příklad demonstruje některá omezení typu Deny. Knihovna obsahuje třídu, která má dvě metody, které jsou identické s výjimkou požadavků zabezpečení, které je chrání.

[!code-csharp[FxCop.Security.PermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]

## <a name="example-2"></a>Příklad 2

Následující aplikace ukazuje účinky odmítnutí na zabezpečené metody z knihovny.

[!code-csharp[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_2.cs)]

Tento příklad vytvoří následující výstup:

```txt
Demand: Caller's Deny has no effect on Demand with the asserted permission.
LinkDemand: Caller's Deny has no effect on LinkDemand with the asserted permission.
LinkDemand: Caller's Deny has no effect with LinkDemand-protected code.
LinkDemand: This Deny has no effect with LinkDemand-protected code.
```

## <a name="see-also"></a>Viz také:

- <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>
- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
- <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
- [Pokyny pro zabezpečené kódování](/dotnet/standard/security/secure-coding-guidelines)
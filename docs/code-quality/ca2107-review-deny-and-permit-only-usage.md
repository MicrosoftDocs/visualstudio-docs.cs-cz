---
title: 'CA2107: Revize použití operací odepřít a povolit pouze'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4324805c90c3a0f1b8dbfddcdfe277c5c8a2fd05
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49868037"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Revize použití operací odepřít a povolit pouze

|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Metoda obsahuje kontrolu zabezpečení, která určuje akce zabezpečení PermitOnly nebo odepřít.

## <a name="rule-description"></a>Popis pravidla
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> Akce zabezpečení by měly být používány pouze těmi, kdo mají pokročilé znalosti o zabezpečení rozhraní .NET Framework. Kód používající tyto bezpečnostní akce by měl být podroben revizi zabezpečení.

 Odepřít mění výchozí chování procházení zásobníku, ke které dochází v reakci na požadavek zabezpečení. To vám umožní určit oprávnění, která nesmí být po dobu trvání metodu zamítnutí bez ohledu na skutečnou oprávnění volajících v zásobníku volání. Pokud procházení zásobníku zjistí metodu, která je zabezpečena pomocí Odepřít a pokud požadované oprávnění je součástí odepření oprávnění, procházení zásobníku selže. PermitOnly také mění výchozí chování procházení zásobníku. Je možné zadat pouze oprávnění, která lze udělit, bez ohledu na oprávnění volající kód. Pokud procházení zásobníku zjistí metodu, která je zabezpečena pomocí PermitOnly, a pokud oprávnění, která jsou určena podle PermitOnly není součástí požadované oprávnění, procházení zásobníku selže.

 Kód, který závisí na tyto akce by pečlivě vyhodnotit pro ohrožení zabezpečení z důvodu jejich užitečnost omezené a drobným chování. Vezměte v úvahu následující:

- [Požadavky na propojení](/dotnet/framework/misc/link-demands) nejsou ovlivněny Deny nebo PermitOnly.

- Dojde-li Deny nebo PermitOnly v rámci zásobníku jako požadavek, který způsobí, že procházení zásobníku, akce zabezpečení nemají žádný vliv.

- Hodnoty, které se používají k vytvoření oprávnění na základě cest lze obvykle zadat několika způsoby. Odepření přístupu pro jednu formu cesty není odepření přístupu pro všechny formuláře. Například, pokud sdílenou složku \\\Server\Share je namapována na síťovou jednotku X: k odepření přístupu k souboru ve sdílené složce, musíte zakázat \\\Server\Share\File X:\File a každá cesta, která přistupuje k souboru.

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> Můžete ukončit procházení zásobníku, předtím, než je dosaženo Deny nebo PermitOnly.

- Pokud odepřít nemá žádný vliv, konkrétně, pokud volající nemá oprávnění, které zablokovaly odepřít, volající přístup chráněných prostředků přímo, bez použití odepřít. Podobně pokud volající nemá oprávnění k odepření, procházení zásobníku selže bez odepřít.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Jakékoli použití tyto bezpečnostní akce způsobí, že je porušení pravidel. Chcete-li opravit porušení, nepoužívejte tyto bezpečnostní akce.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění tohoto pravidla, až poté, co dokončíte kontrolu zabezpečení.

## <a name="example-1"></a>Příklad 1
 Následující příklad ukazuje některá omezení Odepřít.

 Následující knihovny obsahuje třídu, která má dvě metody, které jsou stejné až požadavky na zabezpečení, které je chránit.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]

## <a name="example-2"></a>Příklad 2
 Následující aplikace ukazuje účinky odepřít na zabezpečené metody v knihovně.

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
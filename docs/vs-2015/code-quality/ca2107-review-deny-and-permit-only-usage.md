---
title: 'CA2107: revize pouze použití metody Deny a Permit | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7f273ea5f58babf7a0c04f6b0758732d43aab7db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547768"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Zkontrolujte použití čistého odepření a povolení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Metoda obsahuje kontrolu zabezpečení, která určuje akci zabezpečení PermitOnly nebo Deny.

## <a name="rule-description"></a>Popis pravidla
 [Použití metody PermitOnly](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649) a <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> akcí zabezpečení by se měly používat jenom u těch, kteří mají pokročilé znalosti o [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zabezpečení. Kód používající tyto bezpečnostní akce by měl být podroben revizi zabezpečení.

 Deny změní výchozí chování procházení zásobníku, ke kterému dochází v reakci na požadavek zabezpečení. Umožňuje zadat oprávnění, která nesmí být udělena po dobu trvání metody odepření, bez ohledu na skutečná oprávnění volajícího v zásobníku volání. Pokud procházení zásobníku detekuje metodu, která je zabezpečená metodou Deny, a pokud je požadované oprávnění zahrnuté do odepřených oprávnění, procházení zásobníku se nepovede. PermitOnly také mění výchozí chování procházení zásobníku. Umožňuje kódu určit pouze ta oprávnění, která lze udělit, bez ohledu na oprávnění volajících. Pokud procházení zásobníku detekuje metodu, která je zabezpečena pomocí metody PermitOnly, a pokud požadované oprávnění není zahrnuto v oprávněních, která jsou určena parametrem PermitOnly, procházení zásobníku se nezdařilo.

 Kód, který závisí na těchto akcích, by měl být pečlivě vyhodnocován z důvodu slabých chyb zabezpečení z důvodu jejich omezené využitelnosti a jemného chování. Zvažte použití těchto zdrojů:

- [Požadavky na propojení](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) nejsou ovlivněny pomocí metody Deny nebo PermitOnly.

- Pokud se Deny nebo PermitOnly vyskytne ve stejném bloku zásobníku jako poptávka, která způsobuje procházení zásobníku, akce zabezpečení nemají žádný vliv.

- Hodnoty, které se používají k vytvoření oprávnění založeného na cestách, je obvykle možné zadat několika způsoby. Odepření přístupu k jedné z těchto cest neodepře přístup všem formulářům. Pokud je například sdílená složka \\ \Server\Share namapována na síťovou jednotku X:, chcete-li odepřít přístup k souboru ve sdílené složce, je nutné zamítnout \\ \Server\Share\File, X:\file a všechny další cesty, které přistupují k souboru.

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>Může ukončit procházení zásobníku před dosažením zamítnutí nebo PermitOnly.

- Pokud má zamítnutí nějaký účinek, konkrétně v případě, že volající má oprávnění, které je blokováno odepřením, volající má přímý přístup k chráněnému prostředku a obcházení zamítnutí. Podobně pokud volající nemá oprávnění Odepřít, procházení zásobníku selže bez odmítnutí.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Jakékoli použití těchto akcí zabezpečení způsobí porušení. Chcete-li opravit porušení, nepoužívejte tyto akce zabezpečení.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačí upozornění od tohoto pravidla až po dokončení kontroly zabezpečení.

## <a name="example"></a>Příklad
 Následující příklad demonstruje některá omezení typu Deny.

 Následující knihovna obsahuje třídu, která má dvě metody, které jsou identické s výjimkou požadavků zabezpečení, které je chrání.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny/cs/FxCop.Security.PermitAndDeny.cs#1)]

## <a name="example"></a>Příklad
 Následující aplikace ukazuje účinky odmítnutí na zabezpečené metody z knihovny.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestPermitAndDeny/cs/FxCop.Security.TestPermitAndDeny.cs#1)]

 Tento příklad vytvoří následující výstup.

 **Poptávka: zamítnutí volajícího nemá žádný vliv na poptávku s vydaným oprávněním.** 
 **LinkDemand: zamítnutí volajícího nemá žádný vliv na LinkDemand s kontrolním oprávněním.** 
 **LinkDemand: zamítnutí volajícího nemá žádný vliv na kód chráněný LinkDemand.** 
 **LinkDemand: Toto zamítnutí nemá žádný vliv na kód chráněný pomocí LinkDemand.**
## <a name="see-also"></a>Viz také
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
 [Pokyny pro zabezpečené kódování](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [přepisují kontroly zabezpečení](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [pomocí metody PermitOnly](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649)

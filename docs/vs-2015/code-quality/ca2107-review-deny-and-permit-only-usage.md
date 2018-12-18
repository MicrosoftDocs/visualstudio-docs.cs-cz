---
title: 'CA2107: Revize Odepřít a povolit pouze | Dokumentace Microsoftu'
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
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f7a82e6b1acdb8eee1d97dcf6f264ebf66343b58
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851102"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Revize použití operací odepřít a povolit pouze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Metoda obsahuje kontrolu zabezpečení, která určuje akce zabezpečení PermitOnly nebo odepřít.

## <a name="rule-description"></a>Popis pravidla
 [Použití metody PermitOnly](http://msdn.microsoft.com/en-us/8c7bdb7f-882f-45b7-908c-6cbaa1767649) a <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> akce zabezpečení by měly být používány pouze těmi, kdo mají pokročilé znalosti o [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zabezpečení. Kód používající tyto bezpečnostní akce by měl být podroben revizi zabezpečení.

 Odepřít mění výchozí chování procházení zásobníku, ke které dochází v reakci na požadavek zabezpečení. To vám umožní určit oprávnění, která nesmí být po dobu trvání metodu zamítnutí bez ohledu na skutečnou oprávnění volajících v zásobníku volání. Pokud procházení zásobníku zjistí metodu, která je zabezpečena pomocí Odepřít a pokud požadované oprávnění je součástí odepření oprávnění, procházení zásobníku selže. PermitOnly také mění výchozí chování procházení zásobníku. Je možné zadat pouze oprávnění, která lze udělit, bez ohledu na oprávnění volající kód. Pokud procházení zásobníku zjistí metodu, která je zabezpečena pomocí PermitOnly, a pokud oprávnění, která jsou určena podle PermitOnly není součástí požadované oprávnění, procházení zásobníku selže.

 Kód, který závisí na tyto akce by pečlivě vyhodnotit pro ohrožení zabezpečení z důvodu jejich užitečnost omezené a drobným chování. Vezměte v úvahu následující:

-   [Požadavky na propojení](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) nejsou ovlivněny Deny nebo PermitOnly.

-   Dojde-li Deny nebo PermitOnly v rámci zásobníku jako požadavek, který způsobí, že procházení zásobníku, akce zabezpečení nemají žádný vliv.

-   Hodnoty, které se používají k vytvoření oprávnění na základě cest lze obvykle zadat několika způsoby. Odepření přístupu pro jednu formu cesty není odepření přístupu pro všechny formuláře. Například, pokud sdílenou složku \\\Server\Share je namapována na síťovou jednotku X: k odepření přístupu k souboru ve sdílené složce, musíte zakázat \\\Server\Share\File, X:\File a každá cesta, která přistupuje k souboru.

-   <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> Můžete ukončit procházení zásobníku, předtím, než je dosaženo Deny nebo PermitOnly.

-   Pokud odepřít nemá žádný vliv, konkrétně, pokud volající nemá oprávnění, které zablokovaly odepřít, volající přístup chráněných prostředků přímo, bez použití odepřít. Podobně pokud volající nemá oprávnění k odepření, procházení zásobníku selže bez odepřít.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Jakékoli použití tyto bezpečnostní akce způsobí, že je porušení pravidel. Chcete-li opravit porušení, nepoužívejte tyto bezpečnostní akce.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění tohoto pravidla, až poté, co dokončíte kontrolu zabezpečení.

## <a name="example"></a>Příklad
 Následující příklad ukazuje některá omezení Odepřít.

 Následující knihovny obsahuje třídu, která má dvě metody, které jsou stejné až požadavky na zabezpečení, které je chránit.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny/cs/FxCop.Security.PermitAndDeny.cs#1)]

## <a name="example"></a>Příklad
 Následující aplikace ukazuje účinky odepřít na zabezpečené metody v knihovně.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestPermitAndDeny/cs/FxCop.Security.TestPermitAndDeny.cs#1)]

 Tento příklad vytvoří následující výstup.

 **Vyžádání: Odepřít volajícího, jež nemá žádný vliv na vyžádání s potvrzením oprávnění. ** 
 **LinkDemand: odepřít volajícího, jež nemá žádný vliv na LinkDemand s potvrzením oprávnění.** 
 **LinkDemand: odepřít volajícího, jež nemá žádný vliv kódem chráněné LinkDemand.** 
 **LinkDemand: Tento odepřít nemá žádný vliv kódem chráněné LinkDemand.**
## <a name="see-also"></a>Viz také
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName><xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
 [Pokyny pro zabezpečené kódování](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [přepsání kontrol zabezpečení](http://msdn.microsoft.com/en-us/4acdeff5-fc05-41bf-8505-7387cdbfca28) [použití metody PermitOnly](http://msdn.microsoft.com/en-us/8c7bdb7f-882f-45b7-908c-6cbaa1767649)




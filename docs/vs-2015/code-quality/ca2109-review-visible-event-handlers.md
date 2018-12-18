---
title: 'CA2109: Revize viditelných obslužných rutin událostí | Dokumentace Microsoftu'
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
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 328df28441fa5c96fee40baed11a54c3044542b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880374"
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109: Revize viditelných obslužných rutin událostí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|CheckId|CA2109|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Byla zjištěna veřejná nebo chráněná metoda zpracování událostí.

## <a name="rule-description"></a>Popis pravidla
 Externě viditelná metoda zpracování událostí představuje problém zabezpečení, která vyžaduje kontrolu.

 Metody zpracování událostí by neměly být vystaveny, pokud to není nezbytně nutné. Obslužné rutiny události, delegát typu, který vyvolá metodu vystavené lze přidat na libovolnou událost shodují signatury obslužné rutiny a události. Události může potenciálně navýšit tak, že veškerý kód a jsou často vydané kódem vysoce důvěryhodných systému v odpovědi s uživatelskými akcemi, jako je kliknutí na tlačítko. Přidání kontrolu zabezpečení metody zpracování událostí nebrání kód obslužné rutiny události, která volá metodu registrace.

 Požadavek nelze spolehlivě chránit metoda vyvolá obslužnou rutinu události. Pomoc se požadavky na zabezpečení chránit kódu z nedůvěryhodných volajících prozkoumáním volající v zásobníku volání. Kód, který přidá obslužnou rutinu události pro událost se nutně nenachází v zásobníku volání při spuštění metody obslužné rutiny události. Proto zásobník volání může mít pouze vysoce důvěryhodné volající při vyvolání metody obslužné rutiny události. To způsobí, že požadavky metodu obslužné rutiny události úspěšné. Požadované oprávnění může být také, uplatněna při vyvolání metody. Z těchto důvodů riziko není opravit porušení tohoto pravidla lze pouze použit k vyhodnocení po kontrole metody zpracování událostí. Při kontrole kódu, zvažte následující skutečnosti:

-   Obslužnou rutinu události provádět žádné operace, které jsou nebezpečné nebo zneužitelné, jako je například potvrzující oprávnění nebo potlačení oprávnění nespravovaného kódu?

-   Co jsou bezpečnostní hrozby na a z vašeho kódu, protože může probíhat kdykoli bez pouze vysoce důvěryhodné volající v zásobníku?

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zkontrolujte metodu a vyhodnoťte následující:

-   Budete moct nastavit metodu zpracování událostí neveřejné?

-   Můžete přesunout všechny funkce nebezpečné mimo obslužnou rutinu události?

-   Pokud je zavedena požadavku zabezpečení, můžete to provést jiným způsobem?

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačení upozornění tohoto pravidla až po přezkoumání pečlivé ověření zabezpečení, abyste měli jistotu, že váš kód nepředstavuje bezpečnostní hrozbu.

## <a name="example"></a>Příklad
 Následující kód ukazuje metodu zpracování událostí, které mohou být zneužity škodlivý kód.

 [!code-csharp[FxCop.Security.EventSecLib#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.EventSecLib/cs/FxCop.Security.EventSecLib.cs#1)]

## <a name="see-also"></a>Viz také
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName><xref:System.EventArgs?displayProperty=fullName>
 [Požadavky na zabezpečení](http://msdn.microsoft.com/en-us/324c14f8-54ff-494d-9fd1-bfd20962c8ba)




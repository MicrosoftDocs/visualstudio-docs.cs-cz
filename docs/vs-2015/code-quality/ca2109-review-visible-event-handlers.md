---
title: 'CA2109: Kontrola viditelných obslužných rutin událostí | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 38a1b7c00c79c7a2e89ef64598b8c409709561ef
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658707"
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109: Zkontrolujte viditelné obslužné rutiny událostí
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
 Externě viditelná metoda zpracování událostí představuje problémy se zabezpečením, které vyžadují kontrolu.

 Metody zpracování událostí by neměly být vystaveny, pokud to není nezbytně nutné. Obslužná rutina události, typ delegáta, který vyvolá vystavenou metodu, lze přidat k jakékoli události, pokud se shodují signatury obslužné rutiny a události. Události mohou být vyvolány jakýmkoli kódem a často jsou vyvolány vysoce důvěryhodným systémovým kódem v reakci na akce uživatele, jako je například kliknutí na tlačítko. Přidání kontroly zabezpečení do metody zpracování události nebrání kódu v registraci obslužné rutiny události, která vyvolá metodu.

 Poptávka nemůže spolehlivě chránit metodu vyvolanou obslužnou rutinou události. Požadavky na zabezpečení pomůžou chránit kód před nedůvěryhodnými volajícími prozkoumáním volajících v zásobníku volání. Kód, který přidá obslužnou rutinu události do události, není nutně přítomen v zásobníku volání při spuštění metod obslužné rutiny události. Proto zásobník volání může mít pouze vysoce důvěryhodné volající, když je vyvolána metoda obslužné rutiny události. To způsobí, že požadavky provedené metodou obslužné rutiny události budou úspěšné. Vyžádané oprávnění může také být při vyvolání metody uplatněno. Z těchto důvodů může být riziko, že není nutné opravit porušení tohoto pravidla, posouzeno pouze po kontrole metody zpracování událostí. Při revizi kódu Vezměte v úvahu následující problémy:

- Provádí vaše obslužná rutina události nějaké operace, které jsou nebezpečné nebo zneužitelné, jako je například vyhodnocení oprávnění nebo potlačení oprávnění nespravovaného kódu?

- Jaké jsou bezpečnostní hrozby a z vašeho kódu, protože může běžet kdykoli a s pouze vysoce důvěryhodnými volajícími v zásobníku?

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, Projděte si metodu a vyhodnoťte následující:

- Je možné provést neveřejnou metodu zpracování událostí?

- Je možné přesunout ze všech nebezpečných funkcí z obslužné rutiny události?

- Pokud je zajištěna žádost o zabezpečení, je možné ji provést nějakým jiným způsobem?

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačí upozornění od tohoto pravidla až po pečlivém přezkoumání zabezpečení, abyste se ujistili, že váš kód nepředstavuje bezpečnostní riziko.

## <a name="example"></a>Příklad
 Následující kód ukazuje metodu zpracování událostí, která může být zneužita škodlivým kódem.

 [!code-csharp[FxCop.Security.EventSecLib#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.EventSecLib/cs/FxCop.Security.EventSecLib.cs#1)]

## <a name="see-also"></a>Viz také
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName><xref:System.EventArgs?displayProperty=fullName>
 [Požadavky na zabezpečení](https://msdn.microsoft.com/324c14f8-54ff-494d-9fd1-bfd20962c8ba)

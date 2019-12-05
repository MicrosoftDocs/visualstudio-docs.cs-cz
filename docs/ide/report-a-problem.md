---
title: 'Nahlášení problému: stavy a nejčastější dotazy'
description: Poskytuje přehled o nástroji nahlásit problém a obsahuje stavy a definice problémů.
ms.date: 11/15/2018
ms.custom: seodec18
ms.topic: conceptual
author: seaniyer
ms.author: seiyer
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d024e28d696a60a9fc77c290283382dcd0e0ede8
ms.sourcegitcommit: 2148f3fd69569d8ec54fd21a66370932ce610ce4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74853500"
---
# <a name="report-a-problem-states-and-faq"></a>Nahlášení problému: stavy a nejčastější dotazy

Nástroj ohlásit problém umožňuje komunitě vývojářů sady Visual Studio odesílat problémy. Každá z vašich sestav problémů se stává pracovní položkou v našem jádrovém systému, který vám umožní přímo se zapojit do našich produktových týmů a pomoct tak identifikovat a vyřešit ovlivněné problémy. Vaše zpětná vazba odeslaná s bohatými diagnostickými informacemi je důležitá pro zlepšení produktové řady Visual Studio. Opravdu si vybereme čas k nahlášení problémů.

Kromě toho můžete hlasovat o zpětné vazbě jiných členů komunity a věnovat vám tak větší pozornost problému a jejich rychlejšímu řešení.

## <a name="problem-status"></a>Stav problému

Po nahlášení problému se stavem označují, kde se vaše příspěvky nacházejí v životním cyklu. Protože Microsoft Teams provedou vaše názory, nastaví je s odpovídajícím stavem.  Sledovat průběh hlášení o problémech na základě níže uvedených stavů spolu s jejich významem a barevnými indikátory.

![Nový stav pro hlášení problémů na komunitě vývojářů](../ide/media/ProblemStates/New.jpg)

**Novinka** znamená, že chyba nebo problém jsou nově hlášeny, a zatím není provedena žádná akce.

- - -

![Stav pro hlášení problémů na komunitě vývojářů](../ide/media/ProblemStates/Triaged.jpg)

**Třídění** naznačuje, že jsou dokončeny předběžné kroky, jako je moderování, překlad a prvotní kontroly duplicit. Váš lístek byl pro zvážení směrován na příslušný technický tým.

- - -

![Ve stavu zvážení hlášení problémů na komunitě vývojářů](../ide/media/ProblemStates/UnderConsideration.jpg)

**V této části** je uvedeno, že společnost Microsoft zkoumá váš problém s ohledem na dopad na komunitu a podle toho bude upřednostňovat. Pokud není dopad komunity jasný ani významný, budeme dál monitorovat problém v tomto stavu.

- - -

![Stav šetření pro hlášení problémů na komunitě vývojářů](../ide/media/ProblemStates/UnderInvestigation.jpg)

**V rámci šetření** se dozvíte, že technici aktivně vyšetřují váš problém, aby našli řešení.

- - -

![Pro vytváření sestav problémů na komunitě vývojářů potřebujete více informací o stavu](../ide/media/ProblemStates/NeedMoreInfo.jpg)

**Potřebujete další informace o** tom, že od vás potřebujeme další diagnostické informace, abychom mohli pokračovat v šetření.  [Přečtěte si, jak reagovat na nutnost dalších žádostí o informace.](./how-to-report-a-problem-with-visual-studio.md#when-further-information-is-needed-need-more-info)

- - -

![Opraveno – čeká se na stav vydání pro hlášení problémů na komunitě vývojářů.](../ide/media/ProblemStates/FixedPendingRelease.jpg)

**Nevyřešená verze** znamená, že máme opravu problému a bude k dispozici v nadcházející verzi Preview nebo vydání.  Pokud je oprava k dispozici ve verzi Preview, bude problém označen značkou Fixed in, která určuje verzi Preview.

- - -

![Uzavřeno – pevný stav pro hlášení problémů na komunitě vývojářů](../ide/media/ProblemStates/ClosedFixed.jpg)

**Uzavřeno – opraveno** znamená, že jsme vydali opravu problému. Tento problém se také teď označí příznakem "opraveno v:", který určuje verzi vydání.

- - -

![Uzavřeno – duplicitní stav pro hlášení problémů na komunitě vývojářů](../ide/media/ProblemStates/ClosedDuplicate.jpg)

**Uzavřeno – duplicitní** znamená, že váš problém již byl nahlášen prostřednictvím jiné zpětné vazby. Poskytneme vám odkaz, kde můžete sledovat původní zprávu o problému.

- - -

![Stav Uzavřeno – nižší priorita pro hlášení problémů na komunitě vývojářů](../ide/media/ProblemStates/ClosedLowerPriority.jpg)

**Uzavřeno – nižší priorita** Abychom se mohli soustředit na to, co je naše komunita vývojářů nejlepší, nakonfigurujeme problémy s největším dopadem na zákazníky. I když v tuto chvíli nemůžeme vyřešit tento konkrétní problém, je zaručeno, že všechny vaše názory jsou cenné a pomáhají zdokonalit Visual Studio.

- - -

![Uzavřeno – nejedná se o stav chyby pro hlášení problémů na komunitě vývojářů.](../ide/media/ProblemStates/ClosedNotABug.jpg)

**Uzavřeno – není chyba** znamená, že jsme zjistili, že se jedná o aktuální návrh.

- - -

![Uzavřeno – nedostatek informací o stavu pro hlášení problémů na komunitě vývojářů](../ide/media/ProblemStates/ClosedNotEnoughInfo.jpg)

**Uzavřeno –** nedostatek informací indikuje, že nemáme k dispozici dostatek informací, abychom to mohli prozkoumat. Až budete mít k dispozici potřebné informace, budeme rádi znovu považovat zpětnou vazbu.

- - -

![Uzavřeno – jiný stav produktu pro hlášení problémů na komunitě vývojářů](../ide/media/ProblemStates/ClosedOtherProduct.jpg)

**Uzavřeno – jiný produkt** znamená, že jsme zjistili, že váš problém platí pro jiný produkt. Podívejte se na komentář od Microsoftu, pro který externí produkt a všechny související odkazy.

- - -

![Uzavřeno – nebude opravovat stav pro hlášení problémů na komunitě vývojářů](../ide/media/ProblemStates/ClosedWontFix.jpg)

**Uzavřeno – nebude opraveno** znamená, že tento problém nemůžeme provést kvůli faktorům, jako je například nedostatečné zarovnání v oddělení produktu nebo dopad na komunitu. Další přehlednost najdete v komentářích od Microsoftu.  I když nemůžeme vyřešit tento konkrétní problém, je zaručeno, že veškerá vaše zpětná vazba je cenná a pomáhá zdokonalit Visual Studio.

- - -

## <a name="faq"></a>Nejčastější dotazy

### <a name="how-can-i-increase-the-chance-of-my-problem-getting-resolved-quickly"></a>Jak můžu zvýšit pravděpodobnost, že se problém vyřeší rychle?

Doporučujeme, abyste pomocí vyhledávání zajistili, že problém, který chcete ohlásit, už není nahlášený. Pokud najdete existující položku odpovídající vašemu problému, sledujte tento lístek problému a Hlasujte na něj.

Poskytněte všechny informace, které vám pomůžou naši týmy pomáhat s tím, co se setkáváte.  Tyto informace zahrnují nezbytné kroky reprodukci, fragmenty kódu, snímky obrazovky, záznamy reprodukci, soubory protokolů a další artefakty.  Zde je [uveden postup nahlášení problému v aplikaci Visual Studio](./how-to-report-a-problem-with-visual-studio.md).

### <a name="how-is-my-feedback-prioritized"></a>Jak mám prioritu mého názoru?

Od našich zákazníků získáme velký počet cenných problémů. Aby bylo zajištěno, že chceme v naší komunitě vývojářů dodávat nejlepší hodnotu, nastavíme u názoru na zpětnou vazbu, která má nejvyšší dopad na komunitu, prioritní akci.

Pokud se nám nedaří odpovědět osobně na váš názor, nezapomeňte vám, že váš vstup je plně ocení. Zajistěte, aby se všechny vaše názory dostaly do správného týmu.

Skutečně jsme vyhodnotí čas, který investovali do poskytování sady Visual Studio lépe.

### <a name="what-actions-can-i-take-if-im-not-satisfied-with-the-resolution"></a>Jaké akce mohu provést, pokud mi nevyhovuje řešení?

Naši týmy mají nejlepší diagnostikovat a opravovat všechny problémy, ke kterým dochází, ale můžou nastat situace, kdy nebudete plně spokojeni s naším doporučením. Přihlaste se zpět na zpětnou vazbu a dejte nám vědět přesně to, co nejste spokojeni, a my zkusíme, abychom Splníme vaše potřeby.

### <a name="how-will-i-get-notified-of-progress-on-my-feedback"></a>Jak se mi pošle oznámení o pokroku na zpětnou vazbu?

Technické týmy Microsoftu budou s vámi komunikovat pomocí komentářů na základě lístku zpětné vazby a změnou stavu lístku v průběhu provádění. Sledujte e-mailová oznámení, která se odesílají při změně stavu lístku nebo odeslání komentáře.  Četnost oznámení můžete spravovat v nastavení profil a předvolby na webu komunity pro vývojáře.

### <a name="why-cant-i-add-a-problem-for-visual-studio-ide-on-the-developer-community-website"></a>Proč nemůžu přidat problém pro prostředí Visual Studio IDE na webu komunity vývojářů?

Nahlášení problému prostřednictvím sady Visual Studio umožňuje, aby byly diagnostické informace automaticky zahrnuty do sestavy. Jsou to důležité informace, které našim inženýrům poskytují kontext, který potřebuje k plnému pochopení vašeho problému a k tomu, aby je mohl vyřešit.

Při vytváření sestav prostřednictvím sady Visual Studio můžete snadno sdílet Podrobné diagnostické informace, jako jsou například velké soubory protokolů, informace o chybách, snímky obrazovky, záznam reprodukci a další artefakty, které nám pomáhají zajistit rychlejší řešení vyšší kvality.

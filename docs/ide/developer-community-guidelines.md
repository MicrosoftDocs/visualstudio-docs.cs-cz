---
title: Pokyny pro komunitu vývojářů
description: Popisuje pokyny pro práci s Visual Studio Developer Community.
ms.date: 6/30/2020
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 21cf3bd6a0c208a78cd391f93702865e905482e0
ms.sourcegitcommit: 3c6c263a1c0b20f084290ce45295a46027da33b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2021
ms.locfileid: "113756889"
---
# <a name="developer-community-guidelines"></a>Pokyny pro komunitu vývojářů

Vývojářský Community sleduje problémy a návrhy funkcí pro Visual Studio.

## <a name="submitting-problems-and-suggestions"></a>Odesílání problémů a návrhů

Aplikace [Visual Studio Developer Community](https://aka.ms/feedback/suggest?space=8) sleduje problémy a návrhy funkcí pro Visual Studio.

### <a name="before-submitting-an-issue"></a>Před odesláním problému

Vyhledejte svůj problém v Visual Studio Developer Community a ujistěte se, že ještě neexistuje. Pokud zjistíte, že váš problém už existuje, připomínky a hlasujte.

Pokud máte problém s dotazem, zeptejte se komunity [na Stack Overflow](https://stackoverflow.com/questions/tagged/visual-studio?tab=Newest) pomocí značky _visual-studio_. Máme pracovníky zákaznické podpory, kteří tuto značku monitoruje, a pomůže vám zodpovědět otázky.

Pokud nemůžete najít existující problém, který popisuje vaši chybu nebo funkci, pomocí následujících pokynů odešlete problém.

### <a name="writing-a-good-bug-report-or-feature-suggestion"></a>Psaní vhodné zprávy o chybách nebo návrhu funkcí

- Pro každý problém zakažte jenom jeden problém nebo žádost o funkci.

  - Zkombinováním více problémů nebo žádostí o funkce do jednoho problému je pro nás obtížnější diagnostikovat a pro ostatní uživatele je těžší hlasovat pro váš problém.
  - Pokud to není pro stejný vstup, přidejte problém jako komentář k existujícímu problému. Mnoho problémů vypadá podobně, ale má různé příčiny, což nám ztěžuje diagnostiku vašeho problému.

- Čím více informací nám můžete poskytnout, tím jednodušší bude reprodukovat a opravit váš problém.
- Ke každému problému zahr9te následující kroky.

  - Reprodukovatelné kroky (1... 2... 3...) a co jste očekávali oproti tomu, co jste měli.
  - Obrázky, animace nebo odkaz na video Obrázky a animace ilustrují kroky pro _reprodukci, ale nenahrazuje_ je.
  - Podle potřeby můžeme fragment kódu, který demonstruje problém, nebo odkaz na úložiště kódu, snadno stáhnout na náš počítač a problém znovu vytvořit.

- Nezapomeňte provést následující kroky:

  - Vyhledejte a podívejte se, jestli existuje duplicitní. Pokud ano, hlasujte pro stávající problém a podle potřeby připomínky nebo vyjasnění.
  - Po zákazu všech rozšíření problém vytvořte znovu. Pokud zjistíte, že příčinou problému je rozšíření, které jste nainstalovali, zahájte problém s rozšířením.
  - Zjednodušte si kód, který tento problém obchádí, abychom mohli problém lépe izolovat.

I v případě problémů, které obsahují podrobné informace, možná problém nedokážeme reprodukovat a můžeme požádat o další informace.

## <a name="managing-problem-reports"></a>Správa zpráv o problémech

Triaging an issue is a multi-step process that is collaboratively done within the feature team. Triaging obvykle trvá jeden týden, ale může trvat déle. Cílem tohoto procesu je jasně porozumět tomu, co se s vaším problémem stane. Například po rozhodnutí o hodnocení víte, jestli máme v plánu váš problém vyřešit, nebo počkat na další zpětnou vazbu od komunity.

Po nahlášení problému se v stavech uvádí, kde jsou vaše odeslání v jejich životním cyklu. Jak Visual Studio produktové týmy zpětnou vazbu prošestaví, nastaví ji s odpovídajícím stavem. Sledujte průběh hlášení problémů pomocí stavů [problémů a nejčastějších dotazů.](./report-a-problem.yml)

### <a name="prioritizing-which-issues-to-fix"></a>Určení priorit problémů, které se mají vyřešit

Nemůžeme opravit všechny nahlášené problémy. Některé jsou příliš nákladné na opravu, některé můžou způsobit regresi jiných oblastí funkcí a některé můžou mít příliš nízký dopad. Chápeme, že pokud jste si probrali čas na odeslání zprávy o problému, může to být zklamaní. Všichni jsme tam byli, ať už v tomto projektu nebo v jiných projektech, do které jsme přispěli. Pokud byl problém uzavřen a máte pocit, že důvod, který jsme dali, nesplňuje, můžete svůj případ použití objasnit a požádat o opětovné aktivaci problému pro další průchod. V tuto chvíli vás můžeme požádat o další informace.

### <a name="missing-important-information"></a>Chybějící důležité informace

Pokud u problému chybí důležité informace, přiřadíme stav _Potřebuje další_ informace. K problému se okomentuje konkrétní informace, které potřebujeme, a obdržíte e-mailové oznámení. Pokud tyto informace neobdržíte do sedmi dnů, pošleme vám připomenutí. Potom tento lístek zavřeme po 14 dnech nečinnosti.

### <a name="other-product"></a>Jiný produkt

Při hlášení problému se někdy ukáže, že příčinou je jiný produkt, a ne Visual Studio. Může to být jiná související aplikace nebo rozšíření. 

Když k tomu dojde, zavřeme problém a požádáme vás, abyste ho otevřeli u druhého produktu. Tady je několik běžných míst, kde můžete tyto problémy vyřešit:

* [SQL Server](https://feedback.azure.com/forums/908035-sql-server)
* [Visual Studio Podpora předplatného](https://feedback.azure.com/forums/908035-sql-server)
* [Office](https://support.office.com/article/how-do-i-give-feedback-on-microsoft-office-2b102d44-b43f-4dd2-9ff4-23cf144cfb11)
* [Windows](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)

#### <a name="additional-information"></a>Další informace

- [Jak zvýšit pravděpodobnost, že se vyřeší problém s výkonem](./how-to-increase-chances-of-performance-issue-being-fixed.md)
- [Řešení potíží a vytváření protokolů pro MSBuild potíží](./msbuild-logs.md)

## <a name="managing-feature-suggestions"></a>Správa návrhů funkcí

Návrhy funkcí jsou způsob komunikace mezi námi a členy komunity vývojářů. Technicky bychom mohli nechat všechny žádosti o funkce otevřené napořád. Zachováním otevřených problémů by se ale snížil přehled komunity o skutečném stavu funkce. Žádosti o funkce tedy uzavřeme, nebudeme řešit a přiřazovat funkce, které můžeme řešit, k popisku _V rámci_ revize.

Pokud jste navrhli funkci, možná budete zklamaní, že vaši žádost nebudeme řešit. Tomu rozumíme. Všichni jsme tam už byli – v tomto projektu nebo v dalších projektech, do které jsme přispěli. Takže si můžete být jistí, že se nám líbí všechny vaše vstupy. Při zavření nebo přiřazení popisku Pod  kontrolou k vašemu návrhu se nemusíte dotáhnět osobního trestného činu. Pokud si myslíte, že váš návrh funkce si zaslouží zůstat otevřený, vyjasníte si svůj případ použití a kontaktujte nás nebo shromážděte další hlasy.

V našem rozhodovacím procesu se podíváme na následující charakteristiky návrhu funkce:

- Odpovídá obecný směr produktu?
- Můžeme si dovolit ho sestavit a udržovat?
- Je v souladu s naší celkovou [strategií plánu?](/visualstudio/productinfo/vs-roadmap)
- Má podporu komunity, jak je uvedeno hlasy a komentáři?
- Líbí se nám to i s nízkou podporou komunity?

Když na žádnou z těchto otázek nemůžeme odpovědět "ano", zavřeme ji. Tento návrh ale často zůstane otevřený jako _V rámci revize,_ aby získal další zpětnou vazbu od komunity.

Pokud návrh neodpovídá našemu celkovému směru produktu, zavřeme ho jako *Mimo rozsah*. Podobné investice můžeme mít například do jiných členů skupiny Visual Studio produktů. Nebo navrhovaná funkce může být relevantní jenom pro několik lidí, takže rozšíření je pro jeho poskytnutí lépe vhodné.

Sledujte průběh návrhu funkce s odkazem na [stavy návrhů a nejčastější dotazy.](./report-a-problem.yml)

## <a name="discussion-etiquette"></a>Etikta diskuze

Aby byla konverzace jasná a transparentní, omezte diskuzi na angličtinu a udržujte vše, co je relevantní pro tento problém. Buďte ohleduplní k ostatním a vždy se snažte být ohleduplní a profesionální.

Další informace najdete na webu [Microsoft Community etický kodex.](https://answers.microsoft.com/en-us/page/codeofconduct)

Jakékoli porušení pravidel diskuze může vést k odebrání komentáře a nakonec k zákazu uživatele.

## <a name="data-privacy"></a>Ochrana osobních údajů

Komentáře a odpovědi jsou veřejně viditelné, ale všechny připojené soubory se soukromě sdílí pouze s Microsoftem. Tato viditelnost je výhodná, protože umožňuje celé komunitě zobrazit problémy a řešení nalezené jinými uživateli. Pokud vás zajímá ochrana osobních údajů vašich dat nebo identity, máte k dispozici možnosti. Přečtěte si další informace [o ochraně Community dat pro vývojáře.](./developer-community-privacy.md)

## <a name="next-steps"></a>Další kroky

Přejděte na web Visual Studio [Developer Community hlášení](https://aka.ms/feedback/suggest?space=8) problémů, navrhovat funkce nebo procházet existující lístky. Užijte si ji!

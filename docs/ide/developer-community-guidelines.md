---
title: Pokyny pro komunitu vývojářů
description: Popisuje pokyny pro práci s komunitou vývojářů sady Visual Studio.
ms.date: 6/30/2020
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb7f821a7b815b29c9f85b6ab0686edb0292866d
ms.sourcegitcommit: 4d5cd0b9de7a87efb69f17b02c2331b749e6ec8d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/08/2020
ms.locfileid: "86137563"
---
# <a name="developer-community-guidelines"></a>Pokyny pro komunitu vývojářů

Komunita vývojářů sleduje problémy a návrhy funkcí pro Visual Studio.

## <a name="submitting-problems-and-suggestions"></a>Odesílání problémů a návrhů

[Komunita vývojářů sady Visual Studio](https://developercommunity.visualstudio.com/) sleduje problémy a návrhy funkcí pro Visual Studio.

### <a name="before-submitting-an-issue"></a>Před odesláním problému

Vyhledejte svůj problém v komunitě vývojářů sady Visual Studio, abyste zajistili, že ještě neexistuje. Pokud zjistíte, že váš problém již existuje, udělejte si příslušné komentáře a hlaste se.

Pokud se jedná o otázku, zeptejte se komunity na [Stack Overflow](https://stackoverflow.com/questions/tagged/visual-studio?tab=Newest) pomocí značky _Visual-Studio_. Pracovník podpory zákazníkům podporuje sledování této značky a pomůže vám na otázky odpovědět.

Pokud nemůžete najít existující problém, který popisuje vaši chybu nebo funkci, odešlete problém pomocí níže uvedených pokynů.

### <a name="writing-a-good-bug-report-or-feature-suggestion"></a>Zápis správné zprávy o chybě nebo návrhu funkce

- Zadává jenom jeden problém nebo žádost o funkce na jeden problém.

  - Kombinování více problémů nebo žádostí o funkce do jednoho problému usnadňuje diagnostikování a obtížnější ostatním uživatelům hlasovat o vašem problému.
  - Nedávejte svůj problém jako komentář k existujícímu problému, pokud se nejedná o stejný vstup. Mnohé problémy vypadají podobně, ale mají různé příčiny, což nám usnadňuje diagnostiku vašeho problému.

- Další informace, které můžete poskytnout, usnadňují, aby bylo možné problém reprodukování a opravy.
- U každého problému zahrňte následující kroky.

  - Reprodukovatelné kroky (1... 2... 3...) a co jste očekávali oproti vašim zkušenostem.
  - Obrázky, animace nebo odkaz na video Obrázky a animace ilustrují reprodukci-Steps, ale _nenahrazují je_ .
  - Podle potřeby fragment kódu, který demonstruje problém, nebo odkaz na úložiště kódu, můžeme snadno vytvořit problém na našem počítači.

- Nezapomeňte provést následující kroky:

  - Pokud chcete zjistit, jestli existuje duplicitní, vyhledejte hledání. Pokud ano, zahlaste se s existujícím problémem a poskytněte další komentáře nebo vysvětlení podle potřeby.
  - Znovu vytvořit problém po zakázání všech rozšíření Pokud narazíte na problém, který je způsoben rozšířením, které jste nainstalovali, zapište problém v tomto rozšíření.
  - Zjednodušte svůj kód kolem problému, abychom mohli problém lépe izolovat.

I s problémy, které obsahují podrobné informace, nemůžeme tento problém reprodukován a může požádat o další informace.

## <a name="managing-problem-reports"></a>Správa sestav problémů

Třídění problému je proces s více kroky, který je v rámci týmu funkcí spolupracovat. Třídění obvykle trvá jeden týden, ale může trvat delší dobu. Cílem třídění je poskytnout jasné informace o tom, co se stane s vaším problémem. Například po určení příjímání informací o tom, jestli plánujeme problém vyřešit, nebo počkat na další názory na komunitu.

Po nahlášení problému se stavem označují, kde se vaše příspěvky nacházejí v životním cyklu. Díky tomu, že týmy produktu Visual Studio provedou zpětnou vazbu, nastavují příslušný stav. Sledovat průběh hlášení o problémech, které odkazují na [stavy problému a nejčastější dotazy](https://docs.microsoft.com/visualstudio/ide/report-a-problem).

Pokud problém neobsahuje důležité informace, přiřadíme stav _potřebuje více informací_ . K tomuto problému přiřadíme konkrétní informace, které potřebujeme, a obdržíte e-mailové oznámení. Pokud tyto informace do sedmi dnů neobdržíme, pošleme vám připomenutí. Potom uzavřete lístek po 14 dnech nečinnosti.

### <a name="wont-fix-bugs"></a>Neopraví chyby

Některé chyby zavřou, když se vyrovnává negativní náklady na zvýhodnění. Například pokud je oprava složitá a rizika pro mnoho uživatelů se regresí, oprava nemusí být přiměřená. Když tuto chybu zavřu, vysvětlíme, proč to máme.

### <a name="other-product"></a>Jiný produkt

V některých případech může při nahlášení problému dojít k tomu, že je způsoben jiným produktem a nikoli aplikací Visual Studio. Může se jednat o jinou související aplikaci nebo rozšíření. 

Pokud k tomu dojde, problém povedeme a požádáme vás, abyste ho otevřeli s jiným produktem. Tady jsou některé běžné místo pro tyto problémy:

* [SQL Server](https://feedback.azure.com/forums/908035-sql-server)
* [Podpora Visual Studio Subscription](https://feedback.azure.com/forums/908035-sql-server)
* [Office](https://support.office.com/article/how-do-i-give-feedback-on-microsoft-office-2b102d44-b43f-4dd2-9ff4-23cf144cfb11)
* [Windows](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)

#### <a name="additional-information"></a>Další informace

- [Jak zvýšit pravděpodobnost vyřešeného problému s výkonem](https://docs.microsoft.com/visualstudio/ide/how-to-increase-chances-of-performance-issue-being-fixed)
- [Řešení potíží a vytváření protokolů pro problémy nástroje MSBuild](https://docs.microsoft.com/visualstudio/ide/msbuild-logs)

## <a name="managing-feature-suggestions"></a>Správa návrhů funkcí

Návrhy funkcí představují způsob, jak komunikovat mezi námi a členy komunity vývojářů. Technicky, můžeme uchovávat všechny žádosti o funkce, které jsou trvale otevřené. Ale udržování otevřených problémů by mělo omezit viditelnost komunity na skutečný stav funkce. Proto jsme uzavřeli žádosti o funkce, které neřešíme a přiřadíme funkce, které můžeme adresovat na pod popiskem _Revize_ .

Pokud jste navrhli funkci, možná jste disappointedi, že neplánujeme vaši žádost řešit. Chápeme, že. Vše, co nám bylo v tomto projektu, nebo s ostatními jsme na to udělali. Takže jsme si jisti, že všechno vaše vstupy pozbylé. Po zavření nebo přiřazení popisku _recenze_ k vašemu návrhu neprovádějte osobní OFFENSE. Pokud se domníváte, že váš návrh funkce zůstane otevřený, vyjasněte si případ použití a kontaktujte nás nebo Shromážděte více hlasů.

V našem procesu rozhodování se podíváme na následující charakteristiky návrhu funkcí:

- Můžu si ho pro Build a údržbu dovolit?
- Je v souladu s naší celkovou strategií pro [plány](https://docs.microsoft.com/visualstudio/productinfo/vs-roadmap) ?
- Má komunitní podpora, jak je uvedeno ve hlasy a komentářích?
- Líbí se vám to i s nízkou podporou komunity?

Když nemůžeme na některé z těchto otázek odpovědět "Ano", my ji zavřeme. Ale často návrh zůstane _v rámci revize_ otevřený, aby se získalo více vašich názorů na komunitu.

Sledujte průběh návrhu vaší funkce, který odkazuje na [stavy návrhů a nejčastější dotazy](https://docs.microsoft.com/visualstudio/ide/report-a-problem).

## <a name="discussion-etiquette"></a>Pravidlech používání žádostí diskuze

Chcete-li zachovat jasný a transparentní konverzaci, omezte diskuzi na angličtinu a zajistěte, aby byly problémy relevantní. Considerate se na ostatní a vždycky se snaží Courteous a Professional.

Další informace najdete v [kodexu chování komunity Microsoft](https://answers.microsoft.com/en-us/page/codeofconduct).

Každé porušení diskuze pravidlech používání žádostí může vést k odebrání komentáře a následně k jeho zakázání.

## <a name="data-privacy"></a>Ochrana osobních údajů

Komentáře a odpovědi jsou veřejně viditelné, ale všechny připojené soubory jsou soukromě sdíleny pouze s Microsoftem. Tato viditelnost je výhodná, protože umožňuje celé komunitě zobrazit problémy a řešení nalezené jinými uživateli. Pokud máte obavy o soukromí dat nebo identity, máte možnosti. Přečtěte si další informace o [ochraně osobních údajů komunity vývojářů](https://docs.microsoft.com/visualstudio/ide/developer-community-privacy).

## <a name="next-steps"></a>Další kroky

Přihlaste se k [komunitě vývojářů sady Visual Studio](https://developercommunity.visualstudio.com/) , abyste mohli nahlásit problémy, navrhovat funkce nebo procházet stávající lístky. Užijte si ji!

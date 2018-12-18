---
title: Modelování aplikace&#39;s architektury
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7322738fe1bd17944bc5d1883bc9c16e56cc59e6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855073"
---
# <a name="model-your-app39s-architecture"></a>Modelování aplikace&#39;s architektury
K zajištění, že softwarový systém nebo aplikace splňuje uživatelů potřebuje, si můžete vytvořit modelů v sadě Visual Studio jako součást vaší popis celkovou strukturu a chování softwarového systému nebo aplikace. Použití modelů, může také popisovat vzory, které se používají v návrhu. Tyto modely umožňují pochopit stávající architekturou, změny a jasně komunikovat vaše záměry.

 Chcete-li zjistit, jaké edice sady Visual Studio podporují tuto funkci, přečtěte si téma [podpora edice nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Účel modelu je, abyste snížili nejasnosti, ke kterým dochází v přirozeném jazyce popisy a vy i vaši kolegové vizualizovat návrhu a diskutovat o alternativní návrhy. Model je třeba použít společně s další dokumenty nebo diskusí. Model samostatně, nepředstavuje kompletní specifikaci architektury.

> [!NOTE]
>  V tomto tématu "systém" znamená, že software, který vyvíjíte. Může být velkou kolekci mnoho softwarové a hardwarové součásti, nebo jedné aplikace nebo součást aplikace.

 Architektura systému je možné rozdělit do dvou oblastí:

-   [Podrobný návrh](#Structure). Popisuje hlavní součásti a jejich vzájemné interakce mezi sebou ke splnění každý požadavek. Pokud systém je velká, může být jednotlivé komponenty vlastní hlavnímu návrhu, který ukazuje, jak se skládají z menších komponent.

-   [Vzory návrhu](#Patterns) a pravidla týkající se používají v návrzích komponenty. Vzor popisuje konkrétní přístup k dosažení cíle programování. Pomocí stejné vzorce v celém návrh váš tým může snížit náklady na provedení změn a vývoji nového softwaru.

## <a name="Structure"></a> Návrh vysoké úrovně
 Návrh vysoké úrovně popisuje hlavní součásti systému a jejich vzájemné interakce mezi sebou k dosažení cíle návrhu. Aktivity v následujícím seznamu jsou součástí vývoje nejvyšší úrovni návrhu, i když nemusí nutně jít v určitém pořadí.

 Pokud aktualizujete existující kód, může začít popisuje hlavní součásti. Ujistěte se, že pochopit změny s požadavky uživatele a pak přidat nebo upravit interakce mezi komponentami. Pokud vyvíjíte na nový systém, začněte tím, že vysvětlení si hlavní funkce potřebám uživatelů. Můžete pak prozkoumejte sekvence interakcí pro případy použití hlavní a pak sloučit sekvence na návrh komponent.

 Ve všech případech je užitečné pro vývoj různé aktivity paralelně a pro vývoj kódu a testy v rané fázi. Vyhněte se pokusům o proveďte jeden z těchto aspektů před spuštěním jiného. Obvykle požadavky a pochopíte nejlepší způsob, jak navrhnout systému se změní při psaní a testování kódu. Proto měli byste začít tak, že porozumění a psaní kódu si hlavní funkce požadavky a návrhu. Vyplňte podrobnosti v pozdější iterace projektu.

-   [Principy požadavky](#Requirements). Výchozí bod jakékoli návrhu je pochopili, že potřebám uživatelů.

-   [Vzorech architektury](#BigDecisions). Volby, které jste provedli o základních technologií a prvky architektury systému.

-   Datový Model, komponent a rozhraní. Je-li nakreslit diagramy tříd k popisu informace, které se ukládají v součásti a předány mezi komponentami.

## <a name="Requirements"></a> Vysvětlení požadavků
 Hlavnímu návrhu dokončené aplikace je efektivní vyvinutý spolu s modelem požadavky nebo jiný popis potřebám uživatelů. Další informace o modelech požadavky najdete v části [modelování uživatelských požadavků](../modeling/model-user-requirements.md).

 Pokud systém, který vyvíjíte je součástí větší systému, může být část nebo všechny vaše požadavky shrnuta v programových rozhraní.

 Požadavky na model poskytuje tyto základní údaje:

- Poskytované rozhraní. Poskytované rozhraní obsahuje seznam služeb nebo operací, které systém nebo komponenta musí poskytnout uživatelům, ať už jsou lidské uživatele nebo další softwarové komponenty.

- Požadovaná rozhraní. Požadované rozhraní obsahuje seznam služeb nebo operací, které můžete použít systém nebo komponenty. V některých případech bude možné navrhnout všechny tyto služby jako součást vlastní systému. V ostatních případech zejména v případě, že součást, kterou můžete kombinovat s jinými součástmi v řadě konfigurací, navrhujete požadované rozhraní se nastavit externí aspekty.

- Kvalita požadavků na služby. Výkon, zabezpečení, odolnosti a další cíle a omezení, které musí splnit systému.

  Model požadavků se zapíše z pohledu uživatele vašeho systému, ať už jsou lidé, případně další softwarové komponenty. Které znají nic vnitřní fungování systému. Vaším cílem v architektuře modelu naopak je popíšou vnitřní činnost a ukážou, jak vyhovují uživatelů potřebuje.

  Pokud oddělíte požadavků a architektury modelů je užitečné, protože usnadňuje požadavky s uživateli. Pomáhá také Refaktorovat návrhu a zvážit alternativní architektury, při zachování požadavky beze změny.

  Množství podrobností, které byste měli umístit do požadavky nebo Architektonický model závisí na škálování projektu a velikost a rozmístění týmu. Malý tým na krátké projektu je možné dát další než zobrazení diagramu tříd obchodních konceptů a některé vzory návrhu; velký projekt distribuovat napříč více než jedné oblasti, bude nutné výrazně více podrobností.

## <a name="BigDecisions"></a> Vzorech architektury
 V rané fázi vývoje budete muset zvolit hlavní technologie a prvky, na kterých závisí návrhu. Oblasti, ve kterých se musí provádět tyto možnosti patří:

- Základní technologické volby, jako je například výběr mezi databází a systém souborů a možností volby mezi aplikace v síti a webovému klientovi a tak dále.

- Volby architektury, jako je například možností volby mezi Windows Workflow Foundation nebo ADO.NET Entity Framework.

- Integrace metody se nemusíte rozhodovat, například mezi enterprise service bus nebo kanál typu point-to-point.

  Tyto možnosti jsou často určené kvalitu požadavků služby, jako je škálovatelnost a flexibilitu a můžete provést předtím, než jsou známé podrobné požadavky. V rozsáhlém systému se důrazně vzájemně propojené konfigurace hardwaru a softwaru.

  Vámi provedeném výběru vliv na způsob používání a interpretace Architektonický model. Například v systému, která používá databázi, asociace v diagramu tříd může představovat vztahů nebo cizí klíče v databázi, že v systému, který je založen na soubory XML, přidružení může znamenat křížové odkazy, které používají XPath. V distribuovaném systému může představovat zprávy v sekvenčním diagramu zprávy v přenosové; samostatná aplikace může představovat volání funkce.

## <a name="Patterns"></a> Vzory návrhu
 Vzor návrhu je přehled toho, jak navrhnout konkrétní aspekt software, hlavně jeden, který se opakuje v různých součástí systému. Přijetím jednotný přístup napříč projektu můžete snížit náklady na návrh, zajistit konzistenci v uživatelském rozhraní a snížit náklady na principy a změny kódu.

 Některé obecné návrhové vzory, třeba pozorovatel jsou dobře známé a široce použitelné. Kromě toho jsou vzorce, které se dají použít jenom pro váš projekt. Například v systému Prodejní web, bude existovat několik operací v kódu ve kterém se změny provedly pořadí na základě. Aby bylo zajištěno, že se v každé fázi přesně zobrazí stav objednávky, musí všechny tyto operace postupujte podle konkrétní protokol k aktualizaci databáze.

 Během práce softwarovou architekturu je nutné určit, co by měl být modely přijatých přes návrhu. To je obvykle probíhající úlohy, protože nová schémata a vylepšení stávajících vzory, bude zjištěno v průběhu projektu. Je vhodné uspořádat plán vývoje tak, aby každý z vašich hlavních návrhové vzory výkonu v rané fázi.

 Většina vzorů návrhu může být částečně shrnuta v kódu rozhraní framework. Součást vzorku lze snížit vyžadováním pro vývojáře pro použití určitých tříd nebo komponenty, jako je například vrstva přístupu k databázi, který zajistí, že je správně zpracovat databázi.

 Vzor návrhu je popsaný v dokumentu a obvykle zahrnuje tyto části:

-   Jméno.

-   Popis kontext, ve které se vztahuje. Jakých kritérií by měl vytvořit vývojář, jestli nebude lepší uplatňovat tento model?

-   Stručné vysvětlení problému, který řeší.

-   Model hlavních částí a jejich vztahy. Může se jednat třídy nebo součásti a rozhraní se přidružení a závislostí mezi nimi. Elementy obvykle spadají do dvou kategorií:

-   Zásady vytváření názvů.

-   Popis jak vzoru byl problém vyřešen.

-   Popis změn, která se můžou vývojáři moci přijmout.

## <a name="see-also"></a>Viz také

- [Vizualizace kódu](../modeling/visualize-code.md)
- [Modelování uživatelských požadavků](../modeling/model-user-requirements.md)
- [Vývoj testů z modelu](../modeling/develop-tests-from-a-model.md)
- [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)
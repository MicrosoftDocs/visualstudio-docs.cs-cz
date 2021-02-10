---
title: Modelování architektury aplikace &apos;
description: Přečtěte si, jak můžete vytvořit modely v aplikaci Visual Studio jako součást popisu celkové struktury a chování softwarového systému nebo aplikace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e78e88884801b7aa7fcbcfe1147afd6fad653fd8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954368"
---
# <a name="model-your-app39s-architecture"></a>Modelování architektury aplikace&#39;s
Aby bylo zajištěno, že váš softwarový systém nebo aplikace vyhovují potřebám vašich uživatelů, můžete vytvořit modely v aplikaci Visual Studio jako součást popisu celkové struktury a chování softwarového systému nebo aplikace. Pomocí modelů můžete také popsat vzory používané v celém návrhu. Tyto modely vám pomůžou pochopit stávající architekturu, diskutovat o změnách a jasně sdělit své záměry.

 Pokud chcete zjistit, které edice sady Visual Studio podporují tuto funkci, přečtěte si téma [Podpora edice pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Účelem modelu je snížit nejednoznačnosti, ke kterým dochází v popisech v přirozeném jazyce, a pomáhat vám a vašim kolegům vizualizovat návrh a diskutovat o alternativních návrzích. Model by se měl používat společně s ostatními dokumenty nebo diskuzemi. Sám o sobě model nepředstavuje úplnou specifikaci architektury.

> [!NOTE]
> V celém tomto tématu označuje "systém" software, který vyvíjíte. Může se jednat o velkou kolekci mnoha softwarových a hardwarových komponent nebo o jednu aplikaci nebo součást aplikace.

 Architektura systému může být rozdělena do dvou oblastí:

- [Návrh vysoké úrovně](#Structure). To popisuje hlavní komponenty a jejich vzájemné vzájemné interakce ke splnění jednotlivých požadavků. Pokud je systém velký, může mít každá součást vlastní návrh vysoké úrovně, který ukazuje, jak se skládá z menších součástí.

- [Vzory](#Patterns) a konvence návrhu používané v rámci návrhů komponent. Vzor popisuje konkrétní přístup k dosažení cíle programování. Díky použití stejných vzorů v rámci návrhu může váš tým snížit náklady na provádění změn a vývoj nového softwaru.

## <a name="high-level-design"></a><a name="Structure"></a> Návrh na nejvyšší úrovni
 Návrh vysoké úrovně popisuje hlavní součásti systému a způsob, jak vzájemně komunikují, abyste dosáhli cílů návrhu. Aktivity v následujícím seznamu jsou zapojeny do vývoje vysoké úrovně návrhu, přestože nejsou nutně v konkrétní posloupnosti.

 Pokud aktualizujete existující kód, můžete začít tím, že popisujete hlavní součásti. Ujistěte se, že rozumíte jakýmkoli změnám požadavků uživatelů a pak přidáte nebo upravíte interakce mezi komponentami. Pokud vyvíjíte nový systém, začněte tím, že budete rozumět hlavním funkcím potřeb uživatelů. Pak můžete prozkoumat posloupnosti interakcí pro hlavní případy použití a potom sloučit sekvence do návrhu komponent.

 V každém případě je vhodné vyvíjet různé aktivity paralelně a vyvíjet kód a testy v rané fázi. Vyhněte se pokusu o dokončení některého z těchto aspektů předtím, než začnete s jiným. Při psaní a testování kódu se obvykle změní jak požadavky, tak i vaše porozumění nejlepšímu způsobu návrhu systému. Proto byste měli začít pochopením a kódováním hlavních funkcí požadavků a návrhu. Vyplňte podrobnosti v pozdějších iteracích projektu.

- [Principy požadavků](#Requirements). Výchozím bodem jakéhokoli návrhu je jasné porozumění potřebám uživatelů.

- [Modely architektury](#BigDecisions). Volby, které jste provedli na základních technologiích a prvcích architektury systému.

- Datový model komponent a rozhraní. Můžete nakreslit diagramy tříd pro popis informací, které jsou předány mezi komponentami a uloženy v rámci komponent.

## <a name="understanding-the-requirements"></a><a name="Requirements"></a> Principy požadavků
 Nejdůležitější návrh kompletní aplikace je nejúčinnější vyvinutý spolu s modelem požadavků nebo jiným popisem potřeb uživatelů. Další informace o modelech požadavků najdete v článku [modelování uživatelských požadavků](../modeling/model-user-requirements.md).

 Pokud je systém, který vyvíjíte, součástí většího systému, část nebo všechny vaše požadavky mohou být součástí programových rozhraní.

 Model požadavků poskytuje tyto podstatné informace:

- Poskytnutá rozhraní. Zadané rozhraní obsahuje seznam služeb nebo operací, které musí systém nebo součást poskytnout svým uživatelům, ať už se jedná o lidské uživatele nebo jiné softwarové komponenty.

- Požadovaná rozhraní. Požadované rozhraní obsahuje seznam služeb nebo operací, které může systém nebo komponenta používat. V některých případech budete moci navrhnout všechny tyto služby jako součást svého vlastního systému. V jiných případech, zejména pokud navrhujete komponentu, kterou je možné zkombinovat s jinými komponentami v mnoha konfiguracích, bude požadované rozhraní nastaveno externími požadavky.

- Požadavky na službu Quality of Service. Výkon, zabezpečení, odolnost a další cíle a omezení, které systém musí splňovat.

  Model požadavků se zapisuje z pohledu uživatelů vašeho systému, ať už jde o osoby nebo jiné softwarové součásti. Neznají žádná interní pracovní prostředí systému. Naopak vaším cílem v modelu architektury je popsat interní pracovní postupy a Ukázat, jak vyhovují potřebám uživatelů.

  Udržování požadavků a modelů architektury je užitečné, protože usnadňuje pojednání s požadavky uživatelů. Pomůže vám taky Refaktorovat návrh a vzít v úvahu alternativní architektury a zároveň zachovat požadavky beze změny.

  Množství podrobností, které byste měli umístit buď do požadavků, nebo do modelu architektury, závisí na rozsahu projektu a velikosti a rozdělení týmu. Malý tým v krátkém projektu může pokračovat bez vytváření náčrtů diagramu tříd obchodních konceptů a některých vzorů návrhu. velký projekt distribuovaný do více než jedné oblasti by vyžadoval podstatně více podrobností.

## <a name="architectural-patterns"></a><a name="BigDecisions"></a> Modely architektury
 V rané fázi vývoje musíte zvolit hlavní technologie a prvky, na kterých bude návrh záviset. Mezi oblasti, ve kterých se tyto volby musí udělat, patří následující:

- Výběr základních technologií, jako je například volba mezi databází a systémem souborů a volba mezi síťovou aplikací a webovým klientem atd.

- Volby rozhraní, jako je například volba mezi programovací model Windows Workflow Foundation nebo ADO.NET Entity Framework.

- Volby metod integrace, například mezi podnikovou sběrnicí nebo kanálem typu Point-to-Point.

  Tyto možnosti jsou často určeny požadavky na kvalitu služeb, jako je například škálování a flexibilita, a je možné je provést před známými podrobnými požadavky. V rozsáhlých systémech se konfigurace hardwaru a softwaru silně vzájemně souvisí.

  Volby, které provedete, budou mít vliv na způsob používání a interpretace modelu architektury. Například v systému, který používá databázi, může přidružení v diagramu tříd představovat vztahy nebo cizí klíče v databázi, zatímco v systému, který je založen na souborech XML, mohou přidružení značit křížové odkazy, které používají XPath. V distribuovaném systému mohou zprávy v sekvenčním diagramu představovat zprávy na lince. v samostatné aplikaci mohou představovat volání funkcí.

## <a name="design-patterns"></a><a name="Patterns"></a> Vzory návrhu
 Vzor návrhu je Osnova návrhu konkrétního aspektu softwaru, zejména z toho, který se opakuje v různých částech systému. Přijetím jednotného přístupu v rámci projektu můžete snížit náklady na návrh, zajistit konzistenci v uživatelském rozhraní a snížit náklady na porozumění a změnu kódu.

 Některé obecné vzory návrhu, jako je pozorovatel, jsou dobře známé a často použitelné. Kromě toho existují vzory, které platí pouze pro váš projekt. Například v systému webového prodeje bude v kódu k dispozici několik operací, kde se změny v objednávce zákazníka provedou. Aby se zajistilo, že se stav objednávky přesně zobrazuje v každé fázi, všechny tyto operace musí při aktualizaci databáze postupovat podle konkrétního protokolu.

 Součástí práce softwarové architektury je určit, jaké vzorky by se měly přijmout v rámci návrhu. To je obvykle probíhající úkol, protože nové vzory a vylepšení stávajících vzorů budou zjištěny v průběhu projektu. Je vhodné uspořádat plán vývoje, abyste měli v brzké fázi provádět jednotlivé hlavní vzory návrhu.

 Většina vzorů návrhu může být částečně obsažena v kódu rozhraní. Část vzoru se dá snížit, aby vývojář mohl používat konkrétní třídy nebo komponenty, jako je databázová vrstva přístupu, která zajišťuje správné zpracování databáze.

 Vzor návrhu je popsán v dokumentu a obvykle zahrnuje tyto části:

- Název.

- Popis kontextu, ve kterém je možné ho použít. Jaká kritéria by měl vývojář zvážit při použití tohoto vzoru?

- Stručné vysvětlení problému, který řeší.

- Model hlavních částí a jejich vztahů. Můžou to být třídy nebo komponenty a rozhraní s přidruženími a závislostmi mezi nimi. Prvky obvykle spadají do dvou kategorií:

- Zásady vytváření názvů.

- Popis způsobu, jakým vzorek tento problém vyřeší.

- Popis variací, které mohou vývojáři přijmout.

## <a name="see-also"></a>Viz také

- [Vizualizace kódu](../modeling/visualize-code.md)
- [Modelování uživatelských požadavků](../modeling/model-user-requirements.md)
- [Vývoj testů z modelu](../modeling/develop-tests-from-a-model.md)
- [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)

---
title: Modelování &apos; architektury aplikace
description: Zjistěte, jak můžete vytvářet modely v Visual Studio jako součást popisu celkové struktury a chování vašeho softwarového systému nebo aplikace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fa2be8f4da963c21d9f7f68939421dd7d2d72d0b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390109"
---
# <a name="model-your-app39s-architecture"></a>Modelování architektury&#39;aplikace
Pokud chcete zajistit, aby váš softwarový systém nebo aplikace splňovaly potřeby uživatelů, můžete v nástroji Visual Studio vytvořit modely v rámci popisu celkové struktury a chování vašeho softwarového systému nebo aplikace. Pomocí modelů můžete také popsat vzory, které se používají v celém návrhu. Tyto modely vám pomůžou porozumět stávající architektuře, diskutovat o změnách a jasně sdělovat své záměry.

 Informace o tom, které edice Visual Studio tuto funkci podporují, najdete v tématu Podpora edicí [pro nástroje architektury a modelování.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

 Účelem modelu je omezit nejednoznačnosti, ke kterým dochází v popisech přirozeného jazyka, a pomáhat vám a vašim kolegům vizualizovat návrh a diskutovat o alternativních návrhech. Model by se měl používat společně s jinými dokumenty nebo diskuzemi. Model sám o sobě nepředstavuje úplnou specifikaci architektury.

> [!NOTE]
> V tomto tématu "systém" označuje software, který vyvíjíte. Může to být velká kolekce mnoha softwarových a hardwarových komponent, jedna aplikace nebo součást aplikace.

 Architekturu systému lze rozdělit do dvou oblastí:

- [Návrh vysoké úrovně.](#Structure) Popisuje hlavní komponenty a způsob, jakým vzájemně komunikují, aby splnily každý požadavek. Pokud je systém velký, může mít každá komponenta svůj vlastní návrh vysoké úrovně, který ukazuje, jak se skládá z menších komponent.

- [Vzory a](#Patterns) konvence návrhu používané v návrhech komponent Vzor popisuje konkrétní přístup k dosažení programovacího cíle. Díky použití stejných vzorů v celém návrhu může váš tým snížit náklady na provádění změn a vývoj nového softwaru.

## <a name="high-level-design"></a><a name="Structure"></a> Návrh vysoké úrovně
 Základní návrh popisuje hlavní součásti systému a způsob, jakým spolu vzájemně komunikují, aby bylo možné dosáhnout cílů návrhu. Aktivity v následujícím seznamu se podílejí na vývoji návrhu vysoké úrovně, i když ne nutně v konkrétním pořadí.

 Pokud aktualizujete existující kód, můžete začít popisem hlavních komponent. Ujistěte se, že rozumíte změnám uživatelských požadavků, a pak přidejte nebo upravte interakce mezi komponentami. Pokud vyvíjíte nový systém, začněte pochopením hlavních funkcí potřeb uživatelů. Pak můžete prozkoumat sekvence interakcí pro hlavní případy použití a pak je konsolidovat do návrhu komponent.

 V každém případě je užitečné vyvíjet různé aktivity paralelně a vyvíjet kód a testy v rané fázi. Před zahájením dalšího se pokuste jeden z těchto aspektů dokončit. Při psaní a testování kódu se obvykle změní požadavky i pochopení nejlepšího způsobu návrhu systému. Proto byste měli začít pochopením a kódováním hlavních funkcí požadavků a vašeho návrhu. Vyplňte podrobnosti v pozdějších iteracích projektu.

- [Vysvětlení požadavků](#Requirements) Výchozím bodem jakéhokoli návrhu je jasné porozumění potřebám uživatelů.

- [Architektonické vzory](#BigDecisions). Volby týkající se základních technologií a architektonických prvků systému.

- Datový model komponent a rozhraní. Diagramy tříd můžete nakreslit a popsat tak informace, které se předá mezi komponentami a uloží uvnitř komponent.

## <a name="understanding-the-requirements"></a><a name="Requirements"></a> Vysvětlení požadavků
 Návrh kompletní aplikace na nejvyšší úrovni se nejhodněji vyvíjí společně s modelem požadavků nebo jiným popisem potřeb uživatelů. Další informace o modelech požadavků najdete v tématu [Požadavky uživatelů modelu.](../modeling/model-user-requirements.md)

 Pokud je systém, který vyvíjíte, součástí většího systému, může být část nebo všechny vaše požadavky vtělené do programových rozhraní.

 Model požadavků poskytuje tyto základní informace:

- Poskytnutá rozhraní. Poskytované rozhraní obsahuje seznam služeb nebo operací, které musí systém nebo komponenta poskytnout svým uživatelům, ať už se jedná o lidské uživatele nebo jiné softwarové komponenty.

- Požadovaná rozhraní. Požadované rozhraní obsahuje seznam služeb nebo operací, které může systém nebo komponenta používat. V některých případech budete moct navrhnout všechny tyto služby jako součást vlastního systému. V jiných případech, zejména pokud navrhujete komponentu, kterou lze kombinovat s jinými komponentami v mnoha konfiguracích, bude požadované rozhraní nastaveno externími aspekty.

- Požadavky na kvalitu služeb. Výkon, zabezpečení, odolnost a další cíle a omezení, které musí systém splnit.

  Model požadavků je napsán z pohledu uživatelů vašeho systému, ať už se jedná o lidi nebo jiné softwarové komponenty. Neznají nic o interním fungování vašeho systému. Naopak vaším cílem v modelu architektury je popsat interní fungování a ukázat, jak splňují potřeby uživatelů.

  Oddělení požadavků a modelů architektury je užitečné, protože usnadňuje diskuzi o požadavcích s uživateli. Pomáhá také refaktorovat návrh a zvažovat alternativní architektury a přitom zachovat požadavky beze změny.

  Množství podrobností, které byste měli umístit do požadavků nebo modelu architektury, závisí na rozsahu projektu a velikosti a rozdělení týmu. Malý tým na krátkém projektu nemusí jít dál než načrtat diagram tříd obchodních konceptů a některých vzorů návrhu. Velký projekt distribuovaný ve více než jedné oblasti by potřeboval výrazně více podrobností.

## <a name="architectural-patterns"></a><a name="BigDecisions"></a> Architektonické vzory
 Na začátku vývoje musíte zvolit hlavní technologie a prvky, na kterých návrh závisí. Mezi oblasti, ve kterých je třeba tyto volby vybrat, patří:

- Základní technologické volby, například volba mezi databází a systémem souborů a volba mezi síťovou aplikací a webovým klientem atd.

- Volby architektur, například volba mezi programovací model Windows Workflow Foundation nebo ADO.NET Entity Framework.

- Možnosti metod integrace, například mezi podnikovou sběrnici Service Bus nebo kanálem point-to-point.

  Tyto volby se často určují podle kvality požadavků na služby, jako je škálování a flexibilita, a je možné je udělat před tím, než jsou známé podrobné požadavky. Ve velkém systému je konfigurace hardwaru a softwaru silně propojená.

  Výběry, které použijete, ovlivňují způsob použití a interpretace modelu architektury. Například v systému, který používá databázi, mohou asociace v diagramu tříd představovat relace nebo cizí klíče v databázi, zatímco v systému založeném na souborech XML mohou asociace indikovat křížové odkazy, které používají XPath. V distribuovaném systému mohou zprávy v sekvenčním diagramu představovat zprávy na drátu. v samostatné aplikaci mohou představovat volání funkcí.

## <a name="design-patterns"></a><a name="Patterns"></a> Vzory návrhu
 Návrhový vzor je přehled toho, jak navrhnout konkrétní aspekt softwaru, zejména ten, který se bude opakovat v různých částech systému. Jednotným přístupem v rámci projektu můžete snížit náklady na návrh, zajistit konzistenci v uživatelském rozhraní a snížit náklady na pochopení a změnu kódu.

 Některé obecné vzory návrhu, jako je pozorovatel, jsou dobře známé a široce použitelné. Kromě toho existují vzory, které se vztahují pouze na váš projekt. Například ve webovém prodejním systému bude v kódu několik operací, ve kterých se provádí změny v objednávce zákazníka. Aby se zajistilo, že se stav objednávky přesně zobrazí v každé fázi, musí všechny tyto operace při aktualizaci databáze dodržovat konkrétní protokol.

 Součástí práce softwarové architektury je určit, jaké vzory by se měly v rámci návrhu použít. Obvykle se jedná o probíhající úlohu, protože při průběhu projektu se objeví nové vzory a vylepšení stávajících vzorů. Je užitečné uspořádat plán vývoje tak, abyste si procvičíte každý z hlavních vzorů návrhu v rané fázi.

 Většina vzorů návrhu může být částečně ztělesněna v kódu architektury. Část modelu se může omezit tak, aby vývojáři vyžadovat použití konkrétních tříd nebo komponent, jako je vrstva přístupu k databázi, která zajišťuje správné zpracování databáze.

 Vzor návrhu je popsán v dokumentu a obvykle zahrnuje tyto části:

- Název.

- Popis kontextu, ve kterém se vztahuje Jaká kritéria by měla vývojáře přimět zvážit použití tohoto modelu?

- Stručné vysvětlení problému, který řeší.

- Model hlavních částí a jejich vztahů. Můžou to být třídy nebo komponenty a rozhraní s přidruženími a závislostmi mezi nimi. Prvky obvykle spadají do dvou kategorií:

- Zásady vytváření názvů.

- Popis způsobu, jakým vzor řeší problém

- Popis variací, které můžou vývojáři přijmout

## <a name="see-also"></a>Viz také

- [Vizualizace kódu](../modeling/visualize-code.md)
- [Modelování uživatelských požadavků](../modeling/model-user-requirements.md)
- [Vývoj testů z modelu](../modeling/develop-tests-from-a-model.md)
- [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)

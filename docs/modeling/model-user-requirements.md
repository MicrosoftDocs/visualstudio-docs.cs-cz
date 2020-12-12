---
title: Modelování uživatelských požadavků
description: Naučte se, jak Visual Studio pomáhá pochopit, diskutovat a sdělovat potřeby vašich uživatelů pomocí kreslicích diagramů o jejich aktivitách.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- requirements
- stories
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40418b2d188ac5482a12dd4ffdddd221bf5d2f97
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361960"
---
# <a name="model-user-requirements"></a>Modelování uživatelských požadavků

Visual Studio vám pomůže pochopit, diskutovat a sdělovat potřeby vašich uživatelů vykreslením diagramů o jejich aktivitách a části vašeho systému, který pomáhá dosahovat svých cílů. Model požadavků je sada těchto diagramů, z nichž každá se zaměřuje na jiný aspekt potřeb uživatelů. Ukázku videa najdete v tématu [modelování obchodní domény](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain).

Chcete-li zjistit, které verze aplikace Visual Studio podporují jednotlivé typy modelů, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Model požadavků vám pomůže:

- Soustřeďte se na externí chování systému, a to odděleně od jeho interního návrhu.

- Popište požadavky uživatelů a zúčastněných stran s mnohem menší nejednoznačnější, než můžete v přirozeném jazyce.

- Definujte konzistentní Glosář termínů, které mohou používat uživatelé, vývojáři a testery.

- Snižte mezery a nekonzistence v požadavcích.

- Zmenšete práci potřebnou k reakci na změny požadavků.

- Naplánujte pořadí, ve kterém budou funkce vyvíjeny.

- Použijte modely jako základ pro systémové testy a vytvořte tak jasný vztah mezi testy a požadavky. Když se požadavky změní, tento vztah vám pomůže správně aktualizovat testy. Tím se zajistí, že systém splňuje nové požadavky.

Model požadavků poskytuje nejvyšší výhody, pokud ho používáte k zaměření diskusí s uživateli nebo jejich zástupci a na začátku každé iterace. Před psaním kódu ho nemusíte podrobně doplňovat. Částečně funkční aplikace, a to i v případě, že je velmi zjednodušená, všeobecně tvoří základ pro diskuzi o požadavcích s uživateli. Model představuje efektivní způsob sumarizace výsledků těchto diskusí. Další informace najdete v tématu [použití modelů v procesu vývoje](../modeling/use-models-in-your-development-process.md).

> [!NOTE]
> V těchto tématech "systém" znamená systém nebo aplikaci, kterou vyvíjíte. Může se jednat o velkou kolekci mnoha softwarových a hardwarových komponent. nebo jedna aplikace; nebo softwarová součást v rámci většího systému. V každém případě model požadavků popisuje chování, které je viditelné mimo váš systém bez ohledu na to, jestli jde o uživatelské rozhraní nebo rozhraní API.

## <a name="common-tasks"></a>Běžné úkoly

Můžete vytvořit několik různých zobrazení požadavků uživatelů.  Každé zobrazení poskytuje konkrétní typ informací.  Když vytváříte tato zobrazení, je nejlepší je často přesunout z jedné do druhé. Můžete začít z libovolného zobrazení.

|Diagram nebo dokument|Jak popisuje model požadavků|Sekce|
|-|-|-|
|Diagram koncepční třídy|Glosář typů, které se používají k popisu požadavků; typy viditelné v rozhraní systému.||
|Další dokumenty nebo pracovní položky|Kritéria pro výkon, zabezpečení, použitelnost a spolehlivost.|[Popisující požadavky na službu Quality of Service](#QoSRequirements)|
|Další dokumenty nebo pracovní položky|Omezení a pravidla nespecifická pro konkrétní případ použití|[Zobrazení obchodních pravidel](#BusinessRules)|

Všimněte si, že většinu typů diagramů lze použít pro jiné účely. Přehled typů diagramů najdete v tématu [vytvoření modelů pro vaši aplikaci](../modeling/create-models-for-your-app.md).

## <a name="showing-business-rules"></a><a name="BusinessRules"></a> Zobrazení obchodních pravidel

Obchodní pravidlo je požadavek, který není přidružený k určitému případu použití, a měl by být pozorován v celém systému.

Mnoho obchodních pravidel je omezení pro vztahy mezi koncepčními třídami. Tato *statická obchodní pravidla* můžete zapsat jako komentáře přidružené k příslušným třídám v diagramu koncepční třídy. Příklad:

![Pravidlo v komentáři připojené ke třídě Order](../modeling/media/uml_reqmcd2.png)

*Dynamická obchodní pravidla* omezí možné posloupnosti událostí. Například můžete použít diagram sekvence nebo aktivity k zobrazení, že se uživatel musí přihlásit před provedením dalších operací v systému.

Mnoho dynamických pravidel ale může být efektivnější a obecně řečeno jejich nahrazením statickými pravidly. Například můžete přidat logický atribut "přihlášen" do třídy v modelu koncepční třídy. Přidali jste přihlášeni jako následná podmínka v případu použití protokolu a přidáte ho jako podmínku pro většinu ostatních případů použití. Tento přístup vám umožní vyhnout se definování všech možných kombinací posloupnosti událostí. Je také pružnější, pokud pro model potřebujete přidat nové případy použití.

Všimněte si, že zvolený postup je o tom, jak definujete požadavky a že je nezávisle na tom, jak implementujete požadavky v kódu programu.

Další informace najdete v následujících tématech:

|Další informace|Číst|
|-|-|
|Postup vývoje kódu, který dodržuje obchodní pravidla|[Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)|

## <a name="describing-quality-of-service-requirements"></a><a name="QoSRequirements"></a> Popisující požadavky na službu Quality of Service

Existuje několik kategorií požadavků na kvalitu služeb. Jsou to tyto:

- Výkon

- Zabezpečení

- Použitelnost

- Spolehlivost

- Robustnost

Některé z těchto požadavků můžete zahrnout do popisu konkrétního případu použití. Jiné požadavky nejsou specifické pro případy použití a jsou efektivně napsány v samostatném dokumentu. Když můžete, je vhodné dodržovat slovník definovaný modelem požadavků. V následujícím příkladu si všimněte, že hlavní slova použitá v požadavku jsou názvy objektů Actor, případy použití a třídy v předchozí ilustraci:

Pokud restaurace odstraní položku nabídky, když zákazník seřazení moučky, položka objednávky, která odkazuje na tuto položku nabídky, se zobrazí červeně.

Podívejte se na téma [modelování architektury vaší aplikace](../modeling/model-your-app-s-architecture.md) a Naučte se vyvíjet kód, který dodržuje požadavky na kvalitu služeb.

## <a name="see-also"></a>Viz také:

- [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)
- [Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)

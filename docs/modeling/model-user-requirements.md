---
title: Modelování uživatelských požadavků
description: Zjistěte, Visual Studio vám pomůže pochopit, diskutovat a sdělovat potřeby uživatelů tím, že vykreslí diagramy jejich aktivit.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- requirements
- stories
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 381395eb0b9dabde0e94c479cb43033bc8443c8f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390148"
---
# <a name="model-user-requirements"></a>Modelování uživatelských požadavků

Visual Studio pomáhá porozumět potřebám uživatelů, diskutovat o nich a sdělovat je tím, že vykresluje diagramy jejich aktivit a část, kterou váš systém hraje při dosahování jejich cílů. Model požadavků je sada těchto diagramů, z nichž každý se zaměřuje na jiný aspekt potřeb uživatelů. Ukázku videa najdete v tématu Modelování [obchodní domény](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain).

Informace o tom, které Visual Studio podporují jednotlivé typy modelů, najdete v tématu [Podpora verzí pro nástroje architektury a modelování.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

Model požadavků vám pomůže:

- Zaměřte se na externí chování systému odděleně od jeho interního návrhu.

- Popište potřeby uživatelů a účastníků s mnohem méně nejednoznačností, než je možné v přirozeném jazyce.

- Definujte konzistentní glosář termínů, které mohou používat uživatelé, vývojáři a testeři.

- Omezte mezery a nekomistence v požadavcích.

- Omezte práci potřebnou k reagování na změny požadavků.

- Naplánujte pořadí, ve kterém budou funkce vyvíjeny.

- Modely používejte jako základ pro systémové testy, aby byl mezi testy jasný vztah a požadavky. Když se požadavky změní, pomůže vám tento vztah správně aktualizovat testy. Tím se zajistí, že systém splňuje nové požadavky.

Model požadavků poskytuje největší výhodu, pokud ho použijete k zaměření diskuzí s uživateli nebo jejich zástupci a k jeho opakování na začátku každé iterace. Před psaním kódu ho není možné dokončovat podrobně. Částečně funkční aplikace, i když je velmi zjednodušená, obvykle tvoří nejpohodnější základ pro diskuzi o požadavcích s uživateli. Model je efektivní způsob, jak shrnout výsledky těchto diskuzí. Další informace najdete v tématu [Použití modelů ve vývojovém procesu](../modeling/use-models-in-your-development-process.md).

> [!NOTE]
> V těchto tématech "systém" označuje systém nebo aplikaci, kterou vyvíjíte. Může to být velká kolekce mnoha softwarových a hardwarových komponent. nebo jednu aplikaci; nebo softwarovou komponentu uvnitř většího systému. V každém případě popisuje model požadavků chování, které je viditelné mimo váš systém, ať už prostřednictvím uživatelského rozhraní nebo rozhraní API.

## <a name="common-tasks"></a>Běžné úkoly

Můžete vytvořit několik různých zobrazení požadavků uživatelů.  Každé zobrazení poskytuje konkrétní typ informací.  Při vytváření těchto zobrazení je nejlepší mezi sebou často přechádovat. Můžete začít z libovolného zobrazení.

|Diagram nebo dokument|Co popisuje v modelu požadavků|Sekce|
|-|-|-|
|Koncepční diagram tříd|Glosář typů, které se používají k popisu požadavků. Typy viditelné v rozhraní systému.||
|Další dokumenty nebo pracovní položky|Kritéria výkonu, zabezpečení, použitelnosti a spolehlivosti.|[Popis kvality požadavků na službu](#QoSRequirements)|
|Další dokumenty nebo pracovní položky|Omezení a pravidla, která nejsou specifická pro konkrétní případ použití|[Zobrazení obchodních pravidel](#BusinessRules)|

Všimněte si, že většinu typů diagramu lze použít k jiným účelům. Přehled typů diagramů najdete v tématu [Vytváření modelů pro vaši aplikaci.](../modeling/create-models-for-your-app.md)

## <a name="showing-business-rules"></a><a name="BusinessRules"></a> Zobrazeno Business Rules

Obchodní pravidlo je požadavek, který není přidružený ke konkrétnímu případu použití a měl by se dodržovat v celém systému.

Mnoho obchodních pravidel je omezením vztahů mezi koncepčními třídami. Tato statická obchodní pravidla můžete *napsat jako* komentáře přidružené k relevantním třídám v diagramu koncepčních tříd. Příklad:

![Pravidlo v komentáři připojeném k třídě Order](../modeling/media/uml_reqmcd2.png)

*Dynamická obchodní* pravidla omezují povolitelné sekvence událostí. Pomocí sekvenčního diagramu nebo diagramu aktivit můžete například ukázat, že se uživatel musí před provedením dalších operací v systému přihlásit.

Mnoho dynamických pravidel ale může být efektivněji a obecněji uvedeno tak, že je nahradíte statickými pravidly. Do třídy v modelu koncepční třídy můžete například přidat logický atribut Přihlášený. Jako podmínku pro případ použití protokolu byste přidali Logged In (Přihlášeno) a přidali byste ho jako podmínku pro většinu ostatních případů použití. Tento přístup umožňuje vyhnout se definování všech možných kombinací sekvencí událostí. Je také flexibilnější, když potřebujete do modelu přidat nové případy použití.

Všimněte si, že volba zde je o tom, jak definujete požadavky a že to je nezávislé na způsobu implementace požadavků v kódu programu.

Další informace najdete v následujících tématech:

|Další informace|Číst|
|-|-|
|Vývoj kódu, který dodržuje obchodní pravidla|[Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)|

## <a name="describing-quality-of-service-requirements"></a><a name="QoSRequirements"></a> Popis požadavků na kvalitu služeb

Existuje několik kategorií požadavků na kvalitu služby. Patří mezi ně následující:

- Výkon

- Zabezpečení

- Použitelnost

- Spolehlivost

- Robustnost

Některé z těchto požadavků můžete zahrnout do popisů konkrétních případů použití. Další požadavky nejsou specifické pro případy použití a jsou nejuceněji napsané v samostatném dokumentu. Pokud je to možné, je užitečné dodržovat slovník definovaný modelem požadavků. V následujícím příkladu si všimněte, že hlavní slova použitá v požadavku jsou názvy aktérů, případů použití a tříd na předchozích obrázcích:

Pokud restaurace odstraní položku nabídky, zatímco zákazník objednává jídlo, všechny položky objednávky, které na tuto položku nabídky odkazují, se zobrazí červeně.

Informace [o tom, jak](../modeling/model-your-app-s-architecture.md) vyvíjet kód, který dodržuje požadavky na kvalitu služeb, najdete v tématu Modelování architektury aplikace.

## <a name="see-also"></a>Viz také

- [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)
- [Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)

---
title: Modelování uživatelských požadavků
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- requirements
- stories
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 4791566d3c37517c3c93e62e371bf4cbc9fc6604
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966554"
---
# <a name="model-user-requirements"></a>Modelování uživatelských požadavků

Visual Studio vám pomáhá pochopit, diskutovat a sdělovat požadavky uživatelů ve vytvoření diagramů o svých aktivit a části systému hraje v usnadňuje dosáhli svých cílů. Model požadavků je sada tyto diagramy, z nichž každý se zaměřuje na různé aspekty potřebám uživatelů. Video ukázku naleznete v tématu: [modelování obchodní domény](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain).

Které verze sady Visual Studio podporovat každý typ modelu najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Požadavky na modelu vám pomůže:

- Zaměřte se na chování systému externí, odděleně od jeho vnitřní strukturou.

- Popište uživatelů a zúčastněných stran pomocí musí mít mnohem méně nejednoznačnost, než v přirozeném jazyce.

- Definujte konzistentní Glosář termínů, které je možné uživatele, vývojáři a testeři.

- Snížit prostoje a nekonzistence v požadavcích.

- Omezení práce potřebné reakce na změny požadavků.

- Naplánujte pořadí, ve kterém se funkce vyvinuté.

- Pomocí modelu jako základ pro testy systému, což jasný vztah mezi testy a požadavky. Při změně požadavků, tato relace vám pomůže aktualizovat testy správně. Tím je zajištěno, že systém splňuje nové požadavky.

Požadavky na model poskytuje největší výhody, pokud jej používat k aktivní diskuze s uživateli nebo svých zástupci a opakování na začátku každé iterace. Není nutné pro dokončení podrobně před psaním kódu. Částečně funkční aplikaci, i v případě velmi výrazně zjednodušené, obecně tento balíček je základem nejvíce podporovat diskuzi o požadavky s uživateli. Model je účinný způsob, jak vytvořit souhrn výsledků tyto diskuse. Další informace najdete v tématu [použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md).

> [!NOTE]
> V těchto tématech "systém" znamená, že systém nebo aplikace, kterou vyvíjíte. Rozsáhlá kolekce řadu softwarových a hardwarových součástí; může být nebo si jednu aplikaci; nebo softwarová součást uvnitř větší systému. V každém případě model požadavků popisuje chování, které je viditelné z vnějšku systému prostřednictvím uživatelského rozhraní nebo rozhraní API.

## <a name="common-tasks"></a>Běžné úlohy

Můžete vytvořit několik různých zobrazení podle požadavků uživatelů.  Každé zobrazení obsahuje konkrétního typu informací.  Při vytváření těchto zobrazení je nejvhodnější často přesunout na další. Můžete spustit z jakékoli zobrazení.

|Diagram nebo dokumentu|Co se popisuje v modelu požadavky|Oddíl|
|-|-|-|
|Třída koncepční diagram|Glosář typů, které se používají k popisu požadavků; typy viditelný na rozhraní v systému.||
|Další dokumenty nebo pracovních položek|Kritéria výkonu, zabezpečení, využitelnost a spolehlivost.|[Popisující kvality požadavků na služby](#QoSRequirements)|
|Další dokumenty nebo pracovních položek|Omezení a pravidla není specifická pro konkrétní případ použití|[Zobrazení obchodních pravidel](#BusinessRules)|

Všimněte si, že většina typů diagramu můžete používat pro jiné účely. Přehled typů diagramu, naleznete v tématu [vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md).

##  <a name="BusinessRules"></a> Zobrazení obchodních pravidel

Obchodní pravidlo je požadavek, který není spojen s případem použití konkrétní a by měl v celém systému.

Mnoho obchodní pravidla jsou omezení na vztahy mezi koncepční třídy. Můžete napsat tyto *statické obchodní pravidla* jako komentáře přidružené k příslušné třídy v diagramu tříd koncepční. Příklad:

![Pravidlo v komentář připojený na třídu pořadí.](../modeling/media/uml_reqmcd2.png)

*Dynamické obchodní pravidla* omezit povolený sledů událostí. Například pomocí diagramu pořadí nebo aktivity zobrazíte, že uživatel musí přihlásit, před provedením další operace ve vašem systému.

Nicméně mnoho dynamická pravidla můžete efektivněji a obecně zobrazovat nahrazením je statická pravidla. Například můžete přidat atribut typu Boolean zaznamenána v na třídu v koncepčním třídy modelu. By přidejte zaznamenána v jako neplatná následná protokolu v případu použití a přidejte ho jako předběžnou podmínku většinu dalších případů použití. Tento přístup umožňuje Vyhněte se definování všech možných kombinací sledů událostí. Je také flexibilnější když budete chtít do modelu přidat nové případy použití.

Všimněte si, že tady je o tom, jak definovat požadavky a, že se jedná o nezávislé implementace požadavky v kódu programu.

Další informace naleznete v následujících tématech:

|Další informace o|Číst|
|-|-|
|Postupy při vývoji kódu, který splňuje obchodní pravidla|[Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)|

##  <a name="QoSRequirements"></a> Popisující kvality požadavků na služby

Existuje několik kategorií kvality služby. Jsou to tyto země:

-   Výkon

-   Zabezpečení

-   Použitelnosti

-   Spolehlivost

-   Robustnost

Může obsahovat některé z těchto požadavků v popisech zvláštní případy. Další požadavky nejsou specifická pro případy použití a efektivní zapsány v samostatných dokumentu. Pokud je to možné, je vhodné dodržovat slovník určené model požadavků. V následujícím příkladu Všimněte si, že hlavní slova používaná požadavek na názvy objektů actor, případy použití a třídy v vidět na předchozím obrázku:

Pokud restaurace odstraní položku nabídky, zatímco zákazník je pokrmu, jakoukoli objednávky položku, který odkazuje na danou položku nabídky se zobrazí červeně.

Zobrazit [modelování architektury aplikace](../modeling/model-your-app-s-architecture.md) se naučíte vyvíjet kód, který používá kvality požadavků na služby.

## <a name="see-also"></a>Viz také:

- [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)
- [Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)

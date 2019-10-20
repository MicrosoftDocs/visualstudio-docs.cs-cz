---
title: Co&#39;je nového pro návrh
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- what's new [VIsual Studio], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio], What's New
ms.assetid: 36ab5c17-6dc0-4075-a28e-a0fa49b11260
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c68db12f8ecea523327250fec1f600639a2f267
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659248"
---
# <a name="whats-new-for-design-in-visual-studio-in-visual-studio-2015"></a>Co je nového pro návrh v aplikaci Visual Studio v aplikaci Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Tato verze sady Visual Studio obsahuje následující vylepšení, která vám pomůžou lépe pochopit a navrhovat kód.

 **Mapy kódu a grafy závislostí**

 V Visual Studio Enterprise, pokud chcete pochopit konkrétní závislosti ve vašem kódu, Vizualizujte si je vytvořením map kódu. Tyto vztahy pak můžete procházet pomocí mapy, která se zobrazí vedle vašeho kódu. Mapy kódu vám také pomůžou sledovat své místo v kódu při práci nebo ladění kódu, takže budete číst méně kódu, zatímco se dozvíte více o návrhu kódu.

 V konečné (RTM) vydané verzi jsme místní nabídky pro prvky kódu a odkazy zjednodušili tím, že je seskupíte příkazy do oddílů souvisejících s výběrem, úpravou, správou skupin a změnou rozložení obsahu skupiny. Všimněte si také, že testovací projekty se zobrazují v jiném stylu než ostatní projekty a že jsme aktualizovali ikony pro prvky na mapě na vhodnější verze.

 ![Zobrazit vybrané položky na nové mapě kódu](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 Mezi další vylepšení patří:

- **Vylepšené diagramy v horní části**. Pro střední až velká řešení sady Visual Studio teď můžete použít zjednodušenou nabídku architektury pro získání užitečnějších map kódu pro vaše řešení. Sestavení vašeho řešení se seskupují podle složek řešení, takže je můžete vidět v kontextu a využít úsilí, které jste vložili do struktury řešení. Okamžitě uvidíte odkazy na projekt a sestavení a pak se zobrazí typy propojení. Kromě toho jsou sestavení mimo vaše řešení seskupena způsobem kompaktnějšího.

- **Projekty testů mají jiný styl a dají se filtrovat**. Nyní můžete snadněji a rychle identifikovat projekty testů na mapě, protože mají jiný styl. Lze je také odfiltrovat, abyste se mohli zaměřit na funkční kód aplikace.

- **Zjednodušené odkazy externích závislostí**. Odkazy závislostí už nepředstavují dědičnost z typů System. Object, System. ValueType, System. Enum a System. Delegate, což usnadňuje zobrazení externích závislostí ve vaší mapě kódu.

- **Možnost přejít na odkazy závislostí bere v úvahu filtry**. Po rozbalení se vám zobrazí užitečný a jasný diagram pro pochopení příspěvků na odkaz závislosti. Diagram je méně zbytečný a bere v úvahu možnosti filtrování odkazů, které jste vybrali.

- **Prvky kódu jsou přidány do mapy kódu s jejich kontextem**. Vzhledem k tomu, že diagramy se nyní zobrazují spolu se svým kontextem (až do složky sestavení a řešení, které můžete v případě potřeby odfiltrovat), můžete získat užitečnější diagramy při přetahování prvků kódu z Průzkumník řešení, Zobrazení tříd Prohlížeč objektů; nebo při výběru prvků v Průzkumník řešení a výběru možnosti Zobrazit na mapě kódu.

- Rychlejší **získání reaktivních map kódu**. Operace přetažení poskytují okamžitý výsledek a propojení mezi uzly jsou vytvořena mnohem rychleji, aniž by to ovlivnilo následné uživatelem iniciované operace, jako je například rozbalení uzlu nebo vyžadování více uzlů. Při vytváření map kódu bez sestavování řešení se nyní zpracovávají všechny rohové případy, například když nejsou sestavení sestavena.

- **Přeskočit opakované sestavování řešení.** Poskytuje lepší výkon při vytváření a úpravách diagramů.

- **Filtrování uzlů prvků kódu a skupin**. Můžete rychle vyjasněit vaše mapy zobrazením nebo skrytím prvků kódu na základě jejich kategorie, a také seskupením prvků kódu podle složek řešení, sestavení, oborů názvů, složek projektu a typů.

- **Filtrováním vztahů zajistíte snazší čtení diagramů**. Filtr propojení se teď vztahuje také na propojení mezi skupinami, což umožňuje méně rušivé práce s oknem filtru, než bylo v předchozích verzích.

- **Vytváření diagramů z zobrazení tříd a prohlížeč objektů** Soubory a sestavení můžete přetáhnout do nové nebo existující mapy z Zobrazení tříd a Prohlížeč objektů Windows.

  Podívejte [se na téma mapování závislostí napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md).

  **Další změny návrhu a modelování v této verzi:**

- **Diagramy vrstev**. Aktualizujte tyto diagramy pomocí Zobrazení tříd a Prohlížeč objektů. Abyste splnili požadavky na návrh softwaru, použijte diagramy vrstev k popsání požadovaných závislostí pro váš software. Kód, který nesplňuje tato omezení, ponechte v souladu s tímto návrhem, a to tak, že pomocí tohoto směrného plánu ověřujete budoucí kód.

- **Diagramy UML**. Z kódu už nemůžete vytvářet diagramy tříd UML a sekvenční diagramy. Přesto ale tyto diagramy vytvoříte pomocí nových elementů UML.

- **Průzkumník architektury**. Nemůžete už používat Průzkumníka architektury k vytváření diagramů. Ale můžete i nadále používat Průzkumník řešení.

## <a name="VersionSupport"></a>Podpora edice pro nástroje pro architekturu a modelování

Visual Studio 2015 je k dispozici v několika edicích. Ne všechny tyto možnosti poskytují podporu pro architektury a nástroje pro modelování. V následující tabulce je uveden seznam dostupnosti jednotlivých nástrojů.

|**Zapnut**|**Společnosti**|**Pracovní**|**Community**|**Express**|
|-----------------|--------------------|----------------------|-------------------|-----------------|
|**Mapy kódu**|Ano|Podporuje pouze čtení a filtrování map kódu, přidávání nových obecných uzlů a vytvoření nového orientovaného grafu z výběru.|-|-|
|**Diagramy tříd UML**|Ano|-|-|-|
|**Sekvenční diagramy UML**|Ano|-|-|-|
|**Diagramy případů použití UML**|Ano|-|-|-|
|**Diagramy činnosti UML**|Ano|-|-|-|
|**Diagramy komponent UML**|Ano|-|-|-|
|**Diagramy vrstev**|Ano|-|-|-|
|**Orientované grafy** (diagramy DGML)|Ano|Ano|-|-|
|**Klon kódu**|Ano|-|-|-|
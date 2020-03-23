---
title: Co&#39;nového pro design
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302369"
---
# <a name="whats-new-for-design-in-visual-studio-in-visual-studio-2015"></a>Co je nového pro návrh ve Visual Studiu ve Visual Studiu 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Tato verze sady Visual Studio obsahuje následující vylepšení, která vám pomohou lépe pochopit a navrhnout kód.

 **Mapy kódu a grafy závislostí**

 V sadě Visual Studio Enterprise, pokud chcete pochopit konkrétní závislosti ve vašem kódu, vizualizovat je vytvořením mapy kódu. Tyto vztahy pak můžete navigovat pomocí mapy, která se zobrazí vedle vašeho kódu.  Mapy kódu vám také můžou pomoct sledovat své místo v kódu při práci nebo ladění kódu, takže si budete číst méně kódu, zatímco se dozvíte více o návrhu kódu.

 V konečné verzi (RTM) jsme místní nabídky pro prvky kódu a odkazy mnohem snadněji používali seskupením příkazů do oddílů souvisejících s výběrem, úpravami, správou skupin a změnou rozložení obsahu skupiny. Všimněte si taky, že testovací projekty se zobrazují jiným stylem než ostatní projekty a že ikony prvků na mapě jsme aktualizovali, aby byl jejich vzhled vhodnější. 

 ![Zobrazit vybrané položky na novém mapě kódu](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 Další vylepšení zahrnují:

- **Vylepšené diagramy shora dolů**. Pro střední až velká řešení sady Visual Studio teď můžete použít zjednodušenou nabídku Architektura, ve které pro vaše řešení získáte užitečnější mapy kódu.  Sestavení vašeho řešení se seskupují podle složek řešení, takže je můžete vidět v kontextu a využít úsilí, které jste vložili do struktury řešení.  Okamžitě uvidíte odkazy na projekt a sestavení a pak se zobrazí typy propojení.  Externí sestavení vašeho řešení se navíc seskupují kompaktnějším způsobem.

- **Projekty testů mají jiný styl a dají se filtrovat**.  Nyní můžete snadněji a rychleji identifikovat testovací projekty na mapě, protože jsou stylizovány odlišně. Dají se taky odfiltrovat, abyste se mohli zaměřit na funkční kód aplikace.

- **Zjednodušené odkazy externích závislostí**.  Odkazy závislostí už nepředstavují dědičnost z typů System.Object, System.ValueType, System.Enum a System.Delegate. Snadněji tak ve vaší mapě kódu rozpoznáte externí závislosti.

- **Rozdělení na odkazy závislostí zohledňuje filtry**.  Užitečný a jasný diagram získáte, když ho rozbalíte, abyste pochopili příspěvky k odkazu závislostí.  Diagram je méně přeplněný a bere v úvahu vybrané možnosti filtrování odkazů.

- **Prvky kódu jsou přidány do mapy kódu s jejich kontextem**. Vzhledem k tomu, že diagramy se nyní zobrazují s jejich kontextem (až do složky sestavení a řešení, kterou můžete v případě potřeby odfiltrovat), získáte užitečnější diagramy při přetahování prvků kódu z Průzkumníka řešení, zobrazení tříd, prohlížeče objektů; nebo při výběru prvků v Průzkumníku řešení a výběru Zobrazit na mapě kódu.

- **Rychlejší získání reaktivních map kódu**.  Výsledek operací přetažení se dostaví okamžitě a vazby mezi uzly se vytvoří mnohem rychleji, aniž by ovlivnily následné uživatelem iniciované operace, třeba rozbalení uzlu nebo požadavek na víc uzlů.  Když vytváříte mapy kódu bez vytváření řešení, jsou nyní zpracovány všechny rohové případy , které nejsou vytvořeny.

- **Přeskočte přestavbu řešení.** Poskytuje lepší výkon při vytváření a úpravách diagramů.

- **Filtrování skupin a uzlů prvků kódu**.  Svoje mapy můžete rychle zpřehlednit tím, že prvky kódu zobrazíte nebo skryjete na základě jejich kategorie, a taky tím, že prvky kódu seskupíte podle složek řešení, sestavení, oborů názvů, složek projektu a typů.

- **Filtrování vztahů v zájmu větší přehlednosti diagramů**.  Filtrování odkazů se nyní vztahuje také na propojení mezi skupinami, což činí práci s oknem filtru méně rušivou než v předchozích verzích.

- **Vytváření diagramů ze zobrazení tříd a Prohlížeče objektů**.  Soubory a sestavení můžete přetáhnout do nové nebo existující mapy z oken zobrazení tříd a Prohlížeče objektů.

  Viz [Mapovat závislosti napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md).

  **Další změny návrhu a modelování v této verzi:**

- **Diagramy vrstev**. Aktualizujte tyto diagramy pomocí zobrazení tříd a prohlížeče objektů. Abyste splnili požadavky na návrh softwaru, použijte diagramy vrstev k popsání požadovaných závislostí pro váš software.  Udržujte kód konzistentní s tímto návrhem vyhledáním kódu, který nesplňuje tato omezení, a ověřením budoucího kódu s tímto směrným plánem.

- **Diagramy UML**.  Z kódu už nejde vytvářet diagramy tříd UML a sekvenční diagramy.  Můžete je ale pořád vytvářet pomocí nových elementů UML.

- **Průzkumník architektury**. K vytváření diagramů již nelze použít Průzkumníkarchitektury. Ale stále můžete použít Průzkumníka řešení.

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport"></a>Podpora edice pro architekturu a nástroje pro modelování

Visual Studio 2015 je k dispozici v několika vydáních. Ne všechny tyto poskytují podporu pro architekturu a modelování nástroje. V následující tabulce je uvedena dostupnost jednotlivých nástrojů.

|**Funkce**|**Podnik**|**Professional**|**Komunita**|**Express**|
|-----------------|--------------------|----------------------|-------------------|-----------------|
|**Mapy kódu**|Ano|Podporuje pouze čtení a filtrování map kódu, přidávání nových obecných uzlů a vytváření nového řízeného grafu z výběru.|-|-|
|**Diagramy tříd UML**|Ano|-|-|-|
|**Sekvenční diagramy UML**|Ano|-|-|-|
|**Diagramy případu použití UML**|Ano|-|-|-|
|**Diagramy aktivit UML**|Ano|-|-|-|
|**Diagramy komponent UML**|Ano|-|-|-|
|**Diagramy vrstev**|Ano|-|-|-|
|**Orientované grafy** (diagramy DGML)|Ano|Ano|-|-|
|**Klon kódu**|Ano|-|-|-|
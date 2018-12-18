---
title: Co&#39;s nový návrh
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
ms.assetid: 36ab5c17-6dc0-4075-a28e-a0fa49b11260
caps.latest.revision: 34
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 666402a0488fdfd0e09e12e711c9b74b2f3b2fd1
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068118"
---
# <a name="whats-new-for-design-in-visual-studio"></a>Novinky pro programátory ve Visual Studiu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Tato verze sady Visual Studio zahrnuje následující vylepšení vám pomůže lépe pochopit a návrhu kódu.

 **Mapy kódu a grafy závislostí**

 V sadě Visual Studio Enterprise Pokud chcete pochopit specifické závislosti ve vašem kódu, Vizualizujte si je vytvořením map kódu. Tyto vztahy pak můžete Navigovat pomocí mapy, která se zobrazí vedle vašeho kódu. Může také pomoct map kódu můžete sledovat, kde v kódu během práce nebo ladění kódu, zatímco další informace o návrhu vašeho kódu se věnovat čtení menším množstvím kódu.

 V konečné verzi (RTM) jsme používání místních nabídek pro prvky kódu a odkazy zjednodušili tak příkazy seskupili do oddílů souvisejících s výběrem, úpravy, správu skupin a změnami rozložení obsahu skupin. Všimněte si také, že testovací projekty se zobrazují jiným stylem než ostatní projekty a že ikony prvků na mapě aktualizovali vhodnější.

 ![Zobrazit vybrané položky na mapu s novým kódem](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 Mezi další vylepšení patří:

- **Vylepšené vertikální diagramy**. Pro střední až velká řešení sady Visual Studio můžete nyní použít zjednodušenou nabídku architektura získáte užitečnější kód mapy pro vaše řešení. Sestavení vašeho řešení se seskupují podle složek řešení, takže můžete vidět v kontextu a využít úsilí, které jste vložili do struktury řešení. Okamžitě uvidíte projekt a odkazy na sestavení a pak se zobrazí typy propojení. Kromě toho sestavení externí do vašeho řešení se seskupují kompaktnějším způsobem.

- **Projekty testů mají jiný styl a dají se filtrovat**. Teď můžete snadno a rychle identifikovat projekty testů na mapě protože mají jiný styl. Můžete se taky odfiltrovat, aby se mohli soustředit na funkční kód aplikace.

- **Zjednodušené odkazy externích závislostí**. Odkazy závislostí už nepředstavují dědičnost z System.Object, System.ValueType, System.Enum a System.Delegate. Díky tomu snadněji rozpoznáte externí závislosti ve vaší mapě kódu.

- **"Procházení – na odkazy závislostí" zohledňuje filtry**. Užitečný a jasný diagram získáte, když ho rozbalíte, abyste pochopili příspěvky k odkazu závislostí. Diagram není moc zaplněný a zohledňuje možnosti, které jste vybrali filtrování propojení.

- **Prvky kódu se přidávají do mapy kódu s jejich kontextem**. Protože teď diagramy zobrazují se svým kontextem (až po sestavení řešení a složky, která můžete filtrovat podle potřeby), můžete získat užitečnější diagramy při přetažení prvků kódu z Průzkumníka řešení, zobrazení tříd, prohlížeče objektů nebo když vyberete prvky v Průzkumníku řešení a zvolíte zobrazení na mapě kódu.

- **Rychlejší získání reaktivních map kódu**. Operací přetažení výsledek se dostaví okamžitě a vazby mezi uzly se vytvoří mnohem rychleji, aniž by ovlivnily následné uživatelem iniciované operace, třeba rozbalení uzlu nebo požadavek na víc uzlů. Při vytváření map kódu bez sestavování řešení, všechny krajní případy, takové kdy třeba sestavení nejsou vytvořená – se teď zpracují.

- **Přeskočit opětovné sestavování svého řešení.** Poskytuje lepší výkon při vytváření a úpravách diagramů.

- **Filtrování skupin a uzlů prvků kódu**. Můžete rychle zpřehlednit tím vaše mapy zobrazení nebo skrytí prvky kódu na základě jejich kategorie a prvky kódu seskupíte podle složek řešení, sestavení, oborů názvů, složek projektu a typů.

- **Filtrování vztahů v zájmu usnadnění diagramy**. Filtrování vazeb se teď týká i propojení mezi skupinami, takže práce s oknem filtru je teď míň obtěžující než v předchozích verzích.

- **Vytváření diagramů ze zobrazení tříd a prohlížeče objektů**. Přetáhněte a umístěte soubory a sestavení do nové nebo existující mapy z oken zobrazení tříd a prohlížeče objektů.

  Zobrazit [mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md).

  **Další změny návrhu a modelování v této verzi:**

- **Diagramy vrstev**. Zobrazení tříd a prohlížeče objektů tyto diagramy můžete aktualizujte. Abyste splnili požadavky na návrh softwaru, použijte diagramy vrstev k popsání požadovaných závislostí pro váš software. Udržujte kód v souladu s tímto návrhem najděte kód, který nevyhovuje těmto omezením a ověřujte budoucí kód podle tohoto směrného plánu.

- **Diagramy UML**. Můžete už vytvoření diagramů tříd UML a sekvenční diagramy z kódu. Ale můžete pořád vytvářet pomocí nových elementů UML.

- **Průzkumník architektury**. Průzkumník architektury již slouží k vytváření diagramů. Ale můžete pořád použít Průzkumník řešení.

##  <a name="VersionSupport"></a> Podpora edice nástroje architektury a modelování

Visual Studio 2015 je k dispozici v několika edicích. Ne všechny tyto poskytovat podporu pro architektury a nástroje modelování. V následující tabulce jsou uvedeny dostupnost jednotlivých nástrojích.

|**Funkce**|**Enterprise**|**Professional**|**Community**|**Express**|
|-----------------|--------------------|----------------------|-------------------|-----------------|
|**Mapy kódu**|Ano|Podporuje pouze pro čtení a filtrování mapy kódu, přidání nové obecné uzly a vytvoření nového orientovaného grafu z výběru.|-|-|
|**Diagramy tříd UML**|Ano|-|-|-|
|**Sekvence UML diagramů**|Ano|-|-|-|
|**Diagramy případů použití UML**|Ano|-|-|-|
|**Diagramy činnosti UML**|Ano|-|-|-|
|**Diagramy komponent UML**|Ano|-|-|-|
|**Diagramy vrstev**|Ano|-|-|-|
|**Řízených grafů** (diagramy DGML)|Ano|Ano|-|-|
|**Klonování kódu**|Ano|-|-|-|
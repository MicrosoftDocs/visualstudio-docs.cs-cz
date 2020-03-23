---
title: Přejmenování a přesunutí tříd a typů v Návrháři tříd
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.ClassDesigner.OverrideMembersDialog
helpviewer_keywords:
- members, overriding
- overriding members
- classes [Visual Studio], refactoring
- type members, overriding
- refactoring, types
- types [Visual Studio], refactoring
- Class Designer [Visual Studio], refactoring classes
- refactoring, classes
ms.assetid: dcf07bb4-fa3b-4224-9dec-566fd924a8ce
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e060f044af666f5a4357e527819286d3bd87267
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590745"
---
# <a name="refactor-classes-and-types-in-class-designer"></a>Refaktorování tříd a typů v Návrháři tříd

Při refaktorování kódu usnadňujete pochopení, údržbu a efektivnější změnou jeho vnitřní struktury a způsobu, jakým jsou navrženy jeho objekty, nikoli jeho externí chování. Pomocí návrháře tříd a okna Podrobnosti o třídě snížit práci, kterou musíte udělat, a šance na zavedení chyb při refaktorování kódu Jazyka C#, Visual Basic nebo C++ v projektu sady Visual Studio.

> [!NOTE]
> Soubory projektu může být jen pro čtení, protože projekt je pod řízení zdrojového kódu a není rezervován, je odkazovaný projekt nebo jeho soubory jsou označeny jako jen pro čtení na disku. Při práci v projektu v jednom z těchto stavů se zobrazí různé způsoby uložení práce v závislosti na stavu projektu. To platí pro refaktoring kód a také kód, který změníte jiným způsobem, jako je například přímo upravit.

## <a name="common-tasks"></a>Běžné úkoly

|Úkol|Podpůrný obsah|
|----------| - |
|**Třídy refaktoringu:** Operace refaktoringu můžete použít k rozdělení třídy do částečných tříd nebo k implementaci abstraktní základní třídy.|-   [Postup: Rozdělení třídy na částečné třídy](how-to-split-a-class-into-partial-classes.md)|
|**Práce s rozhraními:** V Návrháři tříd můžete implementovat rozhraní v diagramu třídy připojením ke třídě, která poskytuje kód pro metody rozhraní.|-   [Postup: Implementace rozhraní](how-to-implement-an-interface.md)|
|**Typy refaktoringu, členy typu a parametry:** Pomocí Návrháře tříd můžete přejmenovat typy, přepsat členy textu nebo je přesunout z jednoho typu do druhého. Můžete také vytvořit typy s možnou hodnotou null.|-   [Přejmenování typů a členů typu](#rename-types-and-type-members)<br />-   [Přesunutí členů textu z jednoho typu na jiný](#move-type-members-from-one-type-to-another)<br />-   [Postup: Vytvoření typu s možnou hodnotou Null](how-to-create-a-nullable-type.md)|

## <a name="rename-types-and-type-members"></a>Přejmenování typů a členů typu

V Návrháři tříd můžete přejmenovat typ nebo člen typu v diagramu třídy nebo v okně **Vlastnosti.** V okně **Podrobnosti třídy** můžete změnit název člena, ale ne typu. Přejmenování typu nebo člena typu se rozšíří do všech oken a umístění kódu, kde se starý název objevil.

### <a name="rename-in-the-class-designer"></a>Přejmenování v Návrháři tříd

1. V diagramu třídy vyberte typ nebo člen a vyberte název.

     Název člena se stane upravitelným.

2. Zadejte nový název pro typ nebo typ člena.

### <a name="rename-in-the-class-details-window"></a>Přejmenovat v okně Podrobnosti o třídě

1. Chcete-li zobrazit okno **Podrobnosti o třídě,** klepněte pravým tlačítkem myši na typ nebo člen typu a vyberte **položku Podrobnosti třídy**.

     Zobrazí se okno **Podrobnosti o třídě.**

2. Ve sloupci **Název** změňte název člena typu.

3. Chcete-li přesunout fokus mimo buňku, stiskněte klávesu **Enter** nebo klepněte mimo buňku.

    > [!NOTE]
    > V okně **Podrobnosti třídy** můžete změnit název člena, ale ne typu.

### <a name="rename-in-the-properties-window"></a>Přejmenovat v okně Vlastnosti

1. V diagramu třídy nebo v okně **Podrobnosti o třídě** klepněte pravým tlačítkem myši na typ nebo člen a pak vyberte **vlastnosti**.

     Zobrazí se okno **Vlastnosti,** které zobrazí vlastnosti pro typ nebo člena typu.

2. Ve vlastnosti **Name** změňte název typu nebo člena typu.

     Nový název se rozšíří do všech oken a umístění kódu v aktuálním projektu, kde se starý název objevil.

## <a name="move-type-members-from-one-type-to-another"></a>Přesunutí členů textu z jednoho typu na jiný

Pomocí **Návrháře tříd**můžete přesunout člena typu z jednoho typu na jiný typ. Oba typy musí být viditelné v aktuálním diagramu třídy.

1. U typu, který je viditelný na návrhové ploše, klikněte pravým tlačítkem myši na člen, který chcete přesunout na jiný typ, a pak vyberte **Vyjmout**.

2. Klepněte pravým tlačítkem myši na cílový typ a vyberte **vložit**.

     Vlastnost je odebrána ze zdrojového typu a zobrazí se v cílovém typu.

## <a name="see-also"></a>Viz také

- [Navrhování tříd a typů](designing-and-viewing-classes-and-types.md)

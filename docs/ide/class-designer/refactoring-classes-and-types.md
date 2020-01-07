---
title: Přejmenování a přesun tříd a typů v Návrhář tříd
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590745"
---
# <a name="refactor-classes-and-types-in-class-designer"></a>Refaktoring tříd a typů v Návrhář tříd

Při refaktorování kódu je snazší pochopit, udržovat a zefektivnit změnou jeho vnitřní struktury a způsobu návrhu jeho objektů, nikoli vnějšího chování. Pomocí Návrhář tříd a okna podrobností třídy můžete snížit práci, kterou je třeba provést, a šance na představení chyb při refaktorování C#, Visual Basic nebo C++ kódu v projektu sady Visual Studio.

> [!NOTE]
> Soubory projektu mohou být pouze pro čtení, protože projekt je pod správou zdrojového kódu a není rezervován, jedná se o odkazovaný projekt, nebo jeho soubory jsou na disku označeny jako jen pro čtení. Když pracujete v projektu v jednom z těchto stavů, budete mít k dispozici různé způsoby, jak uložit práci v závislosti na stavu projektu. To platí pro refaktoring kódu a také kódu, který změníte jiným způsobem, jako je například přímo v úpravách.

## <a name="common-tasks"></a>Běžné úkoly

|Úloha|Podpůrný obsah|
|----------| - |
|**Třídy refaktoringu:** Operace refaktoringu můžete použít k rozdělení třídy na částečné třídy nebo k implementaci abstraktní základní třídy.|-   [Postupy: rozdělení třídy na částečné třídy](how-to-split-a-class-into-partial-classes.md)|
|**Práce s rozhraními:** V Návrhář tříd můžete implementovat rozhraní v diagramu tříd tím, že ho propojíte s třídou, která poskytuje kód pro metody rozhraní.|-   [Postupy: implementace rozhraní](how-to-implement-an-interface.md)|
|**Refaktoring typů, členů typu a parametrů:** Pomocí Návrhář tříd můžete přejmenovat typy, přepsat členy typu nebo je přesunout z jednoho typu do jiného. Můžete také vytvořit typy s možnou hodnotou null.|-   [Přejmenovat typy a členy typu](#rename-types-and-type-members)<br />-   [Přesunout členy typu z jednoho typu do druhého](#move-type-members-from-one-type-to-another)<br />-   [Postupy: vytvoření typu s možnou hodnotou null](how-to-create-a-nullable-type.md)|

## <a name="rename-types-and-type-members"></a>Přejmenovat typy a členy typu

V Návrhář tříd můžete přejmenovat typ nebo člen typu v diagramu tříd nebo v okně **vlastnosti** . V okně **podrobností třídy** můžete změnit název člena, ale ne typ. Přejmenování typu nebo členu typu se rozšíří do všech oken a umístění kódu, kde se objevil starý název.

### <a name="rename-in-the-class-designer"></a>Přejmenovat v Návrhář tříd

1. V diagramu tříd vyberte typ nebo člen a vyberte název.

     Název člena se bude upravovat.

2. Zadejte nový název pro typ nebo člen typu.

### <a name="rename-in-the-class-details-window"></a>Přejmenovat v okně podrobností třídy

1. Chcete-li zobrazit okno **podrobností třídy** , klikněte pravým tlačítkem myši na typ nebo člen typu a vyberte položku **Podrobnosti třídy**.

     Zobrazí se okno **Podrobnosti třídy** .

2. Ve sloupci **název** změňte název typu členu.

3. Pokud chcete přesunout fokus z buňky, stiskněte klávesu **ENTER** nebo klikněte na pryč z buňky.

    > [!NOTE]
    > V okně **podrobností třídy** můžete změnit název člena, ale ne typ.

### <a name="rename-in-the-properties-window"></a>Přejmenovat v okno Vlastnosti

1. V diagramu tříd nebo v okně **podrobností třídy** klikněte pravým tlačítkem na typ nebo člen a pak vyberte **vlastnosti**.

     Zobrazí se okno **vlastnosti** , ve kterém se zobrazí vlastnosti pro typ nebo člen typu.

2. Ve vlastnosti **Name** změňte název typu nebo členu typu.

     Nový název se rozšíří do všech oken a umístění kódu v aktuálním projektu, ve kterém se objevil starý název.

## <a name="move-type-members-from-one-type-to-another"></a>Přesunout členy typu z jednoho typu na jiný

Pomocí **Návrhář tříd**můžete přesunout člena typu z jednoho typu na jiný typ. Oba typy musí být viditelné v aktuálním diagramu tříd.

1. V typu, který je viditelný na návrhové ploše, klikněte pravým tlačítkem na člen, který chcete přesunout na jiný typ, a pak vyberte **Vyjmout**.

2. Klikněte pravým tlačítkem na cílový typ a vyberte **Vložit**.

     Vlastnost je odebrána ze zdrojového typu a zobrazí se v cílovém typu.

## <a name="see-also"></a>Viz také:

- [Navrhování tříd a typů](designing-and-viewing-classes-and-types.md)

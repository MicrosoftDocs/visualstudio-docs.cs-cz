---
title: Refaktoring tříd a typů (Návrhář tříd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5803b720ae1271d8319310820d1f0dc159db8bf9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670271"
---
# <a name="refactoring-classes-and-types-class-designer"></a>Refaktoring tříd a typů (návrhář tříd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při refaktorování kódu je snazší pochopit, udržovat a zefektivnit změnou jeho vnitřní struktury a způsobu návrhu jeho objektů, nikoli vnějšího chování. Pomocí Návrhář tříd a okna podrobností třídy můžete snížit práci, kterou je třeba provést, a šance na zavedení chyb při refaktorování Visual C# .net, Visual Basic .NET nebo C++ kódu v projektu sady Visual Studio.

> [!NOTE]
> Soubory projektu mohou být pouze pro čtení, protože projekt je v rámci správy zdrojového kódu a není rezervován; je to odkazovaný projekt; nebo jsou soubory na disku označeny jako jen pro čtení. Když pracujete v projektu v jednom z těchto stavů, budete mít k dispozici různé způsoby, jak uložit práci v závislosti na stavu projektu. To platí pro refaktoring kódu a také kódu, který změníte jiným způsobem, jako je například přímo v úpravách. Další informace najdete v tématu [zobrazení informací jen pro čtení (návrhář tříd)](https://msdn.microsoft.com/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).

## <a name="common-tasks"></a>Obecné úlohy

|Úloha|Podpůrný obsah|
|----------|------------------------|
|**Třídy refaktoringu:** Operace refaktoringu můžete použít k rozdělení třídy na částečné třídy nebo k implementaci abstraktní základní třídy.|-   [Postupy: rozdělení třídy na částečné třídy (návrhář tříd)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md)|
|**Práce s rozhraními:** V Návrhář tříd můžete implementovat rozhraní v diagramu tříd tím, že ho propojíte s třídou, která poskytuje kód pro metody rozhraní.|-   [Postupy: implementace rozhraní (návrhář tříd)](../ide/how-to-implement-an-interface-class-designer.md)|
|**Refaktoring typů, členů typu a parametrů:** Pomocí Návrhář tříd můžete přejmenovat typy, přepsat členy typu nebo je přesunout z jednoho typu do jiného. Můžete také vytvořit typy s možnou hodnotou null.|-   [přejmenování typů a členů typu](../ide/refactoring-classes-and-types-class-designer.md#RenamingTypesAndMembers)<br />-   [přesunu členů typu z jednoho typu do druhého](../ide/refactoring-classes-and-types-class-designer.md#MovingTypeMembers) .<br />-   [Postupy: vytvoření typu s možnou hodnotou null (návrhář tříd)](../ide/how-to-create-a-nullable-type-class-designer.md)|

### <a name="RenamingTypesAndMembers"></a>Přejmenování typů a členů typu
 V Návrhář tříd můžete přejmenovat typ nebo člen typu v diagramu tříd nebo v okno Vlastnosti. V okně podrobností třídy můžete změnit název člena, ale ne typ. Přejmenování typu nebo členu typu se rozšíří do všech oken a umístění kódu, kde se objevil starý název.

##### <a name="to-rename-a-name-in-the-class-designer"></a>Přejmenování názvu v Návrhář tříd

1. V diagramu tříd vyberte typ nebo člen a klikněte na název.

     Název člena se bude upravovat.

2. Zadejte nový název pro typ nebo člen typu.

##### <a name="to-rename-a-name-in-the-class-details-window"></a>Přejmenování názvu v Okno podrobností třídy

1. Chcete-li zobrazit okno podrobností třídy, klikněte pravým tlačítkem myši na typ nebo člen typu a poté klikněte na položku **Podrobnosti třídy**.

     Zobrazí se okno Podrobnosti třídy.

2. Ve sloupci **název** změňte název typu členu.

3. Pokud chcete přesunout fokus z buňky, stiskněte klávesu **ENTER** nebo klikněte na pryč z buňky.

    > [!NOTE]
    > V okně podrobností třídy můžete změnit název člena, ale ne typ.

##### <a name="to-rename-a-name-in-the-properties-window"></a>Přejmenování názvu v okno Vlastnosti

1. V diagramu tříd nebo v okně podrobností třídy klikněte pravým tlačítkem na typ nebo člen a pak klikněte na **vlastnosti**.

     Zobrazí se okno Vlastnosti a zobrazí vlastnosti pro typ nebo člen typu.

2. Ve vlastnosti **Name** změňte název typu nebo členu typu.

     Nový název se rozšíří do všech oken a umístění kódu v aktuálním projektu, ve kterém se objevil starý název.

### <a name="MovingTypeMembers"></a>Přesun členů typu z jednoho typu na jiný
 Pomocí **Návrhář tříd**lze přesunout člen typu z jednoho typu na jiný typ, pokud jsou obě zobrazeny v aktuálním diagramu třídy.

##### <a name="to-move-a-type-member-from-one-type-to-another"></a>Přesunutí člena typu z jednoho typu na jiný

1. V typu, který je viditelný na návrhové ploše, klikněte pravým tlačítkem na člen, který chcete přesunout na jiný typ, a potom klikněte na **Vyjmout**.

2. Klikněte pravým tlačítkem na cílový typ a pak klikněte na **Vložit**.

     Vlastnost je odebrána ze zdrojového typu a zobrazí se v cílovém typu.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Zobrazování typů a vztahů (Návrhář tříd)](../ide/viewing-types-and-relationships-class-designer.md)||
|[Navrhování tříd a typů (Návrhář tříd)](../ide/designing-classes-and-types-class-designer.md)||

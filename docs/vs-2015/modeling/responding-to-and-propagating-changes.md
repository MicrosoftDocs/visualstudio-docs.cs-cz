---
title: Reagování na změny a šíření změn | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: fc2e9ac5-7a84-44ed-9945-94e45f89c227
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b216e89e6a04fb38537f9c45336d07cf6df4abdc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671274"
---
# <a name="responding-to-and-propagating-changes"></a>Reagování na změny a šíření změn
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při vytvoření, odstranění nebo aktualizaci prvku můžete napsat kód, který šíří změnu do jiných částí modelu, nebo do externích prostředků, jako jsou soubory, databáze nebo jiné komponenty.

## <a name="in-this-section"></a>V tomto oddílu
 Jako vodítko zvažte tyto techniky v uvedeném pořadí:

|Hlediska|Scénáře|Další informace|
|---------------|---------------|--------------------------|
|Definujte vlastnost počítané domény.|Doménová vlastnost, jejíž hodnota je počítána z jiných vlastností v modelu. Například cena, která je součtem cen souvisejících prvků.|[Vypočtené a vlastní vlastnosti úložiště](../modeling/calculated-and-custom-storage-properties.md)|
|Definujte vlastní vlastnost domény úložiště.|Doménová vlastnost uložená v jiných částech modelu nebo externě. Například můžete analyzovat řetězec výrazu do stromové struktury v modelu.|[Vypočtené a vlastní vlastnosti úložiště](../modeling/calculated-and-custom-storage-properties.md)|
|Přepište obslužné rutiny změn, jako je OnValueChanging a při odstraňování|Udržujte různé prvky synchronizované a udržujte externí hodnoty synchronizované s modelem.<br /><br /> Omezte hodnoty na definované rozsahy.<br /><br /> Volá se bezprostředně před a po hodnotě vlastnosti a dalšími změnami. Změnu můžete ukončit vyvoláním výjimky.|[Obslužné rutiny změny hodnoty vlastnosti domény](../modeling/domain-property-value-change-handlers.md)|
|Pravidly|Můžete definovat pravidla, která jsou zařazená do fronty pro spuštění těsně před koncem transakce, ve které došlo ke změně. Neprovádějí se při vrácení akce zpět nebo opakování. Použijte je k udržení jednoho dílu úložiště v synchronizaci s jiným.|[Pravidla šířící změny v modelu](../modeling/rules-propagate-changes-within-the-model.md)|
|Ukládat události|Úložiště modelování poskytuje oznámení o událostech, jako je například přidání nebo odstranění prvku nebo propojení nebo změna hodnoty vlastnosti. Událost se také spustí při vrácení akce zpět a znovu. Pomocí událostí úložiště aktualizujete hodnoty, které nejsou ve Storu.|[Obslužné rutiny události šířící změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|Události .NET|Obrazce mají obslužné rutiny událostí, které reagují na kliknutí myší a další gesta. Musíte se zaregistrovat pro tyto události pro každý objekt. Registrace se obvykle provádí v přepsání InitializeInstanceResources a musí se provést pro každý prvek.<br /><br /> K těmto událostem obvykle dochází mimo transakci.|[Postupy: Zachycení kliknutí na obrazec nebo dekorátor](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|Pravidla vazeb|Pravidlo vázané na hranice se používá konkrétně k omezení hranic tvaru.|[Umístění a velikost obrazce omezení BoundsRules](../modeling/boundsrules-constrain-shape-location-and-size.md)|
|Pravidla výběru|Pravidla výběru výslovně omezí, co může uživatel vybrat.|[Postupy: Přístup k aktuálnímu výběru a jeho omezení](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|Určete stavy prvků modelu pomocí funkcí tvarů a konektorů, jako jsou stíny, šipky, barva a tloušťka čáry a styl.|[Aktualizace obrazců a konektorů k vyjádření modelu](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="comparing-rules-and-store-events"></a>**Porovnávání pravidel a událostí úložiště**
 Změny událostí, pravidla a události se spustí, když dojde ke změnám v modelu.

 Pravidla jsou obvykle použita na konci transakce, ve které došlo ke změně, a po provedení změn v transakci jsou aplikovány události.

 Pomocí událostí úložiště můžete synchronizovat model s objekty mimo úložiště a pravidla zachovat konzistenci v rámci úložiště.

- **Vytváření vlastních pravidel** Vlastní pravidlo vytvoříte jako odvozenou třídu z abstraktního pravidla. Také je nutné upozornit rozhraní na vlastní pravidlo. Další informace najdete v tématu [pravidla šířící změny v modelu](../modeling/rules-propagate-changes-within-the-model.md).

- **Přihlášení k odběru událostí** Předtím, než se můžete přihlásit k odběru události, vytvořte obslužnou rutinu události a delegáta. Pak použijte <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>property k přihlášení k odběru události. Další informace najdete v tématu [obslužné rutiny událostí rozšiřovat změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md).

- **Rušení změn** Při vrácení transakce zpět dojde k události, ale pravidla se nepoužívají. Pokud pravidlo změní hodnotu a tuto změnu zrušíte, v rámci akce vrátit se hodnota obnoví na původní hodnotu. Při vyvolání události je nutné ručně změnit hodnotu zpět na původní hodnotu. Další informace o transactons a vrácení zpět naleznete v tématu [How to: use Transactions to Update a model](../modeling/how-to-use-transactions-to-update-the-model.md).

- **Předávání argumentů události pravidlům a událostem** Událostem i pravidlům jsou předány `EventArgs` parametr, který obsahuje informace o tom, jak se model změnil.

## <a name="see-also"></a>Viz také
 [Postupy: zachycení kliknutí na obrazec nebo dekoratér](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md) [psaní kódu pro přizpůsobení jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md)

---
title: Reagování na změny a šíření změn
description: Přečtěte si, že při vytvoření, odstranění nebo aktualizaci prvku můžete napsat kód, který šíří změnu do jiných částí modelu nebo do externích prostředků.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e44def032854e46b00638cff77c8bea91eb0f09
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360609"
---
# <a name="respond-to-and-propagate-changes"></a>Reagování na změny a šíření změn

Při vytvoření, odstranění nebo aktualizaci prvku můžete napsat kód, který šíří změnu do jiných částí modelu, nebo do externích prostředků, jako jsou soubory, databáze nebo jiné komponenty.

## <a name="reference"></a>Referenční informace

Jako vodítko zvažte tyto techniky v uvedeném pořadí:

|Technika|Scénáře|Další informace|
|-|-|-|
|Definujte vlastnost počítané domény.|Doménová vlastnost, jejíž hodnota je počítána z jiných vlastností v modelu. Například cena, která je součtem cen souvisejících prvků.|[Vypočtené a vlastní vlastnosti úložiště](../modeling/calculated-and-custom-storage-properties.md)|
|Definujte vlastní vlastnost domény úložiště.|Doménová vlastnost uložená v jiných částech modelu nebo externě. Například můžete analyzovat řetězec výrazu do stromové struktury v modelu.|[Vypočtené a vlastní vlastnosti úložiště](../modeling/calculated-and-custom-storage-properties.md)|
|Přepište obslužné rutiny změn, jako je OnValueChanging a při odstraňování|Udržujte různé prvky synchronizované a udržujte externí hodnoty synchronizované s modelem.<br /><br /> Omezte hodnoty na definované rozsahy.<br /><br /> Volá se bezprostředně před a po hodnotě vlastnosti a dalšími změnami. Změnu můžete ukončit vyvoláním výjimky.|[Obslužné rutiny změny hodnoty vlastnosti domény](../modeling/domain-property-value-change-handlers.md)|
|Pravidla|Můžete definovat pravidla, která jsou zařazená do fronty pro spuštění těsně před koncem transakce, ve které došlo ke změně. Neprovádějí se při vrácení akce zpět nebo opakování. Použijte je k udržení jednoho dílu úložiště v synchronizaci s jiným.|[Pravidla šířící změny v modelu](../modeling/rules-propagate-changes-within-the-model.md)|
|Ukládat události|Úložiště modelování poskytuje oznámení o událostech, jako je například přidání nebo odstranění prvku nebo propojení nebo změna hodnoty vlastnosti. Událost se také spustí při vrácení akce zpět a znovu. Pomocí událostí úložiště aktualizujete hodnoty, které nejsou ve Storu.|[Obslužné rutiny události šířící změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|Události .NET|Obrazce mají obslužné rutiny událostí, které reagují na kliknutí myší a další gesta. Musíte se zaregistrovat pro tyto události pro každý objekt. Registrace se obvykle provádí v přepsání InitializeInstanceResources a musí se provést pro každý prvek.<br /><br /> K těmto událostem obvykle dochází mimo transakci.|[Postupy: Zachycení kliknutí na obrazec nebo dekorátor](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|Pravidla vazeb|Pravidlo vázané na hranice se používá konkrétně k omezení hranic tvaru.|[Umístění a velikost obrazce omezení BoundsRules](/previous-versions/visualstudio/visual-studio-2015/modeling/boundsrules-constrain-shape-location-and-size?preserve-view=true&view=vs-2015)|
|Pravidla výběru|Pravidla výběru výslovně omezí, co může uživatel vybrat.|[Postupy: Přístup k aktuálnímu výběru a jeho omezení](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|Určete stavy prvků modelu pomocí funkcí tvarů a konektorů, jako jsou stíny, šipky, barva a tloušťka čáry a styl.|[Aktualizace obrazců a konektorů k vyjádření modelu](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="compare-rules-and-store-events"></a>Porovnání pravidel a událostí úložiště

Změny událostí, pravidla a události se spustí, když dojde ke změnám v modelu.

Pravidla jsou obvykle použita na konci transakce, ve které došlo ke změně, a po provedení změn v transakci jsou aplikovány události.

Pomocí událostí úložiště můžete synchronizovat model s objekty mimo úložiště a pravidla zachovat konzistenci v rámci úložiště.

- **Vytváření vlastních pravidel** Vlastní pravidlo vytvoříte jako odvozenou třídu z abstraktního pravidla. Také je nutné upozornit rozhraní na vlastní pravidlo. Další informace najdete v tématu [pravidla šířící změny v modelu](../modeling/rules-propagate-changes-within-the-model.md).

- **Přihlášení k odběru událostí** Předtím, než se můžete přihlásit k odběru události, vytvořte obslužnou rutinu události a delegáta. Pak použijte <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A> vlastnost k přihlášení k odběru události. Další informace najdete v tématu [obslužné rutiny událostí rozšiřovat změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md).

- **Rušení změn** Při vrácení transakce zpět dojde k události, ale pravidla se nepoužívají. Pokud pravidlo změní hodnotu a tuto změnu zrušíte, v rámci akce vrátit se hodnota obnoví na původní hodnotu. Při vyvolání události je nutné ručně změnit hodnotu zpět na původní hodnotu. Další informace o transakcích a vrácení zpět naleznete v tématu [How to: use Transactions to Update a model](../modeling/how-to-use-transactions-to-update-the-model.md).

- **Předávání argumentů události pravidlům a událostem** Události a pravidla jsou předány `EventArgs` parametr, který obsahuje informace o tom, jak se model změnil.

## <a name="see-also"></a>Viz také:

- [Postupy: Zachycení kliknutí na obrazec nebo dekorátor](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)
- [Psaní kódu pro přizpůsobení Domain-Specificho jazyka](../modeling/writing-code-to-customise-a-domain-specific-language.md)
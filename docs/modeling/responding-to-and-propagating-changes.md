---
title: Reagování na změny a šíření změn
description: Zjistěte, že při vytvoření, odstranění nebo aktualizaci elementu můžete napsat kód, který změnu rozšíří do jiných částí modelu nebo do externích prostředků.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6fc8345ca90414f410dde9a089d9529ed19536b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387577"
---
# <a name="respond-to-and-propagate-changes"></a>Reakce na změny a jejich šíření

Při vytvoření, odstranění nebo aktualizaci prvku můžete napsat kód, který změnu rozšíří do jiných částí modelu nebo do externích prostředků, jako jsou soubory, databáze nebo jiné komponenty.

## <a name="reference"></a>Reference

Jako vodítko zvažte tyto techniky v následujícím pořadí:

|Technika|Scénáře|Další informace|
|-|-|-|
|Definujte vlastnost počítané domény.|Vlastnost domény, jejíž hodnota se počítá z jiných vlastností v modelu. Například cena, která je součtem cen souvisejících prvků.|[Vypočtené a vlastní vlastnosti úložiště](../modeling/calculated-and-custom-storage-properties.md)|
|Definujte vlastnost vlastní domény úložiště.|Vlastnost domény uložená v jiných částech modelu nebo externě. Můžete například parsovat řetězec výrazu do stromu v modelu.|[Vypočtené a vlastní vlastnosti úložiště](../modeling/calculated-and-custom-storage-properties.md)|
|Přepsání obslužných rutin změn, jako jsou OnValueChanging a OnDeleting|Udržujte různé prvky synchronizované a udržujte externí hodnoty synchronizované s modelem.<br /><br /> Omezte hodnoty na definované rozsahy.<br /><br /> Volá se bezprostředně před a po hodnotě vlastnosti a dalších změnách. Změnu můžete ukončit vyvoláním výjimky.|[Obslužné rutiny změny hodnoty vlastnosti domény](../modeling/domain-property-value-change-handlers.md)|
|Pravidla|Můžete definovat pravidla, která se zařadit do fronty pro provádění těsně před koncem transakce, ve které došlo ke změně. Nejsou spouštěny při vrácení zpět nebo znovu. Používejte je k podržíte jednu část obchodu v synchronizované s jinou.|[Pravidla šířící změny v modelu](../modeling/rules-propagate-changes-within-the-model.md)|
|Store Events|Úložiště modelování poskytuje oznámení o událostech, jako je přidání nebo odstranění prvku nebo propojení nebo změna hodnoty vlastnosti. Událost se také spustí při příkazu Zpět a Znovu. Události úložiště použijte k aktualizaci hodnot, které nejsou v obchodě.|[Obslužné rutiny události šířící změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|Události rozhraní .NET|Obrazce mají obslužné rutiny událostí, které reagují na kliknutí myší a další gesta. Tyto události musíte zaregistrovat pro každý objekt. Registrace se obvykle provádí v přepsání InitializeInstanceResources a musí se provést pro každý prvek.<br /><br /> K těmto událostem obvykle dochází mimo transakci.|[Postupy: Zachycení kliknutí na obrazec nebo dekorátor](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|Pravidla meze|Pravidlo meze se používá speciálně k omezení meze obrazce.|[Umístění a velikost obrazce omezení BoundsRules](/previous-versions/visualstudio/visual-studio-2015/modeling/boundsrules-constrain-shape-location-and-size?preserve-view=true&view=vs-2015)|
|Pravidla výběru|Pravidla výběru konkrétně omezují, co může uživatel vybrat.|[Postupy: Přístup k aktuálnímu výběru a jeho omezení](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|Označte stavy prvků modelu pomocí vlastností tvarů a konektorů, jako jsou stín, šipky, barva a šířka linií a styl.|[Aktualizace obrazců a konektorů k vyjádření modelu](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="compare-rules-and-store-events"></a>Porovnání pravidel a ukládání událostí

Když v modelu dojde ke změnám, spustí se změna notifikátorů, pravidel a událostí.

Pravidla se obvykle používají na konci transakce, ve které došlo ke změně, a události jsou použity po potvrzení změn v transakci.

Události úložiště slouží k synchronizaci modelu s objekty mimo Store a pravidly pro zachování konzistence v rámci úložiště.

- **Vytváření vlastních pravidel** Vlastní pravidlo vytvoříte jako odvozenou třídu z abstraktního pravidla. Musíte také upozornit rozhraní na vlastní pravidlo. Další informace najdete v tématu [Pravidla šíří změny v rámci modelu.](../modeling/rules-propagate-changes-within-the-model.md)

- **Přihlášení k odběru událostí** Než se můžete přihlásit k odběru události, vytvořte obslužnou rutinu události a delegáta. Pak použijte <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A> vlastnost k přihlášení k odběru události. Další informace najdete v tématu [Obslužné rutiny událostí šíří změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md).

- **Vrácení změn zpět** Když vrátíte zpět transakci, jsou vyvolány události, ale pravidla nejsou použita. Pokud pravidlo změní hodnotu a tato změna se vrátí zpět, hodnota se během akce vrácení zpět resetuje na původní hodnotu. Když je vyvolána událost, je nutné ručně změnit hodnotu zpět na původní hodnotu. Další informace o transakcích a jejich vrácení zpět najdete v tématu [Postupy: Použití transakcí k aktualizaci modelu.](../modeling/how-to-use-transactions-to-update-the-model.md)

- **Předávání argumentů událostí pravidlům a událostem** Události i pravidla se předá `EventArgs` parametr, který obsahuje informace o tom, jak se model změnil.

## <a name="see-also"></a>Viz také

- [Postupy: Zachycení kliknutí na obrazec nebo dekorátor](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)
- [Psaní kódu pro přizpůsobení Domain-Specific jazyka](../modeling/writing-code-to-customise-a-domain-specific-language.md)
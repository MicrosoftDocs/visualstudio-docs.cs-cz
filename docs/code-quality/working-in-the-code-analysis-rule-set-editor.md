---
title: Použití editoru sad pravidel analýzy kódu
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffaf964b24fea41d8e364d610806ba92980b1dc7
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659176"
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Použití editoru sad pravidel pro analýzu kódu

Editor sady pravidel nástroje Analýza kódu umožňuje zadat pravidla, která jsou součástí vlastní sady pravidel, a nastavit závažnost porušení pravidel.

V následující tabulce jsou uvedeny možnosti závažnosti:

|Akce (závažnost)|Description|
|-|-|
|Upozornění|Vygeneruje upozornění v **Seznam chyb** a také v čase sestavení.|
|Chyba|Vygeneruje chybu v **Seznam chyb** a také v čase sestavení.|
|Informace|Vygeneruje zprávu v **Seznam chyb**.|
|Skrytý|Toto porušení není pro uživatele viditelné. Integrované vývojové prostředí (IDE) je však oznámeno porušení.|
|Žádné|Pravidlo je potlačeno. Chování je stejné jako při odebrání pravidla ze sady pravidel.|

Editor zobrazuje pravidla ve stromové struktuře, která seskupují pravidla podle zadaného pole sady pravidel. Chcete-li přidat nebo odebrat pravidla ze sady pravidel, proveďte jeden nebo více následujících kroků:

- Zaškrtnutím nebo zrušením zaškrtnutí políčka uzlu skupiny přidejte nebo odeberte všechna pravidla ve skupině. Když vyberete skupinu, všechna pravidla se nastaví na akci **Upozornění** .

   > [!TIP]
   > Způsob seskupení pravidel můžete změnit v rozevíracím seznamu **Seskupit podle** .

- Klikněte na pole **Akce** skupiny a zadejte akci, která se má použít pro všechna pravidla ve skupině.

- Zaškrtněte nebo zrušte zaškrtnutí políčka pro jednotlivá pravidla. Když zaškrtnete políčko pro pravidlo, pravidlo je nastaveno na akci **Upozornění** .

## <a name="toolbar"></a>Panel nástrojů

Panel nástrojů editoru sady pravidel můžete použít k seskupení, filtrování a hledání dat, která se zobrazí v mřížce sady pravidel.

Následující tabulka popisuje ovládací prvky na panelu nástrojů editoru sady pravidel.

|Ovládací prvek Toolbar|Description|
|---------------------|-----------------|
|**Rozbalit vše**|Zobrazuje pravidla ve všech skupinách.|
|**Sbalit vše**|Skryje pravidla ve všech skupinách.|
|**Seskupit podle**|Určuje pole, podle kterého se pravidla seskupují. Kliknutím **\<None>** zobrazíte pravidla bez skupin.|
|**Možnosti sloupců**|Určuje pole pravidla, která se mají zobrazit.|
|**Skrýt pravidla, která se nevztahují na aktuální řešení**|Zobrazí nebo skryje pravidla, která nejsou stejného cílového typu jako řešení.|
|**Zobrazit pravidla, která mohou generovat chyby analýzy kódu**|Zobrazí nebo skryje pravidla, kterým je přiřazena akce chyby.|
|**Zobrazit pravidla, která mohou generovat upozornění analýzy kódu**|Zobrazí nebo skryje pravidla, kterým je přiřazena akce upozornění.|
|**Zobrazit nepovolená pravidla**|Zobrazí nebo skryje pravidla, která mají přiřazenou akci None.|
|**Přidat nebo odebrat podřízené sady pravidel**|Přidá nebo odebere pravidla ve vybraných sadách pravidel.|
|**Vyhledat pravidla**|Vyhledá všechny hodnoty polí zadaného řetězce.|

## <a name="rule-set-fields"></a>Pole sady pravidel

Pole sady pravidel zobrazují informace o sadě pravidel a lze je použít k řazení a seskupení seznamu pravidel. Chcete-li zobrazit nebo skrýt pole, vyberte **Možnosti sloupců** na panelu nástrojů editoru sad pravidel a zaškrtněte nebo zrušte zaškrtnutí políček u polí, která chcete zobrazit nebo skrýt.

V následující tabulce jsou popsána pole sady pravidel:

|Pole|Description|
|-----------|-----------------|
|**ÚČET**|Identifikátor pravidla|
|**Kategorie**|Kromě jejich členství v sadách pravidel se pravidla analýzy kódu také seskupují podle kategorií. Další informace najdete v tématu [upozornění analýzy kódu](/dotnet/fundamentals/code-analysis/quality-rules/index).|
|**Název**|Název pravidla|
|**Obor názvů**|Obor názvů pravidla|
|**Cílový typ**|Označuje, zda je pravidlo pro nativní, spravovaný nebo databázový kód.|
|**Akce**|Akce provedená v případě porušení pravidla při spuštění analýzy kódu. Můžete upravit pole **Akce** .|
|**Zdrojové sady pravidel**|Sada pravidel, která obsahuje pravidlo|

## <a name="sort-and-filter-rule-sets"></a>Řazení a filtrování sad pravidel

Z záhlaví sloupců mřížky sady pravidel můžete seřadit a filtrovat pravidla podle hodnot pole.

- Pokud chcete seznam sad pravidel seřadit, vyberte záhlaví sloupce pole, podle kterého chcete řadit. Pokud jsou sady pravidel seskupené, jednotlivé skupiny se jednotlivě seřadí.

- Chcete-li filtrovat sady pravidel podle hodnoty pole, vyberte tlačítko Filtr v záhlaví sloupce pole, podle kterého chcete filtrovat. Zaškrtněte políčka u hodnot, které chcete zobrazit, a zrušte zaškrtnutí políček u hodnot, které chcete skrýt.

## <a name="see-also"></a>Viz také

- [Vytvoření vlastní sady pravidel](../code-quality/how-to-create-a-custom-rule-set.md)

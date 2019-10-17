---
title: Použití editoru sad pravidel pro analýzu kódu
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3672d2c85a8da9f8e249da33311d780391d43401
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72445581"
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Použití editoru sad pravidel pro analýzu kódu

Editor sady pravidel nástroje Analýza kódu umožňuje zadat pravidla, která jsou součástí vlastní sady pravidel, a nastavit závažnost porušení pravidel.

V následující tabulce jsou uvedeny možnosti závažnosti:

|Akce (závažnost)|Popis|
|-|-|
|Upozornění|Vygeneruje upozornění v **Seznam chyb** a také v čase sestavení.|
|Chyba|Vygeneruje chybu v **Seznam chyb** a také v čase sestavení.|
|Informace o|Vygeneruje zprávu v **Seznam chyb**.|
|Hidden|Toto porušení není pro uživatele viditelné. Integrované vývojové prostředí (IDE) je však oznámeno porušení.|
|Žádné|Pravidlo je potlačeno. Chování je stejné jako při odebrání pravidla ze sady pravidel.|

Editor zobrazuje pravidla ve stromové struktuře, která seskupují pravidla podle zadaného pole sady pravidel. Chcete-li přidat nebo odebrat pravidla ze sady pravidel, proveďte jeden nebo více následujících kroků:

- Zaškrtnutím nebo zrušením zaškrtnutí políčka uzlu skupiny přidejte nebo odeberte všechna pravidla ve skupině. Když vyberete skupinu, všechna pravidla se nastaví na akci **Upozornění** .

   > [!TIP]
   > Způsob seskupení pravidel můžete změnit v rozevíracím seznamu **Seskupit podle** .

- Klikněte na pole **Akce** skupiny a pak zadejte akci, která se má použít pro všechna pravidla ve skupině.

- Zaškrtněte nebo zrušte zaškrtnutí políčka pro jednotlivá pravidla. Když zaškrtnete políčko pro pravidlo, pravidlo je nastaveno na akci upozornění.

## <a name="toolbar"></a>Panel nástrojů

Panel nástrojů editoru sady pravidel můžete použít k seskupení, filtrování a hledání dat, která se zobrazí v mřížce sady pravidel.

Následující tabulka popisuje ovládací prvky na panelu nástrojů editoru sady pravidel.

|Ovládací prvek Toolbar|Popis|
|---------------------|-----------------|
|**Rozbalit vše**|Zobrazuje pravidla ve všech skupinách.|
|**Sbalit vše**|Skryje pravidla ve všech skupinách.|
|**Seskupit podle**|Určuje pole, podle kterého se pravidla seskupují. Kliknutím na **\<None >** zobrazíte pravidla bez skupin.|
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

|Pole|Popis|
|-----------|-----------------|
|**ÚČET**|Identifikátor pravidla|
|**Kategorií**|Kromě jejich členství v sadách pravidel se pravidla analýzy kódu také seskupují podle kategorií. Další informace najdete v tématu [upozornění analýzy kódu](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Jméno**|Název pravidla|
|**Hosting**|Obor názvů pravidla|
|**Cílový typ**|Označuje, zda je pravidlo pro nativní, spravovaný nebo databázový kód.|
|**Kroky**|Akce provedená v případě porušení pravidla při spuštění analýzy kódu. Můžete upravit pole **Akce** .|
|**Zdrojové sady pravidel**|Sada pravidel, která obsahuje pravidlo|

## <a name="sort-and-filter-rule-sets"></a>Řazení a filtrování sad pravidel

Z záhlaví sloupců mřížky sady pravidel můžete seřadit a filtrovat pravidla podle hodnot pole.

- Pokud chcete seznam sad pravidel seřadit, klikněte na záhlaví sloupce pole, podle kterého chcete řadit. Pokud jsou sady pravidel seskupené, jednotlivé skupiny se jednotlivě seřadí.

- Chcete-li filtrovat sady pravidel podle hodnoty pole, klikněte na tlačítko Filtr v záhlaví sloupce pole, podle kterého chcete filtrovat. Zaškrtněte políčka u hodnot, které chcete zobrazit, a zrušte zaškrtnutí políček u hodnot, které chcete skrýt.

## <a name="see-also"></a>Viz také:

- [Vytvoření vlastní sady pravidel](../code-quality/how-to-create-a-custom-rule-set.md)

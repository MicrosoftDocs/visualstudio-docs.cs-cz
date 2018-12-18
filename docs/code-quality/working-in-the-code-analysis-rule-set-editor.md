---
title: Použití editoru sad pravidel analýzy kódu
ms.date: 04/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdd80031530049b204c0befc445c1416aa08b43e
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000813"
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Použití editoru sad pravidel analýzy kódu

Pravidel nástroje Analýza kódu nastavit editor umožňuje určit pravidla, která jsou součástí vlastní pravidlo nastavit a nastavit závažnost porušení pravidel.

V následující tabulce jsou uvedeny možnosti závažnost:

|Akce (závažnost)|Popis|
|-|-|
|Upozornění|Vygeneruje upozornění v **seznam chyb** a také v okamžiku sestavení.|
|Chyba|Dojde k chybě v **seznam chyb** a také v okamžiku sestavení.|
|Informace o|Generuje zprávu ve **seznam chyb**.|
|Hidden|Porušení zásad není viditelné pro uživatele. Rozhraní IDE je informováni o porušení zásad, ale.|
|Žádné|Toto pravidlo je potlačeno. Chování je stejné jako v případě, že pravidlo se odebral ze sady pravidel.|

Editor zobrazí pravidla ve stromové struktuře, která skupiny pravidla pomocí pravidla nastavena pole, které určíte. Chcete-li přidat nebo odebrat pravidla sadu pravidel, proveďte jeden nebo více z následujících kroků:

- Zaškrtněte nebo zrušte zaškrtnutí políček u uzlu skupiny pro přidání nebo odebrání všech pravidel ve skupině. Když vyberete skupinu, všechna pravidla jsou nastaveny na **upozornění** akce.

   > [!TIP]
   > Můžete změnit způsob seskupení pravidel v **Seskupit podle** rozevíracího seznamu.

- Klikněte na tlačítko **akce** pole skupiny a pak zadejte akce, která platí pro všechna pravidla ve skupině.

- Zaškrtněte nebo zrušte zaškrtnutí políčka u jednotlivých pravidel. Vyberete-li zaškrtnutí políčka pro pravidlo, je pravidlo nastavené na akci upozornění.

## <a name="toolbar"></a>Panel nástrojů

Na panelu nástrojů editoru sad pravidel slouží k seskupení, filtrovat a vyhledávat data, která se zobrazí v mřížce sady pravidel.

Následující tabulka popisuje ovládací prvky na panelu nástrojů editoru sad pravidel.

|Toolbar – ovládací prvek|Popis|
|---------------------|-----------------|
|**Rozbalit vše**|Obsahuje pravidla ve všech skupin.|
|**Sbalit vše**|Skryje pravidla ve všech skupinách.|
|**Seskupit podle**|Určuje pole, pravidla se seskupují. Klikněte na tlačítko  **\<žádný >** zobrazíte pravidla bez skupin.|
|**Možnosti sloupce**|Určuje pravidla polí k zobrazení.|
|**Skrýt pravidla, která se nevztahují na aktuální řešení**|Zobrazí nebo skryje pravidla, která nejsou stejného typu cílového jako řešení.|
|**Zobrazit pravidla, která mohou generovat chyby analýzy kódu**|Zobrazí nebo skryje pravidla, které jsou přiřazeny akce chyby.|
|**Zobrazit pravidla, která mohou generovat upozornění analýzy kódu**|Zobrazí nebo skryje pravidla, které jsou přiřazeny akce upozornění.|
|**Zobrazit pravidla, která nejsou povolena**|Zobrazí nebo skryje pravidla, která jsou přiřazena žádná akce.|
|**Přidat nebo odebrat podřízené sady pravidel**|Přidá nebo odstraní pravidla v sadách vybrané pravidlo.|
|**Vyhledat pravidla**|Vyhledá všechny hodnoty polí pro řetězec, který zadáte.|

## <a name="rule-set-fields"></a>Sada pravidel polí

Pravidlo sadu polí zobrazení informací o sadu pravidel a je možné seřadit a seskupit na seznamu pravidel. Chcete-li zobrazit nebo skrýt pole, vyberte **možnosti sloupce** na pravidlo nastavte nástrojů editoru a zaškrtněte nebo zrušte zaškrtnutí polí k zobrazení nebo skrytí.

Následující tabulka popisuje pole sadu pravidel:

|Pole|Popis|
|-----------|-----------------|
|**ID**|Identifikátor pravidla.|
|**Kategorie**|Kromě jejich členství v sadách pravidel pravidel analýzy kódu také jsou seskupené podle kategorie. Další informace najdete v tématu [upozornění analýzy kódu](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Jméno**|Název pravidla.|
|**Namespace**|Obor názvů pravidla.|
|**Cílový typ**|Označuje, zda pravidlo je pro nativní, spravované nebo databáze kódu.|
|**Akce**|Akce provedená v případě porušení pravidla analýzy kódu, spusťte. Můžete upravit **akce** pole.|
|**Zdroj sad pravidel**|Sada pravidel, který obsahuje pravidlo.|

## <a name="sort-and-filter-rule-sets"></a>Řazení a filtrování sady pravidel

V záhlaví sloupců mřížky sadu pravidel můžete řadit a filtrovat pravidla podle hodnot pole.

- Seřadit seznamy sadu pravidel, klikněte na záhlaví sloupce pole, podle kterého chcete řadit. Pokud jsou seskupené sady pravidel, každou skupinu je seřazen jednotlivě.

- Sady pravidel filtrování podle hodnoty pole, klikněte na tlačítko filtru na záhlaví sloupce pole, podle kterého chcete filtrovat. Vyberte zaškrtávací pole hodnot, které chcete zobrazit a zrušte zaškrtnutí políček hodnot, které chcete skrýt.

## <a name="see-also"></a>Viz také:

- [Vytvoření vlastní sady pravidel](../code-quality/how-to-create-a-custom-rule-set.md)
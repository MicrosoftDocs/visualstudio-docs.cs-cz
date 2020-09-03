---
title: Práce v editoru sad pravidel nástroje Code Analysis | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f25cc5a5f56c20f6a1696baa5aa3e9ee5ebdf2fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72621511"
---
# <a name="working-in-the-code-analysis-rule-set-editor"></a>Práce s Editorem sad pravidel nástroje Analýza kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor sady pravidel nástroje Analýza kódu umožňuje zadat pravidla, která jsou obsažena v sadě vlastních pravidel a zadat akci. Můžete také zadat akci, která má být provedena, když dojde k analýze kódu v případě porušení pravidla.

|Akce|Popis|
|------------|-----------------|
|**Upozornění**|Vygeneruje upozornění v okně **Seznam chyb** .|
|**Chyba**|Vygeneruje chybu v okně **Seznam chyb** .|
|**Žádný**|Zakáže pravidlo.|

 Editor zobrazuje pravidla ve stromové struktuře, která seskupují pravidla podle zadaného pole sady pravidel. Chcete-li přidat nebo odebrat pravidla ze sady pravidel, proveďte jeden nebo více následujících kroků:

- Zaškrtnutím nebo zrušením zaškrtnutí políčka uzlu skupiny přidejte nebo odeberte všechna pravidla ve skupině. Když vyberete skupinu, všechna pravidla se nastaví na akci **Upozornění** .

- Klikněte na pole **Akce** skupiny a pak zadejte akci, která se má použít pro všechna pravidla ve skupině.

- Zaškrtněte nebo zrušte zaškrtnutí políčka pro jednotlivá pravidla. Když zaškrtnete políčko pro pravidlo, pravidlo je nastaveno na akci upozornění.

## <a name="rule-set-editor-toolbar"></a>Panel nástrojů editoru sad pravidel
 Panel nástrojů editoru sady pravidel můžete použít k seskupení, filtrování a hledání dat, která se zobrazí v mřížce sady pravidel.

 Následující tabulka popisuje ovládací prvky na panelu nástrojů editoru sady pravidel.

|Ovládací prvek Toolbar|Popis|
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
 Pole sady pravidel zobrazují informace o sadě pravidel a lze je použít k řazení a seskupení seznamu pravidel. Chcete-li zobrazit nebo skrýt pole, klikněte na tlačítko **Možnosti sloupců** na panelu nástrojů editoru sad pravidel a zaškrtněte nebo zrušte zaškrtnutí políček u polí, která chcete zobrazit nebo skrýt.

 V následující tabulce jsou popsána pole sady pravidel.

|Pole|Popis|
|-----------|-----------------|
|**ID**|Identifikátor pravidla|
|**Kategorie**|Kromě jejich členství v sadách pravidel se pravidla analýzy kódu také seskupují podle kategorií. Další informace najdete v tématu [upozornění analýzy kódu pro spravovaný kód](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Name**|Název pravidla|
|**Obor názvů**|Obor názvů pravidla|
|**Cílový typ**|Označuje, zda je pravidlo pro nativní, spravovaný nebo databázový kód.|
|**Akce**|Akce provedená v případě porušení pravidla při spuštění analýzy kódu.<br /><br /> **Upozornění** – vygeneruje upozornění.<br /><br /> **Chyba** – vygeneruje chybu.<br /><br /> **None** – zakáže pravidlo.<br /><br /> Můžete upravit pole akce. Nastavení hodnoty na hodnotu žádné je stejné jako zrušení zaškrtnutí políčka pro pravidlo.|
|**Zdrojové sady pravidel**|Sada pravidel, která obsahuje pravidlo|

## <a name="sorting-and-filtering-rule-sets"></a>Řazení a filtrování sad pravidel
 Z záhlaví sloupců mřížky sady pravidel můžete seřadit a filtrovat pravidla podle hodnot pole.

- Pokud chcete seznam sad pravidel seřadit, klikněte na záhlaví sloupce pole, podle kterého chcete řadit. Pokud jsou sady pravidel seskupené, jednotlivé skupiny se jednotlivě seřadí.

- Chcete-li filtrovat sady pravidel podle hodnoty pole, klikněte na tlačítko Filtr v záhlaví sloupce pole, podle kterého chcete filtrovat. Zaškrtněte políčka u hodnot, které chcete zobrazit, a zrušte zaškrtnutí políček u hodnot, které chcete skrýt.

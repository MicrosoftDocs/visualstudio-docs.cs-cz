---
title: 'Postupy: Vytvoření vlastní sady pravidel | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6e4aef02a2bb320112d7d268da28cf66b1ec6751
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657452"
---
# <a name="how-to-create-a-custom-rule-set"></a>Postupy: Vytvoření vlastní sady pravidel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)], [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] a [!INCLUDE[vsPro](../includes/vspro-md.md)] můžete vytvořit a upravit vlastní *sadu pravidel* tak, aby splňovala konkrétní požadavky projektu spojené s analýzou kódu. Chcete-li vytvořit vlastní sadu pravidel, otevřete v editoru sad pravidel jednu nebo více standardních sad pravidel. Pak můžete přidat nebo odebrat konkrétní pravidla a můžete změnit akci, ke které dojde, když analýza kódu zjistí, že pravidlo bylo porušeno.

 Pokud chcete vytvořit novou vlastní sadu pravidel, uložte ji pomocí nového názvu souboru. Vlastní sada pravidel je automaticky přiřazena k projektu.

## <a name="opening-the-rule-set-editor"></a>Otevření editoru sad pravidel

#### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>Otevření prázdného souboru sady pravidel v editoru sad pravidel

1. V [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] nabídce **soubor** přejděte na příkaz **Nový** a pak klikněte na **soubor**.

2. V dialogovém okně **nový soubor** klikněte v seznamu **Nainstalované šablony** na **Obecné** a vyberte **sada pravidel analýza kódu**.

3. Zobrazí se Editor sady pravidel. V seznamu editoru nejsou vybrána žádná pravidla.

#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Vytvoření vlastního pravidla z jedné existující sady pravidel

1. V Průzkumník řešení klikněte pravým tlačítkem na projekt a pak vyberte **vlastnosti**.

2. Na kartě **vlastnosti** klikněte na **Analýza kódu**.

3. V rozevíracím seznamu **sada pravidel** proveďte jednu z následujících akcí:

   - Vyberte sadu pravidel, kterou chcete upravit.

     \- nebo-

   - Vybrat **\<Browse... >** k určení existující sady pravidel, která není v seznamu.

4. Kliknutím na **otevřít** zobrazte pravidla v editoru sad pravidel.

#### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>Vytvoření vlastní sady pravidel z více existujících sad pravidel

1. V Průzkumník řešení klikněte pravým tlačítkem na projekt a pak vyberte **vlastnosti**.

2. Na kartě **vlastnosti** klikněte na **Analýza kódu**.

3. Vyberte **\<Choose více sad pravidel... >** **Spustit tuto sadu pravidel**.

4. V dialogovém okně **Přidat nebo odebrat sady pravidel** vyberte sady pravidel, na kterých chcete vytvořit novou sadu pravidel, a pak klikněte na **OK**.

5. Uložte novou sadu pravidel.

     V seznamu **Spustit sadu pravidel** je vybraný název nové sady pravidel. Zobrazovaný název sady pravidel můžete změnit v dalším kroku.

6. Volitelné Chcete-li změnit zobrazovaný název sady pravidel, klikněte v nabídce **zobrazení** na **okno Vlastnosti**. Do pole **název** zadejte zobrazovaný název.

7. Chcete-li přidat, odebrat nebo upravit konkrétní pravidla analýzy kódu v nové sadě pravidel, klikněte na tlačítko **otevřít**.

## <a name="modifying-a-rule-set"></a>Úprava sady pravidel

#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Úprava sady pravidel v editoru sad pravidel

- Chcete-li změnit zobrazovaný název sady pravidel, klikněte v nabídce **zobrazení** na **okno Vlastnosti**. Do pole **název** zadejte zobrazovaný název. Všimněte si, že zobrazovaný název se může lišit od názvu souboru.

- Pokud chcete přidat všechna pravidla skupiny do vlastní sady pravidel, zaškrtněte políčko u dané skupiny. Chcete-li odebrat všechna pravidla skupiny, zrušte zaškrtnutí políčka.

- Chcete-li přidat konkrétní pravidlo do sady vlastních pravidel, zaškrtněte políčko pravidla. Pokud chcete pravidlo ze sady pravidel odebrat, zrušte zaškrtnutí políčka.

- Chcete-li změnit akci povedenou při porušení pravidla při analýze kódu, klikněte v poli **Akce** pro pravidlo a vyberte jednu z následujících hodnot:

     **Warn** – vygeneruje upozornění.

     **Chyba** – vygeneruje chybu.

     **None** – zakáže pravidlo. Tato akce je stejná jako odebrání pravidla ze sady pravidel.

## <a name="changing-the-rule-set-editor-display"></a>Změna zobrazení editoru sad pravidel

#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Seskupení, filtrování nebo změna polí v editoru sad pravidel pomocí panelu nástrojů editoru sad pravidel

- Pokud chcete rozšířit pravidla všech skupin, klikněte na **Rozbalit vše**.

- Pokud chcete pravidla sbalit ve všech skupinách, klikněte na **Sbalit vše**.

- Chcete-li změnit pole, podle kterého jsou pravidla seskupena, vyberte pole ze seznamu **Seskupit podle** . Chcete-li zobrazit Neseskupená pravidla, vyberte možnost **\<None >** .

- Pokud chcete přidat nebo odebrat pole ve sloupcích pravidla, klikněte na **Možnosti sloupců**.

- Pokud chcete skrýt pravidla, která se nevztahují na aktuální řešení, **skryjte pravidla, která se nevztahují na aktuální řešení**.

- Chcete-li přepínat mezi zobrazením a skrytím pravidel, kterým je přiřazena akce chyba, klikněte na tlačítko **Zobrazit pravidla, která mohou generovat chyby analýzy kódu**.

- Chcete-li přepínat mezi zobrazením a skrytím pravidel, která jsou přiřazena k akci upozornění, klikněte na tlačítko **Zobrazit pravidla, která mohou generovat upozornění analýzy kódu**.

- Pokud chcete přepínat mezi zobrazením a skrytím pravidel, která jsou přiřazená k akci **none** , klikněte na **Zobrazit pravidla, která nejsou povolená**.

- Chcete-li přidat nebo odebrat výchozí sady pravidel Microsoft pro aktuální sadu pravidel, klikněte na možnost **Přidat nebo odebrat podřízené sady pravidel**.

## <a name="see-also"></a>Viz také
 [Postupy: konfigurace analýzy kódu pro](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md) [odkaz sady pravidel analýzy kódu](../code-quality/code-analysis-rule-set-reference.md) projektu spravovaného kódu

---
title: 'Postupy: vytvoření vlastní sady pravidel | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a5d8a5cb7e29cfd900ce81fa5f4b6253f0c49014
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812462"
---
# <a name="how-to-create-a-custom-rule-set"></a>Postupy: Vytvoření vlastní sady pravidel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)], [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)], a [!INCLUDE[vsPro](../includes/vspro-md.md)], můžete vytvářet a upravovat vlastní *sada pravidel, která* podle potřeb konkrétního projektu související s analýzou kódu. Chcete-li vytvořit vlastní pravidlo nastavte, otevřete jednu nebo více standardních pravidel nastaví v editoru sad pravidel. Potom můžete přidat nebo odebrat konkrétní pravidla a změníte akci, která nastane, pokud analýza kódu určuje, že pravidlo bylo narušeno.  
  
 Chcete-li vytvořit nové vlastní pravidlo nastavte, uložte ho pomocí nového názvu souboru. Sada vlastních pravidel se automaticky přiřadí do projektu.  
  
## <a name="opening-the-rule-set-editor"></a>Otevřete pravidlo s editorem sad  
  
#### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>Chcete-li otevřít prázdná sada pravidel souboru v editoru sad pravidel  
  
1.  Na **souboru** nabídku [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], přejděte na **nový** a potom klikněte na tlačítko **souboru**.  
  
2.  V **nový soubor** dialogové okno, klikněte na tlačítko **Obecné** v **nainstalované šablony** seznamu a pak vyberte **sady pravidel analýzy kódu**.  
  
3.  Zobrazí se editor sad pravidel. Žádná pravidla jsou vybrány v editoru seznamu.  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Chcete-li vytvořit vlastní pravidlo z jednoho stávající sadu pravidel  
  
1. V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a pak vyberte **vlastnosti**.  
  
2. Na **vlastnosti** klikněte na tlačítko **analýzy kódu**.  
  
3. V **sady pravidel** rozevíracího seznamu, proveďte jednu z následujících akcí:  
  
   - Vyberte sadu pravidel, který chcete přizpůsobit.  
  
     \- nebo –  
  
   - Vyberte  **\<Procházet... >** zadat sadu existujících pravidel, která se nenachází v seznamu.  
  
4. Klikněte na tlačítko **otevřít** zobrazíte pravidla v editoru sad pravidel.  
  
#### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>Chcete-li vytvořit vlastní pravidlo nastavit z více existující sady pravidel  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a pak vyberte **vlastnosti**.  
  
2.  Na **vlastnosti** klikněte na tlačítko **analýzy kódu**.  
  
3.  Vyberte  **\<zvolit sady více pravidel... >** z **spustit tuto sadu pravidel**.  
  
4.  V **přidat nebo odebrat sady pravidel** dialogové okno, vyberte pravidlo se nastaví na kterém chcete založit nové sady pravidel a pak klikněte na tlačítko **OK**.  
  
5.  Uložte novou sadu pravidel.  
  
     Je vybrán název nové sady pravidel v **spustit tuto sadu pravidel** seznamu. Můžete změnit zobrazovaný název sady pravidel, která v dalším kroku.  
  
6.  (Volitelné) Chcete-li změnit zobrazovaný název sady pravidel na **zobrazení** nabídky, klikněte na tlačítko **okno vlastností**. Zadejte zobrazovaný název v **název** pole.  
  
7.  Pokud chcete přidat, odebrat, nebo upravte pravidla analýzy kódu konkrétní v nové sadě pravidel, klikněte na **otevřít**.  
  
## <a name="modifying-a-rule-set"></a>Úprava sady pravidel  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Chcete-li upravit pravidlo nastavte v editoru sad pravidel  
  
-   Chcete-li změnit zobrazovaný název sady pravidel na **zobrazení** nabídky, klikněte na tlačítko **okno vlastností**. Zadejte zobrazovaný název v **název** pole. Všimněte si, že zobrazované jméno se může lišit od názvu souboru.  
  
-   Chcete-li přidat do vlastní sady pravidel všechna pravidla skupiny, zaškrtněte políčko skupiny. Pokud chcete odebrat všechna pravidla skupiny, zrušte zaškrtnutí políčka.  
  
-   Chcete-li přidat konkrétní pravidlo do sady vlastních pravidel, zaškrtněte políčko pravidla. Chcete-li odebrat pravidlo ze sady pravidel, zrušte zaškrtnutí políčka.  
  
-   Chcete-li změnit akce provedená v případě porušení pravidla analýzy kódu, klikněte na tlačítko v **akce** pole pravidla a potom vyberte jednu z následujících hodnot:  
  
     **Upozornit** – vygeneruje upozornění.  
  
     **Chyba** – vygeneruje chybu.  
  
     **Žádný** – zakáže pravidlo. Tato akce je stejná jako pravidla odebírání sady pravidel.  
  
## <a name="changing-the-rule-set-editor-display"></a>Změna pravidla nastavit zobrazení editoru  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Do skupiny, filtrování nebo změně polí v editoru sad pravidel pomocí panelu nástrojů editoru sady pravidel  
  
-   Rozbalte pravidla ve všech skupinách, klikněte na tlačítko **Rozbalit vše**.  
  
-   Sbalit pravidla ve všech skupinách, klikněte na tlačítko **Sbalit vše**.  
  
-   Chcete-li změnit pole, pravidla se seskupují podle, vyberte pole ze seznamu **Group** seznamu. Pokud chcete zobrazit pravidla neseskupené, vyberte  **\<žádný >**.  
  
-   Chcete-li přidat nebo odebrat pole ve sloupcích pravidlo, klikněte na tlačítko **možnosti sloupce**.  
  
-   Chcete-li skrýt pravidla, která se nevztahují na aktuální řešení **skrýt pravidla, která se nevztahují na aktuální řešení**.  
  
-   Pro přepínání zobrazení a skrytí pravidla, které jsou přiřazeny akce chyby, klikněte na tlačítko **zobrazit pravidla, která mohou generovat chyby analýzy kódu**.  
  
-   Pro přepínání zobrazení a skrytí pravidla, které jsou přiřazeny akce upozornění, klikněte na tlačítko **zobrazit pravidla, která mohou generovat upozornění analýzy kódu**.  
  
-   Pro přepínání zobrazení a skrytí pravidla, které jsou přiřazeny **žádný** akci, klikněte na tlačítko **zobrazit pravidla, která nejsou povolena**.  
  
-   Chcete-li přidat nebo odebrat Microsoft výchozí pravidlo se nastaví na aktuální sadu pravidel, klikněte na tlačítko **přidat nebo odebrat podřízené sady pravidel**.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Konfigurace analýzy kódu pro spravovaný projekt kódu](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Referenční dokumentace sady pravidel nástroje Analýza kódu](../code-quality/code-analysis-rule-set-reference.md)




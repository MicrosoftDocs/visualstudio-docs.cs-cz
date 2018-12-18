---
title: Použití sad pravidel k určování pravidel C++ pro spuštění | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 42c8926403825032f295c31e2ce113bef4ff1bbd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810264"
---
# <a name="using-rule-sets-to-specify-the-c-rules-to-run"></a>Použití sad pravidel k určování pravidel C++ pro spuštění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] a [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)], můžete vytvářet a upravovat vlastní *sada pravidel, která* podle potřeb konkrétního projektu související s analýzou kódu. Chcete-li vytvořit vlastní pravidlo C++ nastavte, projekt C/C++ musí být otevřeny v integrovaném vývojovém prostředí sady Visual Studio. Potom otevřete sadu standardních pravidel v editoru sad pravidel a pak přidat nebo odebrat konkrétní pravidla a volitelně změnit akce, která nastane, pokud analýza kódu určuje, že pravidlo bylo narušeno.  
  
 Chcete-li vytvořit nové vlastní pravidlo nastavte, uložte ho pomocí nového názvu souboru. Sada vlastních pravidel se automaticky přiřadí do projektu.  
  
## <a name="opening-the-rule-set-editor"></a>Otevřete pravidlo s editorem sad  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Chcete-li vytvořit vlastní pravidlo z jednoho stávající sadu pravidel  
  
1. V Průzkumníku řešení otevřete místní nabídku pro projekt a klikněte na tlačítko **vlastnosti**.  
  
2. Na **vlastnosti** kartě **analýzy kódu**.  
  
3. V **sady pravidel** rozevíracího seznamu, proveďte jednu z následujících akcí:  
  
   - Vyberte sadu pravidel, kterou chcete upravit.  
  
     \- nebo –  
  
   - Zvolte  **\<Procházet... >** zadat sadu existujících pravidel, která se nenachází v seznamu.  
  
4. Zvolte **otevřít** zobrazíte pravidla v editoru sad pravidel.  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Chcete-li upravit pravidlo nastavte v editoru sad pravidel  
  
-   Chcete-li změnit zobrazovaný název sady pravidel na **zobrazení** nabídce zvolte **okno vlastností**. Zadejte zobrazovaný název v **název** pole. Všimněte si, že zobrazované jméno se může lišit od názvu souboru.  
  
-   Chcete-li přidat do vlastní sady pravidel všechna pravidla skupiny, zaškrtněte políčko skupiny. Pokud chcete odebrat všechna pravidla skupiny, zrušte zaškrtnutí políčka.  
  
-   Chcete-li přidat konkrétní pravidlo do sady vlastních pravidel, zaškrtněte políčko pravidla. Chcete-li odebrat pravidlo ze sady pravidel, zrušte zaškrtnutí políčka.  
  
-   Chcete-li změnit akce provedená v případě porušení pravidla analýzy kódu, zvolte **akce** pole pro pravidlo a pak vyberte jednu z následujících hodnot:  
  
     **Upozornit** – vygeneruje upozornění.  
  
     **Chyba** – vygeneruje chybu.  
  
     **Žádný** – zakáže pravidlo. Tato akce je stejná jako pravidla odebírání sady pravidel.  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Do skupiny, filtrování nebo změně polí v editoru sad pravidel pomocí panelu nástrojů editoru sady pravidel  
  
-   Chcete-li rozbalit pravidla ve všech skupinách, zvolte **Rozbalit vše**.  
  
-   Chcete-li sbalit pravidla ve všech skupinách, zvolte **Sbalit vše**.  
  
-   Chcete-li změnit pole, pravidla se seskupují podle, zvolte na pole **Group** seznamu. Chcete-li zobrazit pravidla neseskupené, zvolte  **\<žádný >**.  
  
-   Chcete-li přidat nebo odebrat pole ve sloupcích pravidlo, zvolte **možnosti sloupce**.  
  
-   Chcete-li skrýt pravidla, která se nevztahují na aktuální řešení, zvolte **skrýt pravidla, která se nevztahují na aktuální řešení**.  
  
-   Chcete-li přepnout mezi zobrazení a skrytí pravidla, které jsou přiřazeny akce chyby, zvolte **zobrazit pravidla, která mohou generovat chyby analýzy kódu**.  
  
-   Chcete-li přepnout mezi zobrazení a skrytí pravidla, které jsou přiřazeny akce upozornění, zvolte **zobrazit pravidla, která mohou generovat upozornění analýzy kódu**.  
  
-   Pro přepínání zobrazení a skrytí pravidla, které jsou přiřazeny **žádný** akce, zvolte **zobrazit pravidla, která nejsou povolena**.  
  
-   Chcete-li přidat nebo odebrat Microsoft výchozí pravidlo se nastaví na aktuální sadu pravidel, zvolte **přidat nebo odebrat podřízené sady pravidel**.




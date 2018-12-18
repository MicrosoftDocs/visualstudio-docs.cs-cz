---
title: Práce v pravidel nástroje Analýza kódu s editorem sad | Dokumentace Microsoftu
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
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cd107f2ac0c377765fda2f62f175d7285eb01bb6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269643"
---
# <a name="working-in-the-code-analysis-rule-set-editor"></a>Práce s Editorem sad pravidel nástroje Analýza kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor sad pravidel analýzy kódu umožňuje určit pravidla, které jsou součástí vlastní sady pravidel a určit akci. Můžete také zadat akce má být provedena, pokud narazí porušení pravidla analýzy kódu.  
  
|Akce|Popis|  
|------------|-----------------|  
|**Upozornění**|Vygeneruje upozornění v **seznam chyb** okna.|  
|**Chyba**|Dojde k chybě v **seznam chyb** okna.|  
|**None**|Zakáže pravidlo.|  
  
 Editor zobrazí pravidla ve stromové struktuře, která skupiny pravidla pomocí pravidla nastavena pole, které určíte. Chcete-li přidat nebo odebrat pravidla sadu pravidel, proveďte jeden nebo více z následujících kroků:  
  
-   Zaškrtněte nebo zrušte zaškrtnutí políček u uzlu skupiny pro přidání nebo odebrání všech pravidel ve skupině. Když vyberete skupinu, všechna pravidla jsou nastaveny na **upozornění** akce.  
  
-   Klikněte na tlačítko **akce** pole skupiny a pak zadejte akce, která platí pro všechna pravidla ve skupině.  
  
-   Zaškrtněte nebo zrušte zaškrtnutí políčka u jednotlivých pravidel. Vyberete-li zaškrtnutí políčka pro pravidlo, je pravidlo nastavené na akci upozornění.  
  
## <a name="rule-set-editor-toolbar"></a>Panel nástrojů editoru sady pravidel  
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
  
## <a name="rule-set-fields"></a>Pole sadu pravidel  
 Sada pravidel polí zobrazované informace o pravidle nastavit a je možné seřadit a seskupit na seznamu pravidel. Chcete-li zobrazit nebo skrýt pole, klikněte na tlačítko **možnosti sloupce** na pravidlo nastavte nástrojů editoru a zaškrtněte nebo zrušte zaškrtnutí polí k zobrazení nebo skrytí.  
  
 Následující tabulka popisuje pole sadu pravidel.  
  
|Pole|Popis|  
|-----------|-----------------|  
|**ID**|Identifikátor pravidla.|  
|**Kategorie**|Kromě jejich členství v sadách pravidel pravidel analýzy kódu také jsou seskupené podle kategorie. Další informace najdete v tématu [spravovaného kódu upozornění analýzy kódu pro](../code-quality/code-analysis-for-managed-code-warnings.md).|  
|**Jméno**|Název pravidla.|  
|**Namespace**|Obor názvů pravidla.|  
|**Cílový typ**|Označuje, zda pravidlo je pro nativní, spravované nebo databáze kódu.|  
|**Akce**|Akce provedená v případě porušení pravidla analýzy kódu, spusťte.<br /><br /> **Upozornění** – vygeneruje upozornění.<br /><br /> **Chyba** – vygeneruje chybu.<br /><br /> **Žádný** – zakáže pravidlo.<br /><br /> Můžete upravit pole akce. Nastavením této hodnoty na žádný je stejný jako zrušením zaškrtnutí políčka pro pravidlo.|  
|**Zdroj sad pravidel**|Sada pravidel, který obsahuje pravidlo.|  
  
## <a name="sorting-and-filtering-rule-sets"></a>Řazení a filtrování sady pravidel  
 V záhlaví sloupců mřížky sadu pravidel můžete řadit a filtrovat pravidla podle hodnot pole.  
  
-   Seřadit seznamy sadu pravidel, klikněte na záhlaví sloupce pole, podle kterého chcete řadit. Pokud jsou seskupené sady pravidel, každou skupinu je seřazen jednotlivě.  
  
-   Sady pravidel filtrování podle hodnoty pole, klikněte na tlačítko filtru na záhlaví sloupce pole, podle kterého chcete filtrovat. Vyberte zaškrtávací pole hodnot, které chcete zobrazit a zrušte zaškrtnutí políček hodnot, které chcete skrýt.




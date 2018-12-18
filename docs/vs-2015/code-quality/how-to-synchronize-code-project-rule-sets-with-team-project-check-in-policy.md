---
title: 'Postupy: synchronizace sad pravidel projektu kódu pomocí zásady vracení se změnami projektu týmu | Dokumentace Microsoftu'
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
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 482f3107aeb7545951632f6841c43968067b1b2a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263117"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy"></a>Postupy: Synchronizace sady pravidel projektu kódu se zásadou vrácení se změnami týmového projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Synchronizovat nastavení analýzy kódu pro projekty kódu mají zásady vrácení se změnami pro týmový projekt tak, že zadáte sadu pravidel, která obsahuje aspoň pravidla, která jsou uvedená v pravidle nastavit zásady vrácení se změnami. Váš vedoucí vývojář může informovat o název a umístění sada pravidel pro zásadu vrácení se změnami. Jeden z následujících možností můžete zajistit, že analýzy kódu pro projekt používá správné sady pravidel:  
  
-   Pokud zásady vrácení se změnami používá jedné sady předdefinovaných pravidel společnosti Microsoft, otevřete dialogové okno Vlastnosti projektu kódu, zobrazení stránky pro analýzu kódu a vyberte pravidlo, nastavte na stránce analýzy kódu v nastavení projektu kódu. Společnost Microsoft sad standardních pravidel jsou automaticky nainstalován se sadou Visual Studio jsou nastaveny na jen pro čtení a by neměla být upravována. Pokud se neupravují sady pravidel, pravidel zásad a nastaví místní pravidlo zaručeno tak, aby odpovídaly.  
  
-   Pokud zásady vrácení se změnami používá vlastní sady pravidel, proveďte operaci načíst v souboru sady pravidel v rámci správy verzí, chcete-li vytvořit místní kopii. V nastavení analýzy kódu pro projekt kódu zadejte tento místní umístění. Pravidla zaručeno splněno, pokud je aktuální pravidlo pro nastavení zásady vrácení se změnami.  
  
     Pokud namapujete umístění ovládacího prvku verze do místní složky, který je ve stejné relaci do kořenového adresáře projektu týmu jako kód projektu, umístění pravidla se nastaví pomocí relativní cesty. Relativní cesta se zajistí, že nastavení projektů kód pro analýzu kódu lze přesunout do jiných počítačů.  
  
-   Upravte kopii tohoto pravidla pro nastavení zásady vrácení se změnami pro projekt kódu. Ujistěte se, že nové sady pravidel obsahuje všechna pravidla v zásadách vrácení se změnami a ostatní pravidla, které chcete zahrnout. Ujistěte se, že vaše sada pravidel obsahuje všechna pravidla v pravidle, nastavte pro zásadu vrácení se změnami.  
  
### <a name="to-specify-a-microsoft-standard-rule-set"></a>Chcete-li určit standardních pravidel společnosti Microsoft nastavit  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt kódu a potom klikněte na tlačítko **vlastnosti**.  
  
2.  Klikněte na tlačítko **analýza kódu**.  
  
3.  V **spustit tuto sadu pravidel** klikněte na možnost zásad vrácení se změnami sadu pravidel.  
  
### <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Chcete-li určit sadu pravidel vlastních zásad vrácení se změnami  
  
1.  V případě potřeby proveďte operaci načíst v souboru sady pravidel, která určuje zásady vrácení se změnami.  
  
2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt kódu a potom klikněte na tlačítko **vlastnosti**.  
  
3.  Klikněte na tlačítko **analýza kódu**.  
  
4.  V **spustit tuto sadu pravidel** klikněte na možnost  **\<Procházet... >**.  
  
5.  V **otevřít** dialogového okna zadejte soubor sady pravidel zásad vrácení se změnami.  
  
### <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Chcete-li vytvořit vlastní pravidlo nastavte pro projekt kódu  
  
1.  Postupujte podle jednoho z postupů dříve v tomto tématu vyberte zásadu vrácení se změnami týmového projektu na stránce analýzy kódu v dialogovém okně nastavení projektu.  
  
2.  Klikněte na tlačítko **otevřít**.  
  
3.  Přidání nebo odebrání pravidla pomocí editoru sad pravidel.  
  
     Další informace najdete v tématu [vytvoření vlastní sady pravidel](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
4.  Uložte upravený pravidlo nastavte soubor .ruleset v místním počítači nebo na cestu UNC.  
  
5.  Otevřete dialogové okno Vlastnosti projektu kódu a zobrazit **analýzy kódu** stránky.  
  
6.  V **spustit tuto sadu pravidel** klikněte na možnost  **\<Procházet... >**.  
  
7.  V **otevřít** dialogového okna zadejte soubor sady pravidel.




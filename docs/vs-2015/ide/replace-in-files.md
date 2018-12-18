---
title: Nahradit v souborech | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- Find and Replace window, Replace in Files tab
- Replace in Files tab, Find and Replace window
ms.assetid: ca361466-53bd-44db-a28a-3a74bc03b028
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 92029377d5e7d4faf4c6b7f38deda1eecdeaa395
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228823"
---
# <a name="replace-in-files"></a>Nahradit v souborech
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nahradit v souborech ** umožňuje vyhledávání kódu zadané sady souborů pro řetězec nebo výraz a změnit některé nebo všechny nalezených shod. Nalezených shod a akcí provedených jsou uvedeny v **výsledky hledání** vybraný v interval **způsobit možnosti**.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte nastavení importu a exportu v nabídce Nástroje. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Můžete použít některý z následujících metod k zobrazení **nahradit v souborech** v **najít a nahradit** okna.  
  
### <a name="to-display-replace-in-files"></a>Chcete-li zobrazit nahradit v souborech  
  
1.  Na **upravit** nabídky, rozbalte **najít a nahradit**.  
  
2.  Zvolte **nahradit v souborech**.  
  
     – nebo –  
  
     Pokud **najít a nahradit** , je již otevřeno, na panelu nástrojů zvolte **nahradit v souborech**.  
  
## <a name="find-what"></a>Najít  
 K vyhledání nový textový řetězec nebo výraz, zadejte do pole. K vyhledání všech 20 řetězce, které jste hledali naposledy, otevřete seznam a zvolte řetězce, pro který chcete vyhledávat. Zvolte sousedních **Tvůrce výrazů** tlačítko, pokud chcete použít jeden nebo více regulární výrazy ve vyhledávaném řetězci. Další informace najdete v tématu [pomocí regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## <a name="replace-with"></a>Nahraďte  
 K nahrazení výskytů řetězce v **najít** jiným řetězcem, zadejte v řetězci pro nahrazení **nahradit** pole. Chcete-li odstranit výskytů řetězce v **najít** pole, toto pole nechat prázdné. Otevřete seznam pro zobrazení 20 řetězců, u kterých je prohledán jako poslední. Zvolte sousedních **Tvůrce výrazů** tlačítko, pokud chcete použít jeden nebo více regulárních výrazů v řetězci pro nahrazení. Další informace najdete v tématu [pomocí regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## <a name="look-in"></a>Oblast hledání  
 Možnost výběru z **Hledat v** rozevíracího seznamu určuje, zda **nahradit v souborech** vyhledá pouze v současné době aktivní soubory, nebo vyhledá všechny soubory uložené v určitých složkách. Vyberte obor hledání v seznamu, zadejte cestu ke složce nebo klikněte na tlačítko **Procházet (...)**  tlačítka pro zobrazení **zvolit složky pro hledání** dialogového okna a vyberte sadu složek k prohledání. Můžete také zadat přímo do cesty **Hledat v** pole.  
  
> [!NOTE]
>  Pokud **Hledat v** zaškrtnutou možnost způsobí, že vám umožní vyhledávat soubor, který jste rezervovali ve správě zdrojového kódu, je prohledána pouze verze tohoto souboru, který byl stažen do místního počítače.  
  
## <a name="find-options"></a>Možnosti hledání  
 Můžete rozbalit nebo sbalit **možnosti hledání** oddílu. Následující možnosti můžete vybrané nebo zrušeno:  
  
 Rozlišovat velikost písmen  
 Při výběru **výsledky hledání** windows budou zobrazovat jenom instance **najít** řetězec, který budou odpovídat podle obsahu a případem. Například vyhledejte "MyObject" s **rozlišovat velikost písmen** vybrané se vrátí "MyObject" ale ne "myobject" nebo "MYOBJECT."  
  
 Pouze celá slova  
 Pokud je vybráno, **výsledky hledání** windows budou zobrazovat jenom instance **najít** řetězec, který se shodují v celá slova. Například vyhledejte "MyObject" vrátí "MyObject", ale není "CMyObject" nebo "MyObjectC."  
  
 Použít regulární výrazy  
 Když je toto políčko zaškrtnuto, můžete použít speciální zápisy k definování vzorů textu v **najít** nebo **nahraďte** textová pole. Seznam těchto zápisy najdete v tématu [pomocí regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 Podívejte se na tyto typy souborů  
 Tento seznam uvádí typy souborů pro hledání prostřednictvím v **Hledat v** adresáře. Pokud je toto pole necháte prázdné, všechny soubory v **Hledat v** budou prohledány adresáře.  
  
 Vyberte libovolnou položku v seznamu a zadejte předkonfigurované vyhledávací řetězec, který najdete tyto konkrétní typy souborů.  
  
## <a name="result-options"></a>Možnosti výsledků  
 Můžete rozbalit nebo sbalit **způsobit možnosti** oddílu. Následující možnosti můžete vybrané nebo zrušeno:  
  
 Najít výsledky 1 okno  
 Pokud je vybráno, výsledky aktuální hledání nahradí obsah **Najít výsledky 1** okna. Toto okno se automaticky otevře a zobrazí výsledky hledání. Ručně otevřete toto okno, vyberte **ostatní Windows** z **zobrazení** nabídku a zvolte **Najít výsledky 1**.  
  
 Najít výsledky 2 okno  
 Pokud je vybráno, výsledky aktuální hledání nahradí obsah **Najít výsledky 2** okna. Toto okno se automaticky otevře a zobrazí výsledky hledání. Ručně otevřete toto okno, vyberte **ostatní Windows** z **zobrazení** nabídku a zvolte **Najít výsledky 2**.  
  
 Zobrazit pouze názvy souborů  
 Když je toto políčko zaškrtnuto, windows výsledky hledání jsou uvedeny úplné názvy dnů a cesty pro všechny soubory, které obsahují hledaný řetězec. Výsledky jsou však na řádek kódu, kde se zobrazí řetězec. Toto zaškrtávací políčko je dostupné pro hledání v souborech jenom.  
  
 Ponechat změněné soubory otevřené po Nahradit vše  
 Při výběru, otevřete všechny soubory zůstanou ve kterých nahrazení byly provedeny, můžete vrátit zpět nebo uložte změny. Omezení paměti může být omezen počet souborů, které může zůstat otevřené po operaci nahradit.  
  
> [!CAUTION]
>  Můžete použít **zpět** pouze u souborů, které zůstanou otevřené pro úpravy. Pokud tato možnost není vybraná, soubory, které ještě nebyly otevřete pro úpravy zůstanou uzavřené a ne **zpět** možnost je k dispozici v těchto souborech.  
  
## <a name="see-also"></a>Viz také  
 [Hledání a nahrazení textu](../ide/finding-and-replacing-text.md)   
 [Najít v souborech](../ide/find-in-files.md)   
 [Příkazy sady Visual Studio](../ide/reference/visual-studio-commands.md)




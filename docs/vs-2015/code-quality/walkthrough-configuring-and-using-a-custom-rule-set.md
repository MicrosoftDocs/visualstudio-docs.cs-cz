---
title: 'Návod: Konfigurace a používání vlastní sady pravidel | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5976ee0c0fbfc4befe97f2ab25c46744a8267134
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906042"
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>Návod: Konfigurace a používání vlastní sady pravidel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak pomocí nástrojů pro analýzu kódu, které jsou nakonfigurované na použití vlastní *sada pravidel, která* na knihovny tříd. Můžete vybrat sadu pravidel, která má vztah k typu projektu, který jste zadali pro vaše řešení, nebo můžete vybrat alternativní pravidlo sady ke splnění se specifickými požadavky, jako je skenování starší verzi kódu pro problémy, které lze napravit pevná způsobem. V obou případech sady pravidel se taky dají upravit a vyladit je požadavky projektu.  
  
 V tomto podrobném návodu přesune se krokování přes tyto procesy:  
  
-   Vytvoření knihovny tříd.  
  
-   Vyberte **základní pravidla obecných zásad návrhu společnosti Microsoft** sadu pravidel analýzy kódu.  
  
-   Přidejte vlastní kód do třídy.  
  
-   Spustíte analýzu kódu.  
  
-   Přizpůsobení sady pravidel.  
  
-   Spustit analýzu kódu a podívejte se, jak funguje chování přizpůsobení sady pravidel.  
  
## <a name="prerequisites"></a>Požadavky  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], nebo [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
## <a name="using-rule-sets-with-code-analysis"></a>Použití sad pravidel analýzy kódu  
 Nejprve vytvořte jednoduchou třídu knihovny.  
  
#### <a name="create-a-class-library"></a>Vytvoření knihovny tříd  
  
1. Na **souboru** nabídky, klikněte na tlačítko **nový** a potom klikněte na tlačítko **projektu**.  
  
2. V **nový projekt** dialogovém okně **typy projektů**, klikněte na tlačítko **Visual C#**.  
  
3. V části **Visual C#** vyberte **knihovny tříd**.  
  
4. V **název** textového pole, typ **RuleSetSample** a potom klikněte na tlačítko **OK**.  
  
   V dalším kroku vyberete **základní pravidla obecných zásad návrhu společnosti Microsoft** sady pravidel a uložit ji s projektem.  
  
#### <a name="select-a-code-analysis-rule-set"></a>Vybrat sadu pravidel analýzy kódu  
  
1. Na **analyzovat** nabídky, klikněte na tlačítko **konfigurovat analýzu kódu pro RuleSetSample**.  
  
    Zobrazí se nastavení konfigurace pro analýzu kódu.  
  
2. V **spustit tuto sadu pravidel** rozevíracího seznamu vyberte **všechna pravidla společnosti Microsoft**.  
  
    Další informace o sad pravidel k dispozici, najdete v části [referenční dokumentace sady pravidel nástroje Analýza kódu](../code-quality/code-analysis-rule-set-reference.md).  
  
    V nabídce Soubor klikněte na tlačítko **uložit vybrané položky** aktualizovat soubor projektu s jeho nastavení a informace o sadě pravidel, kterou jste vybrali.  
  
   > [!TIP]
   >  V reálné situaci, je vhodné použít pro určení priority problémy, které chcete cílit s analýzou kódu začínat **Minimální doporučená pravidla** sada pravidel a opravit problémy požadované a postupně přidat Další pravidla nebo pravidlo se nastaví na Najít a opravit další problémy.  
  
   V dalším kroku přidáte nějaký kód do knihovny tříd, který se použije k předvedení porušení CA1704 "Identifikátory by měly být zadány správně" pravidel nástroje Analýza kódu. Další informace najdete v tématu [CA1704: identifikátory by měly být zadány správně](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
#### <a name="add-your-own-code"></a>Přidejte vlastní kód  
  
- V Průzkumníku řešení otevřete soubor Class1.cs a nahraďte existující kód následujícím kódem:  
  
  ```  
  using System;  
  using System.Collections.Generic;  
  using System.Text;  
  
  namespace RuleSetSample  
  {  
      public class Class1  
      {  
          //The variable parameter names "a" and "b" will cause  
          //the warning CA 1704 Microsoft.Naming "Consider   
          //providing a more meaningful name" to fire  
          public int AddIntegers(int a, int b)  
          {  
  
              int sum = a + b;  
  
              return (sum);  
          }  
      }  
  }  
  
  ```  
  
  Nyní můžete spustit analýzu kódu na projektu RuleSetSample a vyhledejte všechny chyby a varování vygenerované v okně Seznam chyb.  
  
#### <a name="run-code-analysis-on-the-rulesetsample-project"></a>Spustit analýzu kódu na projektu RuleSetSample  
  
1. Na **analyzovat** nabídky, klikněte na tlačítko **spustit analýzu kódu na RuleSetSample**.  
  
2. V okně Seznam chyb, klikněte na tlačítko **upozornění** a potom klikněte na tlačítko **popis** záhlaví sloupce seřadíte upozornění alfanumericky.  
  
    V reálné aplikaci by opravit porušení pravidla které stojí za to, v tomto okamžiku opravě nebo volitelně vypnout nebo potlačit pravidlo, je-li určit, že nebylo vhodné řešení. Další informace najdete v tématu [potlačit upozornění s použitím atributu SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
3. Všimněte si, že CA1704 upozornění. Tato porušení tohoto pravidla znamenat, že "zvažte poskytnutí smysluplnějšího názvu pro parametry." Může opravit problém v kódu nebo pravidlo, můžete zakázat, jak je popsáno v následujícím postupu.  
  
   V dalším kroku přizpůsobíte sada k vyloučení upozornění CA1704 pravidel, "Identifikátory by měly být zadány správně".  
  
#### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Přizpůsobení sada pravidel pro projekt tak, aby zakázat konkrétní pravidlo  
  
1. Na **analyzovat** nabídky, klikněte na tlačítko **konfigurovat analýzu kódu pro RuleSetSample**.  
  
2. V **spustit tuto sadu pravidel** rozevíracího seznamu, ověřte, že **všechna pravidla společnosti Microsoft** pravidlo, stále je zvýrazněn sadu a pak klikněte na **otevřít**. Zobrazí se stránka sady pravidel.  
  
3. Rozbalte uzel Microsoft.Naming kategorie a pak vyberte CA1704 upozornění.  
  
4. V části **akce** sloupci vyberte **None.** CA1704 zabrání zobrazení jako upozornění nebo chyby v okně Seznam chyb.  
  
    Teď by byla vhodná doba experimentovat s různými tlačítka panelu nástrojů a filtrování možností a seznamte se s nimi. Například můžete použít **Group** rozevíracího seznamu, které vám pomůžou vyhledání konkrétní pravidlo nebo kategorie pravidla. Dalším příkladem je, že můžete použít **zakázaná pravidla pro skrytí** tlačítko v panelu nástrojů stránky sady pravidel pro skrytí nebo zobrazení všechna pravidla se **akce** sloupec nastaven na **žádný**. To může být užitečné, pokud chcete vyhledat všechna pravidla, která jste vypnuli k ověření, že chcete dál nechat zakázané.  
  
5. V nabídce Zobrazit klikněte na okno vlastností. Typ **Moje vlastní pravidlo nastavené** do pole Název panelu nástrojů Vlastnosti. Tím se změní zobrazovaný název novou sadu pravidel v [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] integrovaného vývojového prostředí.  
  
6. Na **souboru** nabídky, klikněte na tlačítko **uložit všechny Rules.ruleset** uložení vlastního pravidla sady. Přejděte do kořenové složky vašeho projektu. V **název souboru** textového pole, typ **MyCustomRuleSet**. Sada vlastních pravidel je teď vybrat pro použití s projektem.  
  
   S vaší nové pravidlo vytvořené teď musíte nakonfigurovat nastavení projektu k určení, že chcete použít nové pravidlo nastavit s ním.  
  
#### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Zadejte nastavení pro použití s projektem nové pravidlo  
  
1. V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a pak vyberte **vlastnosti**.  
  
2. V **vlastnosti** klikněte na tlačítko **analýzy kódu**.  
  
    V **spustit tuto sadu pravidel** rozevíracího seznamu, klikněte na tlačítko  **\<Procházet... >**. Přejděte do kořenové složky projektu kódu a zvolte možnost **MyCustomRuleSet.ruleset**. Toto je nové sady pravidel, kterou jste vytvořili v předchozím postupu.  
  
3. Na **souboru** nabídky, klikněte na tlačítko **Uložit** uložte konfiguraci projektu. Můžete se teď dá vlastní sady pravidel s projektem.  
  
   Nakonec spustíte znovu pomocí MyCustomRuleSet sady pravidel analýzy kódu. Všimněte si, že porušení pravidla výkonu CA1704 nejsou zobrazeny v okně Seznam chyb.  
  
#### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>Spustit analýzu kódu na projektu RuleSetSample podruhé  
  
1.  Na **analyzovat** nabídky, klikněte na tlačítko **spustit analýzu kódu na RuleSetSample**.  
  
2.  V okně Seznam chyb, Všimněte si, že po kliknutí na **upozornění**, už se nezobrazují upozornění porušení CA1704 pro pravidlo "Identifikátory by měly být zadány správně".  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Konfigurace analýzy kódu pro spravovaný projekt kódu](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Referenční dokumentace sady pravidel nástroje Analýza kódu](../code-quality/code-analysis-rule-set-reference.md)




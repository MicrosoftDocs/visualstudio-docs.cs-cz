---
title: 'Návod: konfigurace a používání vlastní sady pravidel | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8239afd1cf4e8c0a5e702f2b0e4ed64408cada09
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645744"
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>Návod: Konfigurace a používání vlastní sady pravidel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak používat nástroje pro analýzu kódu, které byly nakonfigurovány pro použití vlastní *sady pravidel* v knihovně tříd. Můžete vybrat sadu pravidel, která se vztahuje k typu projektu, který jste určili pro vaše řešení, nebo můžete vybrat alternativní sady pravidel pro splnění konkrétní potřeby, jako je skenování starší verze kódu pro problémy, které je možné vyřešit nepřerušovaným způsobem. V obou případech lze sady pravidel přizpůsobit, aby je bylo možné vyladit na požadavky projektu.

 V tomto návodu provedete kroky těchto procesů:

- Vytvořte knihovnu tříd.

- Vyberte sadu pravidel pravidla analýzy kódu **základní zásady pro návrh společnosti Microsoft** .

- Přidejte do třídy vlastní kód.

- Spusťte analýzu kódu.

- Přizpůsobení sady pravidel.

- Spusťte analýzu kódu a podívejte se, jak chování přizpůsobení sady pravidel funguje.

## <a name="prerequisites"></a>Požadavky

- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] nebo [!INCLUDE[vsPro](../includes/vspro-md.md)]

## <a name="using-rule-sets-with-code-analysis"></a>Použití sad pravidel s analýzou kódu
 Nejprve vytvořte jednoduchou knihovnu tříd.

#### <a name="create-a-class-library"></a>Vytvoření knihovny tříd

1. V nabídce **soubor** klikněte na příkaz **Nový** a potom klikněte na **projekt**.

2. V dialogovém okně **Nový projekt** , v části **typy projektů**klikněte na **možnost C#Visual** .

3. V **části C#vizuál** vyberte **Knihovna tříd**.

4. Do textového pole **název** zadejte **RuleSetSample** a pak klikněte na **OK**.

   V dalším kroku vyberete sadu pravidel **pravidla obecných zásad návrhu pro Microsoft** a uložíte ji do svého projektu.

#### <a name="select-a-code-analysis-rule-set"></a>Vybrat sadu pravidel pro analýzu kódu

1. V nabídce **analyzovat** klikněte na možnost **Konfigurovat analýzu kódu pro RuleSetSample**.

    Zobrazí se nastavení konfigurace pro analýzu kódu.

2. V rozevíracím seznamu **Spustit tuto sadu pravidel** vyberte možnost **Microsoft všechna pravidla**.

    Další informace o dostupných sadách pravidel naleznete v tématu [Referenční dokumentace sady pravidel nástroje Analýza kódu](../code-quality/code-analysis-rule-set-reference.md).

    V nabídce soubor klikněte na **Uložit vybrané položky** a aktualizujte soubor projektu o informace o sadě pravidel, kterou jste vybrali a jejím nastavení.

   > [!TIP]
   > V reálném čase je vhodné použít k určení priorit, na které problémy chcete cílit pomocí analýzy kódu, začít s minimální sadou pravidel **Doporučené pravidla** a opravit požadované problémy a potom přírůstkově přidat další pravidla nebo sady pravidel do Vyhledejte a opravte další problémy.

   V dalším kroku přidáte do knihovny tříd nějaký kód, který bude použit k demonstraci porušení identifikátorů CA1704 "identifikátory by měly být zadány správně" pravidla analýzy kódu. Další informace najdete v tématu [CA1704: identifikátory by měly být zadány správně](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

#### <a name="add-your-own-code"></a>Přidání vlastního kódu

- V Průzkumník řešení otevřete soubor Class1.cs a nahraďte existující kód následujícím kódem:

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

  Nyní můžete spustit analýzu kódu v projektu RuleSetSample a vyhledat všechny chyby a varování vygenerované v okně Seznam chyb.

#### <a name="run-code-analysis-on-the-rulesetsample-project"></a>Spustit analýzu kódu v projektu RuleSetSample

1. V nabídce **analyzovat** klikněte na možnost **Spustit analýzu kódu v RuleSetSample**.

2. V okně Seznam chyb klikněte na tlačítko **Upozornění** a potom klikněte na záhlaví sloupce s **popisem** a zařaďte upozornění alfanumerické znaky.

    V reálné aplikaci byste opravili všechna porušení pravidel, která jsou v tuto chvíli opravená, nebo můžete pravidlo vypnout nebo potlačit, pokud jste zjistili, že neplatilo pro opravu. Další informace naleznete v tématu [potlačení upozornění pomocí atributu SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).

3. Všimněte si upozornění CA1704. Tato porušení pravidla označují, že byste měli zvážit poskytnutí smysluplného názvu pro parametry. Můžete opravit problém ve vašem kódu nebo pravidlo můžete zakázat, jak je vysvětleno v dalším postupu.

   V dalším kroku přizpůsobíte sadu pravidel tak, aby vyloučila upozornění CA1704. "identifikátory by měly být zadány správně".

#### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Přizpůsobení sady pravidel pro projekt za účelem zakázání konkrétního pravidla

1. V nabídce **analyzovat** klikněte na možnost **Konfigurovat analýzu kódu pro RuleSetSample**.

2. V rozevíracím seznamu **Spustit tuto sadu pravidel** ověřte, zda je sada pravidel **Microsoft všechna pravidla** stále zvýrazněna a klikněte na tlačítko **otevřít**. Zobrazí se stránka sada pravidel.

3. Rozbalte uzel kategorie Microsoft. pojmenování a potom vyberte upozornění CA1704.

4. Ve sloupci **Akce** vyberte None ( **žádné).** To brání tomu, aby se CA1704 zobrazoval jako upozornění nebo chyba v okně Seznam chyb.

    Nyní by byl dobrý čas na experimentování s různými tlačítky na panelu nástrojů a možnostmi filtrování, abyste se mohli seznámit s nimi. Můžete například použít rozevírací seznam **Seskupit podle** , který vám umožní vyhledat konkrétní pravidlo nebo kategorii pravidel. Dalším příkladem je, že můžete použít tlačítko **Skrýt zakázaná pravidla** na panelu nástrojů stránky sady pravidel pro skrytí nebo zobrazení všech pravidel se sloupcem **Akce** nastaveným na **žádná**. To může být užitečné, pokud chcete vyhledat jakákoli pravidla, která jste vypnuli, abyste ověřili, že je stále chcete zakázat.

5. V nabídce zobrazení klikněte na položku Vlastnosti okno. Do pole název v okně nástroje vlastnosti zadejte **vlastní množinu pravidel** . Tím se změní zobrazovaný název nové sady pravidel v [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] IDE.

6. V nabídce **soubor** klikněte na **Uložit Microsoft All Rules. ruleset** a uložte si vlastní sadu pravidel. Přejděte do kořenové složky projektu. Do textového pole **název souboru** zadejte **MyCustomRuleSet**. Vlastní sadu pravidel teď můžete vybrat pro použití s vaším projektem.

   Po vytvoření nové sady pravidel je teď nutné nakonfigurovat nastavení projektu, aby se určilo, že chcete použít novou sadu pravidel.

#### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Určení nové sady pravidel pro použití s vaším projektem

1. V Průzkumník řešení klikněte pravým tlačítkem na projekt a pak vyberte **vlastnosti**.

2. Na kartě **vlastnosti** klikněte na **Analýza kódu**.

    V rozevíracím seznamu **Spustit tuto sadu pravidel** klikněte na **\<Browse.. >** . Přejděte do kořenové složky vašeho projektu kódu a pak vyberte **MyCustomRuleSet. ruleset**. Toto je nová sada pravidel, kterou jste vytvořili v předchozím postupu.

3. V nabídce **soubor** klikněte na **Uložit** a uložte konfiguraci projektu. Vlastní sadu pravidel teď můžete použít s vaším projektem.

   Nakonec budete znovu spouštět analýzu kódu pomocí sady pravidel MyCustomRuleSet. Všimněte si, že Seznam chyb okno nezobrazuje porušení pravidla výkonu CA1704.

#### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>Spustit analýzu kódu v projektu RuleSetSample pro druhý čas

1. V nabídce **analyzovat** klikněte na možnost **Spustit analýzu kódu v RuleSetSample**.

2. V okně Seznam chyb si všimněte, že když kliknete na **Upozornění**, nebudete už zobrazovat porušení upozornění CA1704 pro pravidlo "identifikátory by měly být zadány správně".

## <a name="see-also"></a>Viz také
 [Postupy: konfigurace analýzy kódu pro](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md) [odkaz sady pravidel analýzy kódu](../code-quality/code-analysis-rule-set-reference.md) projektu spravovaného kódu

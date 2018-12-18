---
title: Implementace vlastních zásad analýzy kódu vrácení se změnami pro spravovaný kód | Dokumentace Microsoftu
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
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 82f360bb9dc256fd78a8b06aca66d9e49c57ab22
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49268967"
---
# <a name="implementing-custom-code-analysis-check-in-policies-for-managed-code"></a>Implementace vlastních zásad vrácení se změnami Analýzy kódu pro spravovaný kód
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje sadu pravidel, které členy týmového projektu musí běžet na zdrojovém kódu před vrácením se změnami do správy verzí, zásady vrácení se změnami analýzy kódu. Společnost Microsoft poskytuje sadu standard *sad pravidel* pravidel analýzy kódu této skupiny do funkčních oblastí. *Vlastní zásady vrácení se změnami sady pravidel* zadat sadu pravidel analýzy kódu, které jsou specifické pro týmový projekt. Sada pravidel je uložené v souboru analýza.  
  
 Nastavit na úrovni týmového projektu a určeného umístění soubor .ruleset ve stromu ovládacích prvků verze zásad vrácení se změnami. Nejsou žádná omezení umístění ovládacího prvku verze sady team zásad vlastní pravidlo.  
  
 Analýza kódu je nakonfigurovaný pro jednotlivé projekty v okně Vlastnosti pro každý projekt. Vlastní sadu pravidel pro projekt kódu je určená fyzické umístění soubor .ruleset v místním počítači. Je-li soubor .ruleset zadána, který je umístěn na stejné jednotce jako projekt kódu, Visual Studio používá relativní cestu k souboru v konfiguraci projektu.  
  
 Doporučené postupy pro vytvoření týmu projektu vlastní sady pravidel je uložit soubor .ruleset zásad vrácení se změnami ve zvláštní složce, která není součástí žádného projektu kódu. Pokud soubor uchováváte v vyhrazené složky, můžete použít oprávnění, které omezují, kteří mohou upravovat soubor pravidel a můžete snadno přesouvat adresářovou strukturu, která obsahuje projekt do jiného adresáře nebo počítači.  
  
## <a name="creating-the-team-project-custom-check-in-rule-set"></a>Vytvoření sady vlastní pravidlo pro vrácení se změnami týmového projektu  
 Pokud chcete vytvořit vlastní sadu pravidel pro týmový projekt, nejprve vytvoříte speciální složky pro pravidlo zásad vrácení se změnami v **Průzkumníka správy zdrojového kódu**. Vytvoření souboru sady pravidel a přidejte soubor do správy verzí. Nakonec zadejte pravidlo nastavit jako zásady analýzy kódu vrácení se změnami pro týmový projekt.  
  
> [!NOTE]
>  K vytvoření složky v týmovém projektu, je nejprve nutné mapovat kořen projektu týmu do umístění na místním počítači. Další informace najdete v tématu [vytváření a práci s pracovními prostory (staré)](http://msdn.microsoft.com/en-us/db4d5692-179a-44fe-ad31-0c1c900c9cb2).  
  
#### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Chcete-li vytvořit složku správy verzí pro Zásady vracení se změnami sadu pravidel  
  
1.  V [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], rozbalte uzel týmového projektu a pak klikněte na tlačítko **správy zdrojových kódů**.  
  
2.  V **složky** podokně klikněte pravým tlačítkem na týmový projekt a potom klikněte na **novou složku**.  
  
3.  V hlavním podokně správy zdrojového kódu, klikněte pravým tlačítkem na **novou složku**, klikněte na tlačítko **přejmenovat**a zadejte název pro složku sady pravidel.  
  
#### <a name="to-create-the-check-in-policy-rule-set"></a>Chcete-li vytvořit sadu pravidel zásad vrácení se změnami  
  
1.  Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **souboru**.  
  
2.  V **kategorie** klikněte na možnost **Obecné**.  
  
3.  V **šablony** seznamu, klikněte dvakrát na **sady pravidel analýzy kódu**.  
  
4.  Zadejte pravidla, která chcete zahrnout do sady pravidel a potom uložte do složky sady pravidel, kterou jste vytvořili soubor sady pravidel.  
  
     Další informace najdete v tématu [vytvoření vlastní sady pravidel](../code-quality/creating-custom-code-analysis-rule-sets.md)  
  
#### <a name="to-add-the-rule-set-file-to-version-control"></a>Chcete-li přidat pravidla nastavit soubor do správy verzí  
  
1.  V **Průzkumníka správy zdrojového kódu**, klikněte pravým tlačítkem na novou složku a potom klikněte na tlačítko **přidat položky do složky**.  
  
     Další informace najdete v tématu [používání správy verzí](http://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314).  
  
2.  Klikněte na soubor, který jste vytvořili nastavené pravidlo a pak klikněte na tlačítko **Dokončit**.  
  
     Soubor je přidán do správy zdrojového kódu a rezervovány u vás.  
  
3.  V **Průzkumníka správy zdrojového kódu** okno podrobností, klikněte pravým tlačítkem na název souboru a pak klikněte na **vrátit se změnami probíhající změny**.  
  
4.  V **vrácení se změnami** dialogovém okně máte možnost přidat komentář a potom klikněte na **vrátit se změnami**.  
  
    > [!NOTE]
    >  Pokud jste už nakonfigurovali zásady analýzy kódu vrácení se změnami týmového projektu a rozhodli jste **vynutit vrácení se změnami obsahovat soubory, které jsou součástí aktuálního řešení**, se aktivuje upozornění na selhání zásady. V dialogovém okně chyby zásad, vyberte **přepsat zásady selhání a pokračovat vrácení se změnami**. Přidejte požadované komentář a potom klikněte na tlačítko **OK**.  
  
#### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Určit pravidla, nastavte soubor jako zásady vrácení se změnami  
  
1.  Na **týmu** nabídky, přejděte k **nastavení týmového projektu**a potom klikněte na tlačítko **správy zdrojových kódů**.  
  
2.  Klikněte na tlačítko **zásad vrácení se změnami**a potom klikněte na tlačítko **přidat**.  
  
3.  V **zásad vrácení se změnami** seznamu, klikněte dvakrát na **analýzy kódu**a ujistěte se, že **vynutit analýzu kódu pro spravovaný kód** je zaškrtnuto políčko.  
  
4.  V **spustit tuto sadu pravidel** klikněte na možnost  **\<vybrat sadu pravidel ze správy zdrojových kódů >**.  
  
5.  Zadejte cestu souboru sady pravidel zásad vrácení se změnami do správy verzí.  
  
     Cesta musí splňovat následující syntaxi:  
  
     **$/** `TeamProjectName` **/** `VersionControlPath`  
  
    > [!NOTE]
    >  Můžete zkopírovat cestu pomocí jedné z následujících postupů na portále **Průzkumníka správy zdrojového kódu**:  
  
    -   V **složky** podokně klikněte na složku obsahující soubor sady pravidel. Zkopírovat cestu správy verzí ke složce, která se zobrazí v **zdroj** a ručně zadejte název souboru sady pravidel.  
  
    -   V okně podrobností klikněte pravým tlačítkem na soubor sady pravidel a potom klikněte na tlačítko **vlastnosti**. Na **Obecné** kartu, zkopírujte hodnotu v **název serveru**.  
  
## <a name="synchronizing-code-projects-to-the-check-in-policy-rule-set"></a>Synchronizaci projektů kódu do sady pravidel zásad vrácení se změnami  
 Můžete zadat pravidlo zásad vrácení se změnami týmového projektu nastavit jako sada pravidel analýzy kódu kód konfigurace projektu v dialogovém okně Vlastnosti projektu kódu. Pokud je sada pravidel na stejné jednotce jako projekt kódu, relativní cesta se používá k určení sady pravidel, pokud cesta je vybrána v dialogovém okně soubor. Relativní cesta povolí nastavení vlastnosti projektu přenosné na jiné počítače, které používají podobné místní verze řízení struktury.  
  
#### <a name="to-specify-a-team-project-rule-set-as-the-rule-set-of-a-code-project"></a>Chcete zadat pravidlo týmového projektu nastavte jako sady pravidel projektu kódu  
  
1.  V případě potřeby načíst zásady vrácení se změnami pravidlo sady složku a soubor ze správy verzí.  
  
     Tento krok můžete provést **Průzkumníka správy zdrojového kódu** kliknutím pravým tlačítkem myši nastavené pravidlo složku a pak levým na **získat nejnovější verzi**.  
  
2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt kódu a potom klikněte na tlačítko **vlastnosti**.  
  
3.  **Klikněte na tlačítko pro analýzu kódu**.  
  
4.  V případě potřeby klikněte na příslušné možnosti v **konfigurace** a **platformy** seznamy.  
  
5.  Chcete-li spustit analýzu kódu pokaždé, když kód projekt se vytvořil pomocí zadané konfigurace, vyberte **povolit analýzu kódu na sestavení (definuje konstantu CODE_ANALYSIS)** zaškrtávací políčko.  
  
6.  Chcete-li ignorovat kód v součásti od jiných společností, vyberte **potlačit Výsledky generovaného kódu** zaškrtávací políčko.  
  
7.  V **spustit tuto sadu pravidel** klikněte na možnost  **\<Procházet... >**.  
  
8.  Zadejte místní verzi souboru sady pravidel zásad vrácení se změnami.




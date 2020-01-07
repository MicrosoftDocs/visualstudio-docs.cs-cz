---
title: Vlastní zásady vrácení se změnami analýzy kódu pro spravovaný kód
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9386d89ce995131bdb89f94201fa8475058ddba0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587391"
---
# <a name="implement-custom-code-analysis-check-in-policies-for-managed-code"></a>Implementace vlastních zásad vracení zpět se změnami analýzy kódu pro spravovaný kód

Vrácení se změnami Zásady vracení analýzy kódu určuje sadu pravidel, které členy projekt Azure DevOps musí běžet na zdrojovém kódu před vrácením se změnami do správy verzí. Společnost Microsoft poskytuje sadu standard *sad pravidel* pravidel analýzy kódu této skupiny do funkčních oblastí. *Vlastní zásady vrácení se změnami sady pravidel* zadat sadu pravidel analýzy kódu, které jsou specifické pro projekt. Sada pravidel je uložené v souboru analýza.

Zásady vrácení se změnami jsou nastavená na úrovni projekt Azure DevOps a určeného umístění soubor .ruleset ve stromu ovládacího prvku verze. Nejsou žádná omezení umístění ovládacího prvku verze sady team zásad vlastní pravidlo.

Analýza kódu je nakonfigurovaný pro jednotlivé projekty v okně Vlastnosti pro každý projekt. Vlastní sadu pravidel pro projekt kódu je určená fyzické umístění soubor .ruleset v místním počítači. Je-li soubor .ruleset zadána, který je umístěn na stejné jednotce jako projekt kódu, Visual Studio používá relativní cestu k souboru v konfiguraci projektu.

Doporučené postupy pro vytvoření Azure DevOps project vlastní sady pravidel je uložit soubor .ruleset zásad vrácení se změnami ve zvláštní složce, která není součástí žádného projektu kódu. Pokud soubor uchováváte v vyhrazené složky, můžete použít oprávnění, které omezují, kteří mohou upravovat soubor pravidel a můžete snadno přesouvat adresářovou strukturu, která obsahuje projekt do jiného adresáře nebo počítači.

## <a name="create-the-project-custom-check-in-rule-set"></a>Vytvoření sady vlastních pravidel vrácení se změnami projektu

Pokud chcete vytvořit vlastní sadu pravidel pro projekt Azure DevOps, nejprve vytvoříte speciální složky pro pravidlo zásad vrácení se změnami v **Průzkumníka správy zdrojového kódu**. Vytvoření souboru sady pravidel a přidejte soubor do správy verzí. Nakonec zadejte pravidlo nastavit jako zásady analýzy kódu vrácení se změnami pro projekt.

> [!NOTE]
> K vytvoření složky v projektu aplikace Azure DevOps, je nejprve nutné mapovat kořen projektu do umístění na místním počítači.

### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Chcete-li vytvořit složku správy verzí pro Zásady vracení se změnami sadu pravidel

1. V Průzkumníku týmových projektů, rozbalte uzel projektu a pak klikněte na tlačítko **správy zdrojových kódů**.

2. V **složky** podokně klikněte pravým tlačítkem na projekt a potom klikněte na tlačítko **novou složku**.

3. V hlavním podokně správy zdrojového kódu, klikněte pravým tlačítkem na **novou složku**, klikněte na tlačítko **přejmenovat**a zadejte název pro složku sady pravidel.

### <a name="to-create-the-check-in-policy-rule-set"></a>Chcete-li vytvořit sadu pravidel zásad vrácení se změnami

1. Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **souboru**.

2. V **kategorie** klikněte na možnost **Obecné**.

3. V **šablony** seznamu, klikněte dvakrát na **sady pravidel analýzy kódu**.

4. [Zadejte pravidla](../code-quality/how-to-create-a-custom-rule-set.md) zahrnout v sadě pravidel, a potom uložte pravidlo nastavit soubor do složky sady pravidel, kterou jste vytvořili.

### <a name="to-add-the-rule-set-file-to-version-control"></a>Chcete-li přidat pravidla nastavit soubor do správy verzí

1. V **Průzkumníka správy zdrojového kódu**, klikněte pravým tlačítkem na novou složku a potom klikněte na tlačítko **přidat položky do složky**.

     Další informace najdete v tématu [Git a úložiště Azure](/azure/devops/repos/git/overview?view=vsts).

2. Klikněte na soubor, který jste vytvořili nastavené pravidlo a pak klikněte na tlačítko **Dokončit**.

     Soubor je přidán do správy zdrojového kódu a rezervovány u vás.

3. V **Průzkumníka správy zdrojového kódu** okno podrobností, klikněte pravým tlačítkem na název souboru a pak klikněte na **vrátit se změnami probíhající změny**.

4. V **vrácení se změnami** dialogovém okně máte možnost přidat komentář a potom klikněte na **vrátit se změnami**.

    > [!NOTE]
    > Pokud jste už nakonfigurovali zásady analýzy kódu vrácení se změnami pro váš projekt Azure DevOps a rozhodli jste **vynutit vrácení se změnami obsahovat soubory, které jsou součástí aktuálního řešení**, se aktivuje upozornění na selhání zásady. V dialogovém okně chyby zásad, vyberte **přepsat zásady selhání a pokračovat vrácení se změnami**. Přidejte požadované komentář a potom klikněte na tlačítko **OK**.

### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Určit pravidla, nastavte soubor jako zásady vrácení se změnami

1. Na **týmu** nabídky, přejděte k **nastavení projektu**a potom klikněte na tlačítko **správy zdrojových kódů**.

2. Klikněte na tlačítko **zásad vrácení se změnami**a potom klikněte na tlačítko **přidat**.

3. V **zásad vrácení se změnami** seznamu, klikněte dvakrát na **analýzy kódu**a ujistěte se, že **vynutit analýzu kódu pro spravovaný kód** je zaškrtnuto políčko.

4. V **spustit tuto sadu pravidel** klikněte na možnost  **\<vybrat sadu pravidel ze správy zdrojových kódů >** .

5. Zadejte cestu souboru sady pravidel zásad vrácení se změnami do správy verzí.

     Cesta musí splňovat následující syntaxi:

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > Můžete zkopírovat cestu pomocí jedné z následujících postupů na portále **Průzkumníka správy zdrojového kódu**:

    - V **složky** podokně klikněte na složku obsahující soubor sady pravidel. Zkopírovat cestu správy verzí ke složce, která se zobrazí v **zdroj** a ručně zadejte název souboru sady pravidel.

    - V okně podrobností klikněte pravým tlačítkem na soubor sady pravidel a potom klikněte na tlačítko **vlastnosti**. Na **Obecné** kartu, zkopírujte hodnotu v **název serveru**.

## <a name="synchronize-code-projects-to-the-check-in-policy-rule-set"></a>Synchronizaci projektů kódu k sadě pravidel zásad vrácení se změnami

Zadáte pravidlo zásad vrácení se změnami projektu nastavit jako sada pravidel analýzy kódu kód konfigurace projektu v dialogovém okně Vlastnosti projektu kódu. Pokud je sada pravidel na stejné jednotce jako projekt kódu, relativní cesta se používá k určení sady pravidel, pokud cesta je vybrána v dialogovém okně soubor. Relativní cesta povolí nastavení vlastnosti projektu přenosné na jiné počítače, které používají podobné místní verze řízení struktury.

### <a name="to-specify-a-project-rule-set-as-the-rule-set-of-a-code-project"></a>K určení pravidel projektu nastavit jako sady pravidel projektu kódu

1. V případě potřeby načíst zásady vrácení se změnami pravidlo sady složku a soubor ze správy verzí.

   Tento krok můžete provést **Průzkumníka správy zdrojového kódu** kliknutím pravým tlačítkem myši nastavené pravidlo složku a pak levým na **získat nejnovější verzi**.

2. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt kódu a potom klikněte na tlačítko **vlastnosti**.

3. **Klikněte na tlačítko pro analýzu kódu**.

4. V případě potřeby klikněte na příslušné možnosti v **konfigurace** a **platformy** seznamy.

::: moniker range="vs-2017"

5. Chcete-li spustit analýzu kódu pokaždé, když je projekt kódu sestaven pomocí zadané konfigurace, vyberte možnost **Povolit analýzu kódu při sestavení**.

::: moniker-end

::: moniker range=">=vs-2019"

5. Chcete-li spustit analýzu kódu pokaždé, když je projekt kódu sestaven pomocí zadané konfigurace, vyberte možnost **Spustit při sestavení** v části **binární analyzátory** .

::: moniker-end

6. V seznamu **Spustit tuto sadu pravidel** klikněte **\<Procházet >** .

8. Vyberte místní verzi souboru sady pravidel zásad vracení se změnami.

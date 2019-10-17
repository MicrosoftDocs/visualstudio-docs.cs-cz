---
title: Vlastní zásady vrácení se změnami analýzy kódu pro spravovaný kód
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 88703f14091628b1fc13c405ac4fabf48307aac7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448872"
---
# <a name="implement-custom-code-analysis-check-in-policies-for-managed-code"></a>Implementace vlastních zásad vracení zpět se změnami analýzy kódu pro spravovaný kód

Zásada pro vrácení se změnami analýzy kódu určuje sadu pravidel, které musí členové projektu Azure DevOps spustit ve zdrojovém kódu předtím, než se vrátí se změnami do řízení verze. Společnost Microsoft poskytuje sadu standardních *pravidel* , které seskupují pravidla analýzy kódu do funkčních oblastí. *Vlastní sady pravidel zásad vracení se změnami* určují sadu pravidel analýzy kódu, které jsou specifické pro projekt. Sada pravidel je uložena v souboru. RuleSet.

Zásady vracení se změnami jsou nastaveny na úrovni projektu Azure DevOps a určené umístěním souboru. ruleset ve stromu správy verzí. Neexistují žádná omezení umístění správy verzí sady vlastních pravidel pro zásady týmu.

Analýza kódu je nakonfigurována pro jednotlivé projekty kódu v okně Vlastnosti pro každý projekt. Vlastní sada pravidel pro projekt kódu je určena fyzickým umístěním souboru. ruleset v místním počítači. Když je zadán soubor. ruleset, který je umístěn na stejné jednotce jako projekt kódu, používá Visual Studio relativní cestu k souboru v konfiguraci projektu.

Doporučený postup pro vytvoření sady vlastních pravidel pro projekt Azure DevOps je uložit soubor zásad vrácení se změnami. ruleset do speciální složky, která není součástí žádného projektu kódu. Pokud soubor uložíte do vyhrazené složky, můžete použít oprávnění, která omezují, kdo může upravovat soubor pravidel, a můžete snadno přesunout strukturu adresáře, která obsahuje projekt, do jiného adresáře nebo na počítač.

## <a name="create-the-project-custom-check-in-rule-set"></a>Vytvoření sady pravidel pro vlastní vrácení se změnami projektu

Pokud chcete vytvořit vlastní sadu pravidel pro projekt Azure DevOps, nejdřív vytvořte speciální složku pro pravidlo zásad vrácení se změnami nastavenou v **Průzkumník správy zdrojových souborů**. Pak vytvoříte soubor sady pravidel a přidáte ho do správy verzí. Nakonec zadáte sadu pravidel jako zásadu vrácení se změnami analýzy kódu pro projekt.

> [!NOTE]
> Pokud chcete vytvořit složku v projektu Azure DevOps, musíte nejdřív namapovat kořen projektu na umístění v místním počítači.

### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Vytvoření složky správy verzí pro sadu pravidel zásad vracení se změnami

1. V Team Explorer rozbalte uzel projektu a klikněte na možnost **Správa zdrojového kódu**.

2. V podokně **složky** klikněte pravým tlačítkem myši na projekt a potom klikněte na možnost **Nová složka**.

3. V hlavním podokně Správa zdrojového kódu klikněte pravým tlačítkem myši na **Nová složka**, klikněte na příkaz **Přejmenovat**a zadejte název složky sady pravidel.

### <a name="to-create-the-check-in-policy-rule-set"></a>Vytvoření sady pravidel zásad vracení se změnami

1. V nabídce **soubor** přejděte na příkaz **Nový**a poté klikněte na možnost **soubor**.

2. V seznamu **kategorie** klikněte na **Obecné**.

3. V seznamu **šablony** poklikejte na **sada pravidel nástroje Analýza kódu**.

4. [Zadejte pravidla](../code-quality/how-to-create-a-custom-rule-set.md) , která mají být zahrnuta do sady pravidel, a poté uložte soubor sady pravidel do složky sady pravidel, kterou jste vytvořili.

### <a name="to-add-the-rule-set-file-to-version-control"></a>Přidání souboru sady pravidel do správy verzí

1. V **Průzkumník správy zdrojových souborů**klikněte pravým tlačítkem na novou složku a pak klikněte na **Přidat položky do složky**.

     Další informace najdete v tématu [Git a Azure Repos](/azure/devops/repos/git/overview?view=vsts).

2. Klikněte na soubor sady pravidel, který jste vytvořili, a pak klikněte na **Dokončit**.

     Soubor se přidá do správy zdrojového kódu a zarezervuje se na vás.

3. V okně Podrobnosti o **Průzkumník správy zdrojových souborů** klikněte pravým tlačítkem myši na název souboru a potom klikněte na možnost **vrátit se změnami do stavu nedokončené změny**.

4. V dialogovém okně **vrácení se změnami** máte možnost Přidat komentář a potom kliknout na možnost **vrátit se**změnami.

    > [!NOTE]
    > Pokud jste již nakonfigurovali zásadu vrácení se změnami analýzy kódu pro váš projekt Azure DevOps a vybrali jste možnost **vykonat vrácení se změnami, která bude obsahovat pouze soubory, které jsou součástí aktuálního řešení**, dojde k aktivaci upozornění na selhání zásad. V dialogovém okně selhání zásady vyberte možnost **přepsat selhání zásad a pokračovat v vrácení se změnami**. Přidejte požadovaný komentář a potom klikněte na tlačítko **OK**.

### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Určení souboru sady pravidel jako zásady vracení se změnami

1. V nabídce **tým** přejděte na **nastavení projektu**a pak klikněte na **Správa zdrojového kódu**.

2. Klikněte na **Zásady vracení se změnami**a pak klikněte na **Přidat**.

3. V seznamu **zásad vracení se změnami** dvakrát klikněte na **Analýza kódu**a ujistěte se, že je zaškrtnuté políčko **vykonat analýzu kódu pro spravovaný kód** .

4. V seznamu **Spustit tuto sadu pravidel** klikněte na možnost **\<Select sada pravidel ze správy zdrojového kódu >** .

5. Zadejte cestu k souboru sady pravidel zásad vracení se změnami v řízení verze.

     Cesta musí odpovídat následující syntaxi:

     **$/** `TeamProjectName` **/** `VersionControlPath`

    > [!NOTE]
    > Cestu můžete zkopírovat pomocí jednoho z následujících postupů v **Průzkumník správy zdrojových souborů**:

    - V podokně **složky** klikněte na složku, která obsahuje soubor sady pravidel. Zkopírujte cestu správy verzí složky, která se zobrazí v poli **zdroj** , a zadejte název souboru sady pravidel ručně.

    - V okně podrobností klikněte pravým tlačítkem na soubor sady pravidel a pak klikněte na **vlastnosti**. Na kartě **Obecné** Zkopírujte hodnotu do pole **název serveru**.

## <a name="synchronize-code-projects-to-the-check-in-policy-rule-set"></a>Synchronizace kódu projektů do sady pravidel zásad vracení se změnami

V dialogovém okně Vlastnosti projektu kódu zadáte sadu pravidel pro vrácení projektu se změnami, která je nastavena jako sada pravidel analýzy kódu pro konfiguraci projektu kódu. Pokud je sada pravidel umístěna na stejné jednotce jako projekt kódu, k určení sady pravidel při výběru cesty z dialogového okna soubor se použije relativní cesta. Relativní cesta umožňuje, aby nastavení vlastností projektu bylo přenosné na jiné počítače, které používají podobné struktury správy místní verze.

### <a name="to-specify-a-project-rule-set-as-the-rule-set-of-a-code-project"></a>Určení sady pravidel projektu jako sady pravidel projektu kódu

1. V případě potřeby načtěte složku a soubor sady pravidel vrácení se změnami ze správy verzí.

   Tento krok můžete provést v **Průzkumník správy zdrojových souborů** tak, že kliknete pravým tlačítkem na složku sady pravidel a pak kliknete na **načíst nejnovější verzi**.

2. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt kódu a pak klikněte na **vlastnosti**.

3. **Klikněte na analýza kódu**.

4. V případě potřeby klikněte na příslušné možnosti v seznamech **Konfigurace** a **platforma** .

::: moniker range="vs-2017"

5. Chcete-li spustit analýzu kódu pokaždé, když je projekt kódu sestaven pomocí zadané konfigurace, vyberte možnost **Povolit analýzu kódu při sestavení**.

::: moniker-end

::: moniker range=">=vs-2019"

5. Chcete-li spustit analýzu kódu pokaždé, když je projekt kódu sestaven pomocí zadané konfigurace, vyberte možnost **Spustit při sestavení** v části **binární analyzátory** .

::: moniker-end

6. V seznamu **Spustit tuto sadu pravidel** klikněte na **\<Browse >** .

8. Vyberte místní verzi souboru sady pravidel zásad vracení se změnami.

---
title: Implementace vlastních zásad vrácení se změnami analýzy kódu pro spravovaný kód | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1cf759e01e5f152f2220124c90f145bfbbe3c01d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651586"
---
# <a name="implementing-custom-code-analysis-check-in-policies-for-managed-code"></a>Implementace vlastních zásad vrácení se změnami Analýzy kódu pro spravovaný kód
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zásada pro vrácení se změnami analýzy kódu určuje sadu pravidel, které musí být spuštěny ve zdrojovém kódu před vrácením se změnami do správy verzí. Společnost Microsoft poskytuje sadu standardních *pravidel* , které seskupují pravidla analýzy kódu do funkčních oblastí. *Vlastní sady pravidel zásad vracení se změnami* určují sadu pravidel analýzy kódu, které jsou specifické pro týmový projekt. Sada pravidel je uložena v souboru. RuleSet.

 Zásady vrácení se změnami jsou nastaveny na úrovni týmového projektu a určené umístěním souboru. ruleset ve stromu správy verzí. Neexistují žádná omezení umístění správy verzí sady vlastních pravidel pro zásady týmu.

 Analýza kódu je nakonfigurována pro jednotlivé projekty kódu v okně Vlastnosti pro každý projekt. Vlastní sada pravidel pro projekt kódu je určena fyzickým umístěním souboru. ruleset v místním počítači. Když je zadán soubor. ruleset, který je umístěn na stejné jednotce jako projekt kódu, používá Visual Studio relativní cestu k souboru v konfiguraci projektu.

 Doporučený postup pro vytvoření sady vlastních pravidel týmového projektu je uložit soubor zásad vracení se změnami. ruleset do speciální složky, která není součástí žádného projektu kódu. Pokud soubor uložíte do vyhrazené složky, můžete použít oprávnění, která omezují, kdo může upravovat soubor pravidel, a můžete snadno přesunout strukturu adresáře, která obsahuje projekt, do jiného adresáře nebo na počítač.

## <a name="creating-the-team-project-custom-check-in-rule-set"></a>Vytváření sady pravidel pro vlastní vrácení se změnami v týmovém projektu
 Chcete-li vytvořit vlastní sadu pravidel pro týmový projekt, nejprve vytvořte speciální složku pro pravidlo zásad vrácení se změnami nastavenou v **Průzkumník správy zdrojových souborů**. Pak vytvoříte soubor sady pravidel a přidáte ho do správy verzí. Nakonec zadáte sadu pravidel jako zásadu vrácení se změnami analýzy kódu pro týmový projekt.

> [!NOTE]
> Chcete-li vytvořit složku v týmovém projektu, musíte nejprve namapovat kořen týmového projektu na umístění v místním počítači. Další informace najdete v tématu [Vytvoření a práce s pracovními prostory (staré)](https://msdn.microsoft.com/db4d5692-179a-44fe-ad31-0c1c900c9cb2).

#### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Vytvoření složky správy verzí pro sadu pravidel zásad vracení se změnami

1. V [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] rozbalte uzel týmový projekt a potom klikněte na možnost **Správa zdrojového kódu**.

2. V podokně **složky** klikněte pravým tlačítkem myši na týmový projekt a potom klikněte na možnost **Nová složka**.

3. V hlavním podokně Správa zdrojového kódu klikněte pravým tlačítkem myši na **Nová složka**, klikněte na příkaz **Přejmenovat**a zadejte název složky sady pravidel.

#### <a name="to-create-the-check-in-policy-rule-set"></a>Vytvoření sady pravidel zásad vracení se změnami

1. V nabídce **soubor** přejděte na příkaz **Nový**a poté klikněte na možnost **soubor**.

2. V seznamu **kategorie** klikněte na **Obecné**.

3. V seznamu **šablony** poklikejte na **sada pravidel nástroje Analýza kódu**.

4. Zadejte pravidla, která mají být zahrnuta do sady pravidel, a poté uložte soubor sady pravidel do složky sady pravidel, kterou jste vytvořili.

     Další informace najdete v tématu [vytváření vlastních sad pravidel](../code-quality/creating-custom-code-analysis-rule-sets.md) .

#### <a name="to-add-the-rule-set-file-to-version-control"></a>Přidání souboru sady pravidel do správy verzí

1. V **Průzkumník správy zdrojových souborů**klikněte pravým tlačítkem na novou složku a pak klikněte na **Přidat položky do složky**.

     Další informace naleznete v tématu [použití správy verzí](https://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314).

2. Klikněte na soubor sady pravidel, který jste vytvořili, a pak klikněte na **Dokončit**.

     Soubor se přidá do správy zdrojového kódu a zarezervuje se na vás.

3. V okně Podrobnosti o **Průzkumník správy zdrojových souborů** klikněte pravým tlačítkem myši na název souboru a potom klikněte na možnost **vrátit se změnami do stavu nedokončené změny**.

4. V dialogovém okně **vrácení se změnami** máte možnost Přidat komentář a potom kliknout na možnost **vrátit se**změnami.

    > [!NOTE]
    > Pokud jste již nakonfigurovali zásadu vrácení se změnami analýzy kódu pro týmový projekt a vybrali jste možnost vykonat vrácení se změnami, která bude **obsahovat pouze soubory, které jsou součástí aktuálního řešení**, dojde k aktivaci upozornění na selhání zásad. V dialogovém okně selhání zásady vyberte možnost **přepsat selhání zásad a pokračovat v vrácení se změnami**. Přidejte požadovaný komentář a potom klikněte na tlačítko **OK**.

#### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Určení souboru sady pravidel jako zásady vracení se změnami

1. V nabídce **tým** přejděte na položku **nastavení týmového projektu**a poté klikněte na možnost **Správa zdrojového kódu**.

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

## <a name="synchronizing-code-projects-to-the-check-in-policy-rule-set"></a>Synchronizace kódu projektů do sady pravidel zásad vracení se změnami
 Určíte pravidlo zásad vrácení se změnami týmového projektu jako sadu pravidel analýzy kódu v konfiguraci projektu kódu v dialogovém okně Vlastnosti projektu kódu. Pokud je sada pravidel umístěna na stejné jednotce jako projekt kódu, k určení sady pravidel při výběru cesty z dialogového okna soubor se použije relativní cesta. Relativní cesta umožňuje, aby nastavení vlastností projektu bylo přenosné na jiné počítače, které používají podobné struktury správy místní verze.

#### <a name="to-specify-a-team-project-rule-set-as-the-rule-set-of-a-code-project"></a>Určení sady pravidel týmového projektu jako sady pravidel projektu kódu

1. V případě potřeby načtěte složku a soubor sady pravidel vrácení se změnami ze správy verzí.

     Tento krok můžete provést v **Průzkumník správy zdrojových souborů** tak, že kliknete pravým tlačítkem na složku sady pravidel a pak kliknete na **načíst nejnovější verzi**.

2. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt kódu a pak klikněte na **vlastnosti**.

3. **Klikněte na analýza kódu**.

4. V případě potřeby klikněte na příslušné možnosti v seznamech **Konfigurace** a **platforma** .

5. Chcete-li spustit analýzu kódu pokaždé, když je projekt kódu sestaven pomocí zadané konfigurace, vyberte zaškrtávací políčko **Povolit analýzu kódu při sestavení (definuje CODE_ANALYSIS konstanta)** .

6. Chcete-li ignorovat kód v součástech z jiných společností, zaškrtněte políčko **Potlačit výsledky z generovaného kódu** .

7. V seznamu **Spustit tuto sadu pravidel** klikněte na **\<Browse... >** .

8. Zadejte místní verzi souboru sady pravidel zásad vracení se změnami.

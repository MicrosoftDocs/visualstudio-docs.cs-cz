---
title: 'Postupy: přizpůsobení funkce služby SharePoint | Microsoft Docs'
description: Přizpůsobení funkcí služby SharePoint v aplikaci Visual Studio. Návrhář funkcí se otevře při přidání nové funkce v Průzkumník řešení nebo v Průzkumníkovi balíčku služby SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b4846d79af7a031970e8870626f88450e8a3e647
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903660"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>Postupy: přizpůsobení funkce služby SharePoint
  Funkce služby SharePoint můžete vytvořit a přizpůsobit pomocí návrháře funkcí v aplikaci Visual Studio. Můžete například nastavit rozsah funkcí a přidat další funkce jako závislosti. Ve výchozím nastavení se Návrhář funkcí otevře při přidání nové funkce v Průzkumník řešení nebo v Průzkumníkovi balíčku služby SharePoint.

## <a name="opening-the-feature-designer"></a>Otevření návrháře funkcí
 Můžete přidat nebo odebrat položky projektu služby SharePoint do funkce pomocí návrháře funkcí.

#### <a name="to-open-the-feature-designer"></a>Otevření návrháře funkcí

1. V **Průzkumník řešení** rozbalte možnost **funkce**.

2. Dvakrát klikněte na položku *Feature1* , nebo otevřete místní nabídku položky *Feature1* a pak zvolte možnost **Návrhář zobrazení**.

## <a name="view-the-packaged-manifest-file"></a>Zobrazit zabalený soubor manifestu
 Pomocí návrháře funkcí můžete upravit a vygenerovat soubor manifestu zabalený pro funkci (*feature.xml*). Pak můžete zobrazit kód XML pro tento soubor v aplikaci Visual Studio.

#### <a name="to-view-the-packaged-manifest-file"></a>Zobrazení souboru manifestu balíčku

1. V **Návrháři funkcí** klikněte na kartu **manifest** .

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Chcete-li zobrazit zabalený soubor manifestu pomocí Průzkumník řešení

1. V **Průzkumník řešení** klikněte na ikonu **Zobrazit všechny soubory** .

2. Rozbalte položku funkce, rozbalte položku vlastnost a rozbalte možnost vlastnost vlastnosti a pak otevřete soubor *\<FeatureName>.Template.xml* .

    > [!NOTE]
    > Když otevřete soubor XML manifestu šablony funkce, soubory budou automaticky ověřeny a upozornění, která se zobrazí v okně Seznam chyb lze ignorovat.

## <a name="change-the-manifest-template"></a>Změna šablony manifestu
 Můžete změnit kód XML pro soubor manifestu funkce v editoru XML sady Visual Studio nebo v podokně šablona manifestu. Jakékoli změny kódu XML jsou sloučeny do zabaleného souboru manifestu pro danou funkci. Například můžete chtít změnit šablonu manifestu, aby bylo možné přizpůsobit vlastnost funkce.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Změna šablony manifestu pomocí editoru XML

1. V **Návrháři funkcí** klikněte na kartu **manifest** , rozbalte uzel **Možnosti úprav** a pak zvolte odkaz **otevřít v editoru XML** .

     Změny XML jsou sloučeny do zabaleného souboru manifestu.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Změna šablony manifestu pomocí podokna šablony manifestu

1. V **Návrháři funkcí** klikněte na kartu **manifest** , rozbalte uzel **Možnosti úprav** a pak změňte kód XML, který se zobrazí v podokně šablona manifestu.

     Změny XML se zobrazí v podokně **verze Preview sbaleného manifestu** .

## <a name="overwrite-the-packaged-manifest-file"></a>Přepsat zabalený soubor manifestu
 Můžete zakázat návrháře funkcí a vytvořit soubor *feature.xml* ručně. Při prvním provedení tohoto postupu se aktuální nastavení v Návrháři funkcí uloží do souboru XML šablony funkce. Pak můžete kód XML upravit nebo přepsat.

> [!NOTE]
> Pokud přidáte nebo odeberete položky projektu služby SharePoint v souboru XML v době, kdy je Návrhář funkcí zakázán, tyto položky projektu nejsou zabaleny.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Přepsání zabaleného souboru manifestu tím, že zakážete návrháře

1. V **Návrháři funkcí** klikněte na kartu **manifest** .

2. Rozbalte uzel **Možnosti úprav** , zvolte **přepsat vygenerované XML a upravit manifest v odkazu editoru XML** a pak klikněte na tlačítko **Ano** .

     Šablona je aktualizována s aktuálním zabaleným souborem manifestu.

## <a name="enable-the-feature-designer"></a>Povolení návrháře funkcí
 Můžete znovu povolit návrháře funkcí a přizpůsobit soubor *feature.xml* .

#### <a name="to-re-enable-the-designer"></a>Opětovné povolení návrháře

1. V **Návrháři funkcí** zvolte možnost **Zahodit úpravy manifestu a znovu povolit odkaz návrháře** a pak klikněte na tlačítko **Ano** .

2. Šablona se aktualizuje s původním textem a všechny změny v souboru XML se ztratí.

## <a name="see-also"></a>Viz také
- [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

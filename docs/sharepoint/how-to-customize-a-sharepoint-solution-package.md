---
title: 'Postupy: Přizpůsobení balíčku řešení služby SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 77b66160d489f711b5588fdcdd024d13769d734f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016865"
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>Postupy: Přizpůsobení balíčku řešení služby SharePoint
  K vytvoření a přizpůsobení balíčku (*. wsp*) můžete použít návrháře balíčků. Můžete například přidat položky a funkce projektu služby SharePoint, určit, zda je webový server resetován při nasazení řešení, a nastavit typ serveru nasazení.

## <a name="open-the-package-designer"></a>Otevřít návrháře balíčků

#### <a name="to-open-the-package-designer"></a>Otevření návrháře balíčků

- V **Průzkumník řešení**dvakrát klikněte na **balíček**nebo v místní nabídce pro **balíček**vyberte **Návrhář zobrazení** .

## <a name="view-the-packaged-manifestffile"></a>Zobrazit zabalený manifestfFile
 Pomocí návrháře balíčků můžete upravit a vygenerovat zabalený soubor manifestu. Pak můžete zobrazit kód XML pro tento soubor v aplikaci Visual Studio.

#### <a name="to-view-the-xml-source-file"></a>Zobrazení zdrojového souboru XML

1. V **Návrháři balíčků**vyberte možnost **manifest**.

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Chcete-li zobrazit zabalený soubor manifestu pomocí Průzkumník řešení

1. V **Průzkumník řešení**vyberte možnost **Zobrazit všechny soubory**.

2. Rozbalte položku balíček, rozbalte balíček. Package a pak otevřete soubor *Package.Template.xml* .

    > [!NOTE]
    > Když otevřete soubor XML manifestu pro šablonu balíčku, soubory budou automaticky ověřeny a můžete ignorovat upozornění, která se zobrazí v okně Seznam chyb.

## <a name="change-the-manifest-template"></a>Změna šablony manifestu
 Můžete změnit kód XML pro zabalený soubor manifestu v editoru XML sady Visual Studio nebo v podokně šablona manifestu. Všechny změny kódu XML jsou sloučeny do balíčku souboru manifestu balíčku.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Změna šablony manifestu pomocí editoru XML

1. V **Návrháři balíčků**zvolte kartu **manifest** , rozbalte uzel **Možnosti úprav** a pak zvolte odkaz **otevřít v editoru XML** .

     Změny XML jsou sloučeny do zabaleného souboru manifestu.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Změna šablony manifestu pomocí podokna šablony manifestu

1. V **Návrháři balíčků**zvolte kartu **manifest** , rozbalte uzel **Možnosti úprav** a pak změňte XML, které se zobrazí v podokně šablona manifestu.

     Změny XML se zobrazí v podokně **verze Preview sbaleného manifestu** .

## <a name="overwrite-the-packaged-manifest-file"></a>Přepsat zabalený soubor manifestu
 Můžete zakázat návrháře balíčků a vytvořit soubor *manifest.xml* ručně. Při prvním provedení tohoto postupu se aktuální nastavení v Návrháři balíčků uloží do souboru XML šablony balíčku. Pak můžete kód XML upravit nebo přepsat.

> [!NOTE]
> Pokud přidáte nebo odeberete položky projektu služby SharePoint a funkce v souboru XML v době, kdy je Návrhář balíčku zakázán, tyto položky projektu a funkce nejsou zabaleny.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Přepsání zabaleného souboru manifestu tím, že zakážete návrháře

1. V **Návrháři balíčků**klikněte na kartu **manifest** .

2. Rozbalte uzel **Možnosti úprav** , zvolte **přepsat vygenerované XML a upravit manifest v odkazu editoru XML** a pak klikněte na tlačítko **Ano** .

     Šablona je aktualizována s aktuálním zabaleným souborem manifestu.

## <a name="enable-the-package-designer"></a>Povolit návrháře balíčků
 Můžete znovu povolit návrháře balíčku pro přizpůsobení souboru *manifest.xml* .

#### <a name="to-re-enable-the-designer"></a>Opětovné povolení návrháře

1. V **Návrháři balíčků**zvolte možnost **Zahodit úpravy manifestu a znovu povolit odkaz návrháře** a pak klikněte na tlačítko **Ano** .

     Šablona se aktualizuje s původním textem a všechny změny v souboru XML se ztratí.

## <a name="see-also"></a>Viz také
- [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

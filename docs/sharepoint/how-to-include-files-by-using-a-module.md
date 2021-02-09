---
title: 'Postupy: zahrnutí souborů pomocí modulu | Microsoft Docs'
description: Zjistěte, jak zahrnout soubory pomocí modulu, což je kontejner, který umožňuje nasadit soubory, jako jsou hlavní stránky ASPX, textové soubory nebo obrázky, do služby SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e83a1474c7dfe6385c36cc13646bfe40fc897640
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913620"
---
# <a name="how-to-include-files-by-using-a-module"></a>Postupy: zahrnutí souborů pomocí modulu
  *Moduly* (nezaměňovat s [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] moduly) jsou kontejnery, které umožňují nasadit soubory, jako jsou hlavní stránky ASPX, textové soubory nebo obrázky, do SharePointu.

 Můžete zvolit nasazení souboru do knihovny dokumentů nebo jako normální soubor (například default. aspx) mimo knihovnu dokumentů. Chcete-li přidat soubor do knihovny dokumentů, zadejte `Type="GhostableInLibrary"` jako atribut v elementu **File** . Toto nastavení dá službě SharePoint pokyn, aby při přidání do knihovny vytvořila položku seznamu, která má přejít k souboru. Chcete-li nasadit soubor mimo knihovnu dokumentů, buď zadejte `Type="Ghostable"` nebo pouze vynechejte atribut **Type** .

## <a name="add-a-module-to-a-sharepoint-solution"></a>Přidání modulu do řešení služby SharePoint

#### <a name="to-add-a-module"></a>Přidání modulu

1. V aplikaci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otevřete nebo vytvořte projekt služby SharePoint.

     Další informace naleznete v tématu [šablony projektů a položek projektu služby SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. V **Průzkumník řešení** zvolte uzel projektu a potom v řádku nabídek zvolte **projekt**  >  **Přidat novou položku**.

     Otevře se dialogové okno **Přidat novou položku** .

3. V seznamu šablon služby SharePoint zvolte šablonu **modulu** a pak klikněte na tlačítko **Přidat** .

     Tento krok vytvoří uzel v projektu s názvem Module1.

4. V části Module1 odstraňte soubor *Sample.txt* .

     Sample.txt je součástí všech nových modulů pro účely tohoto příkladu a není potřeba. (Všimněte si, že odstranění souboru také odebere jeho položku z *Elements.xml* souboru modulu.)

5. Chcete-li, aby soubory byly nasazeny do konkrétní struktury složek v SharePointu, vytvořte tyto složky v oblasti Module1 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kliknutím na uzel Module1 a potom v řádku nabídek zvolte možnost **projekt**, **Nová složka**.

6. Zvolte složku, do které chcete soubor přidat, a poté v panelu nabídek zvolte možnost **projekt**, **Přidat existující položku**.

7. Zvolte jeden nebo více souborů, které chcete nasadit na SharePoint, a pak klikněte na tlačítko **Přidat** .

     Když do projektu přidáte soubor, automaticky se přidá položka pro tento soubor modulu Elements.xml. Po nasazení projektu jsou soubory zkopírovány na server SharePoint, relativně k kořenovému adresáři projektu, který je určen atributem **URL** elementu **souboru** , například `Url="Module1/New Folder/SomeFile.doc` . Pokud chcete změnit umístění nasazení souboru, přesuňte ho buď do jiné složky v **Průzkumník řešení** nebo změňte jeho nastavení **adresy URL** .

8. Pro všechny soubory, které se mají zobrazit v knihovně dokumentů, přidejte `Type="GhostableInLibrary"` atribut ke své položce v *Elements.xml*. Třeba

    ```xml
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />
    ```

9. Nasaďte projekt.

     Soubory se zkopírují do zadaných umístění na SharePointu.

## <a name="see-also"></a>Viz také
- [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)

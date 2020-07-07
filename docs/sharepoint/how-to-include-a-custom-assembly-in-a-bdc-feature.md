---
title: 'Postupy: Zahrnutí vlastního sestavení ve funkci BDC | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 772cdbaca67cc82fc6b7eb2c5ef5adb6508df34a
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015259"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Postupy: Zahrnutí vlastního sestavení ve funkci BDC
  Projekt může odkazovat na sestavení z jiných projektů ve stejném řešení. Je však nutné přidat tato sestavení do souboru funkce projektu pomocí dialogového okna **Přiřadit odkazovaná sestavení k LobSystems** .

### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Zahrnutí vlastního sestavení do funkce připojení obchodních dat (BDC)

1. V **Průzkumník řešení**vyberte složku, která obsahuje model služby BDC.

2. V nabídce **zobrazení** klikněte na položku **Vlastnosti okno**.

3. V okně **vlastnosti** zvolte vlastnost **Assemblies** a pak klikněte na tlačítko se třemi tečkami (![ASP.NET Mobile Designer – elipsa](../sharepoint/media/mwellipsis.gif "Elipsa ASP.NET Mobile Designer")).

     Zobrazí se dialogové okno **Přiřadit odkazovaná sestavení k LobSystems** .

4. V seznamu **vybrat sestavení** zvolte vlastní sestavení.

    > [!NOTE]
    > Sestavení se zobrazí pouze v dialogovém okně **Přiřadit odkazovaná sestavení do LobSystems** , pokud jste přidali odkaz na projekt, který obsahuje sestavení. Další informace naleznete v tématu [Postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

5. Ve skupině **referenční vlastnosti** otevřete seznam, který se zobrazí pro vlastnost **obor objektu LobSystem** , zvolte systém LOB metod, které používají vlastní sestavení, a poté klikněte na tlačítko **OK** .

    > [!NOTE]
    > Chcete-li ladit kód ve vlastním sestavení, je nutné přidat sestavení do balíčku řešení. Další informace najdete v tématu [Postup: Přidání a odebrání dalších sestavení](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

## <a name="see-also"></a>Viz také:
- [Postupy: použití souboru prostředků k určení lokalizovaných názvů, vlastností a oprávnění](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Postupy: Přidání stávajícího souboru modelu služby BDC do projektu služby SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Postupy: vytvoření modelu služby BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Integragte obchodních dat do služby SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)

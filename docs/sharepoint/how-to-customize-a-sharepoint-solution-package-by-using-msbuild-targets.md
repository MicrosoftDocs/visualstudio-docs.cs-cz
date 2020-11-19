---
title: Přizpůsobení balíčku řešení služby SharePoint pomocí cílů nástroje MSBuild
titleSuffix: ''
description: Přizpůsobení způsobu, jakým Visual Studio vytváří soubory balíčku řešení SharePoint (. wsp) pomocí cílů MSBuild na příkazovém řádku.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 5aa0afbe685c85d9a005dc621f58f17d396c0236
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903647"
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>Postupy: Přizpůsobení balíčku řešení služby SharePoint pomocí cílů nástroje MSBuild
  Pomocí cílů nástroje MSBuild v příkazovém řádku můžete přizpůsobit, jak sada Visual Studio vytváří soubory balíčku služby SharePoint (*. wsp*). Můžete například přizpůsobit vlastnosti nástroje MSBuild pro změnu zprostředkujícího adresáře balení a skupin položek MSBuild, které určují výčtové soubory.

## <a name="customize-and-run-msbuild-targets"></a>Přizpůsobení a spuštění cílů nástroje MSBuild
 Pokud přizpůsobíte cíle BeforeLayout a AfterLayout, můžete provádět úlohy před rozložením balíčku, například přidáním, odebráním nebo úpravou souborů, které budou zabaleny.

#### <a name="to-customize-the-beforelayout-target"></a>Přizpůsobení cíle BeforeLayout

1. Otevřete Editor, například Poznámkový blok, a poté přidejte následující kód.

   ```xml
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Target Name="BeforeLayout">
       <Message Importance="high" Text="In the BeforeLayout Target"></Message>
     </Target>
   </Project>
   ```

    Tento příklad zobrazí zprávu před balením tohoto cíle.

2. Pojmenujte soubor **CustomLayout. SharePoint. targets** a uložte jej do složky pro projekt služby SharePoint.

3. Otevřete projekt, otevřete místní nabídku a zvolte možnost **Uvolnit projekt**.

4. V **Průzkumník řešení** otevřete místní nabídku pro projekt a pak zvolte **Upravit** *\<ProjectName> . vbproj* nebo **Upravit** *\<ProjectName> . csproj*.

5. Po `Import` řádku poblíž konce souboru projektu přidejte následující řádek.

   ```xml
   <Import Project="CustomLayout.SharePoint.targets" />
   ```

6. Uložte a zavřete soubor projektu.

7. V **Průzkumník řešení** otevřete místní nabídku pro projekt a poté zvolte možnost **znovu načíst projekt**.

   Při publikování projektu se zpráva zobrazí ve výstupu před zahájením balení.

#### <a name="to-customize-the-afterlayout-target"></a>Přizpůsobení cíle AfterLayout

1. Na řádku nabídek klikněte na **soubor**  >  **otevřít**  >  **soubor**.

2. V dialogovém okně **otevřít soubor** přejděte do složky projektu, zvolte soubor CustomLayout. Target a pak klikněte na tlačítko **otevřít** .

3. Těsně před `</Project>` tagem přidejte následující kód:

   ```xml
   <Target Name="AfterLayout">
     <Message Importance="high" Text="In the AfterLayout Target"></Message>
   </Target>
   ```

    Tento příklad zobrazí zprávu po zabalení tohoto cíle.

4. Uložte a zavřete soubor cílů.

5. Restartujte Visual Studio a pak otevřete projekt.

   Při publikování projektu se zobrazí zpráva BeforeLayout před spuštěním balení a po dokončení balení se zobrazí zpráva AfterLayout.

## <a name="see-also"></a>Viz také
- [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

---
title: 'Postupy: přizpůsobení balíčku řešení služby SharePoint pomocí cílů nástroje MSBuild | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 434d673c62d0b26efa1559db7d7d98747146fd2d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889679"
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>Postupy: přizpůsobení balíčku řešení služby SharePoint pomocí cílů nástroje MSBuild
  Pomocí cílů nástroje MSBuild na příkazovém řádku můžete přizpůsobit, jak sada Visual Studio vytvoří soubory balíčku služby SharePoint (*.wsp*). Například můžete upravit vlastnosti nástroje MSBuild, chcete-li změnit zprostředkující adresář balení a skupiny nástroje MSBuild položky, které určují výčtu souborů.  
  
## <a name="customize-and-run-msbuild-targets"></a>Přizpůsobení a spuštění cíle nástroje MSBuild  
 Pokud upravíte BeforeLayout a AfterLayout cíle, můžete provádět úlohy před rozložení balíčku, například přidávání, odebírání nebo úpravy souborů, které budou zabalené.  
  
#### <a name="to-customize-the-beforelayout-target"></a>Chcete-li přizpůsobit BeforeLayout cíl  
  
1. Otevřete editor, třeba v poznámkovém bloku a potom přidejte následující kód.  
  
   ```xml  
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
     <Target Name="BeforeLayout">  
       <Message Importance="high" Text="In the BeforeLayout Target"></Message>  
     </Target>  
   </Project>  
   ```  
  
    Tento příklad zobrazí zprávu před balení tento cíl.  
  
2. Název souboru **CustomLayout.SharePoint.targets**a pak ho uložte do složky projektu služby SharePoint.  
  
3. Otevřete projekt, otevřete místní nabídku a zvolte **uvolnit projekt**.  
  
4. V **Průzkumníka řešení**, otevřete místní nabídku pro projekt a klikněte na tlačítko **upravit**  *\<ProjectName > .vbproj* nebo **upravit**  *\<ProjectName > .csproj*.  
  
5. Po `Import` řádek na konci souboru projektu, přidejte následující řádek.  
  
   ```xml  
   <Import Project="CustomLayout.SharePoint.targets" />  
   ```  
  
6. Uložte a zavřete soubor projektu.  
  
7. V **Průzkumníka řešení**, otevřete místní nabídku pro projekt a klikněte na tlačítko **znovu načíst projekt**.  
  
   Při publikování projektu, zpráva se zobrazí ve výstupu před zahájením balení.  
  
#### <a name="to-customize-the-afterlayout-target"></a>Chcete-li přizpůsobit AfterLayout cíl  
  
1. V panelu nabídky zvolte **souboru** > **otevřít** > **souboru**.  
  
2. V **otevřít soubor** dialogové okno, přejděte do složky projektu, zvolte soubor CustomLayout.target a klikněte na tlačítko **otevřít** tlačítko.  
  
3. Těsně před `</Project>` značky, přidejte následující kód:  
  
   ```xml  
   <Target Name="AfterLayout">  
     <Message Importance="high" Text="In the AfterLayout Target"></Message>  
   </Target>  
   ```  
  
    Tento příklad zobrazí zprávu po tento cíl je zabalená.  
  
4. Uložte a zavřete soubor cílů.  
  
5. Restartujte sadu Visual Studio a pak otevřete projekt.  
  
   Při publikování tohoto projektu se zobrazí zpráva BeforeLayout před spuštěním balení a po dokončení vytváření balíčků, zobrazí se zpráva AfterLayout.  
  
## <a name="see-also"></a>Viz také:
 [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  

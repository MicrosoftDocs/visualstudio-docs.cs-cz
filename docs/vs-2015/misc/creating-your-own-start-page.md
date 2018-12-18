---
title: Vytvoření vlastní úvodní stránku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Create start page
- custom start page
- customize start page
ms.assetid: a0df5b9c-0932-4e54-86f0-28530ad9d684
caps.latest.revision: 22
manager: douge
ms.openlocfilehash: 005f9597abd1ce688724af9fcb167a626e4cd885
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815036"
---
# <a name="creating-your-own-start-page"></a>Vytvoření vlastní úvodní stránky
Pomocí šablony projektu stránka Start nebo tak, že vytvoříte prázdnou stránku spuštění můžete vytvořit vlastní úvodní stránky.  
  
 Návrhář XAML neposkytují zcela přesné vizuální reprezentace vlastní úvodní stránky z důvodu závislosti na modelu aplikace Visual Studio.  
  
## <a name="using-the-project-template"></a>Pomocí šablony projektu  
 Úvodní stránka šablony projektu vytvoří projekt úvodní stránku, který je kompletní kopie sady Visual Studio úvodní stránka. Potom můžete upravit úvodní stránku vašich požadavků.  
  
#### <a name="to-create-a-custom-start-page-by-using-the-start-page-project-template"></a>Chcete-li vytvořit vlastní úvodní stránky pomocí šablony projektu úvodní stránka  
  
1.  Stáhněte a nainstalujte [šablonu projektu úvodní stránka](http://go.microsoft.com/fwlink/?LinkId=186204) z Galerie sady Visual Studio.  
  
    > [!WARNING]
    >  V tuto chvíli se neupgradovala šablony projektů Visual Studio 2010 úvodní stránku. Informace o tom, jak upgradovat tuto šablonu naleznete v tématu [postupy: Upgrade Visual Studio vlastní úvodní stránku](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).  
  
2.  Po instalaci šablony, vytvořte nový projekt úvodní stránka s ním.  
  
3.  V levém podokně dialogového okna Nový projekt v rámci **nainstalované šablony**, rozbalte **ostatní typy projektů** uzlu a pak klikněte na tlačítko **rozšiřitelnost**.  
  
4.  V prostředním podokně klikněte na tlačítko **vlastní úvodní stránku**a poté pojmenujte svůj projekt a klikněte na tlačítko **OK**.  
  
     Visual Studio vytvoří projekt úvodní stránku, který je kompletní kopie sady Visual Studio úvodní stránky.  
  
5.  Z **Průzkumníka řešení**, otevřete **StartPage.xaml**.  
  
6.  Upravte StartPage.xaml.  
  
     Práci můžete zobrazit stisknutím klávesy F5 spustíte experimentální instanci sady Visual Studio s vlastní úvodní stránky nainstalované.  
  
## <a name="creating-a-blank-start-page"></a>Vytvoření prázdné úvodní stránky  
 Nejjednodušší způsob, jak vytvořit prázdnou stránku spuštění je použití šablony projektu úvodní stránku a pak odeberte obsah.  
  
#### <a name="to-create-a-blank-start-page-by-using-the-start-page-project-template"></a>Chcete-li vytvořit prázdnou stránku spuštění pomocí šablony projektu úvodní stránka  
  
1. Vytvořte projekt úvodní stránky pomocí šablony projektu úvodní stránku, jak je popsáno v předchozím postupu.  
  
2. Otevřete StartPage.xaml.  
  
3. Odebere veškerý obsah stránky, byste museli opustit jenom vnější xml elementů a obsahující mřížky <xref:System.Windows.Controls.Grid> elementu, tak, aby váš soubor .xaml vypadá podobně jako v následujícím příkladu.  
  
   ```xaml
      <Grid xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
                xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
                xmlns:sp="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.StartPage"
                xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.10.0"
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.10.0"
            mc:Ignorable="d" 
                d:DesignHeight="600" d:DesignWidth="800">
       <Grid>
           <!--Add content here.-->
       </Grid>
   </Grid>
   ```
      
4. Odeberte všechny podpůrné soubory, které nezamýšlíte používat.  
  
    Byste měli mít soubor .vsix a .pkgdef pro účely nasazení.  
  
   Alternativně můžete vytvořit prázdnou stránku začít vytvořením souboru XAML se strukturou správná značka podle sady Visual Studio. Poté můžete přidat značky a modelu code-behind získat požadovaný vzhled a funkce. Další informace najdete v tématu [vytvoření vlastní úvodní stránku](../extensibility/creating-a-custom-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Testování a použití vlastní úvodní stránku  
 Nenastavujte primární instance spuštěné vlastní úvodní stránku, dokud můžete ověřit, že ho nehavaruje. Při testování vaší vlastní úvodní stránky, můžete jej použít do vašeho systému opakováním poslední tři kroky tohoto postupu v primární instance sady Visual Studio.  
  
#### <a name="to-test-a-custom-start-page"></a>Chcete-li otestovat vlastní úvodní stránky  
  
1. Stiskněte klávesu F5.  
  
    Experimentální instanci sady Visual Studio otevře se nová úvodní stránka nainstalované, ale nejsou vybrány.  
  
2. V experimentální instanci sady Visual Studio na **nástroje** nabídky, klikněte na tlačítko **možnosti**.  
  
3. V **možnosti** dialogovém okně **prostředí**vyberte **spuštění**. Potom na **přizpůsobit úvodní stránku** seznamu, vyberte soubor .xaml a klikněte na tlačítko **OK**.  
  
4. Na **zobrazení** nabídky, klikněte na tlačítko **úvodní stránka**.  
  
    Zobrazí se pracovní úvodní stránku. Musí Ukončete experimentální instanci, znovu zkopírujte všechny změněné soubory a poté znovu otevřete experimentální instanci zobrazíte nové změny.  
  
   Můžete sdílet vaše vlastní úvodní stránky tak, že nahrajete soubor VSIX do adresáře bin\debug [Galerie sady Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) webový server nebo do jiného webu nebo intranetu sdílet. Další informace najdete v tématu [nasazení vlastní úvodní stránky](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Viz také  
 [Přizpůsobení úvodní stránky](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Návody: Přidání vlastního souboru XAML na úvodní stránku](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
---
title: Vytvoření vlastní úvodní stránky | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Create start page
- custom start page
- customize start page
ms.assetid: a0df5b9c-0932-4e54-86f0-28530ad9d684
caps.latest.revision: 22
manager: jillfra
ms.openlocfilehash: fba7f1e0801b6f977d47b13af025538f5d2fe031
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850978"
---
# <a name="creating-your-own-start-page"></a>Vytvoření vlastní úvodní stránky
Můžete vytvořit vlastní úvodní stránku buď pomocí šablony projektu úvodní stránky, nebo vytvořením prázdné úvodní stránky.  
  
 Návrhář XAML nemůže poskytnout plně přesné vizuální reprezentace vlastních spouštěcích stránek z důvodu závislostí v modelu aplikace Visual Studio.  
  
## <a name="using-the-project-template"></a>Použití šablony projektu  
 Šablona projektu úvodní stránky vytvoří projekt úvodní stránky, který je úplnou kopií úvodní stránky sady Visual Studio. Pak můžete upravit úvodní stránku podle svých požadavků.  
  
#### <a name="to-create-a-custom-start-page-by-using-the-start-page-project-template"></a>Vytvoření vlastní úvodní stránky pomocí šablony projektu úvodní stránky  
  
1. Stáhněte a nainstalujte [šablonu projektu úvodní stránky](https://visualstudiogallery.msdn.microsoft.com/f655a5dc-1a2d-4eca-b774-76c352c03b87) z galerie sady Visual Studio.  
  
    > [!WARNING]
    > V tuto chvíli nebyla upgradována šablona projektu úvodní stránky sady Visual Studio 2010. Informace o tom, jak upgradovat tuto šablonu, najdete v tématu [Postup: upgrade vlastní úvodní stránky sady Visual Studio](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).  
  
2. Po instalaci šablony vytvořte nový projekt úvodní stránky.  
  
3. V levém podokně dialogového okna Nový projekt rozbalte v části **Nainstalované šablony**uzel **ostatní typy projektů** a potom klikněte na **rozšiřitelnost**.  
  
4. V prostředním podokně klikněte na možnost **vlastní úvodní stránka**a potom zadejte název projektu a klikněte na tlačítko **OK**.  
  
     Visual Studio vytvoří projekt úvodní stránky, který je úplnou kopií úvodní stránky sady Visual Studio.  
  
5. Z **Průzkumník řešení**otevřete **StartPage. XAML**.  
  
6. Upravte StartPage. XAML.  
  
     Můžete zobrazit svou práci stisknutím klávesy F5 a otevřít experimentální instanci sady Visual Studio s nainstalovanou vlastní úvodní stránkou.  
  
## <a name="creating-a-blank-start-page"></a>Vytvoření prázdné úvodní stránky  
 Nejjednodušší způsob, jak vytvořit prázdnou úvodní stránku, je použít šablonu projektu úvodní stránka a pak odebrat obsah.  
  
#### <a name="to-create-a-blank-start-page-by-using-the-start-page-project-template"></a>Vytvoření prázdné úvodní stránky pomocí šablony projektu úvodní stránky  
  
1. Vytvořte projekt úvodní stránky pomocí šablony projektu úvodní stránka, jak je popsáno v předchozím postupu.  
  
2. Otevřete StartPage. XAML.  
  
3. Odeberte veškerý obsah stránky, ponechte pouze vnější prvky XML a obsahující <xref:System.Windows.Controls.Grid> element Grid, aby váš soubor. XAML vypadal jako následující příklad.  
  
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
      
4. Odeberte všechny podpůrné soubory, které nechcete použít.  
  
    Soubory. vsix a. pkgdef byste měli uchovávat pro účely nasazení.  
  
   Alternativně můžete vytvořit prázdnou úvodní stránku vytvořením souboru XAML se správnou strukturou značek, kterou má aplikace Visual Studio rozpoznat. Pak můžete přidat značky a kód na pozadí, abyste získali požadovaný vzhled a funkčnost. Další informace najdete v tématu [Vytvoření vlastní úvodní stránky](../extensibility/creating-a-custom-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Testování a použití vlastní úvodní stránky  
 Nenastavujte primární instanci tak, aby spouštěla vlastní úvodní stránku, dokud neověříte, zda nedošlo k chybě. Když jste otestovali vlastní úvodní stránku, můžete ji použít v systému opakováním posledních tří kroků tohoto postupu v primární instanci aplikace Visual Studio.  
  
#### <a name="to-test-a-custom-start-page"></a>Testování vlastní úvodní stránky  
  
1. Stiskněte klávesu F5.  
  
    Experimentální instance aplikace Visual Studio se otevře s nainstalovanou novou úvodní stránkou, ale není vybraná.  
  
2. V experimentální instanci aplikace Visual Studio v nabídce **nástroje** klikněte na možnost **Možnosti**.  
  
3. V dialogovém okně **Možnosti** vyberte v části **prostředí**možnost **po spuštění**. Poté v seznamu **Přizpůsobit úvodní stránku** vyberte soubor. XAML a klikněte na tlačítko **OK**.  
  
4. V nabídce **zobrazení** klikněte na možnost **Úvodní stránka**.  
  
    Zobrazí se stránka pracovní zahájení. Musíte zavřít experimentální instanci, znovu zkopírovat všechny změněné soubory a potom znovu otevřít experimentální instanci a zobrazit nové změny.  
  
   Vlastní úvodní stránku můžete sdílet tak, že nahrajete soubor. VSIX z adresáře bin\Debug na web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) nebo do jiného webu nebo do sdíleného intranetu. Další informace najdete v tématu [nasazení vlastních spouštěcích stránek](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Viz také  
 [Přizpůsobení úvodní stránky](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Návody: Přidání vlastního souboru XAML na úvodní stránku](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)

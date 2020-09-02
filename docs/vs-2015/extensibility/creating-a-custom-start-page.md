---
title: Vytvoření vlastní úvodní stránky | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: acb7922658a5dd7db0839051a42a119733c8b1d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184206"
---
# <a name="creating-a-custom-start-page"></a>Vytvoření vlastní úvodní stránky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud nemůžete vytvořit vlastní úvodní stránku pomocí šablony projektu úvodní stránka, jak je popsáno v části [úvodní stránky](../misc/creating-your-own-start-page.md), můžete je ručně vytvořit podle kroků v tomto dokumentu.  
  
## <a name="creating-a-blank-start-page"></a>Vytvoření prázdné úvodní stránky  
 Nejprve vytvořte prázdnou úvodní stránku vytvořením souboru. XAML, který obsahuje strukturu značek, kterou bude Visual Studio rozpoznávat. Pak přidejte značky a kód na pozadí, abyste mohli vytvořit vzhled a funkce, které chcete.  
  
#### <a name="to-create-a-blank-start-page"></a>Vytvoření prázdné úvodní stránky  
  
1. Vytvořte nový projekt typu **aplikace WPF** (**Visual C#/Windows Desktop**.  
  
2. Přidejte odkaz na `Microsoft.VisualStudio.Shell.14.0` .  
  
3. Otevřete soubor XAML v editoru XML a změňte element nejvyšší úrovně \<Window> na \<UserControl> prvek bez odebrání jakýchkoli deklarací oboru názvů.  
  
4. Odeberte `x:Class` deklaraci z elementu nejvyšší úrovně. To umožňuje obsah XAML kompatibilní s oknem nástrojů sady Visual Studio, který je hostitelem úvodní stránky.  
  
5. Přidejte následující deklarace oboru názvů do elementu nejvyšší úrovně \<UserControl> .  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Tyto obory názvů umožňují přístup k příkazům, ovládacím prvkům a nastavením uživatelského rozhraní sady Visual Studio. Další informace najdete v tématu [Přidání příkazů sady Visual Studio na úvodní stránku](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     Následující příklad ukazuje značku v souboru. XAML pro prázdnou úvodní stránku. Každý vlastní obsah by měl přejít do vnitřního <xref:System.Windows.Controls.Grid> prvku.  
  
    ```vb  
    <UserControl  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"  
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
        xmlns:local="clr-namespace:StartPageHost"  
        mc:Ignorable="d"  
         Height="350" Width="525">  
        <Grid>  
        <!--Add content here.-->  
        </Grid>  
    </UserControl>  
    ```  
  
6. Přidejte ovládací prvky do prázdného \<UserControl> prvku pro vyplnění vlastní úvodní stránky. Informace o tom, jak přidat funkce, které jsou specifické pro aplikaci Visual Studio, naleznete v tématu [Přidání příkazů sady Visual Studio na úvodní stránku](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Testování a použití vlastní úvodní stránky  
 Nenastavujte primární instanci aplikace Visual Studio tak, aby spouštěla vlastní úvodní stránku, dokud neověříte, zda nedošlo k chybě sady Visual Studio. Místo toho ho testujte v experimentální instanci.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>Otestování ručně vytvořené vlastní úvodní stránky  
  
1. Zkopírujte soubor XAML a všechny podpůrné textové soubory nebo soubory s označením do složky **%USERPROFILE%\My Documents\Visual Studio 2015 \ StartPages \\ ** .  
  
2. Pokud Úvodní stránka odkazuje na jakékoli ovládací prvky nebo typy v sestaveních, která nejsou nainstalována aplikací Visual Studio, zkopírujte sestavení a vložte je do _instalační složky sady Visual Studio_**\Common7\IDE\PrivateAssemblies \\ **.  
  
3. Na příkazovém řádku sady Visual Studio zadejte **devenv/rootsuffix exp** a otevřete experimentální instanci sady Visual Studio.  
  
4. V experimentální instanci přejdete na stránku **Nástroje/možnosti/prostředí/po spuštění** a v rozevíracím seznamu **Přizpůsobit úvodní stránku** vyberete svůj soubor XAML.  
  
5. V nabídce **zobrazení** klikněte na možnost **Úvodní stránka**.  
  
     Měla by se zobrazit vaše vlastní úvodní stránka. Pokud chcete změnit nějaké soubory, musíte zavřít experimentální instanci, provést změny, zkopírovat změněné soubory a potom znovu otevřít experimentální instanci a zobrazit změny.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Použití vlastní úvodní stránky v primární instanci sady Visual Studio  
  
- Po otestování úvodní stránky a jejím nalezení jako stabilní použijte možnost **Přizpůsobit úvodní stránku** v dialogovém okně **Možnosti** a vybrat ji jako úvodní stránku v primární instanci sady Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Přidání vlastního XAML na úvodní stránku](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Přidání uživatelského ovládacího prvku na úvodní stránku](../extensibility/adding-user-control-to-the-start-page.md)   
 [Přidávání příkazů sady Visual Studio na úvodní stránku](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [Návod: ukládání uživatelských nastavení na úvodní stránce](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Nasazení vlastních úvodních stránek](../extensibility/deploying-custom-start-pages.md)

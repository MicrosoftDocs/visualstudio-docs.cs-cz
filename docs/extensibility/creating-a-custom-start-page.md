---
title: Vytvoření vlastní úvodní stránky | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 3ac0abfe9eedf1c03a8be3bacddbe06ff5698380
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739639"
---
# <a name="creating-a-custom-start-page"></a>Vytvoření vlastní úvodní stránky

Vlastní úvodní stránku můžete vytvořit podle kroků v tomto dokumentu.

## <a name="create-a-blank-start-page"></a>Vytvoření prázdné úvodní stránky

Nejprve vytvořte prázdnou úvodní stránku vytvořením souboru *XAML,* který má strukturu značek, kterou visual studio rozpozná. Potom přidejte značky a kód na pozadí k vytvoření vzhledu a funkce, které chcete.

1. Vytvořte nový projekt typu **WPF aplikace** (**Visual C#** > **Windows Desktop**).

2. Přidejte odkaz `Microsoft.VisualStudio.Shell.14.0`na .

3. Otevřete soubor XAML v editoru XML \<a změňte \<element> okna nejvyšší úrovně na element UserControl> bez odebrání všech deklarací oboru názvů.

4. Odeberte deklaraci `x:Class` z prvku nejvyšší úrovně. Díky obsahu XAML kompatibilní s oknem nástroje Visual Studio, který je hostitelem úvodní stránky.

5. Přidejte následující deklarace oboru názvů \<do prvku> ovládacího prvku UserControl nejvyšší úrovně.

    ```vb
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
    ```

     Tyto obory názvů umožňují přístup k příkazům, ovládacím prvkům a nastavení uživatelského rozhraní sady Visual Studio. Další informace naleznete v [tématu Přidání příkazů sady Visual Studio na úvodní stránku](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

     Následující příklad ukazuje značky v souboru *XAML* pro prázdnou úvodní stránku. Jakýkoli vlastní obsah by <xref:System.Windows.Controls.Grid> měl jít do vnitřního prvku.

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

6. Přidejte ovládací \<prvky do prázdného prvku UserControl>, který vyplní vlastní úvodní stránku. Informace o přidání funkcí specifických pro Visual Studio naleznete v [tématu Přidání příkazů sady Visual Studio na úvodní stránku](../extensibility/adding-visual-studio-commands-to-a-start-page.md).

## <a name="test-and-apply-the-custom-start-page"></a>Testování a použití vlastní úvodní stránky

Nenastavujte primární instanci sady Visual Studio tak, aby spouštěla vlastní úvodní stránku, dokud neověříte, že se nezhroutí visual studio. Místo toho jej otestujte v experimentální instanci.

### <a name="to-test-a-manually-created-custom-start-page"></a>Testování ručně vytvořené vlastní úvodní stránky

1. Zkopírujte soubor XAML a všechny podpůrné textové soubory nebo soubory značek do složky *%USERPROFILE%\My\\ Documents\Visual Studio 2015\StartPages.*

2. Pokud úvodní stránka odkazuje na ovládací prvky nebo typy v sestaveních, které nejsou nainstalovány aplikací Visual Studio, zkopírujte sestavení a vložte je do *instalační složky {Visual Studio}\Common7\IDE\PrivateAssemblies\\*.

3. Na příkazovém řádku sady Visual Studio zadejte **příkaz devenv /rootsuffix Exp,** chcete-li otevřít experimentální instanci sady Visual Studio.

4. V experimentální instanci přejděte na**úvodní** stránku**prostředí** >  **Tools** > **Options** > Environment a vyberte soubor XAML v rozevíracím seznamu Přizpůsobit úvodní **stránku.**

5. V nabídce **Zobrazení** klepněte na tlačítko **Úvodní stránka**.

     Měla by být zobrazena vlastní úvodní stránka. Pokud chcete změnit všechny soubory, musíte zavřít experimentální instanci, provést změny, zkopírovat a vložit změněné soubory a pak znovu otevřít experimentální instanci pro zobrazení změn.

### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Použití vlastní úvodní stránky v primární instanci sady Visual Studio

- Po otestování úvodní stránky a zjistíní, že je stabilní, použijte možnost **Přizpůsobit úvodní stránku** v dialogovém okně **Možnosti** a vyberte ji jako úvodní stránku v primární instanci sady Visual Studio.

## <a name="see-also"></a>Viz také

- [Návod: Přidání vlastního xaml na úvodní stránku](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
- [Přidání uživatelského ovládacího prvku na úvodní stránku](../extensibility/adding-user-control-to-the-start-page.md)
- [Přidání příkazů sady Visual Studio na úvodní stránku](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
- [Návod: Uložení uživatelských nastavení na úvodní stránce](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)
- [Nasazení vlastních úvodních stránek](../extensibility/deploying-custom-start-pages.md)

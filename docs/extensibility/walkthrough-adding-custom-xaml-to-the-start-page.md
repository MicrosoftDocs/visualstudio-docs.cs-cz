---
title: 'Návod: Přidání vlastního XAML na úvodní stránku | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: a13aada6cca9b54d8469885ab4c314a89cd06d6c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905964"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Návod: Přidání vlastního kódu XAML na úvodní stránku

Tento návod ukazuje, jak vytvořit vlastní úvodní stránku sady Visual Studio, která obsahuje webový prohlížeč.

## <a name="add-custom-xaml"></a>Přidat vlastní XAML

1. Vytvořte úvodní stránku podle pokynů v části [Vytvoření vlastní úvodní stránky](../extensibility/creating-a-custom-start-page.md).

2. V souboru *MainWindow. XAML* Najděte \<Grid> oddíl.

3. Přidejte \<TabControl> element a \<TabItem> uvnitř \< Grid> prvku, jak je znázorněno v následujícím příkladu.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. Přidejte sekundu \<TabItem> s \<Button> elementem, který otevře nový projekt:

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="MyButton" Height="Auto">
                <Button Name="btnNewProj" Content="New Project"
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
                    CommandParameter="File.NewProject" >
                </Button>
            </TabItem>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

## <a name="test-the-custom-start-page"></a>Testování vlastní úvodní stránky

1. Stiskněte klávesu **F5**.

     Spustí se experimentální instance aplikace Visual Studio s nainstalovanou vlastní úvodní stránkou, ale není vybraná.

2. V experimentální instanci aplikace Visual Studio otevřete stránku **nástroje/Options/prostředí** .

3. Vyberte možnost **po spuštění**. V seznamu **Přizpůsobit úvodní stránku** vyberte soubor *. XAML* a klikněte na tlačítko **OK**.

4. V nabídce **zobrazení** klikněte na možnost **Úvodní stránka**.

5. Klikněte na kartu **Bing** .

     Měla by se zobrazit webová stránka Bingu.

6. Klikněte na kartu **myButton** .

     Mělo by se zobrazit tlačítko **MyProject** , ve kterém se otevře dialogové okno **Nový projekt** .

7. Zavřete experimentální instanci.

Chcete-li použít vlastní úvodní stránku, vyberte v části **nástroje**  >  **Možnosti**  >  **prostředí**možnost **spuštění**. V seznamu **Přizpůsobit úvodní stránku** vyberte soubor *. XAML* a klikněte na tlačítko **OK**.

## <a name="next-steps"></a>Další kroky

Úvodní stránka sady Visual Studio nyní obsahuje kartu, která zobrazuje kartu webového prohlížeče a kartu MyButton. Můžete vytvořit vlastní úvodní stránky, které mají jiné funkce, pomocí modelu *kódu na pozadí* k přidání vlastní knihovny DLL, jak je znázorněno v části [Přidání uživatelského ovládacího prvku na úvodní stránku](../extensibility/adding-user-control-to-the-start-page.md). Můžete sdílet vlastní úvodní stránky s ostatními uživateli publikováním výsledného souboru. VSIX na webu [Visual Studio Marketplace](https://marketplace.visualstudio.com/) , nebo do jiného webu nebo sdílené síťové složky. Další informace najdete v tématu [nasazení vlastních spouštěcích stránek](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>Viz také

- [Přizpůsobení úvodní stránky](../ide/customizing-the-start-page-for-visual-studio.md)
- [Ovládací prvky kontejneru WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)

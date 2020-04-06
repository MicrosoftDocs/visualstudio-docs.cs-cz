---
title: 'Návod: Přidání vlastního xaml na úvodní stránku | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 4e2afc90dc96978e8a8290afaa2d3278e8b621b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697680"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>Návod: Přidání vlastního xaml na úvodní stránku

Tento návod ukazuje, jak vytvořit vlastní úvodní stránku sady Visual Studio, která obsahuje webový prohlížeč.

## <a name="add-custom-xaml"></a>Přidat vlastní XAML

1. Vytvořte úvodní stránku podle pokynů v části [Vytvoření vlastní úvodní stránky](../extensibility/creating-a-custom-start-page.md).

2. V souboru *MainWindow.xaml* \<vyhledejte oddíl Grid>.

3. Přidejte \<prvek> TabControl a \<> \< položky TabItem uvnitř elementu Grid>, jak je znázorněno v následujícím příkladu.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. Přidejte \<druhou> Položky \<tabitem s prvkem Button>, který otevře nový projekt:

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

1. Stiskněte **klávesu F5**.

     Experimentální instance sady Visual Studio se otevře s nainstalovanou vlastní úvodní stránkou, ale není vybrána.

2. V experimentální instanci sady Visual Studio otevřete stránku **Nástroje /Možnosti / Prostředí.**

3. Vyberte **možnost Spustit**. V seznamu **Přizpůsobit úvodní stránku** vyberte soubor *.xaml* a klepněte na **tlačítko OK**.

4. V nabídce **Zobrazení** klepněte na tlačítko **Úvodní stránka**.

5. Klikněte na kartu **Bing.**

     Měla by se zobrazit webová stránka Bingu.

6. Klepněte na kartu **MyButton.**

     Mělo by se zobrazit tlačítko **MyProject,** které otevře dialogové okno **Nový projekt.**

7. Zavřete experimentální instanci.

Chcete-li použít vlastní **Tools** > úvodní stránku, vyberte v části**Tools Options** > **Environment** **položku Startup**. V seznamu **Přizpůsobit úvodní stránku** vyberte soubor *.xaml* a klepněte na **tlačítko OK**.

## <a name="next-steps"></a>Další kroky

Úvodní stránka sady Visual Studio nyní obsahuje kartu, která zobrazuje kartu webového prohlížeče a kartu MyButton. Pomocí modelu *s kódem na pozadí* můžete vytvořit vlastní úvodní stránky, které mají další funkce, a přidat tak vlastní dll, jak je znázorněno v části Přidání [uživatelského ovládacího prvku na úvodní stránku](../extensibility/adding-user-control-to-the-start-page.md). Vlastní úvodní stránky můžete sdílet s ostatními uživateli publikováním výsledného souboru Vsix na webu [Webu Visual Studio Marketplace](https://marketplace.visualstudio.com/) nebo na jiném webu nebo sdílené síťové složce. Další informace naleznete v [tématu Nasazení vlastních úvodních stránek](../extensibility/deploying-custom-start-pages.md).

## <a name="see-also"></a>Viz také

- [Přizpůsobení úvodní stránky](../ide/customizing-the-start-page-for-visual-studio.md)
- [Ovládací prvky kontejneru WPF](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)

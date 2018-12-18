---
title: Vytvoření ovládacího prvku panel nástrojů WPF | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2ad3edfa84ee64425a7a9fbc6b0dfc5098396907
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786025"
---
# <a name="creating-a-wpf-toolbox-control"></a>Vytvoření ovládacího prvku panelu nástrojů WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Šablony ovládacího prvku panelu nástrojů WPF (Windows Presentation Framework) umožňuje vytvořit ovládací prvky WPF, které jsou automaticky přidány do **nástrojů** při instalaci rozšíření. Toto téma ukazuje, jak použít šablonu k vytvoření **nástrojů** ovládacího prvku, které můžete distribuovat ostatním uživatelům.  
  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-wpf-toolbox-control"></a>Vytvoření ovládacího prvku panelu nástrojů WPF  
  
#### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Vytvoření rozšíření pomocí prvku sady nástrojů WPF  
  
1.  Vytvořte projekt VSIX s názvem `MyToolboxControl`. Můžete najít šablonu projektu VSIX v **nový projekt** dialogového okna v části **Visual C# / rozšíření**.  
  
2.  Po otevření projektu, přidejte **ovládacího prvku panelu nástrojů WPF** šablony položky s názvem `MyToolboxControl`. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **Add / nová položka**. V **přidat novou položku** dialogové okno, přejděte na **Visual C# / rozšíření** a vyberte **ovládacího prvku panelu nástrojů WPF**. V **název** pole v dolní části okna, změňte název souboru příkazu `MyToolboxControl.cs`.  
  
     Toto řešení nyní obsahuje uživatelský ovládací prvek, `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> , který přidá ovládací prvek **nástrojů**a **Microsoft.VisualStudio.ToolboxControl** položku prostředku v manifestu VSIX pro  nasazení.  
  
#### <a name="to-create-the-control-ui"></a>Vytvoření ovládacího prvku uživatelského rozhraní  
  
1.  V Návrháři otevřete MyToolboxControl.xaml.  
  
     Návrhář zobrazí <xref:System.Windows.Controls.Grid> ovládací prvek, který obsahuje <xref:System.Windows.Controls.Button> ovládacího prvku.  
  
2.  Upravte si rozložení mřížky. Když vyberete <xref:System.Windows.Controls.Grid> ovládací prvek, na horní a levé hrany mřížky se zobrazí modré ovládací panely. Kliknutím pruhy, můžete přidat řádků a sloupců do mřížky.  
  
3.  Přidejte podřízené ovládací prvky do mřížky. Podřízený ovládací prvek můžete umístit přetažením z **nástrojů** na oddíl v mřížce nebo nastavením jeho `Grid.Row` a `Grid.Column` atributů XAML. Následující příklad přidá dva popisky na horní řádek mřížky a tlačítko ve druhém řádku.  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## <a name="renaming-the-control"></a>Přejmenování ovládacího prvku  
 Ve výchozím nastavení, zobrazí se váš ovládací prvek v **nástrojů** jako **MyToolboxControl** ve skupině s názvem **MyToolboxControl.MyToolboxControl**. Tyto názvy v souboru MyToolboxControl.xaml.cs můžete změnit.  
  
1.  Otevřete MyToolboxControl.xaml.cs v zobrazení kódu.  
  
2.  Najít třídu MyToolboxControl a přejmenujte jej na TestControl. (Nejrychlejší způsob, jak to provést, je pro tuto třídu přejmenovat vyberte **přejmenovat** v místní nabídce a proveďte nutné kroky. (Další informace o **přejmenovat** naleznete [refaktoring přejmenování (C#)](../csharp-ide/rename-refactoring-csharp.md).)  
  
3.  Přejděte `ProvideToolboxControl` atribut a změňte hodnotu prvním parametrem **Test**. Toto je název skupiny, která bude obsahovat ovládacího prvku **nástrojů**.  
  
     Výsledný kód by měl vypadat takto:  
  
    ```csharp  
    [ProvideToolboxControl("Test", true)]  
    public partial class TestControl : UserControl  
    {  
        public TestControl()  
        {  
            InitializeComponent();  
        }  
    }  
    ```  
  
## <a name="building-testing-and-deployment"></a>Sestavování, testování a nasazení  
 Při ladění projektu byste měli najít ovládací prvek nainstalovaný v **nástrojů** experimentální instance sady Visual Studio.  
  
#### <a name="to-build-and-test-the-control"></a>Pro vytváření a testování ovládacího prvku  
  
1.  Projekt znovu sestavte a spusťte ladění.  
  
2.  V nové instanci sady Visual Studio vytvořte projekt aplikace WPF. Ujistěte se, že je otevřený Návrhář XAML.  
  
3.  Najít ovládací prvek ve **nástrojů** a přetáhněte jej na návrhovou plochu.  
  
4.  Spusťte ladění aplikace WPF.  
  
5.  Ověřte, že se zobrazí váš ovládací prvek.  
  
#### <a name="to-deploy-the-control"></a>Nasazení ovládacího prvku  
  
1.  Po sestavení testovaného projektu najdete soubor .vsix \bin\debug\ složky projektu.  
  
2.  Můžete ho nainstalovat na místním počítači poklepáním na soubor .vsix a postupu instalace. Chcete-li odinstalovat ovládací prvek, přejděte na **nástroje / rozšíření a aktualizace** a vyhledejte rozšíření pro ovládací prvky a potom klikněte na **odinstalovat**.  
  
3.  Nahrajte soubor .vsix k síti nebo na web.  
  
     Pokud nahrajete soubor, který má [Galerie sady Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) webové stránky, další uživatelé můžou používat **nástrojů / rozšíření a aktualizace** v sadě Visual Studio online ovládacího prvku najít a nainstalovat ho.


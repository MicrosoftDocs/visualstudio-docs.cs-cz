---
title: 'Návod: Zápis Vizualizéru v jazyce Visual Basic | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 549e1ce240808a3947b2780f5c96485439e44ecc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794879"
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>Návod: Zápis vizualizéru v jazyce Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak napsat Jednoduchý vizualizér pomocí [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. Vizualizaci, kterou vytvoříte v tomto názorném postupu se zobrazí obsah řetězce pomocí Windows Forms okno se zprávou. Tento vizualizér jednoduchým řetězcem je základní příklad, který znázorňuje, jak můžete vytvořit vizualizéry pro ostatní typy dat pro více projektů.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které se zobrazí mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, přejděte **nástroje** nabídky a zvolte **Import a Export** . Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Kód vizualizéru musí být umístěn v knihovně DLL, který bude číst ladicím programem. Prvním krokem je vytvoření projektu knihovny tříd pro knihovnu DLL.  
  
## <a name="create-and-prepare-a-class-library-project"></a>Vytvořte a připravte projekt knihovny tříd  
  
#### <a name="to-create-a-class-library-project"></a>Chcete-li vytvořit projekt knihovny tříd  
  
1. Na **souboru** nabídce zvolte **nový** a klikněte na tlačítko **nový projekt**.  
  
2. V **nový projekt** dialogovém okně **typu projektu**s, klikněte na tlačítko **jazyka Visual Basic**.  
  
3. V **šablony** klikněte **knihovny tříd**.  
  
4. V **název** zadejte vhodný název pro knihovny tříd rozhraní, jako například **MyFirstVisualizer**.  
  
5. Klikněte na tlačítko **OK**.  
  
   Po vytvoření knihovny tříd musíte přidat odkaz na Microsoft.VisualStudio.DebuggerVisualizers.DLL, aby mohli používat třídy definované existuje. Nejprve však je dejte projektu smysluplný název.  
  
#### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>Přejmenovat Class1.vb a přidat Microsoft.VisualStudio.DebuggerVisualizers  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Class1.vb**a v místní nabídce klikněte na tlačítko **přejmenovat**.  
  
2.  Změňte název na něco smysluplného, například DebuggerSide.vb z Class1.vb.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automaticky změní deklaraci třídy v DebuggerSide.vb tak, aby odpovídaly nový název souboru.  
  
3.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Moje první Vizualizéru**a v místní nabídce klikněte na tlačítko **přidat odkaz**.  
  
4.  V **přidat odkaz** dialogovém okně **.NET** klikněte na tlačítko Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
5.  Klikněte na tlačítko **OK**.  
  
6.  V DebuggerSide.vb, přidejte následující příkaz, kterým `Imports` příkazy:  
  
    ```  
    Imports Microsoft.VisualStudio.DebuggerVisualizers  
    ```  
  
## <a name="add-the-debugger-side-code"></a>Přidejte kód, ladicí program na straně  
 Nyní jste připraveni k vytvoření kódových straně ladicího programu. Toto je kód, který běží v rámci ladicího programu k zobrazení informací, které chcete vizualizovat. Nejprve budete muset změnit deklarace `DebuggerSide` objektu tak, aby se dědí ze základní třídy `DialogDebuggerVisualizer`.  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Dědění z DialogDebuggerVisualizer  
  
1. V DebuggerSide.vb přejděte na následující řádek kódu:  
  
   ```  
   Public Class DebuggerSide  
   ```  
  
2. Upravte kód tak, aby vypadá takto:  
  
   ```  
   Public Class DebuggerSide  
   Inherits DialogDebuggerVisualizer  
   ```  
  
   `DialogDebuggerVisualizer` má jednu abstraktní metoda `Show`, který je nutné přepsat.  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Pokud chcete přepsat metodu DialogDebuggerVisualizer.Show  
  
- V `public class DebuggerSide`, přidejte následující metodu:  
  
  ```  
  Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)  
  
      End Sub  
  ```  
  
  `Show` Metoda obsahuje kód, který ve skutečnosti vytvoří dialogové okno vizualizér datasetu nebo jiných prvků uživatelského rozhraní a zobrazí informace, které bylo předáno vizualizéru z ladicího programu. Musíte přidat kód, který vytvoří dialogové okno a zobrazí informace. V tomto podrobném návodu bude to provedete pomocí Windows Forms okno se zprávou. Nejdřív musíte přidat odkaz a `Imports` příkaz pro <xref:System.Windows.Forms>.  
  
#### <a name="to-add-systemwindowsforms"></a>Chcete-li přidat System.Windows.Forms  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy**a v místní nabídce klikněte na tlačítko **přidat odkaz**.  
  
2.  V **přidat odkaz** dialogovém okně **.NET** klikněte na tlačítko **System.Windows.Forms**.  
  
3.  Klikněte na tlačítko **OK**.  
  
4.  V DebuggerSide.cs, přidejte následující příkaz, kterým `Imports` příkazy:  
  
    ```  
    Imports System.Windows.Forms  
    ```  
  
## <a name="create-your-visualizers-user-interface"></a>Vytvoření vašeho Vizualizátor uživatelského rozhraní  
 Teď přidejte kód k vytvoření a zobrazení uživatelského rozhraní pro vaše vizualizér. Protože je to první vizualizéru, bude zjednodušení uživatelského rozhraní a použijte okno se zprávou.  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Chcete-li zobrazit výstup vizualizéru v dialogovém okně  
  
1.  V `Show` metodu, přidejte následující řádek kódu:  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString())  
    ```  
  
     Tento příklad kódu neobsahuje zpracování chyb. By měly zahrnovat zpracování chyb v reálné vizualizéru nebo jakékoli jiné aplikace.  
  
2.  Na **sestavení** nabídky, klikněte na tlačítko **sestavení MyFirstVisualizer**. Projekt má sestavit úspěšně. Než budete pokračovat, opravte případné chyby sestavení.  
  
## <a name="add-the-necessary-attribute"></a>Přidejte atribut nezbytné  
 To je ladicí program side kódu. Ještě jeden krok, je však: vizualizéru se skládá z atributu, který dává pokyn na straně laděného procesu, které kolekce tříd.  
  
#### <a name="to-add-the-debugee-side-code"></a>Chcete-li přidat kódu na straně laděného objektu  
  
1.  Přidejte následující kód atribut DebuggerSide.vb, po `Imports` příkazy ale předtím, než `namespace MyFirstVisualizer`:  
  
    ```  
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>  
    ```  
  
2.  Na **sestavení** nabídky, klikněte na tlačítko **sestavení MyFirstVisualizer**. Projekt má sestavit úspěšně. Než budete pokračovat, opravte případné chyby sestavení.  
  
## <a name="create-a-test-harness"></a>Vytvořit testovací prostředí  
 V tomto okamžiku je dokončena první vizualizér. Pokud jste postupovali podle kroků správně, může sestavení vizualizéru a nainstalujte ho do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Před instalací vizualizéru do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ale měli otestovat a ujistit se, že běží správně. Teď vytvoříte testovací prostředí pro spuštění vizualizéru bez instalace do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Chcete-li přidat testovací metody, chcete-li zobrazit vizualizér  
  
1. Přidejte následující metodu do třídy `public DebuggerSide`:  
  
   ```  
   Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)  
       Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))  
   visualizerHost.ShowVisualizer()  
   End Sub  
   ```  
  
2. Na **sestavení** nabídky, klikněte na tlačítko **sestavení MyFirstVisualizer**. Projekt má sestavit úspěšně. Než budete pokračovat, opravte případné chyby sestavení.  
  
   Dále musíte vytvořit spustitelný projekt volat vaše vizualizéru knihovny DLL. Pro jednoduchost použijte projekt konzolové aplikace.  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>Chcete-li přidat do řešení projekt konzolové aplikace  
  
1. Na **souboru** nabídky, klikněte na tlačítko **přidat**a potom klikněte na tlačítko **nový projekt**.  
  
2. V **přidat nový projekt** v dialogu **šablony** klikněte **konzolovou aplikaci**.  
  
3. V **název** zadejte smysluplný název konzolové aplikace, jako například **MyTestConsole**.  
  
4. Klikněte na tlačítko **OK**.  
  
   Nyní je třeba přidat že nezbytné odkazuje, takže MyTestConsole můžete volat MyFirstVisualizer.  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>Chcete-li přidat potřebné odkazy na MyTestConsole  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **MyTestConsole**a v místní nabídce klikněte na tlačítko **přidat odkaz**.  
  
2.  V **přidat odkaz** dialogovém okně **.NET** klikněte na tlačítko Microsoft.VisualStudio.DebuggerVisualizers.  
  
3.  Klikněte na tlačítko **OK**.  
  
4.  Klikněte pravým tlačítkem na **MyTestConsole**a potom klikněte na tlačítko **přidat odkaz** znovu.  
  
5.  V **přidat odkaz** dialogové okno, klikněte na tlačítko **projekty** kartu a potom vyberte MyFirstVisualizer.  
  
6.  Klikněte na tlačítko **OK**.  
  
## <a name="finish-your-test-harness-and-test-your-visualizer"></a>Dokončení testovací prostředí a testování vaší Vizualizéru  
 Teď přidejte kód k dokončení testovací prostředí.  
  
#### <a name="to-add-code-to-mytestconsole"></a>Přidání kódu do MyTestConsole  
  
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **soubor Program.vb**a v místní nabídce klikněte na tlačítko **přejmenovat**.  
  
2. Upravit název z Module1.vb na nějakou vhodnou hodnotu, jako například **TestConsole.vb**.  
  
    Všimněte si, že [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automaticky změní deklaraci třídy v TestConsole.vb tak, aby odpovídaly nový název souboru.  
  
3. V TestConsole. VB, přidejte následující `Imports` – příkaz:  
  
   ```  
   Imports MyFirstVisualizer  
   ```  
  
4. V metodě `Main`, přidejte následující kód:  
  
   ```  
   Dim myString As String = "Hello, World"  
   DebuggerSide.TestShowVisualizer(myString)  
   ```  
  
   Nyní jste připraveni k testování první vizualizér.  
  
#### <a name="to-test-the-visualizer"></a>K otestování vizualizéru  
  
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **MyTestConsole**a v místní nabídce klikněte na tlačítko **nastavit jako spouštěný projekt**.  
  
2. Na **ladění** nabídky, klikněte na tlačítko **Start**.  
  
    Spuštění aplikace konzoly. Vizualizéru se zobrazí a zobrazí řetězec "Hello, World."  
  
   Blahopřejeme. Stačí mít vytvořené a testovat vaše první vizualizéru.  
  
   Pokud chcete používat vaše vizualizéru v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] místo jen volání z testovací prostředí, je nutné ji nainstalovat. Další informace najdete v tématu [postupy: instalace Vizualizéru](../debugger/how-to-install-a-visualizer.md).  
  
## <a name="see-also"></a>Viz také  
 [Architektura vizualizéru](../debugger/visualizer-architecture.md)   
 [Postupy: instalace Vizualizéru](../debugger/how-to-install-a-visualizer.md)   
 [Vytváření vlastních vizualizérů](../debugger/create-custom-visualizers-of-data.md)




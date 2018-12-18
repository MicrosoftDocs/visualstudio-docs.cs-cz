---
title: Zápis vizualizéru v C# | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 08/01/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 872f1a899bf9731dd86d5d9c14e5639c2a4630aa
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059662"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Návod: Zápis vizualizéru v jazyce C# #
Tento návod ukazuje, jak napsat Jednoduchý vizualizér pomocí jazyka C#. Vizualizaci, kterou vytvoříte v tomto názorném postupu se zobrazí obsah řetězce pomocí okna se zprávou formulářů Windows. Tento vizualizér jednoduchým řetězcem není zvlášť užitečné sám o sobě, ale zobrazuje základní kroky, které je třeba provést pro vytvoření užitečnější vizualizéry pro jiné datové typy.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které se zobrazí mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, přejděte **nástroje** nabídky a zvolte **nastavení importu a exportu**. Další informace najdete v tématu [Resetovat nastavení](../ide/environment-settings.md#reset-settings).

Kód vizualizéru musí být umístěn v knihovně DLL, které budou číst ladicím programem. Proto prvním krokem je vytvoření projektu knihovny tříd pro knihovnu DLL.

## <a name="create-a-visualizer-manually"></a>Ruční vytvoření vizualizéru

Postupujte podle vizualizéru při vytváření úlohy.

### <a name="to-create-a-class-library-project"></a>Chcete-li vytvořit projekt knihovny tříd

1. Na **souboru** nabídce zvolte **nový > projekt**.

2. V **nový projekt** dialogovém okně **Visual C#** a pak vyberte **.NET Standard**.

3. V prostředním podokně vyberte **knihovny tříd**.

4. V **název** zadejte vhodný název pro knihovnu tříd, jako je například MyFirstVisualizer.

5. Klikněte na tlačítko **OK**.

   Po vytvoření knihovny tříd musíte přidat odkaz na Microsoft.VisualStudio.DebuggerVisualizers.DLL, aby mohli používat třídy definované existuje. Před přidáním odkazu však musíte přejmenovat některé třídy tak, aby měla smysluplný název.

### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Přejmenovat Class1.cs a přidat Microsoft.VisualStudio.DebuggerVisualizers

1. V **Průzkumníka řešení**Class1.cs pravým tlačítkem myši a zvolte **přejmenovat** v místní nabídce.

2. Změňte název na něco smysluplného, například DebuggerSide.cs z Class1.cs.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticky změní deklaraci třídy v DebuggerSide.cs tak, aby odpovídaly nový název souboru.

3. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy** a zvolte **přidat odkaz** v místní nabídce.

4. V **přidat odkaz** dialogovém okně **.NET** , vyberte Microsoft.VisualStudio.DebuggerVisualizers.DLL.

5. Klikněte na tlačítko **OK**.

6. V DebuggerSide.cs, přidejte následující příkaz, kterým `using` příkazy:

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   Nyní jste připraveni k vytvoření kódových straně ladicího programu. Toto je kód, který běží v rámci ladicího programu k zobrazení informací, které chcete vizualizovat. Nejprve budete muset změnit deklarace `DebuggerSide` objekt, který dědí ze základní třídy `DialogDebuggerVisualizer`.

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Dědění z DialogDebuggerVisualizer

1. V DebuggerSide.cs přejděte na následující řádek kódu:

   ```csharp
   public class DebuggerSide
   ```

2. Změnou kódu:

   ```csharp
   public class DebuggerSide : DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` má jednu abstraktní metodu (`Show`), který je nutné přepsat.

#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Pokud chcete přepsat metodu DialogDebuggerVisualizer.Show

- V `public class DebuggerSide`, přidejte následující **metody:**

  ```csharp
  protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  `Show` Metoda obsahuje kód, který ve skutečnosti vytvoří dialogové okno vizualizér datasetu nebo jiných prvků uživatelského rozhraní a zobrazí informace, které bylo předáno vizualizéru z ladicího programu. Musíte přidat kód, který vytvoří dialogové okno a zobrazí informace. V tomto podrobném návodu bude to provedete pomocí okna se zprávou formulářů Windows. Nejdřív musíte přidat odkaz a `using` příkaz pro System.Windows.Forms.

### <a name="to-add-systemwindowsforms"></a>Chcete-li přidat System.Windows.Forms

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **odkazy** a zvolte **přidat odkaz** v místní nabídce.

2. V **přidat odkaz** dialogovém okně **.NET** , vyberte v System.Windows.Forms.DLL.

3. Klikněte na tlačítko **OK**.

4. V DebuggerSide.cs, přidejte následující příkaz, kterým `using` příkazy:

   ```csharp
   using System.Windows.Forms;
   ```

   Teď přidejte kód k vytvoření a zobrazení uživatelského rozhraní pro vaše vizualizéru. Protože je to první vizualizéru, budeme zjednodušení uživatelského rozhraní a použijte okno se zprávou.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Chcete-li zobrazit výstup Vizualizéru v dialogovém okně

1. V `Show` metodu, přidejte následující řádek kódu:

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    Tento příklad kódu neobsahuje zpracování chyb. By měly zahrnovat zpracování chyb v reálné vizualizéru nebo jakékoli jiné aplikace.

2. Na **sestavení** nabídce zvolte **sestavení MyFirstVisualizer**. Projekt má sestavit úspěšně. Než budete pokračovat, opravte případné chyby sestavení.

   Který je koncem objektu kód na straně ladicího programu. Ještě jeden krok, je však; atribut, který říká na straně laděného procesu, které kolekce tříd se skládá z vizualizér.

### <a name="to-add-the-debuggee-side-code"></a>Přidání kódu straně laděného procesu

1. Přidejte následující kód atribut DebuggerSide.cs, po `using` příkazy ale předtím, než `namespace MyFirstVisualizer`:

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target = typeof(System.String),
   Description = "My First Visualizer")]
   ```

2. Na **sestavení** nabídce zvolte **sestavení MyFirstVisualizer**. Projekt má sestavit úspěšně. Než budete pokračovat, opravte případné chyby sestavení.

   V tomto okamžiku je dokončena první vizualizér. Pokud jste postupovali podle kroků správně, může sestavení vizualizéru a nainstalujte ho do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Před instalací vizualizéru do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ale měli otestovat a ujistit se, že běží správně. Teď vytvoříte testovací prostředí pro spuštění vizualizéru bez instalace do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Chcete-li přidat testovací metody, chcete-li zobrazit vizualizér

1. Přidejte následující metodu do třídy `public DebuggerSide`:

   ```csharp
   public static void TestShowVisualizer(object objectToVisualize)
   {
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
      visualizerHost.ShowVisualizer();
   }
   ```

2. Na **sestavení** nabídce zvolte **sestavení MyFirstVisualizer**. Projekt má sestavit úspěšně. Než budete pokračovat, opravte případné chyby sestavení.

   Dále musíte vytvořit spustitelný projekt volat vaše vizualizéru knihovny DLL. Pro zjednodušení budeme používat projekt konzolové aplikace.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Chcete-li přidat do řešení projekt konzolové aplikace

1. Na **souboru** nabídce zvolte **přidat** a potom klikněte na tlačítko **nový projekt**.

2. V **přidat nový projekt** dialogového okna zvolte **Visual C#** > **Windows Desktop**a klikněte na tlačítko **konzolovou aplikaci**.

3. V **název** zadejte smysluplný název konzolové aplikace, jako například `MyTestConsole`.

4. Klikněte na tlačítko **OK**.

   Nyní je třeba přidat že nezbytné odkazuje, takže MyTestConsole můžete volat MyFirstVisualizer.

### <a name="to-add-necessary-references-to-mytestconsole"></a>Chcete-li přidat potřebné odkazy na MyTestConsole

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **MyTestConsole** a zvolte **přidat odkaz** v místní nabídce.

2. V **přidat odkaz** dialogovém okně **.NET** , vyberte Microsoft.VisualStudio.DebuggerVisualizers.DLL.

3. Klikněte na tlačítko **OK**.

4. Klikněte pravým tlačítkem na **MyTestConsole** a zvolte **přidat odkaz** znovu.

5. V **přidat odkaz** dialogové okno, klikněte na tlačítko **projekty** kartu a potom klikněte na tlačítko MyFirstVisualizer.

6. Klikněte na tlačítko **OK**.

   Teď přidejte kód k dokončení testovací prostředí.

### <a name="to-add-code-to-mytestconsole"></a>Přidání kódu do MyTestConsole

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor Program.cs a zvolte **přejmenovat** v místní nabídce.

2. Upravte název na něco smysluplnějšího, jako je například TestConsole.cs ze souboru Program.cs.

    **Poznámka:** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticky změní deklaraci třídy v TestConsole.cs tak, aby odpovídaly nový název souboru.

3. V TestConsole.cs, přidejte následující kód, který `using` příkazy:

   ```csharp
   using MyFirstVisualizer;
   ```

4. V metodě `Main`, přidejte následující kód:

   ```csharp
   String myString = "Hello, World";
   DebuggerSide.TestShowVisualizer(myString);
   ```

   Nyní jste připraveni k testování první vizualizér.

### <a name="to-test-the-visualizer"></a>K otestování vizualizéru

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **MyTestConsole** a zvolte **nastavit jako spouštěný projekt** v místní nabídce.

2. Na **ladění** nabídce zvolte **Start**.

    Spuštění aplikace konzoly a Vizualizéru se zobrazí a zobrazí řetězec "Hello, World".

   Blahopřejeme. Stačí mít vytvořené a testovat vaše první vizualizéru.

   Pokud chcete používat vaše vizualizéru v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] místo jen volání z testovací prostředí, je nutné ji nainstalovat. Další informace najdete v tématu [postupy: instalace Vizualizéru](../debugger/how-to-install-a-visualizer.md).

## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Vytvořit pomocí šablony položky Vizualizéru vizualizéru

Zatím tento návod vám ukázal vytvoření vizualizéru ručně. To bylo provedeno jako learning cvičení. Teď, když víte, jak jednoduché vizualizéru funguje, je snadný způsob, jak vytvořit: pomocí šablony položky vizualizér.

Nejprve budete muset vytvořit nový projekt knihovny tříd.

### <a name="to-create-a-new-class-library"></a>Chcete-li vytvořit novou knihovnu tříd

1. Na **souboru** nabídce zvolte **nový > projekt**.

2. V **nový projekt** dialogovém okně **Visual C#** vyberte **.NET Standard**.

3. V prostředním podokně vyberte **knihovny tříd**.

4. V **název** zadejte vhodný název pro knihovnu tříd, jako je například MySecondVisualizer.

5. Klikněte na tlačítko **OK**.

   Teď můžete přidat položku vizualizéru do ní:

### <a name="to-add-a-visualizer-item"></a>Chcete-li přidat položku vizualizéru

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na MySecondVisualizer.

2. V místní nabídce zvolte **přidat** a potom klikněte na tlačítko **nová položka**.

3. V **přidat novou položku** dialogovém okně **položky Visual C#** vyberte **vizualizér**.

4. V **název** zadejte vhodný název, jako je například SecondVisualizer.cs.

5. Klikněte na tlačítko **přidat**.

   To je všechno je to. Podívejte se na soubor SecondVisualizer.cs a zobrazte kód, který šablona přidá za vás. Pokračujte a experimentovat s kódem. Teď, když znáte základy, jste na dobré cestě k vytvoření složitých a užitečné vizualizéry vlastní.

## <a name="see-also"></a>Viz také:

- [Architektura vizualizéru](../debugger/visualizer-architecture.md)
- [Postupy: Instalace vizualizéru](../debugger/how-to-install-a-visualizer.md)
- [Vytváření vlastních vizualizérů](../debugger/create-custom-visualizers-of-data.md)
---
title: Zápis vizualizéru v jazyce C# | Microsoft Docs
description: Postupujte podle návodu k vytvoření jednoduchého vizualizéru v jazyce C#. Zobrazuje požadované kroky s i bez použití šablony položky vizualizéru.
ms.custom: SEO-VS-2020
ms.date: 05/27/2020
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 86123ece79f7bbde4f4f91fac657dcc235056c0b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384990"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Návod: Zápis vizualizéru v jazyce C\#

Tento názorný postup ukazuje, jak napsat jednoduchý vizualizér pomocí jazyka C#. Vizualizér, který vytvoříte v tomto názorném postupu, zobrazí obsah řetězce pomocí okna se zprávou modelu Windows Forms. Tento jednoduchý vizualizér řetězců není zvlášť užitečný sám o sobě, ale ukazuje základní kroky, které musíte provést, abyste vytvořili užitečnější vizualizéry pro jiné datové typy.

> [!NOTE]
> Dialogová okna a příkazy nabídky, které se zobrazí, se můžou lišit od těch popsaných v nápovědě v závislosti na aktivním nastavení nebo edici. Pokud chcete nastavení změnit, přejděte do **nabídky Nástroje** a zvolte Importovat a **exportovat nastavení**. Další informace najdete v tématu [Resetování nastavení.](../ide/environment-settings.md#reset-settings)

Kód vizualizéru musí být umístěn v knihovně DLL, kterou bude číst ladicí program. Proto je prvním krokem vytvoření projektu knihovny tříd pro knihovnu DLL.

## <a name="create-a-visualizer-manually"></a>Ruční vytvoření vizualizéru

Pokud chcete vytvořit vizualizér, postupujte podle následujících úloh.

### <a name="to-create-a-class-library-project"></a>Vytvoření projektu knihovny tříd

1. Vytvořte nový projekt knihovny tříd.

    ::: moniker range=">=vs-2019"
    Stisknutím **klávesy Esc** zavřete úvodní okno. Zadejte **Ctrl + Q** a otevřete vyhledávací pole, zadejte **knihovnu tříd,** zvolte **Šablony** a pak zvolte Vytvořit novou knihovnu tříd **(.NET Framework).** V dialogovém okně, které se zobrazí, zvolte **Vytvořit.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **File** New Project  >  **(Soubor nového**  >  **projektu).** V levém podokně dialogového **okna** Nový projekt v části **Visual C#** zvolte **.NET Framework** a pak v prostředním podokně zvolte Knihovna tříd **(.NET Framework).**
    ::: moniker-end

2. Zadejte odpovídající název knihovny tříd, například , a `MyFirstVisualizer` potom klikněte na **Vytvořit** nebo **OK**.

   Po vytvoření knihovny tříd je nutné přidat odkaz na knihovnu Microsoft.VisualStudio.DebuggerVisualizers.DLL abyste mohli použít třídy definované zde. Před přidáním odkazu je však nutné přejmenovat některé třídy, aby měly smysluplné názvy.

### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Přejmenování souboru Class1.cs a přidání Microsoft.VisualStudio.DebuggerVisualizers

1. V Průzkumník řešení klikněte pravým tlačítkem na Class1.cs **a** v **místní** nabídce zvolte Přejmenovat.

2. Změňte název z Class1.cs na něco smysluplného, například DebuggerSide.cs.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticky změní deklaraci třídy v souboru DebuggerSide.cs tak, aby odpovídala novému názvu souboru.

3. V **Průzkumník řešení** klikněte pravým tlačítkem **na Odkazy** a v **místní** nabídce zvolte Přidat odkaz.

4. V dialogovém **okně Přidat** odkaz na kartě **Procházet** vyberte **Procházet** a vyhledejte Microsoft.VisualStudio.DebuggerVisualizers.DLL.

    Knihovnu DLL najdete v *\<Visual Studio Install Directory> podadresáři \Common7\IDE\PublicAssemblies* Visual Studio instalačního adresáře.

5. Klikněte na **OK**.

6. V souboru DebuggerSide.cs přidejte následující kód do direktiv `using` :

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   Teď jste připraveni vytvořit kód na straně ladicího programu. Jedná se o kód, který běží v ladicím programu a zobrazuje informace, které chcete vizualizovat. Nejprve musíte změnit deklaraci objektu tak, aby `DebuggerSide` dědí ze základní třídy `DialogDebuggerVisualizer` .

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Dědění z DialogDebuggerVisualizer

1. V souboru DebuggerSide.cs přejděte na následující řádek kódu:

   ```csharp
   public class DebuggerSide
   ```

2. Změňte kód na:

   ```csharp
   public class DebuggerSide : DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` má jednu abstraktní metodu ( `Show` ), kterou musíte přepsat.

#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Přepsání metody DialogDebuggerVisualizer.Show

- Do `public class DebuggerSide` souboru přidejte následující **metodu:**

  ```csharp
  protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  Metoda obsahuje kód, který ve skutečnosti vytvoří dialogové okno vizualizéru nebo jiné uživatelské rozhraní a zobrazí informace předané vizualizéru `Show` z ladicího programu. Musíte přidat kód, který vytvoří dialogové okno a zobrazí informace. V tomto názorném postupu to budete dělat pomocí okna se zprávou Windows Forms. Nejprve je nutné přidat odkaz a `using` direktivu pro System.Windows.Forms.

### <a name="to-add-systemwindowsforms"></a>Přidání System.Windows.Forms

1. V **Průzkumník řešení** klikněte pravým tlačítkem **na Odkazy** a v **místní** nabídce zvolte Přidat odkaz.

2. V dialogovém **okně Přidat** odkaz na kartě **Procházet** vyberte **Procházet** a vyhledejte System.Windows.Forms.DLL.

    Knihovnu DLL najdete ve složce *C:\Windows\Microsoft.NET\Framework\v4.0.30319*.

3. Klikněte na **OK**.

4. V souboru DebuggerSide.cs přidejte následující kód do direktiv `using` :

   ```csharp
   using System.Windows.Forms;
   ```

   Teď přidáte kód, který vytvoří a zobrazí uživatelské rozhraní vizualizéru. Vzhledem k tomu, že se jedná o váš první vizualizér, bude uživatelské rozhraní jednoduché a použijeme Okno se zprávou.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Zobrazení výstupu vizualizéru v dialogovém okně

1. Do metody `Show` přidejte následující řádek kódu:

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    Tento příklad kódu nezahrnuje zpracování chyb. Zpracování chyb byste měli zahrnout do skutečného vizualizéru nebo jakéhokoli jiného druhu aplikace.

2. V **nabídce Build (Sestavení)** zvolte **Build MyFirstVisualizer (Sestavit MyFirstVisualizer).** Projekt by se měl úspěšně sestavit. Než budete pokračovat, opravte všechny chyby sestavení.

   To je konec kódu na straně ladicího programu. Je tu ale ještě jeden krok. Atribut, který říká straně debuggee, která kolekce tříd tvoří vizualizér.

### <a name="to-add-the-type-to-visualize-for-the-debuggee-side-code"></a>Přidání typu pro vizualizaci kódu na straně ladění

V kódu na straně ladicího programu určíte typ, který se má vizualizovat (zdroj objektu) pro debuggee pomocí <xref:System.Diagnostics.DebuggerVisualizerAttribute> atributu . Vlastnost `Target` nastaví typ, který se má vizualizovat.

1. Do souboru DebuggerSide.cs přidejte následující kód atributu za direktivy , `using` ale před `namespace MyFirstVisualizer` :

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target = typeof(System.String),
   Description = "My First Visualizer")]
   ```

2. V **nabídce Build (Sestavení)** zvolte **Build MyFirstVisualizer (Sestavit MyFirstVisualizer).** Projekt by se měl úspěšně sestavit. Než budete pokračovat, opravte všechny chyby sestavení.

   V tomto okamžiku je váš první vizualizér dokončený. Pokud jste postupli správně, můžete vizualizér sestavit a nainstalovat do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Před instalací vizualizéru do byste ho ale měli otestovat, abyste se ujistili, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] že funguje správně. Teď vytvoříte nástroj pro testování pro spuštění vizualizéru bez jeho instalace do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Přidání testovací metody pro zobrazení vizualizéru

1. Do třídy přidejte následující metodu `public DebuggerSide` :

   ```csharp
   public static void TestShowVisualizer(object objectToVisualize)
   {
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
      visualizerHost.ShowVisualizer();
   }
   ```

2. V **nabídce Build (Sestavení)** zvolte **Build MyFirstVisualizer (Sestavit MyFirstVisualizer).** Projekt by se měl úspěšně sestavit. Než budete pokračovat, opravte všechny chyby sestavení.

   Dále je nutné vytvořit spustitelný projekt pro volání knihovny DLL vizualizéru. Pro zjednodušení použijeme projekt Konzolová aplikace.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Přidání projektu konzolové aplikace do řešení

1. V Průzkumník řešení klikněte pravým tlačítkem na řešení, zvolte **Přidat** a pak klikněte na **Nový projekt**.

    ::: moniker range=">=vs-2019"
    Do vyhledávacího pole zadejte **konzolová aplikace**, zvolte **Šablony** a pak zvolte **Vytvořit novou konzolovou aplikaci (.NET Framework).** V dialogovém okně, které se zobrazí, zvolte **Vytvořit.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **File** New Project  >  **(Soubor nového**  >  **projektu).** V levém podokně dialogového **okna** Nový projekt v části **Visual C#** zvolte **Windows Desktop** a pak v prostředním podokně zvolte Konzolová aplikace **(.NET Framework).**
    ::: moniker-end

2. Zadejte odpovídající název knihovny tříd, například , a `MyTestConsole` potom klikněte na **Vytvořit** nebo **OK**.

   Teď musíte přidat potřebné odkazy, aby mohl MyTestConsole volat MyFirstVisualizer.

### <a name="to-add-necessary-references-to-mytestconsole"></a>Přidání potřebných odkazů do MyTestConsole

1. V Průzkumník řešení klikněte pravým tlačítkem **na MyTestConsole** **a** **v** místní nabídce zvolte Přidat odkaz.

2. V dialogovém **okně Přidat** odkaz na **kartě Procházet** zvolte Microsoft.VisualStudio.DebuggerVisualizers.DLL.

3. Klikněte na **OK**.

4. Klikněte pravým tlačítkem **na MyTestConsole** a znovu **zvolte Přidat** odkaz.

5. V dialogovém **okně Přidat** odkaz klikněte na kartu **Projekty** a pak klikněte na MyFirstVisualizer.

6. Klikněte na **OK**.

   Teď přidáte kód pro dokončení testovacího využití.

### <a name="to-add-code-to-mytestconsole"></a>Přidání kódu do MyTestConsole

1. V Průzkumník řešení klikněte pravým tlačítkem na Soubor Program.cs **a** **v místní** nabídce zvolte Přejmenovat.

2. Upravte název ze souboru Program.cs na něco smysluplnějšího, například TestConsole.cs.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticky změní deklaraci třídy v souboru TestConsole. cs tak, aby odpovídala novému názvu souboru.

3. V TestConsole. cs přidejte do direktiv následující kód `using` :

   ```csharp
   using MyFirstVisualizer;
   ```

4. Do metody `Main` přidejte následující kód:

   ```csharp
   String myString = "Hello, World";
   DebuggerSide.TestShowVisualizer(myString);
   ```

   Teď jste připraveni otestovat svůj první vizualizér.

### <a name="to-test-the-visualizer"></a>Otestování Vizualizér

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na **MyTestConsole** a v místní nabídce vyberte **nastavit jako spouštěný projekt** .

2. V nabídce **ladit** klikněte na tlačítko **Spustit**.

    Spustí se Konzolová aplikace a zobrazí se Vizualizér a zobrazí řetězec "Hello, World".

   Blahopřejeme. Právě jste vytvořili a otestovali svůj první vizualizér.

   Pokud chcete použít svůj Vizualizér [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] místo toho, aby ho bylo možné volat ze samotného testovacího prostředí, musíte ho nainstalovat. Další informace najdete v tématu [Postup: instalace Vizualizátoru](../debugger/how-to-install-a-visualizer.md).

::: moniker range="vs-2017"

## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Vytvoření Vizualizér pomocí šablony položky Vizualizér

V tomto návodu vám ukázal, jak vytvořit Vizualizér ručně. To bylo provedeno v rámci výukového cvičení. Když teď víte, jak Jednoduchý vizualizér funguje, existuje jednodušší způsob, jak ho vytvořit: pomocí šablony položky Vizualizér.

Nejprve je třeba vytvořit nový projekt knihovny tříd.

### <a name="to-create-a-new-class-library"></a>Vytvoření nové knihovny tříd

1. V nabídce **soubor** vyberte možnost **Nový > projekt**.

2. V dialogovém okně **Nový projekt** vyberte v části **Visual C#** možnost **.NET Framework**.

3. V prostředním podokně vyberte možnost **Knihovna tříd**.

4. Do pole **název** zadejte vhodný název knihovny tříd, například MySecondVisualizer.

5. Klikněte na **OK**.

   Nyní můžete do něj přidat položku Vizualizér:

### <a name="to-add-a-visualizer-item"></a>Přidání položky Vizualizátoru

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na MySecondVisualizer.

2. V místní nabídce vyberte možnost **Přidat** a poté klikněte na položku **Nová položka**.

3. V dialogovém okně **Přidat novou položku** vyberte v části **Visual C# položky** **Vizualizér ladicího programu**.

4. Do pole **název** zadejte vhodný název, například SecondVisualizer. cs.

5. Klikněte na **Přidat**.

   To je vše, co je k dispozici. Podívejte se na soubor SecondVisualizer. cs a zobrazte si kód, který vám šablona přidala. Pokračujte a Experimentujte s kódem. Teď, když jste znali základy, jste na úmyslu vytvořit složitější a užitečné vizualizace, které vlastníte.
::: moniker-end

## <a name="see-also"></a>Viz také

- [Architektura Vizualizátoru](../debugger/visualizer-architecture.md)
- [Postupy: instalace Vizualizátoru](../debugger/how-to-install-a-visualizer.md)
- [Vytváření vlastních vizualizérů](../debugger/create-custom-visualizers-of-data.md)

---
title: Napište Vizualizér do C# | Microsoft Docs
ms.custom: seodec18
ms.date: 04/12/2019
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 995508380fd551af33d98ebd48ab02a8287d0284
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637958"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Návod: zápis Vizualizér do jazyka C \#
Tento návod ukazuje, jak napsat jednoduchý Vizualizér pomocí C#. Vizualizér, který v tomto návodu vytvoříte, zobrazí obsah řetězce pomocí okna se zprávou Windows Forms. Tento jednoduchý Vizualizér řetězců není zvlášť užitečný, ale zobrazuje základní kroky, které je nutné provést, aby bylo možné vytvořit užitečnější vizualizace pro jiné datové typy.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, přejděte do nabídky **nástroje** a vyberte **Nastavení importu a exportu**. Další informace najdete v tématu [resetování nastavení](../ide/environment-settings.md#reset-settings).

Kód Vizualizér musí být umístěn v knihovně DLL, která bude načtena ladicím programem. Proto je prvním krokem vytvoření projektu knihovny tříd pro knihovnu DLL.

## <a name="create-a-visualizer-manually"></a>Ruční vytvoření Vizualizér

Pomocí níže uvedených úloh vytvořte Vizualizér.

### <a name="to-create-a-class-library-project"></a>Vytvoření projektu knihovny tříd

1. Vytvořte nový projekt knihovny tříd.

    ::: moniker range=">=vs-2019"
    Stisknutím klávesy **ESC** zavřete okno Start. Zadáním **CTRL + Q** otevřete vyhledávací pole, zadejte **knihovny tříd**, zvolte **šablony**a pak zvolte **vytvořit novou knihovnu tříd (.NET Standard)** . V dialogovém okně, které se zobrazí, vyberte **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**. V levém podokně dialogového okna **Nový projekt** , v části **vizuál C#** zvolte možnost **.NET Standard**a potom v prostředním podokně zvolte možnost **Knihovna tříd (.NET Standard)** .
    ::: moniker-end

2. Zadejte vhodný název knihovny tříd, například `MyFirstVisualizer`, a pak klikněte na tlačítko **vytvořit** nebo **OK**.

   Po vytvoření knihovny tříd musíte přidat odkaz na Microsoft. VisualStudio. DebuggerVisualizers. DLL, abyste mohli použít třídy, které jsou zde definovány. Před přidáním odkazu však musíte přejmenovat některé třídy, aby měly smysluplné názvy.

### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Přejmenování Class1.cs a přidání Microsoft. VisualStudio. DebuggerVisualizers

1. V **Průzkumník řešení**klikněte pravým tlačítkem na Class1.cs a v místní nabídce vyberte **Přejmenovat** .

2. Změňte název z Class1.cs na něco smysluplného, například DebuggerSide.cs.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticky změní deklaraci třídy v DebuggerSide.cs tak, aby odpovídala novému názvu souboru.

3. V **Průzkumník řešení**klikněte pravým tlačítkem na **odkazy** a v místní nabídce vyberte **Přidat odkaz** .

4. V dialogovém okně **Přidat odkaz** na kartě **Procházet** vyberte **Procházet** a vyhledejte Microsoft. VisualStudio. DebuggerVisualizers. dll.

    Knihovnu DLL můžete najít v instalačním adresáři služby *\<Visual Studio > \Common7\IDE\PublicAssemblies* instalačního adresáře sady Visual Studio.

5. Klikněte na tlačítko **OK**.

6. Do DebuggerSide.cs přidejte následující direktivy `using`:

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   Nyní jste připraveni vytvořit kód na straně ladicího programu. Toto je kód, který běží v ladicím programu pro zobrazení informací, které chcete vizualizovat. Nejprve je třeba změnit deklaraci objektu `DebuggerSide` tak, aby dědil ze základní třídy `DialogDebuggerVisualizer`.

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Dědění z DialogDebuggerVisualizer

1. V DebuggerSide.cs přejdete na následující řádek kódu:

   ```csharp
   public class DebuggerSide
   ```

2. Změňte kód na:

   ```csharp
   public class DebuggerSide : DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` má jednu abstraktní metodu (`Show`), kterou je nutné přepsat.

#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Přepsání metody DialogDebuggerVisualizer. show

- V `public class DebuggerSide` přidejte následující **metodu:**

  ```csharp
  protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  Metoda `Show` obsahuje kód, který ve skutečnosti vytvoří dialogové okno vizualizér, nebo jiné uživatelské rozhraní a zobrazí informace, které byly předány do Vizualizér z ladicího programu. Je nutné přidat kód, který vytvoří dialogové okno a zobrazí informace. V tomto návodu to provedete pomocí okna se zprávou Windows Forms. Nejprve je třeba přidat odkaz a direktivu `using` pro System. Windows. Forms.

### <a name="to-add-systemwindowsforms"></a>Přidání System. Windows. Forms

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **odkazy** a v místní nabídce vyberte **Přidat odkaz** .

2. V dialogovém okně **Přidat odkaz** vyberte na kartě **Procházet** možnost **Procházet**a vyhledejte System. Windows. Forms. dll.

    Knihovnu DLL můžete najít v *C:\Windows\Microsoft.NET\Framework\v4.0.30319*.

3. Klikněte na tlačítko **OK**.

4. Do DebuggerSide.cs přidejte následující direktivy `using`:

   ```csharp
   using System.Windows.Forms;
   ```

   Nyní přidáte nějaký kód pro vytvoření a zobrazení uživatelského rozhraní pro Vizualizér. Vzhledem k tomu, že se jedná o váš první vizualizér, ponecháme uživatelské rozhraní jednoduché a bude používat okno se zprávou.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Zobrazení výstupu Vizualizér v dialogovém okně

1. Do metody `Show` přidejte následující řádek kódu:

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    Tento ukázkový kód nezahrnuje zpracování chyb. Zpracování chyb byste měli zahrnout do reálného Vizualizér nebo jakéhokoli jiného typu aplikace.

2. V nabídce **sestavení** klikněte na příkaz **sestavit MyFirstVisualizer**. Projekt by se měl úspěšně sestavit. Než budete pokračovat, opravte případné chyby sestavení.

   To je konec kódu na straně ladicího programu. Existuje ale ještě ještě víc kroků. atribut, který oznamuje laděného procesu stranu, kterou kolekce tříd zahrnuje vizualizér.

### <a name="to-add-the-debuggee-side-code"></a>Přidání kódu na straně laděného procesu

1. Přidejte následující kód atributu do DebuggerSide.cs za direktivami `using`, ale před `namespace MyFirstVisualizer`:

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target = typeof(System.String),
   Description = "My First Visualizer")]
   ```

2. V nabídce **sestavení** klikněte na příkaz **sestavit MyFirstVisualizer**. Projekt by se měl úspěšně sestavit. Než budete pokračovat, opravte případné chyby sestavení.

   V tomto okamžiku je váš první vizualizér dokončený. Pokud jste postupovali podle pokynů správně, můžete vytvořit Vizualizér a nainstalovat ho do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Než nainstalujete Vizualizér do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], měli byste ho ale otestovat, abyste se ujistili, že funguje správně. Nyní vytvoříte testovací kabel, abyste mohli spustit Vizualizér bez jeho instalace do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Chcete-li přidat testovací metodu pro zobrazení Vizualizér

1. Přidejte následující metodu do třídy `public DebuggerSide`:

   ```csharp
   public static void TestShowVisualizer(object objectToVisualize)
   {
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
      visualizerHost.ShowVisualizer();
   }
   ```

2. V nabídce **sestavení** klikněte na příkaz **sestavit MyFirstVisualizer**. Projekt by se měl úspěšně sestavit. Než budete pokračovat, opravte případné chyby sestavení.

   Dále je nutné vytvořit spustitelný projekt pro volání své knihovny Vizualizátor DLL. Pro zjednodušení použijeme projekt konzolové aplikace.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Přidání projektu konzolové aplikace do řešení

1. V Průzkumník řešení klikněte pravým tlačítkem myši na řešení, vyberte možnost **Přidat**a poté klikněte na možnost **Nový projekt**.

    ::: moniker range=">=vs-2019"
    Do vyhledávacího pole zadejte **Konzolová aplikace**, zvolte **šablony**a pak zvolte **vytvořit novou konzolovou aplikaci (.NET Framework)** . V dialogovém okně, které se zobrazí, vyberte **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**. V levém podokně dialogového okna **Nový projekt** , v části **vizuál C#** zvolte **Windows Desktop**a potom v prostředním podokně zvolte **Konzolová aplikace (.NET Framework)** .
    ::: moniker-end

2. Zadejte vhodný název knihovny tříd, například `MyTestConsole`, a pak klikněte na tlačítko **vytvořit** nebo **OK**.

   Nyní je nutné přidat nezbytné odkazy, aby MyTestConsole mohli volat MyFirstVisualizer.

### <a name="to-add-necessary-references-to-mytestconsole"></a>Přidání nezbytných odkazů na MyTestConsole

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **MyTestConsole** a v místní nabídce vyberte **Přidat odkaz** .

2. V dialogovém okně **Přidat odkaz** klikněte na kartu **Procházet** a vyberte Microsoft. VISUALSTUDIO. DebuggerVisualizers. dll.

3. Klikněte na tlačítko **OK**.

4. Klikněte pravým tlačítkem na **MyTestConsole** a pak znovu vyberte **Přidat odkaz** .

5. V dialogovém okně **Přidat odkaz** klikněte na kartu **projekty** a pak klikněte na MyFirstVisualizer.

6. Klikněte na tlačítko **OK**.

   Nyní přidáte kód pro dokončení testovacího svazku.

### <a name="to-add-code-to-mytestconsole"></a>Přidání kódu do MyTestConsole

1. V **Průzkumník řešení**klikněte pravým tlačítkem na program.cs a v místní nabídce vyberte **Přejmenovat** .

2. Upravte název z Program.cs na smysluplnější, například TestConsole.cs.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticky změní deklaraci třídy v TestConsole.cs tak, aby odpovídala novému názvu souboru.

3. Do TestConsole.cs přidejte následující kód do direktiv `using`:

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

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na **MyTestConsole** a v místní nabídce vyberte **nastavit jako spouštěný projekt** .

2. V nabídce **ladit** klikněte na tlačítko **Spustit**.

    Spustí se Konzolová aplikace a zobrazí se Vizualizér a zobrazí řetězec "Hello, World".

   Blahopřejeme. Právě jste vytvořili a otestovali svůj první vizualizér.

   Pokud chcete použít svůj Vizualizér v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] místo toho, abyste ho volali z testovacího prostředí, musíte ho nainstalovat. Další informace najdete v tématu [Postup: instalace Vizualizátoru](../debugger/how-to-install-a-visualizer.md).

## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Vytvoření Vizualizér pomocí šablony položky Vizualizér

V tomto návodu vám ukázal, jak vytvořit Vizualizér ručně. To bylo provedeno v rámci výukového cvičení. Když teď víte, jak Jednoduchý vizualizér funguje, existuje jednodušší způsob, jak ho vytvořit: pomocí šablony položky Vizualizér.

Nejprve je třeba vytvořit nový projekt knihovny tříd.

### <a name="to-create-a-new-class-library"></a>Vytvoření nové knihovny tříd

1. V nabídce **soubor** vyberte možnost **Nový > projekt**.

2. V dialogovém okně **Nový projekt** vyberte v části **vizuál C#** možnost **.NET Standard**.

3. V prostředním podokně vyberte možnost **Knihovna tříd**.

4. Do pole **název** zadejte vhodný název knihovny tříd, například MySecondVisualizer.

5. Klikněte na tlačítko **OK**.

   Nyní můžete do něj přidat položku Vizualizér:

### <a name="to-add-a-visualizer-item"></a>Přidání položky Vizualizátoru

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na MySecondVisualizer.

2. V místní nabídce vyberte možnost **Přidat** a poté klikněte na položku **Nová položka**.

3. V dialogovém okně **Přidat novou položku** vyberte v části **vizuální C# položky**možnost **Vizualizér ladicího programu**.

4. Do pole **název** zadejte vhodný název, například SecondVisualizer.cs.

5. Klikněte na tlačítko **Přidat**.

   To je vše, co je k dispozici. Podívejte se na soubor SecondVisualizer.cs a zobrazte si kód, který vám šablona přidala. Pokračujte a Experimentujte s kódem. Teď, když jste znali základy, jste na úmyslu vytvořit složitější a užitečné vizualizace, které vlastníte.

## <a name="see-also"></a>Viz také:

- [Architektura vizualizéru](../debugger/visualizer-architecture.md)
- [Postupy: Instalace vizualizéru](../debugger/how-to-install-a-visualizer.md)
- [Vytváření vlastních vizualizérů](../debugger/create-custom-visualizers-of-data.md)

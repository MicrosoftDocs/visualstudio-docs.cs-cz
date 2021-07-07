---
title: Zápis Vizualizér v jazyce C# | Microsoft Docs
description: Postupujte podle návodu a vytvořte jednoduchý Vizualizér v jazyce C#. Zobrazuje kroky požadované jak s, tak i bez použití šablony položky Vizualizér.
ms.custom: SEO-VS-2020
ms.date: 07/02/2021
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
ms.openlocfilehash: 47c7fa8eaa5a735f05b338101a1aefe0601e9915
ms.sourcegitcommit: 4cd3eb514e9fa48e586279e38fe7c2e111ebb304
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2021
ms.locfileid: "113298274"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Návod: zápis Vizualizér v jazyce C\#

Tento návod ukazuje, jak napsat jednoduchý Vizualizér pomocí jazyka C#. vizualizér, který vytvoříte v tomto návodu, zobrazí obsah řetězce pomocí formuláře Windows. Tento jednoduchý Vizualizér řetězců není zvlášť užitečný, ale zobrazuje základní kroky, které je nutné provést, aby bylo možné vytvořit užitečnější vizualizace pro jiné datové typy.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. chcete-li změnit nastavení, přejděte do nabídky **nástroje** a vyberte **importovat a exportovat Nastavení**. Další informace najdete v tématu [resetování nastavení](../ide/environment-settings.md#reset-settings).

Kód Vizualizér musí být umístěn v knihovně DLL, která bude načtena ladicím programem. Proto je prvním krokem vytvoření projektu knihovny tříd pro knihovnu DLL.

## <a name="create-a-visualizer-manually"></a>Ruční vytvoření Vizualizér

Pomocí níže uvedených úloh vytvořte Vizualizér.

### <a name="to-create-a-class-library-project"></a>Vytvoření projektu knihovny tříd

* Vytvořte nový projekt knihovny tříd.

    ::: moniker range=">=vs-2019"
    vyberte **soubor**  >  **nový**  >  **Project**. V rozevíracím seznamu jazyk vyberte **C#**. Do vyhledávacího pole zadejte **Knihovna tříd** a poté zvolte možnost **knihovna tříd (.NET Framework)**. Klikněte na **Next** (Další). V dialogovém okně, které se zobrazí, zadejte název `MyFirstVisualizer` a klikněte na **vytvořit**.

    pro projekt vizualizér se ujistěte, že jste vybrali .NET Framework knihovny tříd a ne rozhraní .net. i když je potřeba vizualizér .NET Framework, volající aplikace může být .net Core.
    ::: moniker-end
    ::: moniker range="vs-2017"
    v horním řádku nabídek vyberte **soubor**  >  **nový**  >  **Project**. v levém podokně dialogového okna **nový projekt** , v části **Visual C#** zvolte možnost **.NET Framework** a potom v prostředním podokně zvolte možnost **knihovna tříd (.NET Framework)**.

    Zadejte vhodný název knihovny tříd, například `MyFirstVisualizer` , a pak klikněte na tlačítko **vytvořit** nebo **OK**.
    ::: moniker-end

   Po vytvoření knihovny tříd je nutné přidat odkaz na Microsoft.VisualStudio.DebuggerVisualizers.DLL, aby bylo možné použít třídy, které jsou zde definovány. Před přidáním odkazu však musíte přejmenovat některé třídy, aby měly smysluplné názvy.

### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Přejmenování Class1. cs a přidání Microsoft. VisualStudio. DebuggerVisualizers

1. V **Průzkumník řešení** klikněte pravým tlačítkem na Class1. cs a v místní nabídce vyberte **Přejmenovat** .

2. Změňte název z Class1. cs na něco smysluplného, například DebuggerSide. cs.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticky změní deklaraci třídy v souboru DebuggerSide. cs tak, aby odpovídala novému názvu souboru.

3. V **Průzkumník řešení** klikněte pravým tlačítkem na **odkazy** a v místní nabídce vyberte **Přidat odkaz** .

4. V dialogovém okně **Přidat odkaz** na kartě **Procházet** vyberte možnost **Procházet** a vyhledejte Microsoft.VisualStudio.DebuggerVisualizers.DLL.

    knihovnu DLL můžete najít v podadresáři *\<Visual Studio Install Directory> \Common7\IDE\PublicAssemblies* instalačního adresáře aplikace Visual Studio.

5. Klikněte na **OK**.

6. V DebuggerSide. cs přidejte následující `using` direktivy:

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   Nyní jste připraveni vytvořit kód na straně ladicího programu. Toto je kód, který běží v ladicím programu pro zobrazení informací, které chcete vizualizovat. Nejprve je třeba změnit deklaraci `DebuggerSide` objektu tak, aby dědil ze základní třídy `DialogDebuggerVisualizer` .

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Dědění z DialogDebuggerVisualizer

1. V DebuggerSide. cs přejít na následující řádek kódu:

   ```csharp
   public class DebuggerSide
   ```

2. Změňte kód na:

   ```csharp
   public class DebuggerSide : DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` má jednu abstraktní metodu ( `Show` ), kterou je nutné přepsat.

#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Přepsání metody DialogDebuggerVisualizer. show

- Do `public class DebuggerSide` přidejte následující **metodu:**

  ```csharp
  protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  `Show`Metoda obsahuje kód, který ve skutečnosti vytvoří dialogové okno vizualizér, nebo jiné uživatelské rozhraní a zobrazí informace, které byly předány Vizualizér z ladicího programu. Je nutné přidat kód, který vytvoří dialogové okno a zobrazí informace. v tomto návodu to provedete pomocí model Windows Forms okno se zprávou. Nejdřív je nutné přidat odkaz a `using` direktivu pro System. Windows. Forem.

### <a name="to-add-systemwindowsforms"></a>Pro přidání systému. Windows. Forem

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **odkazy** a v místní nabídce vyberte **Přidat odkaz** .

2. V dialogovém okně **Přidat odkaz** na kartě **Procházet** vyberte možnost **Procházet** a vyhledejte System.Windows.Forms.DLL.

    knihovnu DLL můžete najít v *C:\ Windows \Microsoft.NET\Framework\v4.0.30319*.

3. Klikněte na **OK**.

4. V DebuggerSide. cs přidejte následující `using` direktivy:

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

### <a name="to-add-the-type-to-visualize-for-the-debuggee-side-code"></a>Postup přidání typu k vizualizaci pro kód na straně laděného procesu

V kódu na straně ladicího programu určíte typ pro vizualizaci (zdroj objektu) pro laděného procesu pomocí <xref:System.Diagnostics.DebuggerVisualizerAttribute> atributu. `Target`Vlastnost nastaví typ pro vizualizaci.

1. Přidejte následující kód atributu do DebuggerSide. cs za `using` direktivami, ale před `namespace MyFirstVisualizer` :

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target = typeof(System.String),
   Description = "My First Visualizer")]
   ```

2. V nabídce **sestavení** klikněte na příkaz **sestavit MyFirstVisualizer**. Projekt by se měl úspěšně sestavit. Než budete pokračovat, opravte případné chyby sestavení.

   V tomto okamžiku je váš první vizualizér dokončený. Pokud jste postupovali podle pokynů správně, můžete vytvořit Vizualizér a nainstalovat ho do nástroje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Než nainstalujete Vizualizér do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , měli byste ho ale otestovat, abyste se ujistili, že funguje správně. Nyní vytvoříte testovací kabel, který bude spustit Vizualizér bez jeho instalace do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Chcete-li přidat testovací metodu pro zobrazení Vizualizér

1. Přidejte následující metodu do třídy `public DebuggerSide` :

   ```csharp
   public static void TestShowVisualizer(object objectToVisualize)
   {
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
      visualizerHost.ShowVisualizer();
   }
   ```

2. V nabídce **sestavení** klikněte na příkaz **sestavit MyFirstVisualizer**. Projekt by se měl úspěšně sestavit. Než budete pokračovat, opravte případné chyby sestavení.

   Dále je nutné vytvořit spustitelný projekt pro volání své knihovny Vizualizátor DLL. Pro zjednodušení použijte projekt konzolové aplikace.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Přidání projektu konzolové aplikace do řešení

1. V Průzkumník řešení klikněte pravým tlačítkem myši na řešení, vyberte možnost **Přidat** a poté klikněte na možnost **Nová Project**.

    ::: moniker range=">=vs-2019"

    vyberte **soubor**  >  **nový**  >  **Project**. V rozevíracím seznamu jazyk vyberte **C#**. do vyhledávacího pole zadejte **konzolová** aplikace a pak zvolte buď **konzolová aplikace (.NET Framework)** nebo **konzolová aplikace** pro .net. Klikněte na **Next** (Další). V dialogovém okně, které se zobrazí, zadejte název `MyTestConsole` a klikněte na **vytvořit**.

    > [!NOTE]
    > pokud chcete vizualizér snadno otestovat pomocí testovacího svazku, vytvořte konzolovou aplikaci .NET Framework. Místo toho můžete vytvořit konzolovou aplikaci .NET, ale testovací kabel popsaný později není pro rozhraní .NET podporovaný, takže budete muset nainstalovat Vizualizér a otestovat ho. V tomto scénáři nejdřív vytvořte konzolovou aplikaci a pak postupujte podle kroků popsaných v tématu [Přidání datového objektu na straně laděného procesu](#add-a-debuggee-side-data-object).
    ::: moniker-end
    ::: moniker range="vs-2017"
    v horním řádku nabídek vyberte **soubor**  >  **nový**  >  **Project**. v levém podokně dialogového okna **nový projekt** , v části **Visual C#** zvolte **Windows plocha** a potom v prostředním podokně zvolte **konzolová aplikace (.NET Framework)**.

    Zadejte vhodný název knihovny tříd, například `MyTestConsole` , a pak klikněte na tlačítko **OK**.
    ::: moniker-end

   Nyní je nutné přidat nezbytné odkazy, aby MyTestConsole mohli volat MyFirstVisualizer.

### <a name="to-add-necessary-references-to-mytestconsole"></a>Přidání nezbytných odkazů na MyTestConsole

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
    > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticky změní deklaraci třídy v souboru TestConsole.cs tak, aby odpovídala novému názvu souboru.

3. Do souboru TestConsole.cs přidejte do direktiv následující `using` kód:

   ```csharp
   using MyFirstVisualizer;
   ```

4. Do metody `Main` přidejte následující kód:

   ```csharp
   String myString = "Hello, World";
   DebuggerSide.TestShowVisualizer(myString);
   ```

   Teď jste připraveni otestovat svůj první vizualizér.

### <a name="to-test-the-visualizer"></a>Testování vizualizéru

1. V Průzkumník řešení klikněte pravým tlačítkem na **MyTestConsole** **a** v místní **nabídce Project** nastavit jako spouštěcí.

2. V **nabídce Ladit** zvolte **Spustit.**

    Spustí se konzolová aplikace a zobrazí se vizualizér s řetězcem "Hello, World".

   Blahopřejeme. Právě jste vybudovali a otestovali svůj první vizualizér.

   Pokud chcete použít vizualizér v nástroji místo jeho volání z nástroje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pro testování, musíte ho nainstalovat. Další informace najdete v tématu [Postupy: Instalace vizualizéru](../debugger/how-to-install-a-visualizer.md).

::: moniker range=">=vs-2019"
## <a name="add-a-debuggee-side-data-object"></a>Přidání datového objektu na straně debuggee

V této části přepnete z `System.String` datového objektu na vlastní datový objekt.  

1. Zvolte **Soubor**  >  **Nový**  >  **Project**. V rozevíracím seznamu jazyka zvolte **C#**. Do vyhledávacího pole zadejte **knihovna tříd** a potom zvolte buď Knihovna tříd **(.NET Framework)** nebo **Knihovna** tříd pro .NET Standard.

   >[!NOTE]
   >Pokud používáte testovací konzolovou .NET Framework, nezapomeňte vytvořit projekt knihovny tříd .NET Framework tříd.

1. Klikněte na **Next** (Další). V dialogovém okně, které se zobrazí, zadejte název a `MyDataObject` pak klikněte na **Vytvořit.**

1. (.NET Standard pouze knihovny tříd) V Průzkumník řešení klikněte pravým tlačítkem na projekt a zvolte **Upravit Project souboru**. Změňte `<TargetFramework>` hodnotu na `netstandard2.0` .

1. V oboru `MyDataObject` názvů nahraďte výchozí kód následujícím kódem.

   ```csharp
   [Serializable] 
   public class CustomDataObject
   {
      public CustomDataObject()
      {
         this.MyData = "MyTestData";
      }
      public string MyData { get; set; }
   }
   ```

   Pro vizualizér jen pro čtení, například v tomto příkladu, není nutné implementovat metody [VisualizerObjectSource](/dotnet/api/microsoft.visualstudio.debuggervisualizers.visualizerobjectsource).

   Dále aktualizujte projekt MyFirstVisualizer tak, aby se nový datový objekt používat.

1. V Průzkumník řešení projektu MyFirstVisualizer klikněte pravým tlačítkem na uzel **Odkazy** a zvolte **Přidat odkaz.**

1. V **části Projekty** vyberte projekt **MyDataObject.**

1. V kódu atributu souboru DebuggerSide.cs aktualizujte hodnotu Target a změňte `System.String` hodnotu na `MyDataObject.CustomDataObject` .

   ```csharp
   Target = typeof(MyDataObject.CustomDataObject),
   ```

1. V projektu MyFirstVisualizer nahraďte kód metody `Show` následujícím kódem.

   ```csharp
   var data = objectProvider.GetObject() as MyDataObject.CustomDataObject;

   // You can replace displayForm with your own custom Form or Control.  
   Form displayForm = new Form();
   displayForm.Text = data.MyData;
   windowService.ShowDialog(displayForm);
   ```

   Předchozí kód používá vlastnost datového objektu k zobrazení v názvu formuláře.

   Dále aktualizujte konzolovou aplikaci tak, aby se používá vlastní datový objekt.

1. V Průzkumník řešení projektu MyTestConsole klikněte pravým tlačítkem na  uzel **Odkazy** nebo Závislosti a přidejte odkaz na projekt `MyDataObject` na .

1. V souboru Program.cs nahraďte kód v `Main` metodě následujícím kódem.

   ```csharp
   // String myString = "Hello, World";
   CustomDataObject customDataObject = new CustomDataObject();

   DebuggerSide.TestShowVisualizer(customDataObject.MyData);
   ```

1. (Konzolová aplikace .NET) Uzavřete volání do příkazu try-catch, protože není podporována funkce pro `TestShowVisualizer` testování.

   ```csharp
   try
   {
         DebuggerSide.TestShowVisualizer(customDataObject.MyData);
   }
   catch (Exception) {
   }
   ```

   Ladicí program potřebuje odkaz na vizualizér. Jedním ze způsobem, jak zachovat odkaz, je zachovat předchozí kód na místě.

1. V případě .NET Framework konzolové aplikace můžete spustit správce testů (stisknutím klávesy **F5)** nebo můžete postupovat podle pokynů v tématu [Postup: Instalace vizualizéru](../debugger/how-to-install-a-visualizer.md).

   Pokud aplikaci spustíte pomocí nástroje pro testování, zobrazí se formulář Windows testu.

1. V případě konzolové aplikace .NET zkopírujte a do složek popsaných v tématu `MyFirstVisualizer.dll` `MyDataObject.dll` [Postupy: Instalace vizualizéru](../debugger/how-to-install-a-visualizer.md).

1. Po instalaci vizualizéru nastavte zarážku, spusťte konzolovou aplikaci a najeďte myší na `customDataObject` . Pokud je všechno správně nastavené, měla by se zobrazit ikona lupy ![VizualizérIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ikona vizualizéru").

   :::image type="content" source="../debugger/media/vs-2019/visualizer-csharp-data-object.png" alt-text="Ikona zvětšovací lupy vizualizéru":::

   Když v lupě zvolíte **MyFirstVisualizer,** zobrazí se v názvu Formulář s textem datového objektu.

   ![Vizualizér zobrazující Windows formuláře](../debugger/media/vs-2019/visualizer-csharp-windows-form.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Vytvoření vizualizéru pomocí šablony položky vizualizéru

Zatím vám tento názorný postup ukázal, jak vytvořit vizualizér ručně. To bylo provedeno jako výukové cvičení. Teď, když víte, jak funguje jednoduchý vizualizér, existuje jednodušší způsob, jak ho vytvořit: pomocí šablony položky vizualizéru.

Nejprve musíte vytvořit nový projekt knihovny tříd.

### <a name="to-create-a-new-class-library"></a>Vytvoření nové knihovny tříd

1. V **nabídce Soubor** zvolte Nový **> Project**.

2. V dialogovém **okně Project** nový soubor v části **Visual C#** **vyberte .NET Framework**.

3. V prostředním podokně zvolte **Knihovna tříd**.

4. Do **pole Název** zadejte odpovídající název knihovny tříd, například MySecondVisualizer.

5. Klikněte na **OK**.

   Teď do ní můžete přidat položku vizualizéru:

### <a name="to-add-a-visualizer-item"></a>Přidání položky vizualizéru

1. V **Průzkumník řešení** klikněte pravým tlačítkem na MySecondVisualizer.

2. V místní nabídce zvolte Přidat **a** pak klikněte na **Nová položka.**

3. V dialogovém **okně Přidat novou položku** v části Položky Visual **C#** vyberte **Vizualizér ladicího programu.**

4. Do pole **Název** zadejte odpovídající název, například SecondVisualizer.cs.

5. Klikněte na **Přidat**.

   A to je všechno. Podívejte se na soubor SecondVisualizer.cs a prohlédněte si kód, který vám šablona přidala. Pokračujte a experimentujte s kódem. Teď, když znáte základy, jste na cestě k vytváření složitějších a užitečnějších vizualizérů.
::: moniker-end

## <a name="see-also"></a>Viz také

- [Architektura vizualizéru](../debugger/visualizer-architecture.md)
- [Postupy: Instalace vizualizéru](../debugger/how-to-install-a-visualizer.md)
- [Vytváření vlastních vizualizérů](../debugger/create-custom-visualizers-of-data.md)

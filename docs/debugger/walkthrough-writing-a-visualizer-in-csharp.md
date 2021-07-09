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
ms.openlocfilehash: a6ce1a6d9f2f8a36d892d484cf9353e1312758b4
ms.sourcegitcommit: 4e09130bcd55bb9cb8ad157507c23b67aa209fad
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2021
ms.locfileid: "113549508"
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
    > pokud chcete vizualizér snadno otestovat pomocí testovacího svazku, vytvořte konzolovou aplikaci .NET Framework. Místo toho můžete vytvořit konzolovou aplikaci .NET, ale testovací kabel popsaný později není pro rozhraní .NET podporovaný, takže budete muset nainstalovat Vizualizér a otestovat ho. Pro konzolovou aplikaci .NET nejprve vytvořte konzolovou aplikaci, přidejte požadované knihovny DLL a odkazy na projekt a pak postupujte podle kroků popsaných v tématu [Přidání datového objektu na straně laděného procesu](#add-a-debuggee-side-data-object).
    ::: moniker-end
    ::: moniker range="vs-2017"
    v horním řádku nabídek vyberte **soubor**  >  **nový**  >  **Project**. v levém podokně dialogového okna **nový projekt** , v části **Visual C#** zvolte **Windows plocha** a potom v prostředním podokně zvolte **konzolová aplikace (.NET Framework)**.

    Zadejte vhodný název knihovny tříd, například `MyTestConsole` , a pak klikněte na tlačítko **OK**.
    ::: moniker-end

   Nyní je nutné přidat nezbytné odkazy, aby MyTestConsole mohli volat MyFirstVisualizer.

### <a name="to-add-necessary-references-to-mytestconsole"></a>Přidání nezbytných odkazů na MyTestConsole

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **MyTestConsole** a v místní nabídce vyberte **Přidat odkaz** .

2. V dialogovém okně **Přidat odkaz** klikněte na kartu **Procházet** a vyberte možnost Microsoft.VisualStudio.DebuggerVisualizers.DLL.

3. Klikněte na **OK**.

4. Klikněte pravým tlačítkem na **MyTestConsole** a pak znovu vyberte **Přidat odkaz** .

5. V dialogovém okně **Přidat odkaz** klikněte na kartu **projekty** a pak klikněte na MyFirstVisualizer.

6. Klikněte na **OK**.

   Nyní přidáte kód pro dokončení testovacího svazku.

### <a name="to-add-code-to-mytestconsole"></a>Přidání kódu do MyTestConsole

1. V **Průzkumník řešení** klikněte pravým tlačítkem na program. cs a v místní nabídce vyberte **Přejmenovat** .

2. Upravte název z programu program. cs na smysluplnější, například TestConsole. cs.

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

1. v **Průzkumník řešení** klikněte pravým tlačítkem na **MyTestConsole** a v místní nabídce vyberte **nastavit jako spouštěcí Project** .

2. V nabídce **ladit** klikněte na tlačítko **Spustit**.

    Spustí se Konzolová aplikace a zobrazí se Vizualizér a zobrazí řetězec "Hello, World".

   Blahopřejeme. Právě jste vytvořili a otestovali svůj první vizualizér!

   Pokud chcete použít svůj Vizualizér [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] místo toho, aby ho bylo možné volat ze samotného testovacího prostředí, musíte ho nainstalovat. Další informace najdete v tématu [Postup: instalace Vizualizátoru](../debugger/how-to-install-a-visualizer.md).

::: moniker range=">=vs-2019"
## <a name="add-a-debuggee-side-data-object"></a>Přidání datového objektu na straně laděného procesu

V této části přepnete z `System.String` datového objektu na vlastní datový objekt.  

1. V Průzkumník řešení klikněte pravým tlačítkem myši na řešení, vyberte možnost **Přidat** a poté klikněte na možnost **Nová Project**. V rozevíracím seznamu jazyk vyberte **C#**. do vyhledávacího pole zadejte **knihovny tříd** a pak zvolte buď **knihovnu tříd (.NET Framework)** , nebo **knihovnu tříd** pro .NET Standard.

   >[!NOTE]
   >pokud používáte aplikaci .NET Framework test console, ujistěte se, že jste vytvořili projekt knihovny tříd .NET Framework.

1. Klikněte na **Next** (Další). V dialogovém okně, které se zobrazí, zadejte název `MyDataObject` a klikněte na **vytvořit**.

1. (.NET Standard pouze knihovna tříd) v Průzkumník řešení klikněte pravým tlačítkem myši na projekt a vyberte možnost **upravit Project soubor**. Změňte `<TargetFramework>` hodnotu na `netstandard2.0` .

   ```xml
   <TargetFramework>netstandard2.0</TargetFramework>
   ```

1. V rámci `MyDataObject` oboru názvů nahraďte výchozí kód následujícím kódem.

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

   Pro Vizualizér jen pro čtení, jako je například v tomto příkladu, není nutné implementovat metody [VisualizerObjectSource](/dotnet/api/microsoft.visualstudio.debuggervisualizers.visualizerobjectsource).

   Dále aktualizujte projekt MyFirstVisualizer, aby používal nový datový objekt.

1. V Průzkumník řešení v projektu MyFirstVisualizer klikněte pravým tlačítkem myši na uzel **odkazy** a vyberte možnost **Přidat odkaz**.

1. V části **projekty** vyberte projekt **MyDataObject** .

1. V kódu atributu DebuggerSide. cs aktualizujte cílovou hodnotu a změňte `System.String` na `MyDataObject.CustomDataObject` .

   ```csharp
   Target = typeof(MyDataObject.CustomDataObject),
   ```

1. V projektu MyFirstVisualizer nahraďte kód `Show` metody následujícím kódem.

   ```csharp
   var data = objectProvider.GetObject() as MyDataObject.CustomDataObject;

   // You can replace displayForm with your own custom Form or Control.  
   Form displayForm = new Form();
   displayForm.Text = data.MyData;
   windowService.ShowDialog(displayForm);
   ```

   Předchozí kód používá vlastnost datového objektu k zobrazení v nadpisu formuláře.

   Dále aktualizujte konzolovou aplikaci tak, aby používala vlastní datový objekt.

1. V Průzkumník řešení v projektu MyTestConsole klikněte pravým tlačítkem myši na uzel **odkazy** nebo **závislosti** a přidejte odkaz na projekt `MyDataObject` .

1. V programu program. cs nahraďte kód v `Main` metodě následujícím kódem.

   ```csharp
   // String myString = "Hello, World";
   CustomDataObject customDataObject = new CustomDataObject();

   DebuggerSide.TestShowVisualizer(customDataObject.MyData);
   ```

1. (Aplikace konzoly .NET) Vložte volání do `TestShowVisualizer` příkazu try-catch, protože testovací svazek není podporován.

   ```csharp
   try
   {
         DebuggerSide.TestShowVisualizer(customDataObject.MyData);
   }
   catch (Exception) {
   }
   ```

   Konzolová aplikace potřebuje pro Vizualizér odkaz na modul runtime. Můžete zachovat odkaz tím, že zachováte předchozí kód a nemusíte ho komentovat.

1. u konzolové aplikace .NET Framework můžete spustit testovací vodič (stiskněte klávesu **F5**), nebo můžete postupovat podle pokynů v tématu [postupy: instalace vizualizátoru](../debugger/how-to-install-a-visualizer.md).

   pokud aplikaci spouštíte pomocí testovacího svazku, aplikace zobrazí formulář Windows.

1. Pro konzolovou aplikaci .NET zkopírujte `MyFirstVisualizer.dll` a `MyDataObject.dll` do složek popsaných v tématu [How to: install a Vizualizér](../debugger/how-to-install-a-visualizer.md).

1. Po instalaci Vizualizér nastavte zarážku, spusťte konzolovou aplikaci a najeďte myší na `customDataObject` . Pokud je všechno správně nastavené, měla by se zobrazit ikona lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ikona Vizualizátoru").

   :::image type="content" source="../debugger/media/vs-2019/visualizer-csharp-data-object.png" alt-text="Ikona zvětšovacího efektu Vizualizér":::

   Když z lupy zvolíte **MyFirstVisualizer** , zobrazí se v nadpisu formulář s textem datového objektu.

   ![vizualizér znázorňující Windows formulář](../debugger/media/vs-2019/visualizer-csharp-windows-form.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Vytvoření Vizualizér pomocí šablony položky Vizualizér

V tomto návodu vám ukázal, jak vytvořit Vizualizér ručně. To bylo provedeno v rámci výukového cvičení. Když teď víte, jak Jednoduchý vizualizér funguje, existuje jednodušší způsob, jak ho vytvořit: pomocí šablony položky Vizualizér.

Nejprve je třeba vytvořit nový projekt knihovny tříd.

### <a name="to-create-a-new-class-library"></a>Vytvoření nové knihovny tříd

1. V nabídce **soubor** vyberte možnost **Nový > Project**.

2. v dialogovém okně **nový Project** v části **Visual C#** vyberte možnost **.NET Framework**.

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

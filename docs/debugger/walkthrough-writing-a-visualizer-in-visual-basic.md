---
title: Napište Vizualizér v Visual Basic | Microsoft Docs
ms.custom: seodec18
ms.date: 05/27/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25720f31c721cae44ed5425631a86b3a41bf475e
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84180529"
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>Návod: Zápis vizualizéru v jazyce Visual Basic

Tento návod ukazuje, jak napsat jednoduchý Vizualizér pomocí [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] . Vizualizér, který v tomto návodu vytvoříte, zobrazí obsah řetězce pomocí okna model Windows Forms zpráva. Tento jednoduchý Vizualizér řetězců je základní příklad, který ukazuje, jak můžete vytvářet vizualizace pro jiné datové typy, které jsou použitelné pro vaše projekty.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, přejděte do nabídky **nástroje** a vyberte možnost **importovat a exportovat** . Další informace najdete v tématu [resetování nastavení](../ide/environment-settings.md#reset-settings).

Kód Vizualizér musí být umístěn v knihovně DLL, která bude načtena ladicím programem. Prvním krokem je vytvoření projektu knihovny tříd pro knihovnu DLL.

## <a name="create-and-prepare-a-class-library-project"></a>Vytvoření a příprava projektu knihovny tříd

### <a name="to-create-a-class-library-project"></a>Vytvoření projektu knihovny tříd

1. Vytvořte nový projekt knihovny tříd.

    ::: moniker range=">=vs-2019"
    Stisknutím klávesy **ESC** zavřete okno Start. Zadáním **CTRL + Q** otevřete vyhledávací pole, zadejte **Visual Basic**, zvolte **šablony**a pak zvolte **vytvořit novou knihovnu tříd (.NET Framework)**. V dialogovém okně, které se zobrazí, vyberte **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek vyberte **soubor**  >  **Nový**  >  **projekt**. V levém podokně dialogového okna **Nový projekt** , v části **Visual Basic**zvolte možnost **.NET Standard**a potom v prostředním podokně zvolte možnost **Knihovna tříd (.NET Standard)**.
    ::: moniker-end

2. Zadejte vhodný název knihovny tříd, například `MyFirstVisualizer` , a pak klikněte na tlačítko **vytvořit** nebo **OK**.

   Pokud jste vytvořili knihovnu tříd, je nutné přidat odkaz na Microsoft. VisualStudio. DebuggerVisualizers. DLL, aby bylo možné použít třídy, které jsou zde definovány. Nejprve však vašemu projektu udělíte smysluplný název.

### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>Přejmenování Class1. vb a přidání Microsoft. VisualStudio. DebuggerVisualizers

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **Class1. vb**a v místní nabídce klikněte na **Přejmenovat**.

2. Změňte název z Class1. vb na něco smysluplného, například DebuggerSide. vb.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]automaticky změní deklaraci třídy v souboru DebuggerSide. vb tak, aby odpovídala novému názvu souboru.

3. V **Průzkumník řešení**klikněte pravým tlačítkem na **můj první vizualizér**a v místní nabídce klikněte na **Přidat odkaz**.

4. V dialogovém okně **Přidat odkaz** na kartě **Procházet** vyberte **Procházet** a vyhledejte Microsoft. VisualStudio. DebuggerVisualizers. dll.

    Knihovnu DLL můžete najít v podadresáři * \<Visual Studio Install Directory> \Common7\IDE\PublicAssemblies* instalačního adresáře sady Visual Studio.

5. Klikněte na tlačítko **OK**.

6. V DebuggerSide. vb přidejte do příkazů následující příkaz `Imports` :

   ```vb
   Imports Microsoft.VisualStudio.DebuggerVisualizers
   ```

## <a name="add-the-debugger-side-code"></a>Přidat kód na straně ladicího programu
 Nyní jste připraveni vytvořit kód na straně ladicího programu. Toto je kód, který běží v ladicím programu pro zobrazení informací, které chcete vizualizovat. Nejprve je třeba změnit deklaraci `DebuggerSide` objektu tak, aby dědil ze základní třídy `DialogDebuggerVisualizer` .

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Dědění z DialogDebuggerVisualizer

1. V DebuggerSide. vb přejít na následující řádek kódu:

   ```vb
   Public Class DebuggerSide
   ```

2. Upravte kód tak, aby vypadal takto:

   ```vb
   Public Class DebuggerSide
   Inherits DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer`má jednu abstraktní metodu, `Show` , kterou je nutné přepsat.

### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Přepsání metody DialogDebuggerVisualizer. show

- Do `public class DebuggerSide` přidejte následující metodu:

  ```vb
  Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)

      End Sub
  ```

  `Show`Metoda obsahuje kód, který ve skutečnosti vytvoří dialogové okno vizualizér, nebo jiné uživatelské rozhraní a zobrazí informace, které byly předány Vizualizér z ladicího programu. Je nutné přidat kód, který vytvoří dialogové okno a zobrazí informace. V tomto návodu to provedete pomocí model Windows Forms okno se zprávou. Nejprve je třeba přidat odkaz a `Imports` příkaz pro <xref:System.Windows.Forms> .

### <a name="to-add-systemwindowsforms"></a>Přidání System. Windows. Forms

1. V **Průzkumník řešení**klikněte pravým tlačítkem na **odkazy**a v místní nabídce klikněte na **Přidat odkaz**.

2. V dialogovém okně **Přidat odkaz** vyberte na kartě **Procházet** možnost **Procházet**a vyhledejte System. Windows. Forms. dll.

    Knihovnu DLL můžete najít v *C:\Windows\Microsoft.NET\Framework\v4.0.30319*.

3. Klikněte na tlačítko **OK**.

4. Do DebuggerSide.cs přidejte do příkazů následující příkaz `Imports` :

    ```vb
    Imports System.Windows.Forms
    ```

## <a name="create-your-visualizers-user-interface"></a>Vytvoření uživatelského rozhraní Vizualizátoru
 Nyní přidáte nějaký kód pro vytvoření a zobrazení uživatelského rozhraní pro Vizualizér. Vzhledem k tomu, že se jedná o váš první vizualizér, budete mít uživatelské rozhraní jednoduché a bude používat okno se zprávou.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Zobrazení výstupu Vizualizér v dialogovém okně

1. Do metody `Show` přidejte následující řádek kódu:

    ```vb
    MessageBox.Show(objectProvider.GetObject().ToString())
    ```

     Tento ukázkový kód nezahrnuje zpracování chyb. Zpracování chyb byste měli zahrnout do reálného Vizualizér nebo jakéhokoli jiného typu aplikace.

2. V nabídce **sestavení** klikněte na příkaz **sestavit MyFirstVisualizer**. Projekt by se měl úspěšně sestavit. Než budete pokračovat, opravte případné chyby sestavení.

## <a name="add-the-necessary-attribute"></a>Přidat potřebný atribut
 To je konec kódu na straně ladicího programu. Existuje však ještě ještě jeden krok: atribut, který oznamuje laděného procesu stranu, kterou kolekce tříd zahrnuje vizualizér.

### <a name="to-add-the-type-to-visualize-for-the-debuggee-side-code"></a>Postup přidání typu k vizualizaci pro kód na straně laděného procesu

V kódu na straně ladicího programu určíte typ pro vizualizaci (zdroj objektu) pro laděného procesu pomocí <xref:System.Diagnostics.DebuggerVisualizerAttribute> atributu. `Target`Vlastnost nastaví typ pro vizualizaci.

1. Přidejte následující kód atributu do DebuggerSide. vb za `Imports` příkazy, ale před `namespace MyFirstVisualizer` :

    ```vb
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>
    ```

2. V nabídce **sestavení** klikněte na příkaz **sestavit MyFirstVisualizer**. Projekt by se měl úspěšně sestavit. Než budete pokračovat, opravte případné chyby sestavení.

## <a name="create-a-test-harness"></a>Vytvoření testovacího svazku
 V tomto okamžiku je váš první vizualizér dokončený. Pokud jste postupovali podle pokynů správně, můžete vytvořit Vizualizér a nainstalovat ho do nástroje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Než nainstalujete Vizualizér do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , měli byste ho ale otestovat, abyste se ujistili, že funguje správně. Nyní vytvoříte testovací kabel, který bude spustit Vizualizér bez jeho instalace do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Chcete-li přidat testovací metodu pro zobrazení Vizualizér

1. Přidejte následující metodu do třídy `public DebuggerSide` :

   ```vb
   Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)
       Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))
   visualizerHost.ShowVisualizer()
   End Sub
   ```

2. V nabídce **sestavení** klikněte na příkaz **sestavit MyFirstVisualizer**. Projekt by se měl úspěšně sestavit. Než budete pokračovat, opravte případné chyby sestavení.

   Dále je nutné vytvořit spustitelný projekt pro volání své knihovny Vizualizátor DLL. Pro zjednodušení použijte projekt konzolové aplikace.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Přidání projektu konzolové aplikace do řešení

1. V Průzkumník řešení klikněte pravým tlačítkem myši na řešení, vyberte možnost **Přidat**a poté klikněte na možnost **Nový projekt**.

    ::: moniker range=">=vs-2019"
    Do vyhledávacího pole zadejte **Visual Basic**, zvolte **šablony**a pak zvolte **vytvořit novou konzolovou aplikaci (.NET Framework)**. V dialogovém okně, které se zobrazí, vyberte **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek vyberte **soubor**  >  **Nový**  >  **projekt**. V levém podokně dialogového okna **Nový projekt** , v části **Visual Basic**zvolte **plocha Windows**a potom v prostředním podokně zvolte **Konzolová aplikace (.NET Framework)**.
    ::: moniker-end

2. Zadejte vhodný název knihovny tříd, například `MyTestConsole` , a pak klikněte na tlačítko **vytvořit** nebo **OK**.

   Nyní je nutné přidat nezbytné odkazy, aby MyTestConsole mohli volat MyFirstVisualizer.

### <a name="to-add-necessary-references-to-mytestconsole"></a>Přidání nezbytných odkazů na MyTestConsole

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na **MyTestConsole**a v místní nabídce klikněte na **Přidat odkaz**.

2. V dialogovém okně **Přidat odkaz** na kartě **Procházet** klikněte na Microsoft. VisualStudio. DebuggerVisualizers.

3. Klikněte na tlačítko **OK**.

4. Klikněte pravým tlačítkem na **MyTestConsole**a potom znovu klikněte na **Přidat odkaz** .

5. V dialogovém okně **Přidat odkaz** klikněte na kartu **projekty** a potom vyberte MyFirstVisualizer.

6. Klikněte na tlačítko **OK**.

## <a name="finish-your-test-harness-and-test-your-visualizer"></a>Dokončete testovací prostředí a otestujte svůj Vizualizér.
 Nyní přidáte kód pro dokončení testovacího svazku.

### <a name="to-add-code-to-mytestconsole"></a>Přidání kódu do MyTestConsole

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na **program. vb**a v místní nabídce klikněte na možnost **Přejmenovat**.

2. Upravte název z Module1. vb na něco vhodného, jako je například **TestConsole. vb**.

    Všimněte si, že [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automaticky změní deklaraci třídy v souboru TestConsole. vb tak, aby odpovídala novému názvu souboru.

3. V TestConsole. vb přidejte následující `Imports` příkaz:

   ```vb
   Imports MyFirstVisualizer
   ```

4. Do metody `Main` přidejte následující kód:

   ```vb
   Dim myString As String = "Hello, World"
   DebuggerSide.TestShowVisualizer(myString)
   ```

   Teď jste připraveni otestovat svůj první vizualizér.

### <a name="to-test-the-visualizer"></a>Otestování Vizualizér

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na **MyTestConsole**a v místní nabídce klikněte na **nastavit jako spouštěný projekt**.

2. V nabídce **ladit** klikněte na tlačítko **Start**.

    Spustí se Konzolová aplikace. Zobrazí se Vizualizér a zobrazí řetězec "Hello, World".

   Blahopřejeme. Právě jste vytvořili a otestovali svůj první vizualizér.

   Pokud chcete použít svůj Vizualizér [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] místo toho, aby ho bylo možné volat ze samotného testovacího prostředí, musíte ho nainstalovat. Další informace najdete v tématu [Postup: instalace Vizualizátoru](../debugger/how-to-install-a-visualizer.md).

## <a name="see-also"></a>Viz také

- [Architektura vizualizéru](../debugger/visualizer-architecture.md)
- [Postupy: instalace Vizualizátoru](../debugger/how-to-install-a-visualizer.md)
- [Vytváření vlastních vizualizérů](../debugger/create-custom-visualizers-of-data.md)
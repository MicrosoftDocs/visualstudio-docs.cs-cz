---
title: Ladění webového formuláře | Microsoft Docs
description: Postupujte podle pokynů a podívejte se, jak ladit webovou aplikaci v ASP.NET (webový formulář), včetně postupu nastavení zarážek a kontrola proměnných.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web pages [.NET Framework], debugging
- Web sites [.NET Framework], debugging
- ASP.NET, debugging Web applications
- Web applications [.NET Framework], debugging
- ASP.NET Web sites, debugging
- ASP.NET Web pages, debugging
- debugging ASP.NET Web applications, Web Forms
- debugging [Visual Studio], Web Forms
ms.assetid: e2b4fa14-8f5b-444d-a903-54070b784bd4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 007a63ea16ab044292f451d8d9c427f4358e3f13
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148218"
---
# <a name="walkthrough-debugging-a-web-form"></a>Návod: Ladění webového formuláře
Kroky v tomto návodu ukazují, jak ladit [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci, označovanou také jako webový formulář. Ukazuje, jak spustit a zastavit provádění, nastavit zarážky a kontrolovat proměnné v okně **kukátko** .

> [!NOTE]
> K dokončení tohoto Názorného postupu musíte mít na serverovém počítači oprávnění správce. Ve výchozím nastavení se [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces, aspnet_wp.exe nebo w3wp.exe, spouští jako [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces. Pro ladění [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] musíte mít v počítači, na kterém [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] je spuštěný, oprávnění správce. Další informace najdete v části [Požadavky na systém](../debugger/aspnet-debugging-system-requirements.md).

Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace najdete v tématu [resetování nastavení](../ide/environment-settings.md#reset-settings).

## <a name="to-create-the-web-form"></a>Vytvoření webového formuláře

1. Pokud už máte řešení otevřené, zavřete ho.

2. V nabídce **soubor** klikněte na příkaz **Nový** a pak klikněte na **Web**.

    Zobrazí se dialogové okno **Nový web** .

3. V podokně **šablony** klikněte na **Web ASP.NET**.

4. Na řádku **umístění** klikněte v seznamu na **http** a do textového pole zadejte **http://localhost/WebSite** .

5. V seznamu **jazyk** klikněte na možnost **Visual C#** nebo **Visual Basic**.

6. Klikněte na **OK**.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Vytvoří nový projekt a zobrazí výchozí zdrojový kód HTML. Také vytvoří nový virtuální adresář s názvem **Web** ve **výchozím webu** ve službě IIS.

7. Na dolním okraji klikněte na kartu **Návrh** .

8. Klikněte na kartu **panelu nástrojů** na levém okraji nebo ji vyberte v nabídce **zobrazení** .

    Otevře se **panel nástrojů** .

9. V sadě **nástrojů** klikněte na ovládací prvek **tlačítko** a přidejte ho na hlavní návrhovou plochu default. aspx.

10. V sadě **nástrojů** klikněte na ovládací prvek **TextBox** a přetáhněte ovládací prvek na hlavní návrhovou plochu default. aspx.

11. Dvakrát klikněte na ovládací prvek tlačítko, který jste zrušili.

     Tím přejdete na znakovou stránku: Default.aspx.cs pro C# nebo default. aspx. vb pro [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] . Kurzor by měl být ve funkci `Button1_Click` .

12. Do `Button1_Click` funkce přidejte následující kód:

    ```vb
    TextBox1.Text = "Button was clicked!"
    ```

    ```csharp
    TextBox1.Text = "Button was clicked!";
    ```

13. V nabídce **Sestavení** klikněte na **Sestavit řešení**.

     Projekt by se měl sestavit bez chyb.

     Nyní jste připraveni začít s laděním.

## <a name="to-debug-the-web-form"></a>Ladění webového formuláře

1. V okně Default.aspx.cs nebo default. aspx. vb klikněte na levý okraj na stejném řádku jako text, který jste přidali:

   ```vb
   TextBox1.Text = "Button was clicked!"
   ```

   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

    Zobrazí se červená tečka a text řádku se zvýrazní červeně. Tato červená tečka představuje zarážku. Při spuštění aplikace pomocí ladicího programu v tomto místě ladicí program přeruší provádění, když je tento řádek kódu dosažen. Poté lze zobrazit stav aplikace a ladit ji. Další informace naleznete v tématu [zarážky](/previous-versions/ktf38f66(v=vs.100)).

2. V nabídce **Ladit** klikněte na **Spustit ladění**.

3. Zobrazí se dialogové okno **ladění není povoleno** . Vyberte možnost **Upravit soubor Web.config pro povolení ladění** a klikněte na tlačítko **OK**.

    Aplikace Internet Explorer se spustí a zobrazí stránku, kterou jste právě navrhli.

4. V Internet Exploreru klikněte na tlačítko.

    V nástroji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vás přesměruje na řádek, kde jste nastavili zarážku na znakové stránce Default.aspx.cs nebo default. aspx. vb. Tento řádek by měl být zvýrazněn žlutou barvou. Nyní lze zobrazit proměnné aplikace a řídit její spuštění. Vaše aplikace zastaví provádění a čeká na příkaz od vás.

5. V nabídce **ladění** klikněte na **Windows**, pak na **sledování** a potom na **Watch1**.

6. V okně **kukátko** zadejte **text TextBox1. text**.

    Okno **kukátka** zobrazuje hodnotu proměnné `TextBox1.Text` :

   '""'

7. V nabídce **ladění** klikněte na **Krok přes**.

    Hodnota `TextBox1.Text` změn v okně **kukátka** pro čtení:

   `"Button was clicked!"`

8. V nabídce **ladit** klikněte na tlačítko **pokračovat**.

9. V Internet Exploreru klikněte na tlačítko znovu.

     Spuštění se znovu zastaví na zarážce.

10. V okně Default.aspx.cs nebo default. aspx. vb klikněte na červenou tečku na levém okraji.

     Tím se odstraní zarážka.

11. V nabídce **Ladit** klikněte na **Zastavit ladění**.

## <a name="to-attach-to-the-web-form-for-debugging"></a>Připojení k webovému formuláři pro ladění

1. V systému [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lze ladicí program připojit ke spuštěnému procesu. Pro nejúčinnější ladění zkompilujte spustitelný soubor jako ladicí verzi se soubory symbolů (PDB).

2. V okně Default.aspx.cs nebo default. aspx. vb klikněte na levý okraj, abyste znovu nastavili zarážku na řádku, který jste přidali:

   ```vb
   TextBox1.Text = "Button was clicked!"
   ```

   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

3. V nabídce **ladit** klikněte na **Spustit bez ladění**.

    Webový formulář začne běžet v aplikaci Internet Explorer, ladicí program však není připojen.

4. Připojte se k [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu. Další informace najdete v tématu [ladění nasazených webových aplikací](../debugger/debugging-deployed-web-applications.md).

5. V Internet Exploreru klikněte na tlačítko ve formuláři.

    V [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , byste měli mít zarážku ve default.aspx.cs, default. aspx. vb nebo default. aspx.

6. Po dokončení ladění klikněte v nabídce **ladění** na položku **Zastavit ladění**.

## <a name="see-also"></a>Viz také

- [Ladění aplikací ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
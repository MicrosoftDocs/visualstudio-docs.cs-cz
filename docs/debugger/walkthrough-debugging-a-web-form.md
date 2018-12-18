---
title: Ladění webového formuláře | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d28ebc797715614aefaf7206f170157d4f4485f2
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055151"
---
# <a name="walkthrough-debugging-a-web-form"></a>Návod: Ladění webového formuláře
Kroky v tomto názorném postupu ukazují, jak ladit [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci, označované také jako webového formuláře. To ukazuje, jak spustit a zastavit provádění, nastavit zarážky a zkontrolovat proměnné v **Watch** okna.

> [!NOTE]
> K dokončení tohoto návodu, musí mít oprávnění správce na počítači serveru. Ve výchozím nastavení [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu, aspnet_wp.exe nebo w3wp.exe, spouští jako [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu. Chcete-li ladit [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], musí mít oprávnění správce na počítači kde [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ji spustí. Další informace najdete v tématu [požadavky na systém](../debugger/aspnet-debugging-system-requirements.md).

Dialogová okna a příkazy nabídek, které se zobrazí mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [Resetovat nastavení](../ide/environment-settings.md#reset-settings).

## <a name="to-create-the-web-form"></a>Chcete-li vytvořit webový formulář

1. Pokud už máte řešení otevřené, zavřete ho.

2. Na **souboru** nabídky, klikněte na tlačítko **nový**a potom klikněte na tlačítko **webu**.

    **Nový web** zobrazí se dialogové okno.

3. V **šablony** podokně klikněte na tlačítko **Web ASP.NET s**.

4. Na **umístění** řádek, klikněte na tlačítko **HTTP** ze seznamu a do textového pole zadejte **http://localhost/WebSite**.

5. V **jazyk** klikněte na možnost **Visual C#** nebo **jazyka Visual Basic**.

6. Klikněte na tlačítko **OK**.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Vytvoří nový projekt a zobrazí výchozí zdrojový kód HTML. Také vytvoří nový virtuální adresář s názvem **webu** pod **výchozí webový server** ve službě IIS.

7. Klikněte na tlačítko **návrhu** karty na dolní okraj.

8. Klikněte na tlačítko **nástrojů** kartu na levý okraj, nebo ho vyberte na **zobrazení** nabídky.

    **Nástrojů** otevře.

9. V **nástrojů**, klikněte na tlačítko **tlačítko** ovládací prvek a přidat ho do hlavní návrhová plocha Default.aspx.

10. V **nástrojů**, klikněte na tlačítko **Textbox** řídit a přetáhněte jej na hlavní návrhová plocha Default.aspx.

11. Poklepejte na ovládací prvek tlačítko, kterou jste přetáhli.

     Tím přejdete na stránku kódu: Default.aspx.cs pro C# nebo Default.aspx.vb pro [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Kurzor by měl být ve funkci `Button1_Click`.

12. V `Button1_Click` funkci, přidejte následující kód:

    ```vb
    TextBox1.Text = "Button was clicked!"
    ```

    ```csharp
    TextBox1.Text = "Button was clicked!";
    ```

13. Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.

     Projekt má sestavit bez chyb.

     Nyní jste připraveni spustit ladění.

## <a name="to-debug-the-web-form"></a>Chcete-li ladit webový formulář

1. V okně Default.aspx.cs nebo Default.aspx.vb klikněte na levý okraj na stejném řádku jako text, který jste přidali:

   ```vb
   TextBox1.Text = "Button was clicked!"
   ```

   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

    Zobrazí se červená tečka a text řádku se zvýrazní červeně. Tato červená tečka představuje zarážku. Při spuštění aplikace pomocí ladicího programu v tomto místě ladicí program přeruší provádění, když je tento řádek kódu dosažen. Poté lze zobrazit stav aplikace a ladit ji. Další informace najdete v tématu [zarážky](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583).

2. Na **ladění** nabídky, klikněte na tlačítko **spustit ladění**.

3. **Ladění není povoleno** zobrazí se dialogové okno. Vyberte **upravit soubor Web.config pro povolení ladění** možnost a klikněte na tlačítko **OK**.

    Aplikace Internet Explorer spustí a zobrazí stránky, které je navrženo.

4. V aplikaci Internet Explorer klikněte na tlačítko.

    V [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], tím přejdete na řádku kde jste nastavili zarážku na znakovou stránku Default.aspx.cs nebo Default.aspx.vb. Tento řádek by měl být zvýrazněn žlutou barvou. Nyní lze zobrazit proměnné aplikace a řídit její spuštění. Vaše aplikace zastaví provádění a čeká příkaz od vás.

5. Na **ladění** nabídky, klikněte na tlačítko **Windows**, klikněte na **Watch**a potom klikněte na tlačítko **Watch1**.

6. V **Watch** okno, zadejte **TextBox1.Text**.

    **Watch** okno zobrazuje hodnotu proměnné `TextBox1.Text`:

   '""'

7. Na **ladění** nabídky, klikněte na tlačítko **Krokovat s přeskočením**.

    Hodnota `TextBox1.Text` se změnami **Watch** okno ke čtení:

   `"Button was clicked!"`

8. Na **ladění** nabídky, klikněte na tlačítko **pokračovat**.

9. V aplikaci Internet Explorer klikněte na tlačítko znovu.

     Provádění zastaví na zarážce znovu.

10. V okně Default.aspx.cs nebo Default.aspx.vb klikněte na červenou tečku na levém okraji.

     Tato operace odebere zarážku.

11. Na **ladění** nabídky, klikněte na tlačítko **Zastavit ladění**.

## <a name="to-attach-to-the-web-form-for-debugging"></a>Připojení k webového formuláře pro ladění

1. V systému [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lze ladicí program připojit ke spuštěnému procesu. Pro největší efektivity dosáhnete, ladění, kompilace spustitelného souboru jako ladicí verze s soubory symbolů (PDB).

2. V okně Default.aspx.cs nebo Default.aspx.vb klikněte na levý okraj řádku, který jste přidali znovu nastavit zarážku:

   ```vb
   TextBox1.Text = "Button was clicked!"
   ```

   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

3. Na **ladění** nabídky, klikněte na tlačítko **spustit bez ladění**.

    Webový formulář spustí v Internet Exploreru, ale není připojen ladicí program.

4. Připojení k [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu. Další informace najdete v tématu [ladění nasazené webové aplikace](../debugger/debugging-deployed-web-applications.md).

5. V aplikaci Internet Explorer klikněte na tlačítko na formuláři.

    V [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], dostanete k zarážce v Default.aspx.cs, Default.aspx.vb nebo Default.aspx.

6. Po dokončení ladění na **ladění** nabídky, klikněte na tlačítko **Zastavit ladění**.

## <a name="see-also"></a>Viz také:

- [Ladění aplikací ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
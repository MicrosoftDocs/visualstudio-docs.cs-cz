---
title: Ladění webového formuláře | Microsoft Docs
description: Postupujte podle návodu a podívejte se, jak ladit ASP.NET aplikace (webový formulář), včetně nastavení zarážek a prozkoumání proměnných.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 18347b7ba9ff52778b5acef685acd8f1ee400793
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385202"
---
# <a name="walkthrough-debugging-a-web-form"></a>Návod: Ladění webového formuláře
Kroky v tomto názorném postupu ukazují, jak ladit [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] webovou aplikaci, která se označuje také jako webový formulář. Ukazuje, jak spustit a zastavit provádění, nastavit zarážky a prozkoumat proměnné v **okně Watch (Sledování).**

> [!NOTE]
> K dokončení tohoto návodu musíte mít na počítači serveru oprávnění správce. Ve výchozím nastavení [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] se aspnet_wp.exe w3wp.exe spouští jako [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces. Chcete-li ladit nástroj , musíte mít na počítači, na kterém je [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] spuštěn, oprávnění správce. Další informace najdete v části [Požadavky na systém](../debugger/aspnet-debugging-system-requirements.md).

Dialogová okna a příkazy nabídky, které se zobrazí, se můžou lišit od těch popsaných v nápovědě v závislosti na aktivním nastavení nebo edici. Pokud chcete nastavení změnit, zvolte **v nabídce Nástroje** možnost Nastavení importu a exportu.  Další informace najdete v tématu [Resetování nastavení.](../ide/environment-settings.md#reset-settings)

## <a name="to-create-the-web-form"></a>Vytvoření webového formuláře

1. Pokud už máte řešení otevřené, zavřete ho.

2. V nabídce **Soubor** klikněte na **Nový** a potom klikněte na **Web.**

    Zobrazí **se dialogové okno Nový** web.

3. V podokně **Šablony** klikněte na ASP.NET **web**.

4. Na řádku **Umístění** klikněte v seznamu na **HTTP** a do textového pole zadejte **http://localhost/WebSite** .

5. V seznamu **Jazyk** klikněte na **Visual C#** **nebo Visual Basic**.

6. Klikněte na **OK**.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vytvoří nový projekt a zobrazí výchozí zdrojový kód HTML. Vytvoří také nový virtuální adresář **WebSite v části** **Výchozí web ve službě** IIS.

7. Klikněte na **kartu Návrh** na dolním okraji.

8. Klikněte na **kartu Panel** nástrojů na levém okraji nebo ji vyberte v **nabídce Zobrazení.**

    Otevře **se panel** nástrojů.

9. V **sadě nástrojů** klikněte na **ovládací prvek Tlačítko** a přidejte ho na hlavní návrhovou plochu Default.aspx.

10. V **sadě nástrojů** klikněte na **ovládací prvek Textové** pole a přetáhněte ho na hlavní návrhovou plochu Default.aspx.

11. Dvakrát klikněte na ovládací prvek tlačítka, který jste vypustili.

     Tím se zobrazí stránka s kódem: Default.aspx.cs pro C# nebo Default.aspx.vb pro [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] . Kurzor by měl být ve funkci `Button1_Click` .

12. Do `Button1_Click` funkce přidejte následující kód:

    ```vb
    TextBox1.Text = "Button was clicked!"
    ```

    ```csharp
    TextBox1.Text = "Button was clicked!";
    ```

13. V nabídce **Sestavení** klikněte na **Sestavit řešení**.

     Projekt by se měl sestavit bez chyb.

     Teď můžete začít s laděním.

## <a name="to-debug-the-web-form"></a>Ladění webového formuláře

1. V okně Default.aspx.cs nebo Default.aspx.vb klikněte na levý okraj na stejném řádku jako přidaný text:

   ```vb
   TextBox1.Text = "Button was clicked!"
   ```

   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

    Zobrazí se červená tečka a text řádku se zvýrazní červeně. Tato červená tečka představuje zarážku. Při spuštění aplikace pomocí ladicího programu v tomto místě ladicí program přeruší provádění, když je tento řádek kódu dosažen. Poté lze zobrazit stav aplikace a ladit ji. Další informace najdete v tématu [Zarážky](/previous-versions/ktf38f66(v=vs.100)).

2. V nabídce **Ladit** klikněte na **Spustit ladění**.

3. Zobrazí **se dialogové okno Ladění není** povoleno. Vyberte **Upravit soubor Web.config a povolte možnost ladění** a klikněte na **OK.**

    Internet Explorer spustí a zobrazí stránku, kterou jste právě navrhli.

4. V Internet Explorer klikněte na tlačítko .

    V nástroji se dostat na řádek, kde nastavíte zarážku na znakové stránce [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Default.aspx.cs nebo Default.aspx.vb. Tento řádek by měl být zvýrazněn žlutou barvou. Nyní lze zobrazit proměnné aplikace a řídit její spuštění. Vaše aplikace se zastaví a čeká na příkaz od vás.

5. V nabídce **Ladit** klikněte na **Windows,** pak na **Sledovat** a pak na **Watch1**.

6. V okně **Watch (Přehrát)** zadejte **TextBox1.Text**.

    V **okně** Watch (Sledování) se zobrazí hodnota proměnné `TextBox1.Text` :

   '""'

7. V nabídce **Ladit** klikněte na **Krok přes**.

    Hodnota změn `TextBox1.Text` v okně **Watch** (Přehrát):

   `"Button was clicked!"`

8. V nabídce **Ladit** klikněte na **Pokračovat.**

9. V Internet Explorer klikněte znovu na tlačítko .

     Provádění se znovu zastaví na zarážce.

10. V okně Default.aspx.cs nebo Default.aspx.vb klikněte na červenou tečku na levém okraji.

     Tím se zarážka odebere.

11. V nabídce **Ladit** klikněte na **Zastavit ladění**.

## <a name="to-attach-to-the-web-form-for-debugging"></a>Připojení k webovému formuláři pro ladění

1. V systému [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lze ladicí program připojit ke spuštěnému procesu. Pokud chcete nejefektivnější ladění, zkompilujte spustitelný soubor jako ladicí verzi se soubory symbolů (PDB).

2. V okně Default.aspx.cs nebo Default.aspx.vb klikněte na levý okraj a znovu nastavte zarážku na řádek, který jste přidali:

   ```vb
   TextBox1.Text = "Button was clicked!"
   ```

   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

3. V nabídce **Ladit** klikněte na **Spustit bez ladění.**

    Webový formulář se spustí v rámci Internet Explorer, ale ladicí program není připojen.

4. Připojte se k [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu. Další informace najdete v tématu [Ladění nasazených webových aplikací.](../debugger/debugging-deployed-web-applications.md)

5. V Internet Explorer klikněte na tlačítko ve formuláři.

    V [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] souboru byste měli narážet na zarážku v souboru Default.aspx.cs, Default.aspx.vb nebo Default.aspx.

6. Po dokončení ladění klikněte v nabídce **Ladit** na **Zastavit ladění.**

## <a name="see-also"></a>Viz také

- [Ladění ASP.NET aplikací](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
---
title: 'Návod: ladění formuláře Windows | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- debugging managed code, Windows Forms
- debugging [Visual Studio], Windows Forms
- Attach to Process dialog box
- debugger, attaching to programs
- Attach to Process dialog box, walkthroughs
- Windows Forms, debugging
- debugging Windows Forms, walkthroughs
ms.assetid: 529db1e2-d9ea-482a-b6a0-7c543d17f114
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a553f77e352b16ba1a0709e13e8893cf0f57a43d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704902"
---
# <a name="walkthrough-debugging-a-windows-form"></a>Návod: Ladění formuláře systému Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikace modelu Windows Form jsou jedny nejběžnějších spravovaných aplikací. Model Windows Form vytvoří standardní aplikaci systému Windows. Tuto rekapitulaci lze dokončit pomocí jazyků Visual Basic, C# nebo C++.  
  
 Nejprve je nutné zavřít všechna otevřená řešení.  
  
### <a name="to-prepare-for-this-walkthrough"></a>Příprava na tento návod  
  
- Pokud již máte své řešení otevřené, zavřete je. (V nabídce **soubor** vyberte **Zavřít řešení**.)  
  
## <a name="create-a-new-windows-form"></a>Vytvoření nové aplikace modelu Windows Form  
 V dalších krocích vytvoříte nový formulář aplikace modelu Windows Form.  
  
#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>Vytvoření formuláře aplikace modelu Windows Form pro tuto rekapitulaci  
  
1. V nabídce **soubor** klikněte na příkaz **Nový** a potom na **projekt**.  
  
     Zobrazí se dialogové okno **Nový projekt**.  
  
2. V podokně typy projektů otevřete uzel **Visual Basic**, **Visual C#** nebo **Visual C++** a potom  
  
    1. Pro Visual Basic nebo Visual C# vyberte uzel **Windows** a potom v podokně **šablony** vyberte možnost **aplikace Windows Form** .  
  
    2. Pro Visual C++ vyberte uzel **CLR** a potom v podokně **šablony** vyberte možnost **aplikace Windows Form** .  
  
3. V podokně **šablony** vyberte možnost **aplikace systému Windows**.  
  
4. V poli **název** zadejte jedinečný název projektu (například Walkthrough_SimpleDebug).  
  
5. Klikněte na **OK**.  
  
     Systém Visual Studio vytvoří nový projekt a nový formulář zobrazí v Návrháři formulářů Windows Forms. Další informace najdete v tématu [Návrhář formulářů](https://msdn.microsoft.com/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
6. V nabídce **zobrazení** vyberte položku **Sada nástrojů**.  
  
     Otevře se panel nástrojů. Další informace najdete v tématu [Sada nástrojů](../ide/reference/toolbox.md).  
  
7. V sadě nástrojů klikněte na ovládací prvek **tlačítko** a přetáhněte ovládací prvek na návrhovou plochu formuláře. Přetáhněte tlačítko na formulář.  
  
8. V sadě nástrojů klikněte na ovládací prvek **TextBox** a přetáhněte ovládací prvek na návrhovou plochu formuláře. Přetáhněte **textové pole** na formuláři.  
  
9. Na návrhové ploše formuláře dvakrát klikněte na tlačítko.  
  
     Tím přejdete na stránku kódu. Kurzor by měl být umístěn v obslužné rutině události `button1_Click`.  
  
10. Do funkce `button1_Click` přidejte následující kód:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
11. V nabídce **sestavení** vyberte **Sestavit řešení**.  
  
     Projekt by se měl sestavit bez chyb.  
  
## <a name="debug-your-form"></a>Ladění formuláře  
 Nyní jste připraveni začít s laděním.  
  
#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>Ladění aplikace modelu Windows Form vytvořené v této rekapitulaci  
  
1. V okně zdroje klikněte na levý okraj řádku, na který jste přidali text:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
     Zobrazí se červená tečka a text řádku se zvýrazní červeně. Tato červená tečka představuje zarážku. Další informace naleznete v tématu [zarážky](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583). Při spuštění aplikace pomocí ladicího programu v tomto místě ladicí program přeruší provádění, když je tento řádek kódu dosažen. Poté lze zobrazit stav aplikace a ladit ji.  
  
    > [!NOTE]
    > Můžete také kliknout pravým tlačítkem na libovolný řádek kódu, nasměrovat na **zarážku**a potom kliknout na **Vložit zarážku** a přidat zarážku na tento řádek.  
  
2. V nabídce **ladit** klikněte na tlačítko **Spustit**.  
  
     Aplikace modelu Windows Form se spustí.  
  
3. Na formuláři aplikace modelu Windows Form klikněte na tlačítko, které jste přidali.  
  
     To vás v systému Visual Studio přenese na stránku kódu k řádku, na který jste nastavili zarážku. Tento řádek by měl být zvýrazněn žlutou barvou. Nyní lze zobrazit proměnné aplikace a řídit její spuštění. Aplikace nyní zastavila provádění a čeká na vaši akci.  
  
4. V nabídce **ladění** zvolte možnost **Windows**, pak **Sledujte**a klikněte na **Watch1**.  
  
5. V okně **Watch1** klikněte na prázdný řádek. Do sloupce **název** zadejte `textBox1.Text` (Pokud používáte Visual Basic, Visual C# nebo J#) nebo `textBox1->Text` (Pokud používáte jazyk C++) a stiskněte klávesu ENTER.  
  
     V okně **Watch1** se zobrazí hodnota této proměnné v uvozovkách jako:  
  
    ```  
    ""  
    ```  
  
6. V nabídce **ladění** vyberte možnost **Krokovat**s vnořením.  
  
     Hodnota textBox1. text se mění v okně **Watch1** na:  
  
    ```  
    Button was clicked!  
    ```  
  
7. V nabídce **ladění** vyberte **pokračovat** a obnovte ladění programu.  
  
8. Klikněte znovu na tlačítko na formuláři aplikace Windows Form.  
  
     Systém Visual Studio znovu přeruší spuštění.  
  
9. Klikněte na červenou tečku představující zarážku.  
  
     Tím tuto zarážku odstraníte z kódu.  
  
10. V nabídce **ladění** vyberte možnost **Zastavit ladění**.  
  
## <a name="attach-to-your-windows-form-application-for-debugging"></a>Připojení k aplikaci modelu Windows Form pro ladění  
 V systému [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] lze ladicí program připojit ke spuštěnému procesu. Pokud používáte verzi Express, není tato funkce podporována.  
  
#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>Připojení k aplikaci modelu Windows Form pro ladění  
  
1. V projektu, který jste vytvořili výše, klikněte na levý okraj řádku, který jste přidali, abyste znovu nastavili zarážku:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!"  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
2. V nabídce **ladění** vyberte **Spustit bez ladění**.  
  
     Aplikace modelu Windows Form se spustí v systému Windows stejně, jako kdyby jste dvakrát kliknuli na její spustitelný soubor. Ladicí program není připojen.  
  
3. V nabídce **ladění** vyberte možnost **připojit k procesu**. (Tento příkaz je k dispozici také v nabídce **nástroje** .)  
  
     Zobrazí se dialogové okno **připojit k procesu** .  
  
4. V podokně **Dostupné procesy** Najděte ve sloupci **Process** název procesu (Walkthrough_SimpleDebug.exe) a klikněte na něj.  
  
5. Klikněte na tlačítko **připojit** .  
  
6. Na formuláři Windows Form vaší aplikace klikněte na tlačítko.  
  
     Ladicí program při dosažení zarážky přeruší spuštění formuláře aplikace modelu Windows Form.  
  
## <a name="see-also"></a>Viz také  
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)

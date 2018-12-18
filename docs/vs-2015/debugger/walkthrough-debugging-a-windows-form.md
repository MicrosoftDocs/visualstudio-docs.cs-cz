---
title: 'Návod: Ladění formuláře Windows | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 8f43835374ac74d50e1e81623ecf268fbfbfe8ca
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726594"
---
# <a name="walkthrough-debugging-a-windows-form"></a>Návod: Ladění formuláře systému Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikace modelu Windows Form jsou jedny nejběžnějších spravovaných aplikací. Model Windows Form vytvoří standardní aplikaci systému Windows. Tuto rekapitulaci lze dokončit pomocí jazyků Visual Basic, C# nebo C++.  
  
 Nejprve je nutné zavřít všechna otevřená řešení.  
  
### <a name="to-prepare-for-this-walkthrough"></a>Příprava pro Tento názorný postup  
  
-   Pokud již máte své řešení otevřené, zavřete je. (Na **souboru** nabídce vyberte možnost **zavřít řešení**.)  
  
## <a name="create-a-new-windows-form"></a>Vytvoření nové aplikace modelu Windows Form  
 V dalších krocích vytvoříte nový formulář aplikace modelu Windows Form.  
  
#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>Vytvoření formuláře aplikace modelu Windows Form pro tuto rekapitulaci  
  
1.  Na **souboru** nabídce zvolte **nový** a klikněte na tlačítko **projektu**.  
  
     **Nový projekt** zobrazí se dialogové okno.  
  
2.  V podokně typy projektů, otevřete **jazyka Visual Basic**, **Visual C#**, nebo **Visual C++** uzlu, pak  
  
    1.  Pro Visual Basic nebo Visual C#, vyberte **Windows** uzlu, pak vyberte **aplikace Windows Form** v **šablony** podokně.  
  
    2.  Visual C++, vyberte **CLR** uzlu, pak vyberte **aplikace Windows Form** v **šablony** podokně...  
  
3.  V **šablony** vyberte **aplikace Windows**.  
  
4.  V **název** pole, zadejte projekt jedinečný název (například Walkthrough_SimpleDebug).  
  
5.  Klikněte na tlačítko **OK**.  
  
     Systém Visual Studio vytvoří nový projekt a nový formulář zobrazí v Návrháři formulářů Windows Forms. Další informace najdete v tématu [Návrháře formulářů Windows](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
6.  Na **zobrazení** nabídce vyberte možnost **nástrojů**.  
  
     Otevře se panel nástrojů. Další informace najdete v tématu [nástrojů](../ide/reference/toolbox.md).  
  
7.  Na panelu nástrojů klikněte na **tlačítko** řídit a přetáhněte jej na návrhovou plochu formuláře. Přetáhněte tlačítko na formulář.  
  
8.  Na panelu nástrojů klikněte na **TextBox** řídit a přetáhněte jej na návrhovou plochu formuláře. Přetáhněte **TextBox** ve formuláři.  
  
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
  
11. Na **sestavení** nabídce vyberte možnost **sestavit řešení**.  
  
     Projekt by se měl sestavit bez chyb.  
  
## <a name="debug-your-form"></a>Ladění formuláře  
 Nyní jste připraveni začít s laděním.  
  
#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>Ladění aplikace modelu Windows Form vytvořené v této rekapitulaci  
  
1.  V okně zdroje klikněte na levý okraj řádku, na který jste přidali text:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
     Zobrazí se červená tečka a text řádku se zvýrazní červeně. Tato červená tečka představuje zarážku. Další informace najdete v tématu [zarážky](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583). Při spuštění aplikace pomocí ladicího programu v tomto místě ladicí program přeruší provádění, když je tento řádek kódu dosažen. Poté lze zobrazit stav aplikace a ladit ji.  
  
    > [!NOTE]
    >  Můžete také pravým tlačítkem na kterýkoli řádek v kódu, přejděte na **zarážku**a potom klikněte na tlačítko **vložit zarážku** pro přidání zarážky na daném řádku.  
  
2.  DÁLE **ladění** nabídce zvolte **spustit**.  
  
     Aplikace modelu Windows Form se spustí.  
  
3.  Na formuláři aplikace modelu Windows Form klikněte na tlačítko, které jste přidali.  
  
     To vás v systému Visual Studio přenese na stránku kódu k řádku, na který jste nastavili zarážku. Tento řádek by měl být zvýrazněn žlutou barvou. Nyní lze zobrazit proměnné aplikace a řídit její spuštění. Aplikace nyní zastavila provádění a čeká na vaši akci.  
  
4.  Na **ladění** nabídce zvolte **Windows**, pak **Watch**a klikněte na tlačítko **Watch1**.  
  
5.  V **Watch1** okna, klikněte na prázdný řádek. V **název** sloupců, typ `textBox1.Text` (Pokud používáte Visual Basic, Visual C# a J#) nebo `textBox1->Text` (Pokud používáte C++), stiskněte klávesu ENTER.  
  
     **Watch1** okno zobrazuje hodnotu této proměnné v uvozovkách jako:  
  
    ```  
    ""  
    ```  
  
6.  Na **ladění** nabídce zvolte **Krokovat s vnořením**.  
  
     Hodnota TextBox1.text v **Watch1** okna:  
  
    ```  
    Button was clicked!  
    ```  
  
7.  Na **ladění** nabídce zvolte **pokračovat** Chcete-li pokračovat v ladění programu.  
  
8.  Klikněte znovu na tlačítko na formuláři aplikace Windows Form.  
  
     Systém Visual Studio znovu přeruší spuštění.  
  
9. Klikněte na červenou tečku představující zarážku.  
  
     Tím tuto zarážku odstraníte z kódu.  
  
10. Na **ladění** nabídce zvolte **Zastavit ladění**.  
  
## <a name="attach-to-your-windows-form-application-for-debugging"></a>Připojení k aplikaci modelu Windows Form pro ladění  
 V systému [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] lze ladicí program připojit ke spuštěnému procesu. Pokud používáte verzi Express, není tato funkce podporována.  
  
#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>Připojení k aplikaci modelu Windows Form pro ladění  
  
1.  V projektu, který jste vytvořili výše, klikněte na levý okraj řádku, který jste přidali, abyste znovu nastavili zarážku:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!"  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
2.  Na **ladění** nabídce vyberte možnost **spustit bez ladění**.  
  
     Aplikace modelu Windows Form se spustí v systému Windows stejně, jako kdyby jste dvakrát kliknuli na její spustitelný soubor. Ladicí program není připojen.  
  
3.  Na **ladění** nabídce vyberte možnost **připojit k procesu**. (Tento příkaz je také k dispozici na **nástroje** nabídky.)  
  
     **Připojit k procesu** zobrazí se dialogové okno.  
  
4.  V **procesy k dispozici** podokno, najděte název procesu (Walkthrough_SimpleDebug.exe) v **procesu** sloupce a klikněte na něj.  
  
5.  Klikněte na tlačítko **připojit** tlačítko.  
  
6.  Na formuláři Windows Form vaší aplikace klikněte na tlačítko.  
  
     Ladicí program při dosažení zarážky přeruší spuštění formuláře aplikace modelu Windows Form.  
  
## <a name="see-also"></a>Viz také  
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)




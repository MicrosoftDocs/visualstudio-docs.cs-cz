---
title: 'Návod: vytváření a spouštění testů jednotek pro aplikace pro Windows Store | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, Windows Store apps
- unit tests, running
ms.assetid: dd3e8a6a-b366-433e-a409-b9a9b89da89a
caps.latest.revision: 23
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f5e62fe83d644b577d7d0a5f87312642f438c490
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851173"
---
# <a name="walkthrough-creating-and-running-unit-tests-for-windows-store-apps"></a>Postupy: Vytváření a spouštění testů jednotek pro aplikace pro web Windows Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio zahrnuje podporu pro testování částí spravovaných aplikací [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] a obsahuje šablony knihovny testů jednotek pro C#Visual, Visual Basic a C++Visual.

> [!TIP]
> Další informace o vývoji aplikací [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] najdete v tématu [Začínáme s aplikacemi pro Windows Store](https://msdn.microsoft.com/windows/apps/br211386.aspx).

 Visual Studio poskytuje následující funkce testování částí:

- [Vytváření projektů testování částí](#CreateAndRunUnitTestWin8Tailored_Create)

- [Upravit manifest pro projekt testu jednotek](#CreateAndRunUnitTestWin8Tailored_Manifest)

- [Kód testu jednotek](#CreateAndRunUnitTestWin8Tailored_Code)

- [Spustit testy jednotek](#CreateAndRunUnitTestWin8Tailored_Run)

  Následující postupy popisují kroky pro vytvoření, spuštění a ladění testů jednotek pro spravovanou aplikaci [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] Windows 8.

## <a name="prerequisites"></a>Požadavky
 Visual Studio

## <a name="CreateAndRunUnitTestWin8Tailored_Create"></a>Vytváření projektů testování částí

#### <a name="to-create-a-unit-test-project-for-a-windows-store-app"></a>Vytvoření projektu testování částí aplikace pro Windows Store

1. Z **souboru** nabídce zvolte **nový projekt**.

     Zobrazí se dialogové okno Nový projekt.

2. V části šablony zvolte programovací jazyk, ve kterém chcete vytvořit test jednotky, a pak zvolte přidruženou knihovnu testu jednotek [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]. Zvolte například možnost **vizuál C#**  , zvolte možnost **Windows Store**a pak zvolte možnost **Knihovna testů jednotek (aplikace pro Windows Store)** .

    > [!NOTE]
    > Visual Studio obsahuje šablony knihovny testů jednotek pro vizuál C#, Visual Basic a vizuál C++.

3. Volitelné Do textového pole **název** zadejte název, který chcete použít pro projekt [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]jednotkového testu.

4. Volitelné Změňte cestu, kam chcete projekt vytvořit, zadáním do textového pole **umístění** nebo kliknutím na tlačítko **Procházet** .

5. (Volitelné) V **řešení** textového pole s názvem, zadejte název, který chcete použít pro vaše řešení.

6. Nechte **vytvořit adresář pro řešení** možnost vybranou a stiskněte tlačítko **OK** tlačítko.

     ![Přizpůsobená knihovna testů jednotek](../test/media/unit-test-win8-1.png "Unit_Test_Win8_1")

     Průzkumník řešení naplní nový projekt testování částí [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]a Editor kódu zobrazí výchozí test jednotky s názvem UnitTest1.

     ![Nově přizpůsobený projekt testu jednotek](../test/media/unit-test-win8-unittestexplorer-newprojectcreated.png "Unit_Test_Win8_UnitTestExplorer_NewProjectCreated")

## <a name="CreateAndRunUnitTestWin8Tailored_Manifest"></a>Upravit manifest pro projekt testu jednotek
 Může být nutné upravit manifest pro projekt testování částí, aby poskytoval požadované možnosti pro spuštění aplikace.

#### <a name="to-edit-the-unit-test-projects-windows-store-application-manifest-file"></a>Úprava souboru manifestu aplikace pro Windows Store projektu testu jednotek

1. V Průzkumník řešení v novém projektu testování jednotky [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] klikněte pravým tlačítkem na soubor Package. appxmanifest a vyberte **otevřít**.

     V Návrháři manifestu se zobrazí pro úpravy.

2. V Návrháři manifestu klikněte na kartu **Možnosti** .

3. V seznamu v části **možnosti**, vyberte možnosti, které potřebujete otestovat u vaší jednotky a kód, který je testován mít. Vyberte například **Internet** zaškrtávací políčko, pokud test jednotky a kód je testování musí mít přístup k Internetu.

    > [!NOTE]
    > Možnosti, které vyberete, by měly obsahovat pouze funkce, které jsou nezbytné pro správné fungování testu [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] jednotky. Funkce by nikdy neměly zahrnovat funkce, které nejsou součástí testované aplikace [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] a obecně by měly být podmnožinou možností určených pro [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]aplikace v rámci testu.

     Další informace o nástroji manifest Designer najdete v tématu [konfigurace Windows 8.1 balíčku aplikace pomocí nástroje manifest Designer](https://msdn.microsoft.com/library/24c58b7f-9c6d-41c3-b385-c1e8497d5b2d).

     ![Manifest testu jednotek](../test/media/unit-test-win8.png "Unit_Test_Win8_")

## <a name="CreateAndRunUnitTestWin8Tailored_Code"></a>Kód testu jednotek

#### <a name="to-code-the-unit-test-for-a-windows-store-app"></a>Vytvoření kódu testu jednotek aplikace pro Windows Store

1. V editoru kódu upravte test jednotky a přidejte výrazy a logiku vyžadované pro váš test.

     Další informace naleznete v tématu [použití tříd Assert](https://msdn.microsoft.com/library/ms182530.aspx) v knihovně MSDN.

## <a name="CreateAndRunUnitTestWin8Tailored_Run"></a>Spustit testy jednotek

#### <a name="to-build-the-solution-and-run-the-unit-test-using-test-explorer"></a>Sestavte řešení a spuštění testování částí pomocí Průzkumníka testů

1. Na **testovací** nabídce zvolte **Windows**a klikněte na tlačítko **Průzkumník testů**.

     Průzkumník testů se zobrazí bez výpisu vašeho testu.

2. Z **sestavení** nabídce zvolte **sestavit řešení**.

     Jednotkový test je nyní obsažena.

    > [!NOTE]
    > Třeba vytvořit řešení Chcete-li aktualizovat seznam testů jednotek v Průzkumníku testů.

    > [!WARNING]
    > Známý problém sady Visual Studio: před sestavením testovacího projektu je nutné otevřít Průzkumníka testů.

3. V Průzkumníku testů vyberte test jednotky, který jste vytvořili.

    > [!TIP]
    > Průzkumník testů obsahuje odkaz na zdrojový kód vedle **zdroj:** .

4. Zvolte **spustit všechny**.

     ![Průzkumník &#45; testů jednotek spustit test jednotek](../test/media/unit-test-win8-unittestexplorer-contextmenurun.png "Unit_Test_Win8_UnitTestExplorer_ContextMenuRun")

    > [!TIP]
    > Vyberte jeden nebo více jednotek testů uvedených v Průzkumníkovi, klepněte pravým tlačítkem myši a zvolte **spustit vybrané testy**.
    >
    >  Kromě toho můžete také **ladit vybrané testy**, **Otevřít testovací**a použít **vlastnosti** možnost.
    >
    >  ![Kontextová nabídka &#45; UNI pro test jednotek v Průzkumníku testu](../test/media/unit-test-win8-unittestexplorer-contextmenu.png "Unit_Test_Win8_UnitTestExplorer_ContextMenu")

     Test jednotky probíhá. Po dokončení zobrazí Průzkumník testů stav testu, uplynulý čas a obsahuje odkaz na zdroj.

     ![Test Průzkumníka &#45; testování částí byl dokončen](../test/media/unit-test-win8-unittestexplorer-done.png "Unit_Test_Win8_UnitTestExplorer_Done")

## <a name="external-resources"></a>Externí prostředky

### <a name="videos"></a>Videa
 [Kanál 9: testování částí aplikací pro Windows Store vytvořených pomocí jazyka XAML](https://channel9.msdn.com/Events/BUILD/BUILD2011/TOOL-529T)

### <a name="forums"></a>Diskuzní fóra
 [Testování částí sady Visual Studio](https://social.msdn.microsoft.com/Forums/en/vsunittest/threads)

### <a name="msdn-library"></a>Knihovna MSDN
 [Knihovna MSDN – vytváření a spouštění testů jednotek pro existující kód (Visual Studio 2010)](https://msdn.microsoft.com/library/hh270865(v=vs.110).aspx)

## <a name="see-also"></a>Viz také
 [Testování aplikací pro Store pomocí sady Visual Studio](../test/testing-store-apps-with-visual-studio.md) [sestavení a otestování aplikace pro Windows Store pomocí Team Foundation Build](https://msdn.microsoft.com/library/d0ca17bb-deae-4f3d-a18d-1a99bebceaa9)

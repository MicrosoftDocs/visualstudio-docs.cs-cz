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
ms.openlocfilehash: 5999edf14692e5ad51f56cb7989ea07eb0f11f5c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657129"
---
# <a name="walkthrough-creating-and-running-unit-tests-for-windows-store-apps"></a>Postupy: Vytváření a spouštění testů jednotek pro aplikace pro web Windows Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio zahrnuje podporu pro testování částí spravovaných aplikací [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] a obsahuje šablony knihovny testů jednotek pro C#Visual, Visual Basic a C++Visual.

> [!TIP]
> Další informace o vývoji aplikací [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] najdete v tématu [Začínáme s aplikacemi pro Windows Store](http://go.microsoft.com/fwlink/?LinkID=241410).

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

1. V nabídce **soubor** klikněte na příkaz **Nový projekt**.

     Zobrazí se dialogové okno Nový projekt.

2. V části šablony zvolte programovací jazyk, ve kterém chcete vytvořit test jednotky, a pak zvolte přidruženou knihovnu testu jednotek [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]. Zvolte například možnost **vizuál C#**  , zvolte možnost **Windows Store**a pak zvolte možnost **Knihovna testů jednotek (aplikace pro Windows Store)** .

    > [!NOTE]
    > Visual Studio obsahuje šablony knihovny testů jednotek pro vizuál C#, Visual Basic a vizuál C++.

3. Volitelné Do textového pole **název** zadejte název, který chcete použít pro projekt [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]unit test.

4. Volitelné Změňte cestu, kam chcete projekt vytvořit, zadáním do textového pole **umístění** nebo kliknutím na tlačítko **Procházet** .

5. Volitelné Do textového pole název **řešení** zadejte název, který chcete použít pro vaše řešení.

6. Ponechte vybranou možnost **vytvořit adresář pro řešení** a klikněte na tlačítko **OK** .

     ![Přizpůsobená knihovna testů jednotek](../test/media/unit-test-win8-1.png "Unit_Test_Win8_1")

     Průzkumník řešení naplní nový projekt [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]unit test a Editor kódu zobrazí výchozí test jednotky s názvem UnitTest1.

     ![Nově přizpůsobený projekt testu jednotek](../test/media/unit-test-win8-unittestexplorer-newprojectcreated.png "Unit_Test_Win8_UnitTestExplorer_NewProjectCreated")

## <a name="CreateAndRunUnitTestWin8Tailored_Manifest"></a>Upravit manifest pro projekt testu jednotek
 Může být nutné upravit manifest pro projekt testování částí, aby poskytoval požadované možnosti pro spuštění aplikace.

#### <a name="to-edit-the-unit-test-projects-windows-store-application-manifest-file"></a>Úprava souboru manifestu aplikace pro Windows Store projektu testu jednotek

1. V Průzkumník řešení v novém projektu testování jednotky [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] klikněte pravým tlačítkem na soubor Package. appxmanifest a vyberte **otevřít**.

     V Návrháři manifestu se zobrazí pro úpravy.

2. V Návrháři manifestu klikněte na kartu **Možnosti** .

3. V seznamu v části **Možnosti**vyberte možnosti, které budete potřebovat pro testování částí, a kód, který má testovat. Například zaškrtněte políčko **Internet** , pokud test jednotky potřebuje a kód, který testuje, musí mít možnost přístupu k Internetu.

    > [!NOTE]
    > Možnosti, které vyberete, by měly obsahovat pouze funkce, které jsou nezbytné pro správné fungování testu [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] jednotky. Funkce by nikdy neměly zahrnovat funkce, které nejsou součástí testované aplikace [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] a obecně by měly být podmnožinou možností určených [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]app v rámci testu.

     Další informace o nástroji manifest Designer najdete v tématu [konfigurace Windows 8.1 balíčku aplikace pomocí nástroje manifest Designer](https://msdn.microsoft.com/library/24c58b7f-9c6d-41c3-b385-c1e8497d5b2d).

     ![Manifest testu jednotek](../test/media/unit-test-win8.png "Unit_Test_Win8_")

## <a name="CreateAndRunUnitTestWin8Tailored_Code"></a>Kód testu jednotek

#### <a name="to-code-the-unit-test-for-a-windows-store-app"></a>Vytvoření kódu testu jednotek aplikace pro Windows Store

1. V editoru kódu upravte test jednotky a přidejte výrazy a logiku vyžadované pro váš test.

     Další informace naleznete v tématu [použití tříd Assert](http://go.microsoft.com/fwlink/?LinkID=224991) v knihovně MSDN.

## <a name="CreateAndRunUnitTestWin8Tailored_Run"></a>Spustit testy jednotek

#### <a name="to-build-the-solution-and-run-the-unit-test-using-test-explorer"></a>Sestavení řešení a spuštění testu jednotek pomocí Průzkumníka testů

1. V nabídce **test** zvolte možnost **Windows**a pak zvolte možnost **Průzkumník testů**.

     Průzkumník testů se zobrazí bez výpisu vašeho testu.

2. V nabídce **sestavení** klikněte na příkaz **Sestavit řešení**.

     Test jednotek je nyní uveden.

    > [!NOTE]
    > Chcete-li aktualizovat seznam testů jednotek v Průzkumníku testů, je nutné sestavit řešení.

    > [!WARNING]
    > Známý problém sady Visual Studio: před sestavením testovacího projektu je nutné otevřít Průzkumníka testů.

3. V Průzkumníku testů vyberte test jednotky, který jste vytvořili.

    > [!TIP]
    > Průzkumník testů poskytuje odkaz na zdrojový kód vedle **zdroje:** .

4. Vyberte **Spustit vše**.

     ![Průzkumník &#45; testů jednotek spustit test jednotek](../test/media/unit-test-win8-unittestexplorer-contextmenurun.png "Unit_Test_Win8_UnitTestExplorer_ContextMenuRun")

    > [!TIP]
    > Můžete vybrat jednu nebo více testů jednotek uvedených v Průzkumníkovi a potom kliknout pravým tlačítkem a zvolit **Spustit vybrané testy**.
    >
    >  Kromě toho můžete zvolit **ladění vybraných testů**, **Otevřít test**a použít možnost **vlastnosti** .
    >
    >  ![Kontextová nabídka &#45; UNI pro test jednotek v Průzkumníku testu](../test/media/unit-test-win8-unittestexplorer-contextmenu.png "Unit_Test_Win8_UnitTestExplorer_ContextMenu")

     Test jednotek je spuštěn. Po dokončení zobrazí Průzkumník testů stav testu, uplynulý čas a obsahuje odkaz na zdroj.

     ![Test Průzkumníka &#45; testování částí byl dokončen](../test/media/unit-test-win8-unittestexplorer-done.png "Unit_Test_Win8_UnitTestExplorer_Done")

## <a name="external-resources"></a>Externí zdroje

### <a name="videos"></a>Videa
 [Kanál 9: testování částí aplikací pro Windows Store vytvořených pomocí jazyka XAML](http://go.microsoft.com/fwlink/?LinkId=226285)

### <a name="forums"></a>Diskuzní fóra
 [Testování částí sady Visual Studio](http://go.microsoft.com/fwlink/?LinkId=224477)

### <a name="msdn-library"></a>Knihovna MSDN
 [Knihovna MSDN – vytváření a spouštění testů jednotek pro existující kód (Visual Studio 2010)](http://go.microsoft.com/fwlink/?LinkID=223683)

## <a name="see-also"></a>Viz také
 [Testování aplikací pro Store pomocí sady Visual Studio](../test/testing-store-apps-with-visual-studio.md) [sestavení a otestování aplikace pro Windows Store pomocí Team Foundation Build](https://msdn.microsoft.com/library/d0ca17bb-deae-4f3d-a18d-1a99bebceaa9)

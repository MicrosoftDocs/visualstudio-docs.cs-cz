---
title: 'Návod: Vytváření a spouštění testů jednotek pro aplikace Windows Store | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, Windows Store apps
- unit tests, running
ms.assetid: dd3e8a6a-b366-433e-a409-b9a9b89da89a
caps.latest.revision: 23
ms.author: gewarren
manager: douge
ms.openlocfilehash: 30a8b7a465c85e60b00f2208bd6e51cc55c4bbe7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49852528"
---
# <a name="walkthrough-creating-and-running-unit-tests-for-windows-store-apps"></a>Postupy: Vytváření a spouštění testů jednotek pro aplikace pro web Windows Store
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio zahrnuje podporu pro testování částí spravovaného [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace a obsahuje šablony knihoven testování jednotek pro jazyk Visual C#, Visual Basic a Visual C++.  
  
> [!TIP]
>  Další informace o vývoji [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikací, najdete v článku [Začínáme s aplikacemi pro Windows Store](http://go.microsoft.com/fwlink/?LinkID=241410).  
  
 Visual Studio poskytuje následující funkce testování:  
  
- [Vytvoření projektů jednotkových testů](#CreateAndRunUnitTestWin8Tailored_Create)  
  
- [Úprava manifestu projektu testování částí](#CreateAndRunUnitTestWin8Tailored_Manifest)  
  
- [Programování testu jednotek](#CreateAndRunUnitTestWin8Tailored_Code)  
  
- [Spouštění testů jednotek](#CreateAndRunUnitTestWin8Tailored_Run)  
  
  Následující postupy popisují postup vytvoření, spuštění a ladění testů jednotky pro spravované systémem Windows 8 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace.  
  
## <a name="prerequisites"></a>Požadavky  
 Visual Studio  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Create"></a> Vytvoření projektů jednotkových testů  
  
#### <a name="to-create-a-unit-test-project-for-a-windows-store-app"></a>Chcete-li vytvořit projekt testů jednotek pro aplikace Windows Store  
  
1.  Z **souboru** nabídce zvolte **nový projekt**.  
  
     Zobrazí se dialogové okno Nový projekt.  
  
2.  V části šablony vyberte programovací jazyk, kterou chcete vytvořit test jednotky a pak zvolte přidruženou [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] knihovna testu jednotek. Například zvolte **Visual C#** , klikněte na tlačítko **Windows Store**a klikněte na tlačítko **testovací knihovna jednotky (aplikace pro Windows Store)**.  
  
    > [!NOTE]
    >  Visual Studio obsahuje šablony knihoven testování jednotek pro jazyk Visual C#, Visual Basic a Visual C++.  
  
3.  (Volitelné) V **název** textového pole zadejte název, kterou chcete použít pro [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]projekt testu jednotek.  
  
4.  (Volitelné) Upravit cestu, kde chcete vytvořit projekt tak, že ho zadáte **umístění** textové pole, nebo výběrem položky **Procházet** tlačítko.  
  
5.  (Volitelné) V **řešení** textového pole s názvem, zadejte název, který chcete použít pro vaše řešení.  
  
6.  Nechte **vytvořit adresář pro řešení** možnost vybranou a stiskněte tlačítko **OK** tlačítko.  
  
     ![Přizpůsobit testovací knihovna jednotky](../test/media/unit-test-win8-1.png "Unit_Test_Win8_1")  
  
     Průzkumník řešení je vyvolán pomocí nové [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]projekt testování částí a editor kódu zobrazí výchozí test jednotky s názvem UnitTest1.  
  
     ![Nový projekt testu jednotky míru](../test/media/unit-test-win8-unittestexplorer-newprojectcreated.png "Unit_Test_Win8_UnitTestExplorer_NewProjectCreated")  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Manifest"></a> Úprava manifestu projektu testování částí  
 Může být nutné upravit manifest pro projekt testování jednotky kvůli poskytnutí požadovaných funkcí a spusťte tak aplikaci.  
  
#### <a name="to-edit-the-unit-test-projects-windows-store-application-manifest-file"></a>Chcete-li upravit soubor manifestu aplikace Windows Store projekt testu jednotek  
  
1.  V Průzkumníku řešení klikněte na novém [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projekt jednotkového testu, klikněte pravým tlačítkem na soubor Package.appxmanifest a zvolte **otevřít**.  
  
     Návrháře manifestu poskytuje zobrazení pro úpravy.  
  
2.  V Návrháři manifestu zvolte **možnosti** kartu.  
  
3.  V seznamu v části **možnosti**, vyberte možnosti, které potřebujete otestovat u vaší jednotky a kód, který je testován mít. Vyberte například **Internet** zaškrtávací políčko, pokud test jednotky a kód je testování musí mít přístup k Internetu.  
  
    > [!NOTE]
    >  Možnosti výběru by měly obsahovat pouze funkce, které jsou nezbytné pro [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] testování částí fungovat správně. Možnosti by nikdy neměli obsahovat funkce, které nejsou součástí [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace otestovali a obecně by měly být dílčí funkce možností určených pro [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]diskutujete testovanou aplikaci.  
  
     Další informace o návrháři manifestu naleznete v tématu [nakonfigurovat balíček aplikace pro Windows 8.1 pomocí návrháře manifestu](http://msdn.microsoft.com/library/24c58b7f-9c6d-41c3-b385-c1e8497d5b2d).  
  
     ![Manifest testu jednotek](../test/media/unit-test-win8.png "Unit_Test_Win8_")  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Code"></a> Programování testu jednotek  
  
#### <a name="to-code-the-unit-test-for-a-windows-store-app"></a>K programování testu jednotek aplikace pro Windows Store  
  
1.  V editoru kódu upravte test jednotky a přidejte kontrolní výrazy a logiku nezbytnou pro test.  
  
     Další informace najdete v tématu v [používání tříd Assert](http://go.microsoft.com/fwlink/?LinkID=224991) v knihovně MSDN.  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Run"></a> Spouštění testů jednotek  
  
#### <a name="to-build-the-solution-and-run-the-unit-test-using-test-explorer"></a>Sestavte řešení a spuštění testování částí pomocí Průzkumníka testů  
  
1.  Na **testovací** nabídce zvolte **Windows**a klikněte na tlačítko **Průzkumník testů**.  
  
     Průzkumník testů se zobrazí bez uvedení vašeho testu.  
  
2.  Z **sestavení** nabídce zvolte **sestavit řešení**.  
  
     Jednotkový test je nyní obsažena.  
  
    > [!NOTE]
    >  Třeba vytvořit řešení Chcete-li aktualizovat seznam testů jednotek v Průzkumníku testů.  
  
    > [!WARNING]
    >  Visual Studio známý problém: Průzkumník testu je nutné otevřít před sestavením zkušebního projektu.  
  
3.  V Průzkumníku testů vyberte test jednotky, kterou jste vytvořili.  
  
    > [!TIP]
    >  Průzkumník testů obsahuje odkaz na zdrojový kód vedle **zdroj:**.  
  
4.  Zvolte **spustit všechny**.  
  
     ![Průzkumník testů jednotek &#45; spustit test jednotek](../test/media/unit-test-win8-unittestexplorer-contextmenurun.png "Unit_Test_Win8_UnitTestExplorer_ContextMenuRun")  
  
    > [!TIP]
    >  Vyberte jeden nebo více jednotek testů uvedených v Průzkumníkovi, klepněte pravým tlačítkem myši a zvolte **spustit vybrané testy**.  
    >   
    >  Kromě toho můžete také **ladit vybrané testy**, **Otevřít testovací**a použít **vlastnosti** možnost.  
    >   
    >  ![Průzkumník testů jednotek &#45; místní nabídka testu uni](../test/media/unit-test-win8-unittestexplorer-contextmenu.png "Unit_Test_Win8_UnitTestExplorer_ContextMenu")  
  
     Test jednotky probíhá. Po dokončení Průzkumník testu svat testu, uplynulý čas a získáte odkaz na zdroj.  
  
     ![Průzkumník testů jednotek &#45; test dokončen](../test/media/unit-test-win8-unittestexplorer-done.png "Unit_Test_Win8_UnitTestExplorer_Done")  
  
## <a name="external-resources"></a>Externí zdroje  
  
### <a name="videos"></a>Videa  
 [Kanál 9: Testování vašich aplikací Windows Store vyvíjené v XAML](http://go.microsoft.com/fwlink/?LinkId=226285)  
  
### <a name="forums"></a>Diskuzní fóra  
 [Testování částí sady Visual Studio](http://go.microsoft.com/fwlink/?LinkId=224477)  
  
### <a name="msdn-library"></a>Knihovna MSDN  
 [Knihovna MSDN – vytváření a spouštění testů jednotek pro existující kód (Visual Studio 2010)](http://go.microsoft.com/fwlink/?LinkID=223683)  
  
## <a name="see-also"></a>Viz také  
 [Testování aplikací pro Store pomocí sady Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Sestavení a testování aplikací pro Windows Store pomocí Team Foundation Build](http://msdn.microsoft.com/library/d0ca17bb-deae-4f3d-a18d-1a99bebceaa9)




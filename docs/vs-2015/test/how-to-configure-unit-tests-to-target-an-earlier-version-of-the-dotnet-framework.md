---
title: 'Postupy: Konfigurace testů jednotek pro cílení na dřívější verzi rozhraní .NET Framework | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: adb6c011-5abd-41d2-8ead-08cd7579bf37
caps.latest.revision: 14
ms.author: gewarren
manager: douge
ms.openlocfilehash: 978f4e3edeb83d5980d793d74cf209e8e8f7205e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892789"
---
# <a name="how-to-configure-unit-tests-to-target-an-earlier-version-of-the-net-framework"></a>Postupy: Konfigurace testů jednotek pro cílení na dřívější verzi rozhraní .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když vytvoříte projekt testů v sadě Microsoft Visual Studio, nejnovější verzi rozhraní .NET Framework ve výchozím nastavení jako cíl. Navíc pokud provedete upgrade projektů testů z předchozích verzí sady Visual Studio, upgradováním cílit na nejnovější verzi rozhraní .NET Framework. Úpravou vlastností projektu můžete explicitně znovu cílit projekt na starší verze rozhraní .NET Framework.  
  
 Jednotky můžete vytvořit projekty testů, které cílí určité verze rozhraní .NET Framework. Cílová verze musí být 3.5 nebo novější a nemůže být verze klienta. Visual Studio umožňuje následující základní podporu pro testování částí, které cílí určité verze:  
  
- Můžete vytvářet projekty testů jednotek a cílit na konkrétní verzi rozhraní .NET Framework.  
  
- Můžete spustit testy jednotek, které se zaměřují na konkrétní verzi rozhraní .NET Framework ze sady Visual Studio na svém místním počítači.  
  
- Jednotkové testy můžete spustit pomocí MSTest.exe z příkazového řádku, které se zaměřují na konkrétní verzi rozhraní .NET Framework.  
  
- Jednotkové testy můžete spustit na agentu sestavení jako součást sestavení.  
  
  **Testování aplikací pro SharePoint**  
  
  Funkce uvedené výše také umožňují zápis testů jednotek a testů integrace pro aplikace SharePoint pomocí sady Visual Studio. [!INCLUDE[crabout](../includes/crabout-md.md)] vývoj aplikací služby SharePoint pomocí sady Visual Studio, naleznete v tématu [vytvořit řešení služby SharePoint](http://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631), [sestavování a ladění řešení služby SharePoint](http://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae) a [ověření a ladění služby SharePoint Kód](http://msdn.microsoft.com/library/b5f3bce2-6a51-41b1-a292-9e384bae420c).  
  
  **Omezení**  
  
  Když míříte znovu používat starší verze rozhraní .NET Framework testovací projekty se vztahují následující omezení:  
  
- V rozhraní .NET Framework 3.5 cílení na více verzí se podporuje pro projekty testů, které obsahují pouze jednotkové testy. Rozhraní .NET Framework 3.5 nepodporuje jakýkoli jiný typ testu, jako je například programový test uživatelského rozhraní nebo zatížení. Změnu cíle je blokované pro typy testů kromě testů jednotek.  
  
- Spuštění testů, které cílí na starší verzi rozhraní .NET Framework je podporováno pouze v výchozího hostitelského adaptéru. Nepodporuje se v adaptéru hostitele technologie ASP.NET. Aplikace ASP.NET, které je nutné spustit v kontextu serveru ASP.NET Development Server musí být kompatibilní s aktuální verzí rozhraní .NET Framework.  
  
- Podpora shromažďování dat je zakázané při spuštění testů, které podporují cílení na více verzí rozhraní .NET Framework 3.5. Spustit pokrytí kódu pomocí nástroje příkazového řádku sady Visual Studio.  
  
- Na vzdáleném počítači nelze spustit testy jednotek, které používají rozhraní .NET Framework 3.5.  
  
- Nelze cílit testů jednotek pro starší verze klienta architektury.  
  
### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-visual-basic-unit-test-projects"></a>Znovu cílení na konkrétní verzi rozhraní .NET Framework pro projekty testů částí Visual Basic  
  
1.  Vytvořte nový projekt testování částí Visual Basic. Na **souboru** nabídce zvolte **nový** a klikněte na tlačítko **projektu**.  
  
     **Nový projekt** se zobrazí dialogové okno.  
  
2.  V části **nainstalované šablony**, rozbalte **jazyka Visual Basic**. Vyberte **testovací** a pak vyberte **testovací projekt** šablony.  
  
3.  V **název** textového pole, zadejte název pro jazyk Visual Basic testovací projekt a klikněte na tlačítko **OK**.  
  
4.  V Průzkumníku řešení zvolte **vlastnosti** z místní nabídky nový testovací projekt jazyka Visual Basic.  
  
     Zobrazí se vlastnosti pro testovací projekt jazyka Visual Basic.  
  
5.  Na **kompilaci** zvolte kartu **Upřesnit možnosti kompilace** jak je znázorněno na následujícím obrázku.  
  
     ![Upřesnit možnosti kompilace](../test/media/howtoconfigureunittest35frameworka.png "HowToConfigureUnitTest35FrameworkA")  
  
6.  Použití **cílového rozhraní (všechny konfigurace)** rozevíracího seznamu, chcete-li změnit cílovou architekturu na **rozhraní .NET Framework 3.5** nebo novější verze, jak je znázorněno na následujícím obrázku popisku B. Neměli zadejte verzi klienta.  
  
     ![Cílové rozhraní framework rozevírací&#45;dolů seznam](../test/media/howtoconfigureunitest35frameworkstepb.png "HowToConfigureUniTest35FrameworkStepB")  
  
### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-visual-c-unit-test-projects"></a>Znovu cílení na konkrétní verzi rozhraní .NET Framework pro Visual C# projektů testů jednotek  
  
1.  Vytvořte nový projekt testování částí Visual C#. Na **souboru** nabídce zvolte **nový** a klikněte na tlačítko **projektu**.  
  
     **Nový projekt** se zobrazí dialogové okno.  
  
2.  V části **nainstalované šablony**, rozbalte **Visual C#**. Vyberte **testovací** a pak vyberte **testovací projekt** šablony.  
  
3.  V **název** textového pole, zadejte název pro váš jazyk Visual C# projekt testů a klikněte na tlačítko **OK**.  
  
4.  V Průzkumníku řešení zvolte **vlastnosti** z místní nabídky Nový projekt testů Visual C#.  
  
     Zobrazí se vlastnosti pro testovací projekt Visual C#.  
  
5.  Na **aplikace** zvolte kartu **Cílová architektura** a klikněte na tlačítko **rozhraní .NET Framework 3.5** nebo novější verzi z rozevíracího seznamu, chcete-li změnit cílové framework.as zobrazí na následujícím obrázku. Neměli zadejte verzi klienta.  
  
     ![Cílové rozhraní framework rozevírací&#45;dolů seznam](../test/media/howtoconfigureunittest35frameworkcsharp.png "HowToConfigureUnitTest35FrameworkCSharp")  
  
### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-ccli-unit-test-projects"></a>Znovu cílení na konkrétní verzi rozhraní .NET Framework pro C + +/ CLI projektů testů jednotek  
  
1.  Vytvoření nového projektu testování částí C++. Na **souboru** nabídce vyberte možnost **nový** a potom klikněte na tlačítko **projektu**.  
  
     **Nový projekt** se zobrazí dialogové okno.  
  
    > [!WARNING]
    >  K sestavení C + +/ CLI částí pro předchozí verze rozhraní .NET Framework pro aplikaci Visual C++, je nutné použít odpovídající verzi sady Visual Studio. Například chcete-li cílit na rozhraní .NET Framework 3.5, musíte nainstalovat [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] a [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] aktualizací Service Pack 1.  
  
2.  V části **nainstalované šablony**, rozbalte **Visual C ++**. Vyberte **testovací** a pak vyberte **testovací projekt** šablony.  
  
3.  V **název** textového pole, zadejte název pro Visual C++ testovací projekt a potom klikněte na **OK**.  
  
4.  V Průzkumníku řešení zvolte **uvolnit projekt** z nového testovacího projektu Visual C++.  
  
5.  V Průzkumníku řešení zvolte uvolněna testovacího projektu Visual C++ a klikněte na tlačítko **upravit \<název projektu > .vcxproj**.  
  
     V editoru se otevře soubor .vcxproj.  
  
6.  Nastavte `TargetFrameworkVersion` verze 3.5 nebo novější verze v `PropertyGroup` označené `"Globals"`. Byste neměli zadávat jako verze klienta:  
  
    ```  
    <PropertyGroup Label="Globals">  
        <TargetName>DefaultTest</TargetName>  
        <ProjectTypes>{3AC096D0-A1C2-E12C-1390-A8335801FDAB};{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}</ProjectTypes>  
        <ProjectGUID>{CE16D77A-E364-4ACD-948B-1EB6218B0EA3}</ProjectGUID>  
        <TargetFrameworkVersion>3.5</TargetFrameworkVersion>  
        <Keyword>ManagedCProj</Keyword>  
        <RootNamespace>CPP_Test</RootNamespace>  
      </PropertyGroup>  
  
    ```  
  
7.  Uložte a zavřete soubor .vcxproj.  
  
8.  V Průzkumníku řešení zvolte **znovu načíst projekt** z místní nabídky pro nový testovací projekt Visual C++.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření a spouštění testů jednotek pro existující kód](http://msdn.microsoft.com/en-us/e8370b93-085b-41c9-8dec-655bd886f173)   
 [Vytvoření řešení služby SharePoint](http://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631)   
 [Sestavování a ladění řešení služby SharePoint](http://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae)   
 [Dialogové okno Pokročilé nastavení kompilátoru (Visual Basic)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)




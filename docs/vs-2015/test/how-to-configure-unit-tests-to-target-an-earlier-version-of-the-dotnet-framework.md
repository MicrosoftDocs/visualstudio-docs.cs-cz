---
title: 'Postupy: konfigurace testů jednotek pro cílení na dřívější verzi .NET Framework | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: adb6c011-5abd-41d2-8ead-08cd7579bf37
caps.latest.revision: 14
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fd212eb304e6cba022b067b8b432cf00fc3f87ba
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660542"
---
# <a name="how-to-configure-unit-tests-to-target-an-earlier-version-of-the-net-framework"></a>Postupy: Konfigurace testování částí pro cílení na dřívější verzi rozhraní .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při vytváření testovacího projektu v Microsoft Visual Studio je nejnovější verze .NET Framework ve výchozím nastavení nastavena jako cíl. Kromě toho, pokud upgradujete testovací projekty z předchozích verzí sady Visual Studio, jsou upgradovány na cílení na nejnovější verzi .NET Framework. Úpravou vlastností projektu můžete explicitně změnit cíl projektu na dřívější verze .NET Framework.

 Můžete vytvořit projekty testování částí, které cílí na konkrétní verze .NET Framework. Cílová verze musí být 3,5 nebo vyšší a nemůže se jednat o verzi klienta. Visual Studio umožňuje následující základní podporu pro testování částí, které cílí na konkrétní verze:

- Můžete vytvořit projekty testování částí a cílit je na konkrétní verzi .NET Framework.

- Můžete spustit testy jednotek, které cílí na konkrétní verzi .NET Framework ze sady Visual Studio na místním počítači.

- Můžete spustit testy jednotek, které cílí na konkrétní verzi .NET Framework pomocí nástroje MSTest. exe z příkazového řádku.

- V rámci sestavení lze spustit testy jednotek v agentovi sestavení.

  **Testování aplikací SharePoint**

  Výše uvedené možnosti také umožňují napsat testy jednotek a testy integrace pro aplikace SharePoint pomocí sady Visual Studio. [!INCLUDE[crabout](../includes/crabout-md.md)] jak vyvíjet aplikace SharePoint pomocí sady Visual Studio, přečtěte si téma [vytváření řešení SharePoint](https://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631), [sestavování a ladění řešení služby SharePoint](https://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae) a [ověřování a ladění kódu služby SharePoint](https://msdn.microsoft.com/library/b5f3bce2-6a51-41b1-a292-9e384bae420c).

  **Omezení**

  Následující omezení platí při opětovném cílení testovacích projektů, aby používaly dřívější verze .NET Framework:

- V .NET Framework 3,5 je pro projekty testů, které obsahují pouze testy jednotek, podporováno cílení na více verzí. .NET Framework 3,5 nepodporuje žádný jiný typ testu, jako je například kódované uživatelské rozhraní nebo zátěžový test. Opětovné cílení je blokováno pro jiné typy testů než testy jednotek.

- Spuštění testů, které jsou zaměřené na starší verzi .NET Framework, je podporováno pouze ve výchozím hostitelském adaptéru. Není podporován hostitelským adaptérem ASP.NET. ASP.NET aplikace, které musí běžet v kontextu vývojového serveru ASP.NET musí být kompatibilní s aktuální verzí .NET Framework.

- Podpora shromažďování dat je zakázána při spuštění testů, které podporují více cílů .NET Framework 3,5. Pokrytí kódu můžete spustit pomocí nástrojů příkazového řádku sady Visual Studio.

- Testy jednotek, které používají .NET Framework 3,5, nelze spustit na vzdáleném počítači.

- Nemůžete cílit testy jednotek na starší verze rozhraní .NET Framework.

### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-visual-basic-unit-test-projects"></a>Změna cílení na konkrétní verzi .NET Framework pro projekty Visual Basic testování částí

1. Vytvořte nový projekt testu jednotek Visual Basic. V nabídce **soubor** klikněte na příkaz **Nový** a pak zvolte možnost **projekt**.

     Zobrazí se dialogové okno **Nový projekt** .

2. V části **Nainstalované šablony**rozbalte položku **Visual Basic**. Vyberte **test** a potom vyberte šablonu **testovacího projektu** .

3. Do textového pole **název** zadejte název testovacího projektu Visual Basic a klikněte na **tlačítko OK**.

4. V Průzkumník řešení v místní nabídce nového projektu Visual Basic testu vyberte možnost **vlastnosti** .

     Zobrazí se vlastnosti testovacího projektu Visual Basic.

5. Na kartě **kompilovat** klikněte na možnost **Pokročilé možnosti kompilace** , jak je znázorněno na následujícím obrázku.

     ![Pokročilé možnosti kompilace](../test/media/howtoconfigureunittest35frameworka.png "HowToConfigureUnitTest35FrameworkA")

6. Pomocí rozevíracího seznamu **Cílová architektura (všechny konfigurace)** Změňte cílovou architekturu na **.NET Framework 3,5** nebo novější verzi, jak je znázorněno v popisku B na následujícím obrázku. Nemusíte určovat verzi klienta.

     ![Rozevírací&#45;seznam cílového rozhraní Framework](../test/media/howtoconfigureunitest35frameworkstepb.png "HowToConfigureUniTest35FrameworkStepB")

### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-visual-c-unit-test-projects"></a>Změna cílení na konkrétní verzi .NET Framework pro projekty Visual C# jednotky test

1. Vytvořte nový projekt Visual C# Unit-Test. V nabídce **soubor** klikněte na příkaz **Nový** a pak zvolte možnost **projekt**.

     Zobrazí se dialogové okno **Nový projekt** .

2. V části **Nainstalované šablony**rozbalte **položku C#vizuál** . Vyberte **test** a potom vyberte šablonu **testovacího projektu** .

3. Do textového pole **název** zadejte název projektu Visual C# test a klikněte na **tlačítko OK**.

4. V Průzkumník řešení v místní nabídce nového projektu Visual C# test vyberte možnost Vlastnosti.

     Zobrazí se vlastnosti projektu Visual C# test.

5. Na kartě **aplikace** zvolte **Cílová architektura** a pak v rozevíracím seznamu zvolte **.NET Framework 3,5** nebo novější verze, abyste změnili cílový Framework.as, jak je znázorněno na následujícím obrázku. Nemusíte určovat verzi klienta.

     ![Rozevírací&#45;seznam cílového rozhraní Framework](../test/media/howtoconfigureunittest35frameworkcsharp.png "HowToConfigureUnitTest35FrameworkCSharp")

### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-ccli-unit-test-projects"></a>Změna cílení na konkrétní verzi .NET Framework pro projekty pro C++testování částí/CLI

1. Vytvořte nový C++ projekt testování částí. V nabídce **soubor** vyberte **Nový** a pak klikněte na **projekt**.

     Zobrazí se dialogové okno **Nový projekt** .

    > [!WARNING]
    > Chcete- C++li vytvořit testy jednotek/CLI pro předchozí verzi rozhraní .NET Framework pro Visual C++, je nutné použít odpovídající verzi sady Visual Studio. Chcete-li například cílit na .NET Framework 3,5, je nutné nainstalovat [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] a [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] aktualizaci Service Pack 1.

2. V části **Nainstalované šablony**rozbalte položku **Visual C + +** . Vyberte **test** a potom vyberte šablonu **testovacího projektu** .

3. Do textového pole **název** zadejte název projektu Visual C++ test a klikněte na tlačítko **OK**.

4. V Průzkumník řešení klikněte na možnost **Uvolnit projekt** z nového projektu Visual C++ test.

5. V Průzkumník řešení zvolte nenačtený projekt Visual C++ test a pak zvolte **upravit \<project název >. vcxproj**.

     V editoru se otevře soubor. vcxproj.

6. Nastavte `TargetFrameworkVersion` na verzi 3,5 nebo novější v `PropertyGroup` s popiskem `"Globals"`. Nemusíte určovat verzi klienta:

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

7. Uložte a zavřete soubor. vcxproj.

8. V Průzkumník řešení zvolte v místní nabídce nového projektu Visual C++ test možnost vybrat **znovu načíst projekt** .

## <a name="see-also"></a>Viz také
 [Vytváření a spouštění testů jednotek pro existující kód](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173) [vytvoření řešení SharePoint](https://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631) vytváření [a ladění řešení sharepoint](https://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae) [Upřesnit nastavení kompilátoru (Visual Basic)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)

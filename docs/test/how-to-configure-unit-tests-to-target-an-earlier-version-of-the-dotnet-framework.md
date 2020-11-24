---
title: Testování částí cílí na starší verzi .NET Framework
description: Naučte se vytvářet projekty testování částí pro cílení na konkrétní verze .NET Framework. Cílová verze musí být 3,5 nebo vyšší a nemůže se jednat o verzi klienta.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
author: mikejo5000
ms.openlocfilehash: 6badbb7723bf4d8ed0c9385558204c2dc4907574
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441245"
---
# <a name="how-to-configure-unit-tests-to-target-an-earlier-version-of-the-net-framework"></a>Postupy: konfigurace testů jednotek pro cílení na dřívější verzi .NET Framework

Při vytváření testovacího projektu v Microsoft Visual Studio je nejnovější verze .NET Framework ve výchozím nastavení nastavena jako cíl. Kromě toho, pokud upgradujete testovací projekty z předchozích verzí sady Visual Studio, jsou upgradovány na cílení na nejnovější verzi .NET Framework. Úpravou vlastností projektu můžete explicitně změnit cíl projektu na dřívější verze .NET Framework.

Můžete vytvořit projekty testování částí, které cílí na konkrétní verze .NET Framework. Cílová verze musí být 3,5 nebo vyšší a nemůže se jednat o verzi klienta. Visual Studio umožňuje následující základní podporu pro testování částí, které cílí na konkrétní verze:

- Můžete vytvořit projekty testování částí a cílit je na konkrétní verzi .NET Framework.

- Můžete spustit testy jednotek, které cílí na konkrétní verzi .NET Framework ze sady Visual Studio na místním počítači.

- Můžete spustit testy jednotek, které cílí na konkrétní verzi .NET Framework pomocí *MSTest.exe* z příkazového řádku.

- V rámci sestavení lze spustit testy jednotek v agentovi sestavení.

**Testování aplikací SharePoint**

Výše uvedené možnosti také umožňují napsat testy jednotek a testy integrace pro aplikace SharePoint pomocí sady Visual Studio. Další informace o tom, jak vyvíjet aplikace SharePoint pomocí sady Visual Studio, naleznete v tématech [vytváření řešení služby SharePoint](../sharepoint/create-sharepoint-solutions.md), [sestavení a ladění řešení služby SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md) a [ověřování a ladění kódu služby SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md).

**Omezení**

Následující omezení platí při opětovném cílení testovacích projektů, aby používaly dřívější verze .NET Framework:

- V .NET Framework 3,5 je pro projekty testů, které obsahují pouze testy jednotek, podporováno cílení na více verzí. .NET Framework 3,5 nepodporuje žádný jiný typ testu, jako je například kódované uživatelské rozhraní nebo zátěžový test. Opětovné cílení je blokováno pro jiné typy testů než testy jednotek.

- Spuštění testů, které jsou zaměřené na starší verzi .NET Framework, je podporováno pouze ve výchozím hostitelském adaptéru. Není podporován hostitelským adaptérem ASP.NET. ASP.NET aplikace, které musí běžet v kontextu vývojového serveru ASP.NET musí být kompatibilní s aktuální verzí .NET Framework.

- Podpora shromažďování dat je zakázána při spuštění testů, které podporují více cílů .NET Framework 3,5. Pokrytí kódu můžete spustit pomocí nástrojů příkazového řádku sady Visual Studio.

- Testy jednotek, které používají .NET Framework 3,5, nelze spustit na vzdáleném počítači.

- Nemůžete cílit testy jednotek na starší verze rozhraní .NET Framework.

## <a name="retargeting-for-visual-basic-unit-test-projects"></a>Změna cílení pro projekty Visual Basic jednotek testu

1. Vytvořte nový projekt Visual Basic **testování částí** .

2. V **Průzkumník řešení** v nabídce klikněte pravým tlačítkem myši na nový projekt testů Visual Basic a vyberte **vlastnosti** .

     Zobrazí se vlastnosti testovacího projektu Visual Basic.

3. Na kartě **kompilovat** klikněte na možnost **Pokročilé možnosti kompilace** , jak je znázorněno na následujícím obrázku.

     ![Pokročilé možnosti kompilace](../test/media/howtoconfigureunittest35frameworka.png)

4. Pomocí rozevíracího seznamu **Cílová architektura (všechny konfigurace)** Změňte cílovou architekturu na **.NET Framework 3,5** nebo novější verzi, jak je znázorněno v popisku B na následujícím obrázku. Nemusíte určovat verzi klienta.

     ![Rozevírací seznam&#45;cílové platformy](../test/media/howtoconfigureunitest35frameworkstepb.png)

## <a name="retargeting-for-c-unit-test-projects"></a>Změna cílení pro projekty testování částí v jazyce C#

1. Vytvoří nový projekt **testů jednotek** C#.

2. V **Průzkumník řešení** vyberte **vlastnosti** v nabídce kliknutím pravým tlačítkem myši v novém projektu testů jazyka C#.

   Zobrazí se vlastnosti testovacího projektu v jazyce C#.

3. Na kartě **aplikace** vyberte **Cílová architektura**. V rozevíracím seznamu vyberte **.NET Framework 3,5** nebo novější verzi, jak je znázorněno na následujícím obrázku. Nemusíte určovat verzi klienta.

   ![Rozevírací seznam&#45;cílové platformy](../test/media/howtoconfigureunittest35frameworkcsharp.png)

## <a name="retargeting-for-ccli-unit-test-projects"></a>Změna cílení pro projekty testování částí v jazyce C++/CLI

1. Vytvořte nový projekt **testů jednotek** C++.

   > [!WARNING]
   > Chcete-li sestavit testy jednotek C++/CLI pro předchozí verzi rozhraní .NET Framework pro Visual C++, je nutné použít odpovídající verzi sady Visual Studio.

2. V **Průzkumník řešení** vyberte **Uvolnit projekt** z nového projektu C++ test.

3. V **Průzkumník řešení** zvolte nenačtený projekt testů jazyka C++ a pak zvolte **Upravit \<project name> . vcxproj**.

   V editoru se otevře soubor *. vcxproj* .

4. Nastavte na `TargetFrameworkVersion` verzi 3,5 nebo novější verzi v `PropertyGroup` popisku `"Globals"` . Nemusíte určovat verzi klienta:

    ```xml
    <PropertyGroup Label="Globals">
        <TargetName>DefaultTest</TargetName>
        <ProjectTypes>{3AC096D0-A1C2-E12C-1390-A8335801FDAB};{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}</ProjectTypes>
        <ProjectGUID>{CE16D77A-E364-4ACD-948B-1EB6218B0EA3}</ProjectGUID>
        <TargetFrameworkVersion>3.5</TargetFrameworkVersion>
        <Keyword>ManagedCProj</Keyword>
        <RootNamespace>CPP_Test</RootNamespace>
      </PropertyGroup>
    ```

5. Uložte a zavřete soubor *. vcxproj* .

6. V **Průzkumník řešení** zvolte v nabídce kliknutím pravým tlačítkem myši v novém projektu testů jazyka C++ možnost vybrat **znovu načíst projekt** .

## <a name="see-also"></a>Viz také

- [Vytváření řešení pro SharePoint](../sharepoint/create-sharepoint-solutions.md)
- [Sestavování a ladění řešení služby SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Dialogové okno Upřesnit nastavení kompilátoru (Visual Basic)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)

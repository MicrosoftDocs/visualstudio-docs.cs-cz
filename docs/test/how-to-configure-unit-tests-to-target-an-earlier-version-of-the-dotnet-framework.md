---
title: Testy jednotek cílit na dřívější verzi rozhraní .NET Framework
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
author: mikejo5000
ms.openlocfilehash: 32380ddc802d1421f39d4920073fc277876cfef4
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596018"
---
# <a name="how-to-configure-unit-tests-to-target-an-earlier-version-of-the-net-framework"></a>Postupy: Konfigurace testů jednotek pro cílení na dřívější verzi rozhraní .NET Framework

Když vytvoříte projekt testů v sadě Microsoft Visual Studio, nejnovější verzi rozhraní .NET Framework ve výchozím nastavení jako cíl. Navíc pokud provedete upgrade projektů testů z předchozích verzí sady Visual Studio, upgradováním cílit na nejnovější verzi rozhraní .NET Framework. Úpravou vlastností projektu můžete explicitně znovu cílit projekt na starší verze rozhraní .NET Framework.

Jednotky můžete vytvořit projekty testů, které cílí určité verze rozhraní .NET Framework. Cílová verze musí být 3.5 nebo novější a nemůže být verze klienta. Visual Studio umožňuje následující základní podporu pro testování částí, které cílí určité verze:

- Můžete vytvářet projekty testů jednotek a cílit na konkrétní verzi rozhraní .NET Framework.

- Můžete spustit testy jednotek, které se zaměřují na konkrétní verzi rozhraní .NET Framework ze sady Visual Studio na svém místním počítači.

- Můžete spustit testy jednotek, které se zaměřují na konkrétní verzi rozhraní .NET Framework pomocí *MSTest.exe* z příkazového řádku.

- Jednotkové testy můžete spustit na agentu sestavení jako součást sestavení.

**Testování aplikací pro SharePoint**

Funkce uvedené výše také umožňují zápis testů jednotek a testů integrace pro aplikace SharePoint pomocí sady Visual Studio. Další informace o tom, jak vyvíjet aplikace služby SharePoint pomocí sady Visual Studio najdete v tématu [řešení služby SharePoint vytvořit](../sharepoint/create-sharepoint-solutions.md), [sestavení a ladění řešení služby SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md) a [ověřte a ladění Kód aplikace SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md).

**Omezení**

Když míříte znovu používat starší verze rozhraní .NET Framework testovací projekty se vztahují následující omezení:

- V rozhraní .NET Framework 3.5 cílení na více verzí se podporuje pro projekty testů, které obsahují pouze jednotkové testy. Rozhraní .NET Framework 3.5 nepodporuje jakýkoli jiný typ testu, jako je například programový test uživatelského rozhraní nebo zatížení. Změnu cíle je blokované pro typy testů kromě testů jednotek.

- Spuštění testů, které cílí na starší verzi rozhraní .NET Framework je podporováno pouze v výchozího hostitelského adaptéru. Nepodporuje se v adaptéru hostitele technologie ASP.NET. Aplikace ASP.NET, které je nutné spustit v kontextu serveru ASP.NET Development Server musí být kompatibilní s aktuální verzí rozhraní .NET Framework.

- Podpora shromažďování dat je zakázané při spuštění testů, které podporují cílení na více verzí rozhraní .NET Framework 3.5. Spustit pokrytí kódu pomocí nástroje příkazového řádku sady Visual Studio.

- Na vzdáleném počítači nelze spustit testy jednotek, které používají rozhraní .NET Framework 3.5.

- Nelze cílit testů jednotek pro starší verze klienta architektury.

## <a name="retargeting-for-visual-basic-unit-test-projects"></a>Změna cílení pro projekty Visual Basic jednotek testu

1. Vytvořte nový projekt Visual Basic **testování částí** .

2. V **Průzkumník řešení**v nabídce klikněte pravým tlačítkem myši na nový projekt testů Visual Basic a vyberte **vlastnosti** .

     Zobrazí se vlastnosti pro testovací projekt jazyka Visual Basic.

3. Na **kompilaci** kartě **Upřesnit možnosti kompilace** jak je znázorněno na následujícím obrázku.

     ![Možnosti rozšířené kompilace](../test/media/howtoconfigureunittest35frameworka.png)

4. Použití **cílového rozhraní (všechny konfigurace)** rozevíracího seznamu, chcete-li změnit cílovou architekturu na **rozhraní .NET Framework 3.5** nebo novější verze, jak je znázorněno na následujícím obrázku popisku B. Neměli zadejte verzi klienta.

     ![Cílové rozhraní framework rozevírací&#45;seznamu dolů](../test/media/howtoconfigureunitest35frameworkstepb.png)

## <a name="retargeting-for-c-unit-test-projects"></a>Změna cílení na C# projekty testů jednotek

1. Vytvořte nový C# projekt **testů jednotek** .

2. V **Průzkumník řešení**v nabídce kliknutím pravým tlačítkem myši v novém C# testovacím projektu vyberte možnost Vlastnosti.

   Zobrazí se vlastnosti C# testovacího projektu.

3. Na **aplikace** kartě **Cílová architektura**. V rozevíracím seznamu zvolte **rozhraní .NET Framework 3.5** nebo novější verze, jak je znázorněno na následujícím obrázku. Neměli zadejte verzi klienta.

   ![Cílové rozhraní framework rozevírací&#45;seznamu dolů](../test/media/howtoconfigureunittest35frameworkcsharp.png)

## <a name="retargeting-for-ccli-unit-test-projects"></a>Změna cílení na C++projekty pro testování jednotek/CLI

1. Vytvořte nový C++ projekt **testů jednotek** .

   > [!WARNING]
   > K sestavení C + +/ CLI částí pro předchozí verze rozhraní .NET Framework pro aplikaci Visual C++, je nutné použít odpovídající verzi sady Visual Studio.

2. V **Průzkumník řešení**klikněte na možnost **Uvolnit projekt** z nového C++ testovacího projektu.

3. V **Průzkumník řešení**zvolte nenačtený C++ testovací projekt a pak zvolte **Upravit \<název projektu >. vcxproj**.

   *.Vcxproj* soubor se otevře v editoru.

4. Nastavte `TargetFrameworkVersion` verze 3.5 nebo novější verze v `PropertyGroup` označené `"Globals"`. Byste neměli zadávat jako verze klienta:

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

5. Uložte a zavřete *.vcxproj* souboru.

6. V **Průzkumník řešení**zvolte v nabídce kliknutím pravým tlačítkem v novém C++ testovacím projektu vybrat **znovu načíst projekt** .

## <a name="see-also"></a>Viz také:

- [Vytvoření řešení služby SharePoint](../sharepoint/create-sharepoint-solutions.md)
- [Sestavování a ladění řešení služby SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Dialogové okno nastavení pokročilé kompilátoru (Visual Basic)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)

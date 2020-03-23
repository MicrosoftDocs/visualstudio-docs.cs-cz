---
title: Testování částí Cílová starší verze rozhraní .NET Framework
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
author: mikejo5000
ms.openlocfilehash: 32380ddc802d1421f39d4920073fc277876cfef4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596018"
---
# <a name="how-to-configure-unit-tests-to-target-an-earlier-version-of-the-net-framework"></a>Postup: Konfigurace testů částí za účelem cílení na starší verzi rozhraní .NET Framework

Při vytváření testovacího projektu v aplikaci Microsoft Visual Studio je nejnovější verze rozhraní .NET Framework ve výchozím nastavení nastavena jako cíl. Navíc pokud upgradujete testovací projekty z předchozích verzí sady Visual Studio, jsou upgradovány tak, aby cílily na nejnovější verzi rozhraní .NET Framework. Úpravou vlastností projektu můžete explicitně znovu cílit projekt na dřívější verze rozhraní .NET Framework.

Můžete vytvořit projekty testování částí, které cílí na konkrétní verze rozhraní .NET Framework. Cílová verze musí být 3.5 nebo novější a nemůže být klientskou verzí. Visual Studio umožňuje následující základní podporu pro testování částí, které cílí na konkrétní verze:

- Můžete vytvořit projekty testování částí a cílit je na konkrétní verzi rozhraní .NET Framework.

- Můžete spustit testy částí, které cílí na konkrétní verzi rozhraní .NET Framework z visual studia v místním počítači.

- Testy částí, které cílí na určitou verzi rozhraní .NET Framework, můžete spustit pomocí programu *MSTest.exe* z příkazového řádku.

- Můžete spustit testy částí na agenta sestavení jako součást sestavení.

**Testování aplikací služby SharePoint**

Výše uvedené funkce také umožňují psát testy částí a testy integrace pro aplikace SharePoint pomocí sady Visual Studio. Další informace o vývoji sharepointových aplikací pomocí Visual Studia najdete v [tématu Vytváření sharepointových řešení](../sharepoint/create-sharepoint-solutions.md), [Vytváření a ladění sharepointových řešení](../sharepoint/building-and-debugging-sharepoint-solutions.md) a Ověřování a ladění kódu [SharePointu](../sharepoint/verifying-and-debugging-sharepoint-code.md).

**Omezení**

Následující omezení platí při opětovném zacílení testovacích projektů na použití dřívějších verzí rozhraní .NET Framework:

- V rozhraní .NET Framework 3.5 je podporováno vícenásobné cílení pro testovací projekty, které obsahují pouze testy částí. Rozhraní .NET Framework 3.5 nepodporuje žádný jiný typ testu, jako je například kódované rozhraní uI nebo zátěžový test. Opětovné cílení je blokováno pro typy testů než testy částí.

- Provádění testů, které jsou zaměřeny na starší verzi rozhraní .NET Framework, je podporováno pouze ve výchozím hostitelském adaptéru. Není podporován v ASP.NET hostitelském adaptéru. ASP.NET aplikace, které musí být spuštěny v kontextu ASP.NET vývojového serveru, musí být kompatibilní s aktuální verzí rozhraní .NET Framework.

- Podpora shromažďování dat je zakázána při spuštění testů, které podporují multitargeting rozhraní .NET Framework 3.5. Pokrytí kódu můžete spustit pomocí nástrojů příkazového řádku sady Visual Studio.

- Testy částí, které používají rozhraní .NET Framework 3.5 nelze spustit ve vzdáleném počítači.

- Nelze cílit testování částí na starší klientské verze rozhraní.

## <a name="retargeting-for-visual-basic-unit-test-projects"></a>Opětovné zacílení pro projekty testování částí jazyka Visual Basic

1. Vytvořte nový projekt **projektu testování částí jazyka** Visual Basic.

2. V **Průzkumníku řešení**zvolte **Vlastnosti** z nabídky po kliknutí pravým tlačítkem myši v novém testovacím projektu jazyka Visual Basic.

     Zobrazí se vlastnosti testovacího projektu jazyka Visual Basic.

3. Na kartě **Kompilace** zvolte **Upřesnit možnosti kompilace,** jak je znázorněno na následujícím obrázku.

     ![Rozšířené možnosti kompilace](../test/media/howtoconfigureunittest35frameworka.png)

4. Pomocí rozevíracího seznamu **Cílové rozhraní (všechny konfigurace)** můžete změnit cílovou architekturu na **rozhraní .NET Framework 3.5** nebo novější verzi, jak je znázorněno na popisku B na následujícím obrázku. Neměli byste zadávat verzi klienta.

     ![Cílový rámec drop&#45;seznamu dolů](../test/media/howtoconfigureunitest35frameworkstepb.png)

## <a name="retargeting-for-c-unit-test-projects"></a>Opětovné zacílení pro projekty testování částí jazyka C#

1. Vytvořte nový projekt **projektu testování částí c#**

2. V **Průzkumníku řešení**zvolte **Vlastnosti** z nabídky po kliknutí pravým tlačítkem myši v novém testovacím projektu jazyka C#.

   Vlastnosti pro testovací projekt jazyka C# jsou zobrazeny.

3. Na kartě **Aplikace** zvolte **Cílový rámec**. V rozevíracím seznamu zvolte **rozhraní .NET Framework 3.5** nebo novější verzi, jak je znázorněno na následujícím obrázku. Neměli byste zadávat verzi klienta.

   ![Cílový rámec drop&#45;seznamu dolů](../test/media/howtoconfigureunittest35frameworkcsharp.png)

## <a name="retargeting-for-ccli-unit-test-projects"></a>Retargeting pro projekty testování částí C++/CLI

1. Vytvořte nový projekt **projektu testování částí c++.**

   > [!WARNING]
   > Chcete-li vytvořit testy částí C++/CLI pro předchozí verzi rozhraní .NET framework pro visual c++, musíte použít odpovídající verzi sady Visual Studio.

2. V **Průzkumníku řešení**zvolte **Uvolnit Project** z nového testovacího projektu C++.

3. V **Průzkumníku řešení**zvolte nezatížený testovací projekt C++ a pak zvolte **Upravit \<název projektu>.vcxproj**.

   V editoru se otevře soubor *.vcxproj.*

4. Nastavte `TargetFrameworkVersion` verzi 3.5 nebo novější verzi `PropertyGroup` v `"Globals"`označeném . Neměli byste zadávat verzi klienta:

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

5. Uložte a zavřete soubor *.vcxproj.*

6. V **Průzkumníku řešení**zvolte **Znovu načíst Project** z nabídky po kliknutí pravým tlačítkem myši v novém testovacím projektu c++.

## <a name="see-also"></a>Viz také

- [Vytvoření řešení SharePointu](../sharepoint/create-sharepoint-solutions.md)
- [Vytváření a ladění řešení SharePointu](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Dialogové okno Upřesnit nastavení kompilátoru (Visual Basic)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)

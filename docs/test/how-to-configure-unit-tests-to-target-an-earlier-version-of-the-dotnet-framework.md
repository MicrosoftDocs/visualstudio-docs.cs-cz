---
title: Testování částí cílí na starší verzi .NET Framework
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
author: jillre
ms.openlocfilehash: 32f34eb9af74f8db06cfc6910db83806383ae3be
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643608"
---
# <a name="how-to-configure-unit-tests-to-target-an-earlier-version-of-the-net-framework"></a>Postupy: konfigurace testů jednotek pro cílení na dřívější verzi .NET Framework

Při vytváření testovacího projektu v Microsoft Visual Studio je nejnovější verze .NET Framework ve výchozím nastavení nastavena jako cíl. Kromě toho, pokud upgradujete testovací projekty z předchozích verzí sady Visual Studio, jsou upgradovány na cílení na nejnovější verzi .NET Framework. Úpravou vlastností projektu můžete explicitně změnit cíl projektu na dřívější verze .NET Framework.

Můžete vytvořit projekty testování částí, které cílí na konkrétní verze .NET Framework. Cílová verze musí být 3,5 nebo vyšší a nemůže se jednat o verzi klienta. Visual Studio umožňuje následující základní podporu pro testování částí, které cílí na konkrétní verze:

- Můžete vytvořit projekty testování částí a cílit je na konkrétní verzi .NET Framework.

- Můžete spustit testy jednotek, které cílí na konkrétní verzi .NET Framework ze sady Visual Studio na místním počítači.

- Můžete spustit testy jednotek, které cílí na konkrétní verzi .NET Framework pomocí nástroje *MSTest. exe* z příkazového řádku.

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

2. V **Průzkumník řešení**v nabídce klikněte pravým tlačítkem myši na nový projekt testů Visual Basic a vyberte **vlastnosti** .

     Zobrazí se vlastnosti testovacího projektu Visual Basic.

3. Na kartě **kompilovat** klikněte na možnost **Pokročilé možnosti kompilace** , jak je znázorněno na následujícím obrázku.

     ![Pokročilé možnosti kompilace](../test/media/howtoconfigureunittest35frameworka.png)

4. Pomocí rozevíracího seznamu **Cílová architektura (všechny konfigurace)** Změňte cílovou architekturu na **.NET Framework 3,5** nebo novější verzi, jak je znázorněno v popisku B na následujícím obrázku. Nemusíte určovat verzi klienta.

     ![Rozevírací&#45;seznam cílového rozhraní Framework](../test/media/howtoconfigureunitest35frameworkstepb.png)

## <a name="retargeting-for-c-unit-test-projects"></a>Změna cílení na C# projekty testů jednotek

1. Vytvořte nový C# projekt **testů jednotek** .

2. V **Průzkumník řešení**v nabídce kliknutím pravým tlačítkem myši v novém C# testovacím projektu vyberte možnost Vlastnosti.

   Zobrazí se vlastnosti C# testovacího projektu.

3. Na kartě **aplikace** vyberte **Cílová architektura**. V rozevíracím seznamu vyberte **.NET Framework 3,5** nebo novější verzi, jak je znázorněno na následujícím obrázku. Nemusíte určovat verzi klienta.

   ![Rozevírací&#45;seznam cílového rozhraní Framework](../test/media/howtoconfigureunittest35frameworkcsharp.png)

## <a name="retargeting-for-ccli-unit-test-projects"></a>Změna cílení na C++projekty pro testování jednotek/CLI

1. Vytvořte nový C++ projekt **testů jednotek** .

   > [!WARNING]
   > Chcete- C++li vytvořit testy jednotek/CLI pro předchozí verzi rozhraní .NET Framework pro Visual C++, je nutné použít odpovídající verzi sady Visual Studio.

2. V **Průzkumník řešení**klikněte na možnost **Uvolnit projekt** z nového C++ testovacího projektu.

3. V **Průzkumník řešení**zvolte nenačtený C++ testovací projekt a pak zvolte **Upravit \<project název >. vcxproj**.

   V editoru se otevře soubor *. vcxproj* .

4. Nastavte `TargetFrameworkVersion` na verzi 3,5 nebo novější v `PropertyGroup` s popiskem `"Globals"`. Nemusíte určovat verzi klienta:

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

6. V **Průzkumník řešení**zvolte v nabídce kliknutím pravým tlačítkem v novém C++ testovacím projektu vybrat **znovu načíst projekt** .

## <a name="see-also"></a>Viz také:

- [Vytváření řešení pro SharePoint](../sharepoint/create-sharepoint-solutions.md)
- [Sestavování a ladění řešení služby SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Dialogové okno Upřesnit nastavení kompilátoru (Visual Basic)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)

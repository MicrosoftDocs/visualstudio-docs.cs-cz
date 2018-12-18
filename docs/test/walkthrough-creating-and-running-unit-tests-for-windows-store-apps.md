---
title: Vytváření a spouštění testů jednotek pro aplikace pro UPW
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: gewarren
manager: douge
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: 66a107fbd738bc26fdf608223ff43f958754e3ae
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065297"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>Návod: Vytváření a spouštění testů jednotek pro aplikace pro UPW

Visual Studio zahrnuje podporu pro testování částí aplikací pro univerzální platformu Windows (UPW). Obsahuje šablony projektů testů jednotek pro jazyk Visual C#, Visual Basic a Visual C++.

> [!TIP]
> Další informace o vývoji aplikací pro UWP, naleznete v tématu [Začínáme s aplikací pro UWP](/windows/uwp/get-started/).

Následující postupy popisují postup vytvoření, spuštění a ladění testů jednotek pro aplikace pro UPW.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>Vytvořte projekt testu jednotek pro aplikace pro UPW

1.  Z **souboru** nabídce zvolte **nový projekt**.

     **Nový projekt** zobrazí se dialogové okno.

2.  V části šablony vyberte programovací jazyk, který chcete vytvořit testy jednotek v a klikněte na tlačítko přidružených jednotek Windows Universal testu knihovny. Například zvolte **Visual C#** , klikněte na tlačítko **Windows Universal**a klikněte na tlačítko **knihovna testu jednotek (Universal Windows)**.

3.  (Volitelné) V **název** textového pole zadejte název, kterou chcete použít pro projekt.

4.  (Volitelné) Upravit cestu, kde chcete vytvořit projekt tak, že ho zadáte **umístění** textové pole, nebo výběrem **Procházet** tlačítko.

5.  (Volitelné) V **řešení** textového pole s názvem, zadejte název, který chcete použít pro vaše řešení.

6.  Nechte **vytvořit adresář pro řešení** možnost vybranou a stiskněte tlačítko **OK** tlačítko.

     ![Knihovna testu jednotek míru](../test/media/unit_test_win8_1.png)

     **Průzkumník řešení** se vyplní projekt testování částí UPW a editor kódu zobrazí výchozí test jednotky s názvem UnitTest1.

     ![Nový projekt testu jednotky míru](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Úprava souboru manifestu aplikace UPW projekt testu jednotek

1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši *Package.appxmanifest* soubor a zvolte **otevřít**.

     **Manifest Designer** zobrazení úprav.

2.  V **Manifest Designer**, zvolte **možnosti** kartu.

3.  V seznamu v části **možnosti**, vyberte možnosti, které potřebujete otestovat u vaší jednotky a kód, který je testován mít. Vyberte například **Internet** zaškrtávací políčko, pokud test jednotky a kód je testování musí mít přístup k Internetu.

    > [!NOTE]
    > Funkce, které vyberete by měl obsahovat pouze funkce, které jsou nezbytné pro správnou funkci testu jednotky.

     ![Manifest testu jednotek](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>Programování testu jednotek pro aplikace pro UPW

V **Editor kódu**, upravte test jednotky a přidejte kontrolní výrazy a logiku nezbytnou pro test.

## <a name="run-unit-tests"></a>Spouštění testů jednotek

### <a name="to-build-the-solution-and-run-the-unit-test-using-test-explorer"></a>Sestavte řešení a spuštění testování částí pomocí Průzkumníka testů

1.  Na **testovací** nabídce zvolte **Windows**a klikněte na tlačítko **Průzkumník testů**.

     **Průzkumník testů** zobrazí bez uvedení vašeho testu.

2.  Z **sestavení** nabídce zvolte **sestavit řešení**.

     Jednotkový test je nyní obsažena.

    > [!NOTE]
    > Třeba vytvořit řešení Chcete-li aktualizovat seznam testů jednotek v Průzkumníku testů.

3.  V **Průzkumníka testů**, vyberte test jednotky, které jste vytvořili.

    > [!TIP]
    > Průzkumník testů obsahuje odkaz na zdrojový kód vedle **zdroj:**.

4.  Zvolte **spustit všechny**.

     ![Průzkumník testů jednotek &#45; spustit test jednotek](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

    > [!TIP]
    > Vyberte jeden nebo více jednotek testů uvedených v Průzkumníkovi, klepněte pravým tlačítkem myši a zvolte **spustit vybrané testy**.
    >
    > Kromě toho můžete také **ladit vybrané testy**, **Otevřít testovací**a použít **vlastnosti** možnost.
    >
    > ![Průzkumník testů jednotek &#45; uni test kontextové nabídky](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

    Test jednotky probíhá. Po dokončení **Průzkumníka testů** svat testu, uplynulý čas a získáte odkaz na zdroj.

    ![Průzkumník testů jednotek &#45; test byl dokončen](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Viz také:

- [Testování aplikací pro UPW pomocí sady Visual Studio](../test/testing-store-apps-with-visual-studio.md)
- [Sestavení a testování aplikací pro UPW](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)

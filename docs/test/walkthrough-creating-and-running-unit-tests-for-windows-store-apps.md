---
title: Vytváření a spouštění testů jednotek pro aplikace pro UPW
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 4109f743caf7c62450591f78e90b92113fc4107e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568877"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>Návod: Vytváření a spouštění testů jednotek pro aplikace pro UPW

Visual Studio zahrnuje podporu pro testování částí aplikací pro univerzální platformu Windows (UPW). Visual Studio poskytuje šablony projektů testů jednotek pro C#, Visual Basic a C++.

> [!TIP]
> Další informace o vývoji aplikací pro UWP, naleznete v tématu [Začínáme s aplikací pro UWP](/windows/uwp/get-started/).

Následující postupy popisují kroky pro vytvoření, spuštění a ladění testování částí aplikace pro UWP.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>Vytvořte projekt testu jednotek pro aplikace pro UPW

::: moniker range=">=vs-2019"

1. Otevřít Visual Studio. V okně Start vyberte možnost **vytvořit nový projekt**.

2. Do vyhledávacího pole na stránce **vytvořit nový projekt** zadejte **Test jednotky**.

   Seznam šablon filtruje hodnoty pro testování částí.

3. Vyberte šablonu **aplikace pro testování částí (Universal Windows)** pro C# nebo Visual Basic a pak vyberte **Další**.

   ![Vytvoření nové aplikace pro testování jednotek UWP v aplikaci Visual Studio](media/vs-2019/new-uwp-unit-test-app.png)

4. Volitelně můžete změnit název projektu nebo řešení a jeho umístění a pak vybrat **vytvořit**.

5. Volitelně můžete změnit cíl a minimální verzi platformy a pak vybrat **OK**.

Po dokončení těchto kroků se vytvoří projekt testování částí a zobrazí se v Průzkumník řešení.

![Projekt testu jednotek UWP v Průzkumník řešení](media/vs-2019/uwp-unit-test-project-solution-explorer.png)

::: moniker-end

::: moniker range="vs-2017"

1. Z **souboru** nabídce zvolte **nový projekt**.

   **Nový projekt** zobrazí se dialogové okno.

2. V části šablony vyberte programovací jazyk, který chcete vytvořit testy jednotek v a klikněte na tlačítko přidružených jednotek Windows Universal testu knihovny. Například zvolte **Visual C#** , klikněte na tlačítko **Windows Universal**a klikněte na tlačítko **knihovna testu jednotek (Universal Windows)** .

3. (Volitelné) V **název** textového pole zadejte název, kterou chcete použít pro projekt.

4. (Volitelné) Upravit cestu, kde chcete vytvořit projekt tak, že ho zadáte **umístění** textové pole, nebo výběrem **Procházet** tlačítko.

5. (Volitelné) V **řešení** textového pole s názvem, zadejte název, který chcete použít pro vaše řešení.

6. Nechte **vytvořit adresář pro řešení** možnost vybranou a stiskněte tlačítko **OK** tlačítko.

   ![Knihovna testu jednotek míru](../test/media/unit_test_win8_1.png)

   **Průzkumník řešení** se vyplní projekt testování částí UPW a editor kódu zobrazí výchozí test jednotky s názvem UnitTest1.

   ![Nový projekt testu jednotky míru](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

::: moniker-end

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Úprava souboru manifestu aplikace UPW projekt testu jednotek

1. V **Průzkumníku řešení**, klikněte pravým tlačítkem myši *Package.appxmanifest* soubor a zvolte **otevřít**.

2. V **Manifest Designer**, zvolte **možnosti** kartu.

3. V seznamu v části **možnosti**, vyberte možnosti, které potřebujete otestovat u vaší jednotky a kód, který je testován mít. Vyberte například **Internet** zaškrtávací políčko, pokud test jednotky a kód je testování musí mít přístup k Internetu.

   > [!NOTE]
   > Funkce, které vyberete by měl obsahovat pouze funkce, které jsou nezbytné pro správnou funkci testu jednotky.

   ![Manifest testu jednotek](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>Programování testu jednotek pro aplikace pro UPW

V editoru kódu upravte test jednotky a přidejte výrazy a logiku vyžadované pro váš test.

## <a name="run-unit-tests"></a>Spuštění testů jednotek

Chcete-li sestavit řešení a spustit test jednotky pomocí Průzkumníka testů:

1. Na **testovací** nabídce zvolte **Windows**a klikněte na tlačítko **Průzkumník testů**.

2. Z **sestavení** nabídce zvolte **sestavit řešení**.

   Test jednotek je nyní zobrazen v Průzkumníku testů.

   > [!NOTE]
   > Třeba vytvořit řešení Chcete-li aktualizovat seznam testů jednotek v Průzkumníku testů.

3. V **Průzkumníka testů**, vyberte test jednotky, které jste vytvořili.

4. Zvolte **spustit všechny**.

   ![Průzkumník testů jednotek &#45; spustit test jednotek](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

   > [!TIP]
   > Můžete vybrat jednu nebo více testů jednotek uvedených v Průzkumníku testů a potom kliknout pravým tlačítkem a vybrat možnost **Spustit vybrané testy**.
   >
   > Kromě toho můžete také **ladit vybrané testy**, **Otevřít testovací**a použít **vlastnosti** možnost.
   >
   > ![Místní nabídka testu &#45; jednotek Průzkumníka testu jednotek](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

   Test jednotky probíhá. Po dokončení zobrazí Průzkumník testů stav testu a uplynulý čas a poskytne odkaz na zdroj.

   ![Průzkumník testů jednotek &#45; test byl dokončen](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Viz také:

- [Testování aplikací pro UPW pomocí sady Visual Studio](../test/unit-test-your-code.md)
- [Sestavení a testování aplikací pro UPW](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)

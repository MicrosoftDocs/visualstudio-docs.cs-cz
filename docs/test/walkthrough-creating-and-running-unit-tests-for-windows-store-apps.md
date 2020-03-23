---
title: Vytváření a spouštění testů jednotek pro aplikace UPW
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568877"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>Návod: Vytváření a spouštění testů jednotek pro aplikace pro UPW

Visual Studio obsahuje podporu pro testování částí univerzální platformy Windows (UPW) aplikace. Visual Studio poskytuje šablony projektu testování částí pro C#, Visual Basic a C++.

> [!TIP]
> Další informace o vývoji aplikací UPW najdete [v tématu Začínáme s aplikacemi UPW](/windows/uwp/get-started/).

Následující postupy popisují kroky k vytvoření, spuštění a ladění testů částí pro aplikaci UPW.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>Vytvoření projektu testování částí pro aplikaci UPW

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio. V počátečním okně zvolte **Vytvořit nový projekt**.

2. Do vyhledávacího pole na stránce **Vytvořit nový projekt** zadejte test **částí**.

   Seznam šablon filtruje pro testování částí.

3. Vyberte šablonu **Testování částí (Universal Windows)** pro C# nebo Visual Basic a pak vyberte **Další**.

   ![Vytvoření nové aplikace pro testování částí JEDNOTKY UPW v sadě Visual Studio](media/vs-2019/new-uwp-unit-test-app.png)

4. Volitelně změňte název a umístění projektu nebo řešení a pak vyberte **Vytvořit**.

5. Volitelně změňte cílové a minimální verze platformy a pak vyberte **OK**.

Po dokončení těchto kroků je vytvořen projekt testování částí a zobrazí se v Průzkumníku řešení.

![Projekt testování částí UWP v Průzkumníku řešení](media/vs-2019/uwp-unit-test-project-solution-explorer.png)

::: moniker-end

::: moniker range="vs-2017"

1. V nabídce **Soubor** zvolte **Nový projekt**.

   Zobrazí se dialogové okno **Nový projekt.**

2. V části Šablony zvolte programovací jazyk, ve kterém chcete vytvořit testy částí, a pak zvolte přidruženou knihovnu testů univerzálních částí systému Windows. Zvolte například **Visual C#** , pak zvolte **Windows Universal**a pak zvolte Unit Test **Library (Universal Windows).**

3. (Nepovinné) Do textového pole **Název** zadejte název, který chcete pro projekt použít.

4. (Nepovinné) Upravte cestu, na kterou chcete vytvořit projekt, zadáním do textového pole **Umístění** nebo výběrem tlačítka **Procházet.**

5. (Nepovinné) Do textového pole **Název řešení** zadejte název, který chcete použít pro své řešení.

6. Ponechte vybranou volbu **Vytvořit adresář pro řešení** a zvolte tlačítko **OK.**

   ![Na míru na míru testovací knihovna](../test/media/unit_test_win8_1.png)

   **Průzkumník řešení** je naplněn projektem testování částí UWP a editor kódu zobrazí výchozí test částí s názvem UnitTest1.

   ![Nový projekt testování částí na míru](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

::: moniker-end

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Upravit soubor manifestu aplikace UPW projektu projektu testování částí

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na soubor *Package.appxmanifest* a zvolte **Otevřít**.

2. V **Návrháři manifestu**zvolte kartu **Schopnosti.**

3. V seznamu **možnosti**vyberte možnosti, které potřebujete testování částí a kód, který testování mít. Pokud například test jednotky potřebuje, zaškrtněte políčko **Internet** a kód, který testuje, musí mít možnost přístupu k Internetu.

   > [!NOTE]
   > Vybrané možnosti by měly zahrnovat pouze funkce, které jsou nezbytné pro správné fungování testu jednotky.

   ![Manifest testu jednotky](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>Kód testování částí pro aplikaci UPW

V editoru kódu upravte testování částí a přidejte nepodmíněných výrazů a logiku požadovanou pro váš test.

## <a name="run-unit-tests"></a>Spuštění testů jednotek

Chcete-li vytvořit řešení a spustit test jednotky pomocí Průzkumníka testů:

1. V nabídce **Test** zvolte **Windows**a pak zvolte **Test Explorer**.

2. V nabídce **Sestavení** zvolte **Build Solution**.

   Test částí je nyní zobrazen v Průzkumníku testů.

   > [!NOTE]
   > Je nutné vytvořit řešení aktualizovat seznam testů částí v Průzkumníku testů.

3. V **Průzkumníkovi testů**vyberte test částí, který jste vytvořili.

4. Zvolte **Spustit vše**.

   ![Průzkumník testování částí &#45; spustit test částí](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

   > [!TIP]
   > Můžete vybrat jeden nebo více testů částí uvedených v Průzkumníkovi testů a potom klepnout pravým tlačítkem myši a vybrat **možnost Spustit vybrané testy**.
   >
   > Kromě toho můžete zvolit **ladění vybrané testy**, Otevřít **test**a použít **vlastnosti** možnost.
   >
   > ![Průzkumník testování částí &#45; kontextové nabídky testování částí](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

   Spustí se test jednotky. Po dokončení Průzkumník testů zobrazí stav testu a uplynulý čas a poskytuje odkaz na zdroj.

   ![Průzkumník testů částí &#45; test dokončen](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Viz také

- [Testování aplikací UPW pomocí Sady Visual Studio](../test/unit-test-your-code.md)
- [Vytvoření a testování aplikace UPW](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)

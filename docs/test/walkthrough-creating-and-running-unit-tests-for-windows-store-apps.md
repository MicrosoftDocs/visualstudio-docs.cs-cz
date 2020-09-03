---
title: Vytváření a spouštění testů jednotek pro aplikace pro UWP
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75568877"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>Návod: Vytváření a spouštění testů jednotek pro aplikace pro UPW

Visual Studio zahrnuje podporu pro aplikace pro testování částí Univerzální platforma Windows (UWP). Visual Studio poskytuje šablony projektů testů jednotek pro C#, Visual Basic a C++.

> [!TIP]
> Další informace o vývoji aplikací pro UWP najdete v tématu [Začínáme s aplikacemi pro UWP](/windows/uwp/get-started/).

Následující postupy popisují kroky pro vytvoření, spuštění a ladění testování částí aplikace pro UWP.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>Vytvoření projektu testu jednotek pro aplikaci UWP

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio. V okně Start vyberte možnost **vytvořit nový projekt**.

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

1. V nabídce **soubor** klikněte na příkaz **Nový projekt**.

   Zobrazí se dialogové okno **Nový projekt** .

2. V části šablony zvolte programovací jazyk, ve kterém chcete vytvořit testy jednotek, a pak zvolte přidruženou knihovnu testů pro Windows Universal Unit Test. Například zvolte **Visual C#** , pak zvolte **Windows Universal**a pak zvolte **Knihovna testů jednotek (univerzální pro Windows)**.

3. Volitelné Do textového pole **název** zadejte název, který chcete použít pro projekt.

4. Volitelné Změňte cestu, kam chcete projekt vytvořit, zadáním do textového pole **umístění** nebo kliknutím na tlačítko **Procházet** .

5. Volitelné Do textového pole název **řešení** zadejte název, který chcete použít pro vaše řešení.

6. Ponechte vybranou možnost **vytvořit adresář pro řešení** a klikněte na tlačítko **OK** .

   ![Přizpůsobená knihovna testů jednotek](../test/media/unit_test_win8_1.png)

   **Průzkumník řešení** se naplní projektem testu jednotek UWP a Editor kódu zobrazí výchozí test jednotky s názvem UnitTest1.

   ![Nově přizpůsobený projekt testu jednotek](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

::: moniker-end

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Upravit soubor manifestu aplikace UWP projektu pro testování jednotek

1. V **Průzkumník řešení**klikněte pravým tlačítkem na soubor *Package. appxmanifest* a vyberte **otevřít**.

2. V **Návrháři manifestu**klikněte na kartu **Možnosti** .

3. V seznamu v části **Možnosti**vyberte možnosti, které budete potřebovat pro testování částí, a kód, který má testovat. Například zaškrtněte políčko **Internet** , pokud test jednotky potřebuje a kód, který testuje, musí mít možnost přístupu k Internetu.

   > [!NOTE]
   > Možnosti, které vyberete, by měly obsahovat pouze funkce, které jsou nezbytné pro správné fungování testu jednotky.

   ![Manifest testu jednotek](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>Kódování testování částí aplikace pro UWP

V editoru kódu upravte test jednotky a přidejte výrazy a logiku vyžadované pro váš test.

## <a name="run-unit-tests"></a>Spuštění testů jednotek

Chcete-li sestavit řešení a spustit test jednotky pomocí Průzkumníka testů:

1. V nabídce **test** zvolte možnost **Windows**a pak zvolte možnost **Průzkumník testů**.

2. V nabídce **sestavení** klikněte na příkaz **Sestavit řešení**.

   Test jednotek je nyní zobrazen v Průzkumníku testů.

   > [!NOTE]
   > Chcete-li aktualizovat seznam testů jednotek v Průzkumníku testů, je nutné sestavit řešení.

3. V **Průzkumníku testů**vyberte test jednotky, který jste vytvořili.

4. Vyberte **Spustit vše**.

   ![Průzkumník testů jednotek &#45; spustit test jednotek](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

   > [!TIP]
   > Můžete vybrat jednu nebo více testů jednotek uvedených v Průzkumníku testů a potom kliknout pravým tlačítkem a vybrat možnost **Spustit vybrané testy**.
   >
   > Kromě toho můžete zvolit **ladění vybraných testů**, **Otevřít test**a použít možnost **vlastnosti** .
   >
   > ![Průzkumník testu jednotek &#45; místní nabídka testu jednotek](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

   Test jednotek je spuštěn. Po dokončení zobrazí Průzkumník testů stav testu a uplynulý čas a poskytne odkaz na zdroj.

   ![Průzkumník testů jednotek &#45; test byl dokončen](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Viz také

- [Testování aplikací pro UWP pomocí sady Visual Studio](../test/unit-test-your-code.md)
- [Sestavování a testování aplikace pro UWP](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)

---
title: Vytvoření projektu webového výkonu a zátěžového testu
ms.date: 03/14/2018
ms.topic: quickstart
helpviewer_keywords:
- load testing, quickstart
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f186e8c10d894b98e789480046d43fc957edd8a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75566407"
---
# <a name="quickstart-create-a-load-test-project"></a>Rychlý start: Vytvoření projektu zátěžového testu

V tomto 10minutovém rychlém startu se dozvíte, jak vytvořit a spustit projekt webového výkonu a zátěžového testu v sadě Visual Studio. Zátěžové testy spouštějí testy výkonu webu nebo jednotkových testů, aby simulovaly mnoho uživatelů, kteří přistupují k serveru současně.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="software-requirements"></a>Požadavky na software

Projekty webového výkonu a zátěžového testu jsou k dispozici pouze v **edici Enterprise** sady Visual Studio.

## <a name="install-the-load-testing-component"></a>Instalace součásti zátěžového testování

Pokud ještě nemáte nainstalovanou součást nástrojů pro testování výkonu webu a zatížení, budete ji muset nainstalovat prostřednictvím Instalační služby sady Visual Studio.

1. Otevřete **Instalační službu sady Visual Studio** z nabídky **Start** systému Windows. Můžete k němu také přistupovat v sadě Visual Studio z dialogového okna nového projektu nebo výběrem **nástroje** > **získat nástroje a funkce** z řádku nabídek.

1. V **Instalační službě sady Visual Studio**zvolte kartu Jednotlivé **součásti** a přejděte dolů do části Ladění a **testování.** Vyberte **nástroje pro testování výkonu webu a načítání .**

   ![Součást nástrojů pro testování výkonu webu a zatížení](media/web-perf-load-testing-tools-component.png)

1. Zvolte **tlačítko Změnit.**

   Je nainstalována součást nástrojů pro testování výkonu webu a zátěžového testování.

## <a name="create-a-load-test-project"></a>Vytvoření projektu pro zátěžový test

V této části vytvoříme projekt zátěžového testu jazyka C#. Můžete také vytvořit projekt zátěžového testu jazyka Visual Basic, pokud dáváte přednost.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

2. Z řádku nabídek zvolte **Soubor** > **nového** > **projektu.**

   Otevře se dialogové okno **Nový projekt.**

3. V dialogovém okně **Nový projekt** rozbalte **položku Nainstalováno** a **Visual C#** a vyberte kategorii **Test.** Zvolte šablonu **projektu Výkon webu a Načíst testovací projekt.**

   ![Šablona projektu webového výkonu a zátěžového testu](media/web-perf-load-test-project-template.png)

4. Pokud nechcete použít výchozí název, zadejte název projektu a pak zvolte **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio.

2. V počátečním okně zvolte **Vytvořit nový projekt**.

3. Na stránce **Vytvořit nový projekt** zadejte do vyhledávacího pole webový **test** a pak vyberte šablonu Web Performance and Load Test **Project \[Deprecated]** pro c#. Zvolte **Další**.

4. Pokud nechcete použít výchozí název, zadejte název projektu a pak zvolte **Vytvořit**.

::: moniker-end

   Visual Studio vytvoří projekt a zobrazí soubory v **Průzkumníku řešení**. Projekt zpočátku obsahuje jeden webový testovací soubor s názvem *WebTest1.webtest*.

## <a name="add-a-load-test-to-the-project"></a>Přidání zátěžového testu do projektu

1. Z nabídky pravým tlačítkem myši nebo kontextové nabídky uzlu projektu v **Průzkumníku řešení**zvolte **Přidat** > **zátěžový test**.

   Otevře se **Průvodce novým zátěžového testem.**

1. Vyberte **možnost Místní zátěžový test** a pak zvolte **Další**. Další informace o cloudovém zátěžovém testování naleznete [zde](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts).

   ![Nový průvodce zátěžovým testem - první stránka](media/load-test-wizard-page-1.png)

1. Zvolte **Další,** chcete-li projít průvodcem, dokud nedosáhnete **přidání testů do scénáře zátěžového testu a neupravíte stránku mixu testu.** Vyberte tlačítko **Přidat**.

   Otevře se dialogové okno **Přidat testy.**

1. V **části Dostupné testy**vyberte **WebTest1**a pak zvolte šipku vpravo, kterou chcete přesunout do pole **Vybrané testy.** Zvolte tlačítko **OK.**

   ![Dialogové okno Přidat testy](media/add-tests-dialog-box.png)

1. Zpět v **Průvodci novým zátěžového testu**zvolte tlačítko **Dokončit.**

   Zátěžový test je přidán do projektu a soubor zátěžového testu se otevře v okně editoru.

## <a name="run-the-load-test"></a>Spuštění zátěžového testu

Vytvořili jsme zátěžový test, který moc nedělá, ale stejně ho spusťme.

Z nabídky po kliknutí pravým tlačítkem myši nebo kontextové nabídky zátěžového testu, který je otevřený v editoru, zvolte **Spustit zátěžový test**.

![Nabídka Spustit zátěžový test](media/run-load-test.png)

Spustí se zátěžový test. Okno **Výsledky testu** ukazuje, že probíhá test a analyzátor zátěžového testu se zobrazí v okně editoru. Po dokončení testu, což by mělo být pět minut, pokud jste přijali výchozí hodnoty, souhrn se zobrazí v editoru. Chcete-li získat různé informace o výsledcích zátěžového testu, můžete zvolit **grafy**, **tabulky**nebo **podrobnosti.**

![Okno analyzátoru zátěžového testu](media/load-test-analyzer.png)

## <a name="next-steps"></a>Další kroky

Teď, když jste vytvořili jednoduchý projekt zátěžového testu, je dalším krokem konfigurace scénářů, sad čítačů a nastavení spuštění.

> [!div class="nextstepaction"]
> [Upravit nastavení testu](edit-load-tests.md)

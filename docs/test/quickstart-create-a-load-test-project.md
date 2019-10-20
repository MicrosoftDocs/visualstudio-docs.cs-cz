---
title: Vytvořit projekt testů výkonnosti webu a zátěžového testu
ms.date: 03/14/2018
ms.topic: quickstart
helpviewer_keywords:
- load testing, quickstart
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8d74072c506c4ce48ee93b759ba24aff23aa9419
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646686"
---
# <a name="quickstart-create-a-load-test-project"></a>Rychlý start: Vytvoření projektu zátěžového testu

V tomto rychlém startu se dozvíte, jak vytvořit a spustit projekt testů výkonnosti webu a zátěžového testu v aplikaci Visual Studio. Zátěžové testy spouštějí webový výkon nebo testy jednotek pro simulaci velkého počtu uživatelů, kteří přistupují k serveru současně.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="software-requirements"></a>Požadavky na software

Projekty webového výkonu a zátěžového testu jsou k dispozici pouze v **edici Enterprise** sady Visual Studio.

## <a name="install-the-load-testing-component"></a>Instalace komponenty zátěžového testování

Pokud ještě nemáte nainstalovanou součást Performance Test Tools a nástroj pro testování zatížení, budete ji muset nainstalovat pomocí Instalační program pro Visual Studio.

1. V nabídce **Start** systému Windows otevřete **instalační program pro Visual Studio** . Můžete k němu také přistupovat v aplikaci Visual Studio z dialogového okna Nový projekt nebo výběrem **nástrojů**  > **získat nástroje a funkce** z řádku nabídek.

1. V **instalační program pro Visual Studio**klikněte na kartu **jednotlivé součásti** a přejděte dolů k části **ladění a testování** . Vyberte **Nástroje pro testování výkonu a zatížení webu**.

   ![Komponenta Performance and Load Test Tools](media/web-perf-load-testing-tools-component.png)

1. Klikněte na tlačítko **Upravit** .

   Komponenta Performance and Load Test Tools je nainstalována.

## <a name="create-a-load-test-project"></a>Vytvoření projektu pro zátěžový test

V této části vytvoříme projekt C# zátěžového testu. V případě potřeby můžete také vytvořit projekt Visual Basic zátěžového testu.

::: moniker range="vs-2017"

1. Otevřete Visual Studio.

2. Z řádku nabídek vyberte **soubor** > **Nový** > **projekt** .

   Otevře se dialogové okno **Nový projekt** .

3. V dialogovém okně **Nový projekt** rozbalte položku **nainstalované** a **vizuál C#** a pak vyberte kategorii **test** . Vyberte šablonu **projekt webového výkonu a zátěžového testu** .

   ![Šablona projektu testování výkonu webu a zátěžového testu](media/web-perf-load-test-project-template.png)

4. Zadejte název projektu, pokud nechcete použít výchozí název, a pak zvolte **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete Visual Studio.

2. V okně Start vyberte možnost **vytvořit nový projekt**.

3. Na stránce **vytvořit nový projekt** zadejte do vyhledávacího pole **webový test** a potom vyberte šablonu **výkon webu a zátěžový test \[Deprecated]** pro C#. Klikněte na tlačítko **Další**.

4. Zadejte název projektu, pokud nechcete použít výchozí název, a pak zvolte **vytvořit**.

::: moniker-end

   Visual Studio vytvoří projekt a zobrazí soubory v **Průzkumník řešení**. Projekt zpočátku obsahuje jeden soubor webového testu s názvem *WebTest1. webtest*.

## <a name="add-a-load-test-to-the-project"></a>Přidat zátěžový test do projektu

1. V nabídce klepněte pravým tlačítkem myši nebo v kontextové nabídce uzlu projektu v **Průzkumník řešení**vyberte možnost **Přidat**  > **zátěžový test**.

   Otevře se **nový Průvodce zátěžovým testem** .

1. Vyberte možnost místní **zátěžový test** a klikněte na tlačítko **Další**. Další informace o cloudovém zátěžovém testování najdete [tady](/azure/devops/test/load-test/get-started-simple-cloud-load-test?view=vsts).

   ![Průvodce novým zátěžovým testem – první stránka](media/load-test-wizard-page-1.png)

1. Klikněte na tlačítko **Další** a postupujte podle pokynů průvodce, dokud se nedostanete do **scénáře zátěžového testu a upravíte stránku s kombinací testů** . Klikněte na tlačítko **Přidat** .

   Otevře se dialogové okno **Přidat testy** .

1. V části **Dostupné testy**vyberte **WebTest1**a pak zvolte šipku doprava pro přesunutí do pole **vybrané testy** . Klikněte na tlačítko **OK** .

   ![Přidat testy – dialogové okno](media/add-tests-dialog-box.png)

1. Zpět v **novém Průvodce zátěžovým testem**klikněte na tlačítko **Dokončit** .

   Zátěžový test je přidán do projektu a soubor zátěžového testu se otevře v okně editoru.

## <a name="run-the-load-test"></a>Spustit zátěžový test

Vytvořili jsme zátěžový test, který nefunguje hodně, ale pojďme ho přesto spustit.

V nabídce kliknutím pravým tlačítkem nebo v kontextové nabídce pro zátěžový test, který je otevřen v editoru, vyberte možnost **spustit zátěžový test**.

![Nabídka spustit zátěžový test](media/run-load-test.png)

Zátěžový test začíná běžet. Okno **výsledky testů** ukazuje, že probíhá test, a v okně editoru je zobrazen analyzátor zátěžového testu. Po dokončení testu, který by měl být pět minut, pokud jste přijali výchozí hodnoty, zobrazí se v editoru souhrn. Můžete zvolit **grafy**, **tabulky**nebo **Podrobnosti** a získat tak různé informace o výsledcích zátěžového testu.

![Okno analyzátoru zátěžového testu](media/load-test-analyzer.png)

## <a name="next-steps"></a>Další kroky

Teď, když jste vytvořili jednoduchý projekt zátěžového testu, je dalším krokem konfigurace scénářů, sad čítačů a nastavení spuštění.

> [!div class="nextstepaction"]
> [Upravit nastavení testu](edit-load-tests.md)

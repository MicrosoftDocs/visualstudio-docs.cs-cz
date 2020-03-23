---
title: Vytvoření projektu testování částí
ms.date: 01/29/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 313083090c94c94f4e196e87f3bf6cf6df36e118
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565250"
---
# <a name="create-a-unit-test-project"></a>Vytvoření projektu testování částí

Jednotkové testy často zrcadlí strukturu testovaného kódu. Například projekt testování částí by být vytvořen pro každý projekt kódu v produktu. Testovací projekt může být ve stejném řešení jako produkční kód, nebo může být v samostatném řešení. V řešení můžete mít více projektů testování částí.

> [!NOTE]
> Umístění testů částí pro nativní kód a strukturu testovacího projektu se může lišit od struktury popsané v tomto článku. Další informace naleznete [v tématu Zápis testů částí pro C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Vytvoření projektu testování částí

1. V nabídce **Soubor** zvolte **Nový** > **projekt**nebo stiskněte **Ctrl**+**Shift**+**N**.

::: moniker range="vs-2017"

2. V dialogovém okně **Nový projekt** rozbalte **nainstalovaný** uzel, zvolte jazyk, který chcete použít pro testovací projekt, a pak zvolte **Testovat**.

3. Vyberte šablonu projektu pro testovací architekturu, kterou chcete použít, například **MSTest Test Project** nebo **NUnit Test Project**. Pojmenujte projekt a pak zvolte **OK**.

   ![Testování šablon projektů ve Visual Studiu 2017](media/test-project-templates.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Na stránce **Vytvořit nový projekt** zadejte do vyhledávacího pole test **částí.** Vyberte šablonu projektu pro testovací architekturu, kterou chcete použít, například **MSTest Test Project** nebo **NUnit Test Project**, a pak zvolte **Další**.

   ![Testování šablon projektů ve Visual Studiu 2019](media/vs-2019/test-project-templates.png)

3. Na stránce **Konfigurovat nový projekt** zadejte název projektu a pak zvolte **Vytvořit**.

::: moniker-end

4. V projektu testování částí přidejte odkaz na testovaný kód. Chcete-li přidat odkaz na projekt kódu ve stejném řešení:

   1. Vyberte testovací projekt v **Průzkumníku řešení**.

   2. V nabídce **Projekt** zvolte **Přidat odkaz**.

   3. Ve **Správci odkazů**vyberte uzel **Řešení** v části **Projekty**. Vyberte projekt kódu, který chcete testovat, a pak vyberte **OK**.

   Pokud je kód, který chcete testovat, v jiném umístění, přečtěte si informace o přidání odkazu [v tématu Správa odkazů v projektu.](../ide/managing-references-in-a-project.md)

## <a name="next-steps"></a>Další kroky

Podívejte se na jednu z následujících částí:

**Psaní testů částí**

- [Testování částí kódu](../test/unit-test-your-code.md)

- [Zápis testů částí pro C/C++](writing-unit-tests-for-c-cpp.md)

- [Použití architektury MSTest v jednotkových testech](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Spuštění testů částí**

- [Spouštění testování částí pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)

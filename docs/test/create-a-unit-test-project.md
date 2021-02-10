---
title: Vytvoření projektu testů jednotek
description: Naučte se vytvořit projekt testování částí. Testovací projekt může být ve stejném řešení jako produkční kód, nebo může být v samostatném řešení.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 8ca3cbe82bf4253e660ce69960570e40702c5512
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942357"
---
# <a name="create-a-unit-test-project"></a>Vytvoření projektu testů jednotek

Testy jednotek často zrcadlí strukturu testovaného kódu. Například projekt testu jednotek by byl vytvořen pro každý projekt kódu v produktu. Testovací projekt může být ve stejném řešení jako produkční kód, nebo může být v samostatném řešení. V řešení můžete mít více projektů testování částí.

> [!NOTE]
> Umístění testů jednotek pro nativní kód a strukturu testovacího projektu se může lišit od struktury popsané v tomto článku. Další informace naleznete v tématu [zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Vytvoření projektu testu jednotek

1. V nabídce **soubor** klikněte na příkaz **Nový**  >  **projekt** nebo stiskněte klávesy **CTRL** + **SHIFT** + **N**.

::: moniker range="vs-2017"

2. V dialogovém okně **Nový projekt** rozbalte uzel **nainstalováno** , zvolte jazyk, který chcete použít pro testovací projekt, a pak zvolte možnost **test**.

3. Vyberte šablonu projektu pro testovací rozhraní, které chcete použít, například **projekt testů MSTest** nebo **projekt testů nunit**. Pojmenujte projekt a klikněte na **tlačítko OK**.

   ![Testování šablon projektů v aplikaci Visual Studio 2017](media/test-project-templates.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Na stránce **vytvořit nový projekt** zadejte do vyhledávacího pole text **Test jednotky** . Vyberte šablonu projektu pro testovací rozhraní, které chcete použít, například **projekt testů MSTest** nebo **projekt testů nunit** a pak zvolte možnost **Další**.

   ![Testování šablon projektů v aplikaci Visual Studio 2019](media/vs-2019/test-project-templates.png)

3. Na stránce **Konfigurace nového projektu** zadejte název projektu a pak zvolte **vytvořit**.

::: moniker-end

4. V projektu testu jednotek přidejte odkaz na testovaný kód. Chcete-li přidat odkaz na projekt kódu ve stejném řešení:

   1. Vyberte projekt testů v **Průzkumník řešení**.

   2. V nabídce **projekt** klikněte na příkaz **Přidat odkaz**.

   3. V okně **Správce odkazů** vyberte uzel **řešení** v části **projekty**. Vyberte projekt kódu, který chcete otestovat, a pak vyberte **OK**.

   Pokud je kód, který chcete testovat, v jiném umístění, přečtěte si téma [Správa odkazů v projektu](../ide/managing-references-in-a-project.md) , kde najdete informace o přidání odkazu.

## <a name="next-steps"></a>Další kroky

Podívejte se na jednu z následujících částí:

**Zápis testů jednotek**

- [Testování částí kódu](../test/unit-test-your-code.md)

- [Zápis testů částí pro C/C++](writing-unit-tests-for-c-cpp.md)

- [Použití rozhraní MSTest v testování částí](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Spouštění testů jednotek**

- [Spouštění testů částí pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)

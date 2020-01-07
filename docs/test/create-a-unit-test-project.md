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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565250"
---
# <a name="create-a-unit-test-project"></a>Vytvoření projektu testování částí

Testy jednotek často zrcadlí struktury kódu v rámci testu. Pro každého kódu projektu v produktu by například vytvořit projekt testování částí. Projekt testů může být ve stejném řešení jako produkční kód nebo může být v samostatném řešení. Můžete mít více jednotek testování projektů v řešení.

> [!NOTE]
> Umístění testů jednotek pro nativní kód a strukturu testovacího projektu se může lišit od struktury popsané v tomto článku. Další informace najdete v tématu [zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Vytvoření projektu testu jednotek

1. V nabídce **soubor** zvolte položku **Nový** > **projekt**nebo stiskněte klávesu **CTRL**+**SHIFT**+**N**.

::: moniker range="vs-2017"

2. V **nový projekt** dialogového okna rozbalte **nainstalováno** uzlu, vyberte jazyk, který chcete použít pro testovací projekt a pak zvolte **testování**.

3. Vyberte šablonu projektu pro testovací rozhraní, které chcete použít, například **projekt testů MSTest** nebo **projekt testů nunit**. Pojmenujte projekt a klikněte na **tlačítko OK**.

   ![Testování šablon projektů v aplikaci Visual Studio 2017](media/test-project-templates.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Na stránce **vytvořit nový projekt** zadejte do vyhledávacího pole text **Test jednotky** . Vyberte šablonu projektu pro testovací rozhraní, které chcete použít, například **projekt testů MSTest** nebo **projekt testů nunit**a pak zvolte možnost **Další**.

   ![Testování šablon projektů v aplikaci Visual Studio 2019](media/vs-2019/test-project-templates.png)

3. Na stránce **Konfigurace nového projektu** zadejte název projektu a pak zvolte **vytvořit**.

::: moniker-end

4. V projektu testování částí přidejte odkaz na testovaný kód. Chcete-li přidat odkaz na projekt kódu ve stejném řešení:

   1. Vyberte projekt testů v **Průzkumník řešení**.

   2. Na **projektu** nabídce zvolte **přidat odkaz**.

   3. V okně **Správce odkazů**vyberte uzel **řešení** v části **projekty**. Vyberte projekt kódu, který chcete otestovat, a pak vyberte **OK**.

   Pokud je kód, který chcete testovat, v jiném umístění, přečtěte si téma [Správa odkazů v projektu](../ide/managing-references-in-a-project.md) , kde najdete informace o přidání odkazu.

## <a name="next-steps"></a>Další kroky

Přečtěte si následující části:

**Zápis testů jednotek**

- [Testování částí kódu](../test/unit-test-your-code.md)

- [Zápis testů jednotek pro C/C++](writing-unit-tests-for-c-cpp.md)

- [Použití rozhraní MSTest při testech jednotek](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Provádění testů jednotek**

- [Spouštění testování částí pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)

---
title: Vytvořit projekt testování částí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: a608bfba-1a43-4a60-b73a-1fe53ef58098
caps.latest.revision: 10
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bfc85b0616fdf8f30732f2409a1a15040967dbb3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660642"
---
# <a name="create-a-unit-test-project"></a>Vytvoření projektu testování částí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Testy jednotek často zrcadlí strukturu testovaného kódu. Například projekt testu jednotek by byl vytvořen pro každý projekt kódu v produktu. Testovací projekt může být ve stejném řešení jako produkční kód, nebo může být v samostatném řešení. V řešení můžete mít více projektů testování částí.

> [!NOTE]
> Umístění testů jednotek pro nativní kód a strukturu testovacích projektů může být jiné než struktura, která je popsána v tomto tématu. Další informace najdete v tématu [Přidání jednotkových testů do C++ existujících aplikací](../test/unit-testing-existing-cpp-applications-with-test-explorer.md).

## <a name="to-create-a-unit-test-project"></a>Chcete-li vytvořit projekt testování částí:

1. V nabídce **soubor** klikněte na příkaz **Nový** a zvolte možnost **projekt** (klávesnice Ctrl + Shift + N).

2. V dialogovém okně Nový projekt rozbalte uzel **nainstalováno** , zvolte jazyk, který chcete použít pro testovací projekt, a pak zvolte možnost **test**.

3. Chcete-li použít jeden z rozhraní testování částí od společnosti Microsoft, v seznamu šablon projektu vyberte možnost **projekt testování částí** . V opačném případě vyberte šablonu projektu pro systém testů jednotek, který chcete použít. Chcete-li otestovat projekt účtů našeho příkladu, pojmenujte projekt AccountsTests.

4. V projektu testu jednotek přidejte odkaz na testovaný kód.  Tady je postup, jak vytvořit odkaz na projekt kódu ve stejném řešení:

    1. Vyberte projekt v Průzkumník řešení.

    2. V nabídce **projekt** vyberte možnost **Přidat odkaz...** .

    3. V dialogovém okně Správce odkazů otevřete uzel **řešení** a vyberte **projekty**. Ověřte název projektu kódu a zavřete dialogové okno.

5. Pokud je kód, který chcete testovat, v jiném umístění, přečtěte si téma [Správa odkazů v projektu](../ide/managing-references-in-a-project.md) , kde najdete informace o přidávání odkazů.

## <a name="next-steps"></a>Další kroky
 **Zápis testů jednotek**

 Podívejte se na jednu z následujících částí:

- [Zápis testů částí pro rozhraní .NET Framework s infrastrukturou pro testování částí Microsoft Unit Test Framework pro spravovaný kód](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)

- [Zápis testů jednotek pro C/C++ s infrastrukturou testování částí Microsoft Unit Testing Framework pro C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)

  **Spouštění testů jednotek**

  [Spouštění testování částí pomocí Průzkumníka testů](../test/run-unit-tests-with-test-explorer.md)

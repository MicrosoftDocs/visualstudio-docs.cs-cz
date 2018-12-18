---
title: Instalace analyzátorů Roslyn
ms.date: 08/03/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: aa0805b3cffe5a44ae2c6198c6ca2682ceca9f95
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865400"
---
# <a name="install-net-compiler-platform-analyzers"></a>Instalace analyzátorů .NET Compiler Platform

Visual Studio 2017 obsahuje základní sadu .NET Compiler Platform (*Roslyn*) analyzátory. Tyto analyzátory jsou vždy zapnuty. Můžete nainstalovat další analyzátory jako balíčky NuGet, nebo jako rozšíření sady Visual Studio v *VSIX* soubory.

## <a name="to-install-nuget-analyzer-packages"></a>Instalace balíčků NuGet analyzátoru

1. Najdete analyzátor balíček, který chcete nainstalovat na www.nuget.org. Například můžete chtít [nainstalovat analyzátory Microsoft FxCop](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package) ke kontrole v kódu, problémy zabezpečení a výkonu, mimo jiné.

2. Nainstalujte balíček v sadě Visual Studio, buď pomocí [Konzola správce balíčků](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) nebo [uživatelské rozhraní Správce balíčků](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console).

   > [!NOTE]
   > Na stránce www.nuget.org pro každý balíček Analyzátor se dozvíte, příkaz a vložte do **Konzola správce balíčků**. Je i užitečný tlačítko ke zkopírování textu do schránky.
   > 
   > ![NuGet.org stránky zobrazující příkaz konzoly Správce balíčků](media/nuget-install-command.png)

   Sestavení analyzátoru jsou nainstalovány a zobrazují v **Průzkumníka řešení** pod **odkazy** > **analyzátory**.

## <a name="to-install-vsix-analyzers"></a>Chcete-li nainstalovat VSIX analyzátory

1. V sadě Visual Studio, vyberte **nástroje** > **rozšíření a aktualizace**.

   **Rozšíření a aktualizace** zobrazí se dialogové okno.

   > [!NOTE]
   > Alternativně lze vyhledat a stáhnout přímo z rozšíření analyzátoru [Visual Studio Marketplace](https://marketplace.visualstudio.com).

2. Rozbalte **Online** v levém podokně a pak vyberte **Visual Studio Marketplace**.

3. Do vyhledávacího pole zadejte název, který chcete nainstalovat rozšíření analyzátoru. Například můžete chtít [nainstalovat analyzátory Microsoft FxCop](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix) ke kontrole v kódu, problémy zabezpečení a výkonu, mimo jiné.

4. Vyberte **Stáhnout**.

   Rozšíření je stažen.

5. Vyberte **OK** dialogové okno zavřete a pak zavřete všechny instance sady Visual Studio ke spuštění **instalátor VSIX**.

   **Instalátor VSIX** zobrazí se dialogové okno.

   ![Instalátor VSIX pro analýzu kódu Microsoft](media/vsix-installer-code-analysis.png)

6. Vyberte **změnit** spusťte instalaci.

7. Po jedné až dvou minutách dokončení instalace. Vyberte **Zavřít**.

8. Znovu otevřete Visual Studio.

Pokud chcete zkontrolovat, zda je rozšíření nainstalované, vyberte **nástroje** > **rozšíření a aktualizace**. V **rozšíření a aktualizace** dialogové okno, vyberte **nainstalováno** kategorie na levé straně a poté vyhledejte rozšíření podle názvu.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Používání analyzátorů Roslyn v sadě Visual Studio](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>Viz také:

- [Přehled analyzátory Roslyn v sadě Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Nainstalujte analyzátory FxCop](../code-quality/install-fxcop-analyzers.md)
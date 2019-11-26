---
title: 'Postupy: Upgrade vlastní úvodní stránku | Dokumentace Microsoftu'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 78342ce6-36c8-485b-a5f6-760e7a420a26
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: a7854de705a961463b1e8435e7340548cfc23bf3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74293378"
---
# <a name="how-to-upgrade-a-visual-studio-custom-start-page"></a>Postupy: Upgrade vlastní úvodní stránku sady Visual Studio
Můžete upgradovat Visual Studio 2010 nebo Visual Studio 2012 vlastní úvodní stránku do sady Visual Studio 2015 podle pokynů uvedených níže.

> [!WARNING]
> Stránka vlastní zahájení upgradováná v tomto postupu je ta vytvořená pomocí šablony [vlastní úvodní stránky](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.CustomStartPageProjectTemplate) v galerii sady Visual Studio. Úvodní stránka může mít jiné funkce, které je potřeba upgradovat.

### <a name="to-upgrade-a-custom-start-page-to-visual-studio-2015"></a>Vlastní úvodní stránku upgradovat na Visual Studio 2015

1. Ujistěte se, že jsou nainstalované Visual Studio 2015 a Visual Studio 2015 SDK. VSSDK si můžete stáhnout z [SDK Microsoft Visual Studio 2013](https://my.visualstudio.com/Downloads?pid=1436).

2. Otevřete svůj projekt vlastní šablony. Zobrazí se zpráva s upozorněním, že projekt je třeba upgradovat. Klikněte na **OK** a počkejte na dokončení upgradu.

3. Ve vlastnostech projektu pro projekt úvodní stránky a řízení projektu, ujistěte se, že Cílová architektura, která je minimálně rozhraní .NET Framework 4.5.

4. V kategorii ladění vlastnosti projektu pro projekt úvodní stránky nastavení cesty k verzi sady Visual Studio 2015 devenv.exe.

5. V odkazech projektu pro oba projekty odkazy na Microsoft.VisualStudio.Shell.11.0 odebrat a přidat odkazy na Microsoft.VisualStudio.Shell.14.0.

6. Otevřete StartPage.xaml pomocí editoru XML a proveďte následující změny:

    1. Aktualizace oboru názvů. Změňte následující řádky:

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"
        ```

         pro následující:

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.142.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.14.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        ```

7. Otevřete MyControl. XAML a změňte referenční obor názvů `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"` na `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"`.
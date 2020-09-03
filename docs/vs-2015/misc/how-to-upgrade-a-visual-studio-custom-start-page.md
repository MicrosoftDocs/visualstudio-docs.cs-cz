---
title: 'Postupy: upgrade vlastní úvodní stránky | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 78342ce6-36c8-485b-a5f6-760e7a420a26
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: a7854de705a961463b1e8435e7340548cfc23bf3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74293378"
---
# <a name="how-to-upgrade-a-visual-studio-custom-start-page"></a>Postupy: upgrade vlastní úvodní stránky sady Visual Studio
Pomocí níže uvedených kroků můžete upgradovat vlastní úvodní stránku sady Visual Studio 2010 nebo Visual Studio 2012 na Visual Studio 2015.

> [!WARNING]
> Stránka vlastní zahájení upgradováná v tomto postupu je ta vytvořená pomocí šablony [vlastní úvodní stránky](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.CustomStartPageProjectTemplate) v galerii sady Visual Studio. Vaše úvodní stránka může mít jiné funkce, které je třeba upgradovat.

### <a name="to-upgrade-a-custom-start-page-to-visual-studio-2015"></a>Upgrade vlastní úvodní stránky na Visual Studio 2015

1. Ujistěte se, že je nainstalována sada Visual Studio 2015 a sada Visual Studio 2015 SDK. VSSDK si můžete stáhnout z [SDK Microsoft Visual Studio 2013](https://my.visualstudio.com/Downloads?pid=1436).

2. Otevřete vlastní projekt šablony. Zobrazí se zpráva s upozorněním, že projekt bude upgradován. Klikněte na **OK** a počkejte na dokončení upgradu.

3. Ve vlastnostech projektu pro projekt počáteční stránky i projekt ovládacího prvku se ujistěte, že je cílový rámec alespoň .NET Framework 4,5.

4. V kategorii ladění vlastností projektu úvodní stránky nastavte cestu k verzi sady Visual Studio 2015 devenv.exe.

5. V projektových odkazech pro oba projekty odeberte odkazy na Microsoft. VisualStudio. Shell. 11.0 a přidejte odkazy na Microsoft. VisualStudio. Shell. 14.0.

6. Otevřete soubor StartPage. XAML pomocí editoru XML a proveďte následující změny:

    1. Aktualizujte obory názvů. Změňte následující řádky:

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"
        ```

         na následující:

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.142.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.14.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        ```

7. Otevřete MyControl. XAML a změňte odkaz na obor názvů `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"` na `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"` .
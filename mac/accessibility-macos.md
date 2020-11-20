---
title: Použití možností usnadnění macOS
description: Použití možností a funkcí macOS Accessibility, jako je vysoký kontrast, navigace pomocí klávesnice a VoiceOver
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/23/2019
ms.assetid: 598FC25A-6DA3-44BB-B128-AD979E9F86EA
ms.topic: how-to
ms.openlocfilehash: 6796ab12716d1d2f3ec2570c32b410c8360b8a81
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998383"
---
# <a name="accessibility-features-of-macos"></a>Funkce usnadnění pro macOS

macOS je přístupný operační systém s řadou funkcí, které pomáhají uživatelům s proměnlivými schopnostmi. Mezi tyto funkce patří režim vysokého kontrastu, navigace pomocí klávesnice a VoiceOver (čtečka obrazovky macOS).

## <a name="enable-accessibility-features"></a>Povolit funkce usnadnění přístupu

V Visual Studio pro Mac je podpora pro technologie pro usnadnění ve výchozím nastavení vypnutá. Pokud chcete povolit podporu usnadnění přístupu:

1. Přejděte na Předvolby jiné sady **Visual Studio (nabídka)**  >  **Preferences**  >  **Other** a vyberte možnost **usnadnění**.

1. Zaškrtněte políčko **Povolit přístupnost** .

   ![Snímek obrazovky s předvolby přístupnosti s vybraným možností povolit přístupnost](media/accessibility-preferences.png)

1. Vyberte **restartovat Visual Studio** , aby se aktivovala podpora pro technologie usnadnění společnosti Apple.

Alternativně můžete pomocí příkazového řádku povolit funkce usnadnění přístupu. Provedete to tak, že v terminálu zadáte následující příkaz:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Po změně tohoto nastavení prostřednictvím příkazového řádku budete muset restartovat Visual Studio.

## <a name="increase-the-contrast-in-macos"></a>Zvýšit kontrast v macOS

Visual Studio pro Mac podporuje zvýšený kontrast v macOS, což zvyšuje kontrast prvků uživatelského rozhraní a usnadňuje vytváření osnovy. Postup pro povolení:

1. Otevřete **Předvolby systému**.

1. Přejít na **přístupnost** a vyberte **Zobrazit**.

1. Zaškrtněte políčko **Zvětšit kontrast** .

---
title: Začínáme s Visual Studio Tools for Unity | Microsoft Docs
description: Zjistěte, jak nainstalovat a nastavit Visual Studio pro vývoj pro Unity.
ms.custom: ''
ms.date: 01/27/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: how-to
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
zone_pivot_groups: platform
ms.openlocfilehash: 791f25b61c86f0115c225d505bdb1edb07869961
ms.sourcegitcommit: 69256dc47489853dc66a037f5b0c1275977540c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2021
ms.locfileid: "109782605"
---
# <a name="get-started-with-visual-studio-and-unity"></a>Začínáme s Visual Studio a Unity

> [!NOTE]
> V této příručce se předpokládá, že už máte Unity nainstalovanou pomocí programu Unity Hub. Pokud je pro vás Unity novinka, doporučujeme navštívit Unity Learn a nejprve dokončit studijní [postup Unity Essentials.](https://learn.unity.com/pathway/unity-essentials)

## <a name="install-unity-support-for-visual-studio"></a>Instalace podpory Unity pro Visual Studio

Visual Studio Tools for Unity je bezplatné rozšíření, které poskytuje podporu pro psaní a ladění jazyka C# a další. Úplný [seznam toho,](./visual-studio-tools-for-unity.md) co rozšíření zahrnují, najdete v přehledu nástrojů pro Unity.

:::zone pivot="windows"

> [!NOTE]
> Tento průvodce instalací je pro Visual Studio. Pokud používáte aplikaci Visual Studio Code, navštivte stránku [Unity Development with VS Code dokumentaci.](https://code.visualstudio.com/docs/other/unity)

1. [Stáhněte si Visual Studio nebo](/visualstudio/install/install-visual-studio.md)ho spusťte, pokud je už nainstalovaný.
2. Klikněte **na Upravit** (pokud už máte nainstalovanou) nebo Nainstalovat (pro nové instalace) pro požadovanou verzi Visual Studio. 
3. Na kartě **Úlohy se** posuňte do části **Hry** a vyberte úlohu Vývoj her **pomocí Unity.**

    ![Pole pro vývoj her pomocí úloh Unity v instalačním programu](../media/vs/unity-workload.png)

:::zone-end
:::zone pivot="macos"

> [!NOTE]
> Tento průvodce instalací je pro Visual Studio pro Mac. Pokud používáte aplikaci Visual Studio Code, navštivte stránku [Unity Development with VS Code dokumentaci.](https://code.visualstudio.com/docs/other/unity)

Nástroje pro Unity jsou součástí instalace Visual Studio pro Mac a nejsou vyžadovány žádné samostatné kroky instalace. Můžete to ověřit v nabídce **Visual Studio pro Mac > rozšíření > Game Development.** **Visual Studio pro Mac by měly být povolené nástroje pro Unity.**

![Zobrazení Správce rozšíření s povolenými Visual Studio pro Mac Tools for Unity](../media/vsm/unity-workload.png)

:::zone-end

## <a name="check-for-updates"></a>Vyhledat aktualizace

Doporučuje se nechat Visual Studio a Visual Studio pro Mac aktualizovat, abyste měli nejnovější opravy chyb, funkce a podporu Unity. To nevyžaduje aktualizaci verze Unity.

:::zone pivot="windows"

1. Klikněte na nabídku **> vyhledat aktualizace v nápovědě** .

    ![Nabídka vyhledat aktualizace v aplikaci Visual Studio 2019](../media/vs/check-for-updates.png)

2. Pokud je k dispozici aktualizace, Instalační program pro Visual Studio zobrazí novou verzi. Klikněte na tlačítko **aktualizovat** .

:::zone-end
:::zone pivot="macos"

1. Kliknutím na **Visual Studio pro Mac > vyhledat aktualizace...** otevřete dialog **aktualizace sady Visual Studio** .
2. Pokud je k dispozici aktualizace, klikněte na tlačítko **nainstalovat** .

:::zone-end

## <a name="configure-unity-to-use-visual-studio"></a>Konfigurace Unity pro použití Visual studia

Ve výchozím nastavení by Unity měla být nakonfigurovaná tak, aby používala aplikaci Visual Studio, nebo Visual Studio pro Mac jako editor skriptu. Můžete to potvrdit nebo změnit externí editor skriptu na konkrétní verzi sady Visual Studio z editoru Unity.

:::zone pivot="windows"

1. V editoru Unity vyberte nabídku **Upravit předvolby >** ..
2. Na levé straně vyberte kartu **externí nástroje** .
3. Rozevírací seznam **editoru externích skriptů** nabízí způsob, jak zvolit různé instalace aplikace Visual Studio. Můžete také kliknout na **Procházet...** v rozevíracím seznamu a přidat tak verzi, která není v seznamu.

    ![Nabídka předvolby externích nástrojů v editoru Unity ve Windows](../media/vs/preferences-external-tools.png)

4. Pokud jste vybrali možnost **Procházet...** , přejděte do adresáře **Common7/IDE** v instalačním adresáři sady Visual Studio a vyberte **devenv.exe**. Pak klikněte na **otevřít**.
5. Jakmile je v seznamu **Editor externích skriptů** vybraná možnost Visual Studio, zkontrolujte, že je zaškrtnuté políčko **připojovat Editor** .
6. Zavřete dialogové okno **Předvolby** a dokončete proces konfigurace.

:::zone-end
:::zone pivot="macos"

1. V Editoru Unity vyberte nabídku **Unity > Předvolby.**
2. Na levé **straně vyberte** kartu Externí nástroje.
3. Rozevírací **seznam Editor externích** skriptů poskytuje způsob, jak zvolit různé instalace Visual Studio. Můžete také **kliknout na Procházet...** z rozevíracího seznamu a přidat neuvedené verze.

    ![Nabídka předvoleb Externí nástroje v Editoru Unity v macOS](../media/vsm/preferences-external-tools.png)

4. Zavřete **dialogové okno** Předvolby a dokončete proces konfigurace.

:::zone-end

## <a name="next-steps"></a>Další kroky

 Informace o tom, jak pracovat s projektem Unity a ladit ho v Visual Studio, najdete v tématu Používání [Visual Studio Tools for Unity](using-visual-studio-tools-for-unity.md).

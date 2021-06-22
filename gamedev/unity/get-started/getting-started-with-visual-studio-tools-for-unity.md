---
title: Začínáme s Visual Studio Tools for Unity | Microsoft Docs
description: Naučte se instalovat a nastavovat Visual Studio pro vývoj Unity.
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
ms.openlocfilehash: 706700c8343d934f7a9a5ce32f98bf96e67d4259
ms.sourcegitcommit: 07e6db4bf2966863093e3974c60c3b46e6953416
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2021
ms.locfileid: "112488842"
---
# <a name="get-started-with-visual-studio-and-unity"></a>Začínáme se sadou Visual Studio a Unity

> [!NOTE]
> V tomto průvodci se předpokládá, že už máte nainstalovanou Unity pomocí programu centrum Unity. Pokud s Unity začínáte, doporučujeme, abyste se seznámili s Unity a nejprve dokončili [výukovou cestu Unity Essentials](https://learn.unity.com/pathway/unity-essentials) .

## <a name="install-unity-support-for-visual-studio"></a>Instalace podpory Unity pro Visual Studio

Visual Studio Tools for Unity je bezplatné rozšíření, které poskytuje podporu pro psaní a ladění C# a dalších. Úplný seznam toho, co rozšíření obsahují, najdete v [přehledu nástrojů pro Unity](./visual-studio-tools-for-unity.md) .

:::zone pivot="windows"

> [!NOTE]
> Tato instalační příručka je určena pro Visual Studio. Pokud používáte Visual Studio Code, navštivte prosím [vývoj Unity s vs Code dokumentaci](https://code.visualstudio.com/docs/other/unity).

1. [Stáhněte si instalační program sady Visual Studio](/visualstudio/install/install-visual-studio.md)nebo ho spusťte, pokud už je nainstalovaný.
2. Klikněte na **Upravit** (Pokud je už nainstalovaný) nebo **nainstalujte** (pro nové instalace) pro požadovanou verzi sady Visual Studio.
3. Na kartě **úlohy** přejděte do části **hry** a vyberte úlohu **vývoj her pomocí Unity** .

    ![V instalačním programu v okně vývoj her s využitím úlohy Unity](../media/vs/unity-workload.png)

:::zone-end
:::zone pivot="macos"

> [!NOTE]
> Tato instalační příručka je určena pro Visual Studio pro Mac. Pokud používáte Visual Studio Code, navštivte prosím [vývoj Unity s vs Code dokumentaci](https://code.visualstudio.com/docs/other/unity).

Nástroje pro Unity jsou součástí instalace Visual Studio pro Mac a nevyžadují se žádné samostatné kroky instalace. To můžete ověřit v nabídce **rozšíření Visual Studio pro Mac > > nabídce vývoj her** . Měla by být povolená **Visual Studio pro Mac nástroje pro Unity** .

![Zobrazení Správce rozšíření zobrazující Visual Studio pro Mac nástrojů pro Unity povoleno](../media/vsm/unity-workload.png)

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

1. V editoru Unity vyberte nabídku **předvolby > Unity** .
2. Na levé straně vyberte kartu **externí nástroje** .
3. Rozevírací seznam **editoru externích skriptů** nabízí způsob, jak zvolit různé instalace aplikace Visual Studio. Můžete také kliknout na **Procházet...** v rozevíracím seznamu a přidat tak verzi, která není v seznamu.

    ![Nabídka předvolby externích nástrojů v editoru Unity v macOS](../media/vsm/preferences-external-tools.png)

4. Zavřete dialogové okno **Předvolby** a dokončete proces konfigurace.

:::zone-end

## <a name="next-steps"></a>Další kroky

 Informace o tom, jak pracovat s a ladit projekt Unity v aplikaci Visual Studio, najdete v tématu [použití Visual Studio Tools for Unity](using-visual-studio-tools-for-unity.md).

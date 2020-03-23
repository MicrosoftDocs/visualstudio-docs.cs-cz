---
title: Stránka Ladění, návrhář projektu
ms.date: 06/27/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2c3e7813e5e07a0fbb8f4ebf5838c883faa0fb8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595719"
---
# <a name="debug-page-project-designer"></a>Stránka Ladění, návrhář projektu

Pomocí stránky **Ladění** **Návrháře projektu** nastavte vlastnosti pro ladění chování v projektu jazyka Visual Basic nebo C#.

Chcete-li získat přístup ke stránce **Ladění,** vyberte uzel projektu v **Průzkumníku řešení**. V nabídce **Project** zvolte ** \<Název_projektu> vlastnosti**. Po zobrazení **Návrháře projektů** klikněte na kartu **Ladění.**

> [!NOTE]
> Toto téma se nevztahuje na aplikace UPW. Viz [Spuštění relace ladění (VB, C#, C++ a XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) pro aplikace UPW.

## <a name="configuration-and-platform"></a>Konfigurace a platforma

Následující možnosti umožňují vybrat konfiguraci a platformu, kterou chcete zobrazit nebo upravit.

**Konfigurace**

Určuje, která nastavení konfigurace se mají zobrazit nebo upravit. Nastavení může být **ladění** (výchozí), **Vydání**nebo **Všechny konfigurace**.

**Platforma**

Určuje, které nastavení platformy se má zobrazit nebo upravit. Volby mohou zahrnovat **libovolný procesor** (výchozí), **x64**a **x86**.

## <a name="start-action"></a>Zahájit akci

**Akce Spuštění** označuje položku, která má být zahájena při odladění aplikace: projekt, vlastní program, adresa URL nebo nic. Ve výchozím nastavení je tato možnost nastavena na **spustit projekt**. Nastavení **Spustit akci** na stránce **Ladění** určuje hodnotu vlastnosti. `StartAction`

**Zahájit projekt**

Tuto možnost zvolte, chcete-li určit, že spustitelný soubor (pro projekty aplikací systému Windows a konzolových aplikací) má být spuštěn při odladění aplikace. Tato možnost je ve výchozím nastavení zaškrtnutá.

**Spuštění externího programu**

Tuto možnost zvolte, chcete-li určit, že určitý program má být spuštěn při odladění aplikace.

**Spuštění prohlížeče s adresou URL**

Tuto možnost zvolte, chcete-li určit, že konkrétní adresa URL má být přístupná při odladění aplikace.

## <a name="start-options"></a>Možnosti spuštění

**Argumenty příkazového řádku**

Do tohoto textového pole zadejte argumenty příkazového řádku, které se mají použít pro ladění.

**Pracovní adresář**

Do tohoto textového pole zadejte adresář, ze kterého bude projekt spuštěn. Nebo klikněte na tlačítko Procházet (**...**) a vyberte adresář.

**Použití vzdáleného počítače**

Chcete-li ladit aplikaci ze vzdáleného počítače, zaškrtněte toto políčko a do textového pole zadejte cestu ke vzdálenému počítači.

## <a name="debugger-engines"></a>Ladicí stroje

**Povolení ladění nativního kódu**

Tato možnost určuje, zda je podporováno ladění nativního kódu. Toto políčko zaškrtněte, pokud voláte k objektům MODELU COM nebo pokud spustíte vlastní program napsaný v nativním kódu, který volá váš projekt a je nutné ladit nativní kód. Zrušte zaškrtnutí tohoto políčka, chcete-li zakázat ladění nespravovaného kódu. Toto políčko je ve výchozím nastavení vymazáno.

**Povolit ladění serveru SQL Server**

Zaškrtnutím nebo zrušením zaškrtnutí tohoto políčka povolíte nebo zakážete ladění procedur SQL z aplikace jazyka Visual Basic. Toto políčko je ve výchozím nastavení vymazáno.

## <a name="see-also"></a>Viz také

- [První seznámení s ladicím programem](../../debugger/debugger-feature-tour.md)
- [Nastavení projektu pro konfigurace ladění jazyka C#](../../debugger/project-settings-for-csharp-debug-configurations.md)
- [Nastavení projektu pro konfiguraci ladění jazyka Visual Basic](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Postupy: Ladění aplikace ClickOnce s omezenými oprávněními](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [Postupy: Vytvoření a úprava konfigurací](../../ide/how-to-create-and-edit-configurations.md)

---
title: Stránka ladění, Návrhář projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 006662d7c07ba0498fff4617eca3fdc7c631d37b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660790"
---
# <a name="debug-page-project-designer"></a>Stránka Ladění, návrhář projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!WARNING]
> Toto téma se nevztahuje na aplikace pro Windows Store. Viz [Spustit ladicí relaci (VB, C# C++ a XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) na stránce Windows Dev Center.

 Pomocí stránky **ladění** v **Návrháři projektu** můžete nastavit vlastnosti pro chování ladění v Visual Basic nebo C# projektu.

 Chcete-li získat přístup ke stránce **ladění** , vyberte uzel projektu v **Průzkumník řešení**. V nabídce **projekt** vyberte**vlastnosti** _ProjectName_. Když se zobrazí **Návrhář projektu** , klikněte na kartu **ladění** .

## <a name="configuration-and-platform"></a>Konfigurace a platforma
 Následující možnosti umožňují vybrat konfiguraci a platformu pro zobrazení nebo úpravu.

 **Konfigurace** Určuje, která nastavení konfigurace se mají zobrazit nebo upravit. Nastavení lze **ladit** (výchozí), **vydávat**nebo **všechny konfigurace**. Další informace naleznete v tématu [Konfigurace projektů ladění a vydávání](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Platforma** Určuje, která nastavení platformy se mají zobrazit nebo upravit. Volby můžou zahrnovat **jakýkoli procesor** (výchozí), **x64**a **x86**. Další informace naleznete v tématu [Konfigurace projektů ladění a vydávání](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

## <a name="start-action"></a>Spustit akci
 **Akce spustit** označuje položku, která se má spustit při ladění aplikace: projekt, vlastní program, adresa URL nebo nic. Ve výchozím nastavení je tato možnost nastavena na hodnotu **spustit projekt**. Nastavení **akce spustit** na stránce **ladění** Určuje hodnotu vlastnosti `StartAction`.

 **Spustit projekt** Tuto možnost zvolte, chcete-li určit, zda má být spuštěn spustitelný soubor (pro projekty aplikace systému Windows a Konzolová aplikace) při ladění aplikace. Tato možnost je vybrána ve výchozím nastavení.

 **Spustit externí program** Tuto možnost vyberte, pokud chcete určit, že se má při ladění aplikace spustit konkrétní program.

 **Spustit prohlížeč s adresou URL** Tuto možnost vyberte, pokud chcete určit, že při ladění aplikace má být k určité adrese URL přistupovaná konkrétní adresa URL.

## <a name="start-options"></a>Možnosti spuštění
 **Argumenty příkazového řádku** Do tohoto textového pole zadejte argumenty příkazového řádku, které chcete použít pro ladění.

 **Pracovní adresář** Do tohoto textového pole zadejte adresář, ze kterého se projekt spustí. Nebo klikněte na tlačítko pro procházení ( **...** ) a vyberte adresář.

 **Použít vzdálený počítač** Chcete-li ladit aplikaci ze vzdáleného počítače, zaškrtněte toto políčko a do textového pole zadejte cestu ke vzdálenému počítači.

## <a name="enable-debuggers"></a>Povolit ladicí programy
 **Povolit ladění nespravovaného kódu** Tato možnost určuje, zda je podporováno ladění nativního kódu. Zaškrtněte toto políčko, pokud provádíte volání objektů COM nebo pokud spustíte vlastní program napsaný v nativním kódu, který volá váš projekt, a musíte ladit nativní kód. Zrušením zaškrtnutí tohoto políčka zakážete ladění nespravovaného kódu. Toto políčko je ve výchozím nastavení zaškrtnuté.

 **Povolit ladění SQL Server** Zaškrtnutím nebo zrušením zaškrtnutí tohoto políčka povolíte nebo zakážete ladění procedur SQL z aplikace Visual Basic. Toto políčko je ve výchozím nastavení zaškrtnuté.

 **Povolit hostující proces sady Visual Studio** Zaškrtnutím tohoto políčka povolíte proces hostování sady Visual Studio. Toto zaškrtávací políčko je vybráno ve výchozím nastavení. Další informace naleznete v tématu [hostující proces (vshost. exe)](../../ide/hosting-process-vshost-exe.md).

 Chcete-li ladit v zóně zabezpečení, je nutné povolit tuto možnost a **Ladit tuto aplikaci s vybranou sadou oprávnění** v [dialogovém okně Upřesnit nastavení zabezpečení](../../ide/reference/advanced-security-settings-dialog-box.md).

## <a name="see-also"></a>Viz také
 [Ladění v](../../debugger/debugging-in-visual-studio.md) [nastavení projektu Visual Studio pro C# konfigurace ladění](../../debugger/project-settings-for-csharp-debug-configurations.md) [nastavení projektu pro Visual Basic konfigurace ladění](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md) [Správa vlastností ladění](https://msdn.microsoft.com/92474d16-e7fe-4fac-9287-6bd6b3a7eb68) [Postupy: ladění aplikace ClickOnce s Omezená oprávnění](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md) [Postupy: vytváření a úpravy konfigurací](../../ide/how-to-create-and-edit-configurations.md)

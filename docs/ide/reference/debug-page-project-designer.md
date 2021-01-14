---
title: Stránka Ladění, návrhář projektu
description: Chcete-li nastavit vlastnosti ladění v projektu Visual Basic nebo C#, použijte stránku ladit Návrháře projektu. Popis nastavení najdete v tomto článku.
ms.custom: SEO-VS-2020
ms.date: 06/27/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8567b762e9858205e3ca8d6aafa8a3dba17a90fe
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205772"
---
# <a name="debug-page-project-designer"></a>Stránka Ladění, návrhář projektu

Pomocí stránky **ladění** v **Návrháři projektu** můžete nastavit vlastnosti pro chování ladění v projektu Visual Basic nebo C#.

Chcete-li získat přístup ke stránce **ladění** , vyberte uzel projektu v **Průzkumník řešení**. V nabídce **projekt** klikněte na příkaz **\<ProjectName> vlastnosti**. Když se zobrazí **Návrhář projektu** , klikněte na kartu **ladění** .

> [!NOTE]
> Toto téma se nevztahuje na aplikace pro UWP. Viz [zahájit ladicí relaci (VB, C#, C++ a XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) pro aplikace pro UWP.

## <a name="configuration-and-platform"></a>Konfigurace a platforma

Následující možnosti umožňují vybrat konfiguraci a platformu pro zobrazení nebo úpravu.

**Konfigurace**

Určuje, která nastavení konfigurace se mají zobrazit nebo upravit. Nastavení lze **ladit** (výchozí), **vydávat** nebo **všechny konfigurace**.

**Platforma**

Určuje, která nastavení platformy se mají zobrazit nebo upravit. Volby můžou zahrnovat **jakýkoli procesor** (výchozí), **x64** a **x86**.

## <a name="start-action"></a>Spustit akci

**Akce spustit** označuje položku, která se má spustit při ladění aplikace: projekt, vlastní program, adresa URL nebo nic. Ve výchozím nastavení je tato možnost nastavena na hodnotu **spustit projekt**. Hodnota vlastnosti určuje nastavení **Akce zahájit** na stránce **ladění** `StartAction` .

**Spustit projekt**

Tuto možnost zvolte, chcete-li určit, zda má být spuštěn spustitelný soubor (pro projekty aplikace systému Windows a Konzolová aplikace) při ladění aplikace. Tato možnost je ve výchozím nastavení zaškrtnutá.

**Spustit externí program**

Tuto možnost vyberte, pokud chcete určit, že se má při ladění aplikace spustit konkrétní program.

**Spustit prohlížeč s adresou URL**

Tuto možnost vyberte, pokud chcete určit, že při ladění aplikace má být k určité adrese URL přistupovaná konkrétní adresa URL.

## <a name="start-options"></a>Možnosti spuštění

**Argumenty příkazového řádku**

Do tohoto textového pole zadejte argumenty příkazového řádku, které chcete použít pro ladění.

**Pracovní adresář**

Do tohoto textového pole zadejte adresář, ze kterého se projekt spustí. Nebo klikněte na tlačítko pro procházení (**...**) a vyberte adresář.

**Použít vzdálený počítač**

Chcete-li ladit aplikaci ze vzdáleného počítače, zaškrtněte toto políčko a do textového pole zadejte cestu ke vzdálenému počítači.

## <a name="debugger-engines"></a>Moduly ladicího programu

**Povolit ladění nativního kódu**

Tato možnost určuje, zda je podporováno ladění nativního kódu. Zaškrtněte toto políčko, pokud provádíte volání objektů COM nebo pokud spustíte vlastní program napsaný v nativním kódu, který volá váš projekt, a musíte ladit nativní kód. Zrušením zaškrtnutí tohoto políčka zakážete ladění nespravovaného kódu. Toto políčko je ve výchozím nastavení zaškrtnuté.

**Povolit ladění SQL Server**

Zaškrtnutím nebo zrušením zaškrtnutí tohoto políčka povolíte nebo zakážete ladění procedur SQL z aplikace Visual Basic. Toto políčko je ve výchozím nastavení zaškrtnuté.

## <a name="see-also"></a>Viz také

- [První seznámení s ladicím programem](../../debugger/debugger-feature-tour.md)
- [Nastavení projektu pro konfiguraci ladění v jazyce C#](../../debugger/project-settings-for-csharp-debug-configurations.md)
- [Nastavení projektu pro konfiguraci Visual Basicho ladění](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Zabezpečení aplikací ClickOnce](../../deployment/securing-clickonce-applications.md)
- [Postupy: Vytvoření a úprava konfigurací](../../ide/how-to-create-and-edit-configurations.md)

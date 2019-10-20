---
title: Dialogové okno Možnosti, projekty a řešení, sestavení a spuštění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
- VS.ToolsOptionsPag.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9b7eb229c5938165607b797205b94a318e3303b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655190"
---
# <a name="options-dialog-box--projects-and-solutions-build-and-run"></a>Dialogové okno Možnosti, Projekty a řešení, Sestavit a spustit
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V tomto dialogovém okně můžete zadat maximální počet vizuálních C++ nebo vizuálních C# projektů, které lze současně sestavit, určité výchozí chování sestavení a některá nastavení protokolu sestavení. Chcete-li otevřít dialogové okno **Možnosti** , klikněte na položku **nástroje**, **Možnosti** na panelu nabídek. Chcete-li získat přístup k této sadě možností, rozbalte položku **projekty a řešení**a pak zvolte možnost **Sestavit a spustit**.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 **maximální počet paralelně sestavovaných projektů** Určuje maximální počet vizuálních C++ a vizuálních C# projektů, které lze současně sestavit. Pro optimalizaci procesu sestavení je maximální počet paralelních sestavení projektu automaticky nastaven na počet procesorů počítače. Maximální hodnota je 32.

 **Při běhu sestavovat pouze spouštěné projekty a závislosti** Pouze projekt po spuštění a jeho závislosti jsou vytvořeny, pokud je toto políčko zaškrtnuto, když zvolíte klávesu F5; Vyberte **ladění**, **Spustit** na řádku nabídek; nebo klikněte na tlačítko **sestavit**, **sestavit** na řádku nabídek. Všechny projekty, závislosti a soubory řešení jsou vytvořeny, pokud je toto políčko zaškrtnuto, pokud zvolíte klávesu F5; Vyberte **ladění**, **Spustit** na řádku nabídek; nebo klikněte na tlačítko **sestavit**, **sestavit** na řádku nabídek. Ve výchozím nastavení je tato možnost prázdná.

 **Spustit, pokud jsou projekty zastaralé**
 > [!NOTE]
> Tento seznam se vztahuje pouze na [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projekty.

 Ve výchozím nastavení se zobrazí zpráva, pokud je konfigurace projektu zastaralá, když vyberete klávesu F5 nebo kliknete na položku **ladit**, **Spustit** na řádku nabídek. Můžete určit, zda má být projekt sestaven, a zda se zobrazí zpráva. Tuto možnost použijte k určení, zda se zobrazí zpráva a co by mělo být chování sestavení, pokud se zpráva nezobrazí.

 **Vždy sestavit** Okno se zprávou se nezobrazí a projekt se sestaví bez ohledu na aktuální konfiguraci. Tato možnost se nastaví, když ve zprávě zaškrtnete políčko **znovu nezobrazovat toto dialogové okno** a pak kliknete na tlačítko **Ano** .

 **Nikdy nevytvářet** Okno se zprávou se nezobrazí a projekt není sestaven. Tato možnost se nastaví, když ve zprávě zaškrtnete políčko **znovu nezobrazovat toto dialogové okno** a pak kliknete na tlačítko **ne** .

 **Dotázat se na sestavení** Zobrazí okno se zprávou pokaždé, když je konfigurace projektu neaktuální.

 **Při spuštění, když dojde k chybám sestavení nebo nasazení** Pokud dojde k chybám sestavení při spuštění sestavení z nabídky **sestavení** , zobrazí se zpráva. Můžete určit, zda chcete pokračovat spuštěním aplikace a zda se zpráva zobrazuje pokaždé, když dojde k chybám sestavení. Tuto možnost použijte, chcete-li určit, zda se zobrazí zpráva a co by mělo být použito, pokud se zpráva nezobrazí.

> [!NOTE]
> Tato možnost se vztahuje pouze na [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projekty.

 **Dotázat se na spuštění** Zobrazí okno se zprávou pokaždé, když dojde k chybám sestavení.

 **Nespouštět** Okno se zprávou se nezobrazí a aplikace se nespustí. Tato možnost je nastavena, když zaškrtnete políčko **příště nezobrazovat toto dialogové okno** v okně se zprávou a pak klikněte na tlačítko **ne** .

 **Spustit starou verzi** Okno se zprávou se nezobrazí a nově vytvořená verze aplikace se nespustí. Tato možnost se nastaví, když v okně se zprávou zaškrtnete políčko **příště nezobrazovat toto dialogové okno** a pak klikněte na tlačítko **Ano** .

 **Pro nová řešení použijte aktuálně vybraný projekt jako spouštěný projekt** . Pokud je toto políčko zaškrtnuté, nová řešení použijí aktuálně vybraný projekt jako spouštěný projekt.

 **Podrobnosti výstupu sestavení projektu nástroje MSBuild** Určuje, kolik informací se zobrazí v okně **výstup** pro sestavení.

 **Podrobnosti souboru protokolu sestavení projektu nástroje MSBuild**
 > [!NOTE]
> Tato možnost se vztahuje pouze C++ na projekty vizuálů.

 Určuje, kolik informací je zapsáno do souboru protokolu sestavení, který je umístěn v \\... \\*ProjectName*\debug. \\*ProjectName*. log.

## <a name="see-also"></a>Viz také
 [Kompilace a sestavení](../../ide/compiling-and-building-in-visual-studio.md)

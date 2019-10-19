---
title: Synchronizace změn mezi Xcode a Visual Studiem | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.topic: conceptual
ms.assetid: c71a4d7c-120e-4559-a114-3a99c4b860a9
ms.technology: vs-ide-mobile
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xamarin
ms.openlocfilehash: 5d7d7fab8080028da0ca906b0e75ddf2bf0f1f8c
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72589123"
---
# <a name="sync-changes-between-xcode-and-visual-studio"></a>Synchronizace změn mezi Xcode a Visual Studiem

Vývoj mobilních aplikací pomocí C++ součástí sady Visual Studio zahrnuje vzdálené možnosti synchronizace vaší práce mezi vaším počítačem a vaším počítačem Mac. Při párování vašich počítačů s Visual Studiem a Mac jsou k dispozici nové možnosti pro projekty aplikací pro iOS v aplikaci Visual Studio, které můžete použít k otevření projektu v Xcode, přesunutí kódu mezi Xcode a Visual Studio a vyčištění dočasného adresáře projektu Xcode.

Chcete-li použít možnosti vzdáleného počítače, projekt musí být projekt aplikace pro iOS a aplikace Visual Studio musí být spárována s vaším počítačem Mac. Požadavky a pokyny, jak spárovat počítač Mac, najdete v tématu [instalace a konfigurace nástrojů pro sestavení pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="the-remote-machine-menu"></a>Nabídka vzdáleného počítače

V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt aplikace pro iOS, aby se zobrazila kontextová nabídka. Vyberte položku **vzdálený počítač** , aby se zobrazily dostupné možnosti vzdáleného počítače.

![Položka nabídky se vzdáleným počítačem v Průzkumník řešení](../cross-platform/media/cppmdd_u2_remotemachine_menu.jpg "CPPMDD_U2_RemoteMachine_Menu")

Tyto příkazy umožňují otevřít projekt v Xcode, přesunout místní změny nebo celý projekt mezi Visual Studio a Xcode a vyčistit dočasné soubory na vzdáleném počítači.

## <a name="open-in-xcode"></a>Otevřít v Xcode

Chcete-li projekt otevřít v Xcode ze sady Visual Studio, v podnabídce **vzdálený počítač** vyberte možnost **otevřít v Xcode** a otevřete vybraný projekt na spárovaném vzdáleném počítači. Server `vcremote` slouží k otevření Xcode na Macu a přechodu do dočasného adresáře vytvořeného na počítači Mac, který obsahuje kopii projektu. V aplikaci Visual Studio se zobrazí dialogové okno s dočasným adresářem, který se používá pro projekt. Akce prováděné na vzdáleném počítači jsou také zobrazeny v okně **výstup** v aplikaci Visual Studio. Chcete-li je zobrazit, může být nutné vybrat možnost  **C++ Visual Remote Machine** v rozevíracím seznamu **Zobrazit výstup z** v horní části okna **výstup** .

![V okně výstup se zobrazí akce vzdáleného počítače.](../cross-platform/media/cppmdd_u2_remotemachine_output.png "CPPMDD_U2_RemoteMachine_Output")

Na Macu můžete použít všechny nástroje Xcode k úpravě kódu a prostředků, scénářů a akcí. V aplikaci Visual Studio je projekt aplikace pro iOS poznámkou "otevřeno v Xcode", aby označoval, že se na vzdáleném počítači mohou provádět změny. Po dokončení úprav můžete použít možnost načíst ze vzdálených příkazů ze vzdáleného nebo přírůstkového vyžádaného kopírování změn zpátky do projektu sady Visual Studio.

## <a name="push-to-remote-and-incremental-push-to-remote"></a>Odeslat do vzdáleného a přírůstkového nabízeného oznámení na vzdálené

Pokud jste provedli změny v projektu aplikace pro iOS v aplikaci Visual Studio, lze přesunout změněné soubory projektu do spárovaného vzdáleného počítače pomocí příkazu Push na vzdálené a přírůstkové vkládání na vzdálené příkazy. Příkaz Odeslat do vzdáleného počítače zkopíruje všechny soubory projektu do vzdáleného počítače. Přírůstkové vložení do vzdáleného příkazu zkopíruje pouze změněné soubory do vzdáleného počítače. U velkých projektů s malými změnami může přírůstkový příkaz ušetřit čas a šířku pásma.

Chcete-li zkopírovat soubory projektu do počítače Mac, v aplikaci Visual Studio v **Průzkumník řešení**klikněte pravým tlačítkem na projekt aplikace pro iOS a otevřete místní nabídku. Vyberte **vzdálený počítač** a zvolte buď možnost **Push na vzdálené** , nebo **přírůstkové vložení na vzdáleném** počítači, kde se zkopírují soubory projektu ze sady Visual Studio do vašeho počítače Mac.

## <a name="pull-from-remote-and-incremental-pull-from-remote"></a>Získat ze vzdáleného a přírůstkového stahování ze vzdáleného úložiště

Až provedete změny projektu v Xcode, přesuňte změny zpět do sady Visual Studio a udržujte projekty synchronizované.

Chcete-li zkopírovat soubory projektu z počítače Mac, v aplikaci Visual Studio v **Průzkumník řešení**klikněte pravým tlačítkem na projekt aplikace pro iOS a otevřete místní nabídku. Vyberte **vzdálený počítač** a zvolte buď možnost získat **ze vzdáleného** počítače, nebo **přírůstkové stahování ze vzdáleného úložiště** a zkopírujte soubory projektu z počítače Mac do sady Visual Studio.

## <a name="clean-remote"></a>Vyčistit vzdálený

K odstranění souborů v dočasném adresáři projektu ve vzdáleném počítači můžete použít příkaz vyčistit vzdálený. Obsah adresáře, včetně všech zdrojových souborů nebo sestavení produktů, se odebere na Macu. Než použijete příkaz vyčistit vzdálený, ujistěte se, že jste si provedli synchronizaci všech změn, které chcete vrátit do sady Visual Studio, pomocí operace Pull ze vzdáleného nebo přírůstkového stažení ze vzdáleného počítače.

Chcete-li vyčistit dočasný adresář projektu na vzdáleném počítači, v aplikaci Visual Studio v **Průzkumník řešení**klikněte pravým tlačítkem na projekt aplikace pro iOS a otevřete místní nabídku. Vyberte **vzdálený počítač** a zvolte možnost **vyčistit vzdálené** pro odebrání souborů adresáře projektu z počítače Mac.

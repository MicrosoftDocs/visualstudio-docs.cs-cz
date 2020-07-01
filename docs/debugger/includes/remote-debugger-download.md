---
title: Stažení vzdáleného ladicího programu
description: Stáhnout odkazy pro vzdálený ladicí program
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 1e90a1d9e03892cf81bd2257d3dcc6e25ab36246
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2019
ms.locfileid: "68149159"
---
Na vzdáleném zařízení nebo serveru, na kterém chcete ladit místo počítače se systémem Visual Studio, Stáhněte a nainstalujte správnou verzi nástrojů Remote Tools z odkazů v následující tabulce.

- Stáhněte si nejnovější nástroje Remote Tools pro vaši verzi sady Visual Studio. Nejnovější verze nástrojů Remote Tools je kompatibilní s dřívější verzí sady Visual Studio, ale starší verze nástrojů pro vzdálenou správu nejsou kompatibilní s novějšími verzemi sady Visual Studio. (Pokud používáte například sadu Visual Studio 2017, Stáhněte si nejnovější aktualizaci nástrojů Remote Tools for Visual Studio 2017. V tomto scénáři nestahujte nástroje Remote Tools for Visual Studio 2019.)
- Stáhněte si nástroje Remote Tools se stejnou architekturou jako počítač, na který jste je instalovali. Například pokud chcete ladit 32 aplikaci na vzdáleném počítači, na kterém běží 64 operační systém, nainstalujte nástroje pro vzdálenou navýšení 64.

::: moniker range=">=vs-2019"

|Verze|Odkaz|Poznámky|
|-|-|-|
|Visual Studio 2019|[Vzdálené nástroje](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019)|Kompatibilní se všemi verzemi sady Visual Studio 2019. Stáhněte si verzi, která odpovídá operačnímu systému zařízení (x86, x64 nebo ARM64). V systému Windows Server, přečtěte si téma [odblokování souboru ke stažení](../../debugger/remote-debugging-unblock-file-download.md) pro nápovědu stažení nástrojů Remote Tools.|
|Visual Studio 2017|[Vzdálené nástroje](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Kompatibilní se všemi verzemi sady Visual Studio 2017. Stáhněte si verzi, která odpovídá operačnímu systému zařízení (x86, x64 nebo ARM64). V systému Windows Server, přečtěte si téma [odblokování souboru ke stažení](../../debugger/remote-debugging-unblock-file-download.md) pro nápovědu stažení nástrojů Remote Tools.|
|Visual Studio 2015|[Vzdálené nástroje](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Nástroje Remote Tools for Visual Studio 2015 jsou dostupné z My.VisualStudio.com. Pokud se zobrazí výzva, připojte se k bezplatnému [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) programu nebo se přihlaste pomocí ID předplatného sady Visual Studio. V systému Windows Server, přečtěte si téma [odblokování souboru ke stažení](../../debugger/remote-debugging-unblock-file-download.md) pro nápovědu stažení nástrojů Remote Tools.|
|Visual Studio 2013|[Vzdálené nástroje](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Stránka pro stažení v dokumentaci k Visual Studio 2013|
|Visual Studio 2012|[Vzdálené nástroje](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Stránka ke stažení v dokumentaci k sadě Visual Studio 2012|

::: moniker-end

::: moniker range="vs-2017"

|Verze|Odkaz|Poznámky|
|-|-|-|
|Visual Studio 2017|[Vzdálené nástroje](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Kompatibilní se všemi verzemi sady Visual Studio 2017. Stáhněte si verzi, která odpovídá operačnímu systému zařízení (x86, x64 nebo ARM64). V systému Windows Server, přečtěte si téma [odblokování souboru ke stažení](../../debugger/remote-debugging-unblock-file-download.md) pro nápovědu stažení nástrojů Remote Tools. Pro nejnovější verzi nástrojů Remote Tools otevřete [dokument sady Visual Studio 2019](../../debugger/remote-debugging.md?view=vs-2019).|
|Visual Studio 2015|[Vzdálené nástroje](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Nástroje Remote Tools for Visual Studio 2015 jsou dostupné z My.VisualStudio.com. Pokud se zobrazí výzva, připojte se k bezplatnému [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) programu nebo se přihlaste pomocí ID předplatného sady Visual Studio. V systému Windows Server, přečtěte si téma [odblokování souboru ke stažení](../../debugger/remote-debugging-unblock-file-download.md) pro nápovědu stažení nástrojů Remote Tools.|
|Visual Studio 2013|[Vzdálené nástroje](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Stránka pro stažení v dokumentaci k Visual Studio 2013|
|Visual Studio 2012|[Vzdálené nástroje](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Stránka ke stažení v dokumentaci k sadě Visual Studio 2012|

::: moniker-end

Vzdálený ladicí program můžete spustit zkopírováním *msvsmon.exe* do vzdáleného počítače místo instalace nástrojů Remote Tools. Průvodce konfigurací vzdáleného ladicího programu (*rdbgwiz.exe*) je však k dispozici pouze při instalaci nástrojů Remote Tools. Chcete-li spustit vzdálený ladicí program jako službu, bude pravděpodobně nutné použít Průvodce pro konfiguraci. Další informace najdete v tématu [(volitelné) konfigurace vzdáleného ladicího programu jako služby](../../debugger/remote-debugging.md#bkmk_configureService).

>[!NOTE]
>- Pokud chcete ladit aplikace pro Windows 10 na zařízeních ARM, použijte ARM64, který je k dispozici v nejnovější verzi nástrojů Remote Tools.
>- Chcete-li ladit aplikace pro Windows 10 na zařízeních s Windows RT, použijte ARM, který je k dispozici pouze ve stahování vzdálených nástrojů sady Visual Studio 2015.

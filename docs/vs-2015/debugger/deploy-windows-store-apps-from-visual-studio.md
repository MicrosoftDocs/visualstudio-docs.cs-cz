---
title: Nasazení aplikací pro Windows Store
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 797983f2f5fcc9ae4e12ca5426b521034f03700d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055790"
---
# <a name="deploy-windows-store-apps-from-visual-studio"></a>Nasazení aplikací pro Windows Store ze sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pouze pro Windows] (.. /Image/windows_only_content.png "windows_only_content")

 Nasazení funkce sady Visual Studio vytvoří a zaregistruje aplikace Windows Store, které jsou vytvořeny pomocí sady Visual Studio na cílovém zařízení. Přesně jak registraci aplikace závisí na tom cílové zařízení pro místní nebo vzdálené:

- Pokud jsou cílem místní počítač s Visual Studio, Visual Studio registruje aplikaci ze složky jeho sestavení.

- Pokud jsou cílem vzdáleného zařízení, Visual Studio zkopíruje soubory potřebné ke vzdálenému počítači a zaregistruje na tomto zařízení aplikaci.

  Nasazení je automaticky při ladění aplikace v sadě Visual Studio s použitím **spustit ladění** možnost (klávesnice: F5) nebo **spustit bez ladění** možnost (klávesnice: CTRL + F5). Aplikaci můžete nasadit také ručně. Ruční nasazení je užitečná v následujících scénářích:

- Ad-hoc testování na místním nebo vzdáleném počítači.

- Nasazení aplikace, který spustí jiné aplikace, kterou chcete ladit.

- Nasazení aplikace, která bude laděn, kdy byla spuštěna jiná aplikace nebo metody.

##  <a name="BKMK_In_this_topic"></a> V tomto tématu
 V tomto tématu se dozvíte:

 [Jak nasadit aplikaci Windows Store](#BKMK_How_to_deploy_a_Windows_Store_app)

 [Určení vzdáleného zařízení](#BKMK_How_to_specify_a_remote_device)

 [Možnosti nasazení](#BKMK_Deployment_options)

##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Jak nasadit aplikaci Windows Store
 Ruční nasazení aplikace je jednoduchý proces:

1.  Pokud provádíte nasazení na vzdáleném zařízení, zadejte název nebo IP adresa zařízení, na stránce vlastností projektu z projektu po spuštění aplikace. (Tento postup jsou uvedeny níže v tomto tématu.).

2.  Na panelu nástrojů ladicího programu sady Visual Studio, zvolte cíl nasazení z rozevíracího seznamu vedle položky **spustit ladění** tlačítko.

     ![Spustit na místním počítači](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")

3.  Na **sestavení** nabídce zvolte **nasazení**

##  <a name="BKMK_How_to_specify_a_remote_device"></a> Určení vzdáleného zařízení
 **Požadované součásti**

 Chcete-li nasadit aplikaci do vzdáleného zařízení:

-   Licence vývojáře musí být nainstalována na vzdáleném zařízení.

-   Visual Studio Remote Tools musí být nainstalovaný na vzdáleném zařízení a sledování vzdáleného ladění musí být spuštěna.

     Nasazení používá síťový kanál. vzdálený ladicí program ke vzdálenému zařízení odesílat soubory aplikace.

#### <a name="to-specify-a-remote-device"></a>K určení vzdáleného zařízení

1. Na stránce vlastností ladění projektu při spuštění zadejte název nebo IP adresa cíle vzdálené nasazení.

2. Chcete-li otevřít stránky vlastnosti ladění, vyberte projekt v Průzkumníku řešení a klikněte na tlačítko **vlastnosti** z místní nabídky.

3. Klikněte na tlačítko **ladění** uzlu v okně Vlastnosti stránky.

4. Můžete zadat název nebo IP adresa vzdáleného zařízení, nebo můžete zvolit ze zařízení **vyberte připojení vzdáleného ladicího programu** dialogové okno.

    ![Dialogové okno Vyberte připojení vzdáleného ladicího programu](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    **Vyberte připojení vzdáleného ladicího programu** dialogové okno zobrazí zařízení, na podsíti místní sítě a zařízení, která je přímo připojený k počítači Visual Studio pomocí kabelu Ethernet.

   **Určení vzdáleného zařízení na stránce projektu JavaScript nebo Visual C++**

   ![C&#43; &#43; vlastnosti pro vzdálené ladění projektu](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")

5. Zvolte **vzdálený ladicí program** z **ladicí program ke spuštění** seznamu.

6. Zadejte síťový název vzdáleného zařízení **název počítače** pole. Nebo můžete použít na šipku dolů v rozevíracím seznamu vyberte zařízení, v dialogovém okně vyberte připojení vzdáleného ladicího programu.

   **Určení vzdáleného zařízení na stránce projektu Visual C# a Visual Basic**

   ![Spravovat vlastnosti projektu pro vzdálené ladění](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")

7. Zvolte **vzdálený počítač** z **cílové zařízení** seznamu.

8. Zadejte síťový název vzdáleného zařízení **vzdálený počítač** pole nebo klikněte na tlačítko **najít** pro výběr zařízení z **vyberte připojení vzdáleného ladicího programu** dialogové okno.

##  <a name="BKMK_Deployment_options"></a> Možnosti nasazení
 Můžete nastavit následující možnosti nasazení na stránky vlastnosti ladění projektu při spuštění.

 **Povolit zpětnou smyčku sítě** z bezpečnostních důvodů [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] není povoleno volat síťových zařízení, je nainstalovaná na aplikaci, která je nainstalovaná standardním způsobem. Ve výchozím nastavení nasazení sady Visual Studio vytvoří výjimku z tohoto pravidla pro aplikace nasazené. Tato výjimka umožňuje testovat postupy komunikace na jednom počítači. Před odesláním aplikace do [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)], měli byste otestovat vaši aplikaci bez výjimky.

 Chcete-li odebrat výjimku zpětnou smyčku sítě z ní:

- Na stránce vlastností jazyka C# a VB ladění, zrušte **povolit zpětnou smyčku sítě** zaškrtávací políčko.

- Na stránce vlastností jazyka JavaScript a ladění, nastavte **povolit zpětnou smyčku sítě** hodnota, která se **ne**.

  **Nespouštět, ale ladit můj kód při spuštění (C# a jazyka Visual Basic) nebo spustit aplikaci (JavaScript a C++)** ke konfiguraci nasazení na automatické spuštění relace ladění při spuštění aplikace:

- Na stránce vlastností jazyka C# a VB ladění zkontrolujte, **nespouštět, ale ladit můj kód při spuštění** zaškrtávací políčko.

- Na stránce vlastností jazyka JavaScript a ladění, nastavte **spustit aplikaci** hodnota, která se **Ano**.

## <a name="see-also"></a>Viz také
 [Spouštění aplikací ze sady Visual Studio](../debugger/run-store-apps-from-visual-studio.md)

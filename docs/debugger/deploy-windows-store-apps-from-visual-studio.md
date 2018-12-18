---
title: Nasazení aplikací pro UWP | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 01/16/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: d8006fb0ddcab4ab3eeee1616632d2dc513428ba
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53056808"
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Nasazení aplikací pro UPW ze sady Visual Studio

Nasazení funkce sady Visual Studio vytvoří a zaregistruje aplikací pro UWP, které jsou vytvořené pomocí sady Visual Studio na cílovém zařízení. Přesně jak registraci aplikace závisí na tom cílové zařízení pro místní nebo vzdálené:

- Pokud jsou cílem místní počítač s Visual Studio, Visual Studio registruje aplikaci ze složky jeho sestavení.

- Pokud jsou cílem vzdáleného zařízení, Visual Studio zkopíruje soubory potřebné ke vzdálenému počítači a zaregistruje na tomto zařízení aplikaci.

Nasazení je automaticky při ladění aplikace v sadě Visual Studio s použitím **spustit ladění** možnost (klávesnice: F5) nebo **spustit bez ladění** možnost (klávesnice: CTRL + F5). Aplikaci můžete nasadit také ručně. Ruční nasazení je užitečná v následujících scénářích:

- Ad-hoc testování na místním nebo vzdáleném počítači.

- Nasazení aplikace, který spustí jiné aplikace, kterou chcete ladit.

- Nasazení aplikace, která bude laděn, kdy byla spuštěna jiná aplikace nebo metody.

##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Jak nasadit aplikace pro UPW
 Ruční nasazení aplikace je jednoduchý proces:

1.  Pokud provádíte nasazení na vzdáleném zařízení, zadejte název nebo IP adresa zařízení, na stránce vlastností projektu z projektu po spuštění aplikace. (Tento postup jsou uvedeny níže v tomto tématu.).

2.  Na panelu nástrojů ladicího programu sady Visual Studio, zvolte cíl nasazení z rozevíracího seznamu vedle položky **spustit ladění** tlačítko.

     ![Spustit na místním počítači](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")

3.  Na **sestavení** nabídce zvolte **nasazení**

##  <a name="BKMK_How_to_specify_a_remote_device"></a> Určení vzdáleného zařízení

**Požadované součásti**

Na vzdáleném zařízení Windows 10, je nutné povolit [vývojářský režim](/windows/uwp/get-started/enable-your-device-for-development). Na zařízení s Windows 10 s aktualizací Update autora nebo novější, nástroje pro vzdálenou instalují automaticky při nasazení vaší aplikace. Další informace najdete v tématu [ladění balíčku nainstalované aplikace](../debugger/debug-installed-app-package.md).

> [!NOTE]
> Na verze pre Tvůrce aktualizací Windows 10 Remote Tools for Visual Studio musí být nainstalovaný na vzdáleném zařízení a vzdálený ladicí program musí být spuštěn.

Nasazení používá síťový kanál. vzdálený ladicí program ke vzdálenému zařízení odesílat soubory aplikace.

#### <a name="to-specify-a-remote-device"></a>K určení vzdáleného zařízení

1. Na stránce vlastností ladění projektu při spuštění zadejte název nebo IP adresa cíle vzdálené nasazení.

2. Chcete-li otevřít stránky vlastnosti ladění, vyberte projekt v Průzkumníku řešení a klikněte na tlačítko **vlastnosti** z místní nabídky.

3. Klikněte na tlačítko **ladění** uzlu v okně Vlastnosti stránky.

4. Pro **cílové zařízení**vyberte **vzdálený počítač**.

5. V části **vzdálený počítač**, klikněte na tlačítko **najít**.

6. Můžete zadat název nebo IP adresa vzdáleného zařízení, nebo můžete zvolit ze zařízení **připojení ke vzdálené** dialogové okno.

    ![Dialogové okno Vyberte připojení vzdáleného ladicího programu](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    **Připojení ke vzdálené** dialogové okno zobrazí zařízení, na podsíti místní sítě a zařízení, která je přímo připojený k počítači Visual Studio pomocí kabelu Ethernet.

   **Určení vzdáleného zařízení na stránce projektu JavaScript nebo Visual C++**

   ![C&#43; &#43; vlastnosti pro vzdálené ladění projektu](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")

7. Zvolte **vzdálený ladicí program** z **ladicí program ke spuštění** seznamu.

8. Zadejte síťový název vzdáleného zařízení **název počítače** pole. Nebo můžete použít na šipku dolů v rozevíracím seznamu vyberte zařízení, v dialogovém okně vyberte připojení vzdáleného ladicího programu.

   **Určení vzdáleného zařízení na stránce projektu Visual C# a Visual Basic**

   ![Spravovat vlastnosti projektu pro vzdálené ladění](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")

9. Zvolte **vzdálený počítač** z **cílové zařízení** seznamu.

10. Zadejte síťový název vzdáleného zařízení **vzdálený počítač** pole nebo klikněte na tlačítko **najít** pro výběr zařízení z **vyberte připojení vzdáleného ladicího programu** dialogové okno.

##  <a name="BKMK_Deployment_options"></a> Možnosti nasazení

Můžete nastavit následující možnosti nasazení na stránky vlastnosti ladění projektu při spuštění.

**Povolit zpětnou smyčku sítě**

Z bezpečnostních důvodů, UPW nebo [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] není povoleno volat síťových zařízení, je nainstalovaná na aplikaci, která je nainstalovaná standardním způsobem. Ve výchozím nastavení nasazení sady Visual Studio vytvoří výjimku z tohoto pravidla pro aplikace nasazené. Tato výjimka umožňuje testovat postupy komunikace na jednom počítači. Před odesláním aplikace do [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)], měli byste otestovat vaši aplikaci bez výjimky.

Chcete-li odebrat výjimku zpětnou smyčku sítě z ní:

- Na C# a ladění jazyka Visual Basic stránka vlastností, zrušte **povolit zpětnou smyčku sítě** zaškrtávací políčko.

- Na stránce vlastností jazyka JavaScript a ladění, nastavte **povolit zpětnou smyčku sítě** hodnota, která se **ne**.

**Nespouštět, ale ladit můj kód při spuštění (C# a Visual Basic) nebo spustit aplikaci (JavaScript a C++)**

Ke konfiguraci nasazení na automatické spuštění relace ladění při spuštění aplikace:

- Na C# a ladění jazyka Visual Basic vlastností, zkontrolujte **nespouštět, ale ladit můj kód při spuštění** zaškrtávací políčko.

- Na stránce vlastností jazyka JavaScript a ladění, nastavte **spustit aplikaci** hodnota, která se **Ano**.

## <a name="see-also"></a>Viz také

- [Pokročilé možnosti vzdáleného nasazení](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Ladění balíčku nainstalované aplikace](../debugger/debug-installed-app-package.md)
- [Spouštění aplikací ze sady Visual Studio](../debugger/run-store-apps-from-visual-studio.md)

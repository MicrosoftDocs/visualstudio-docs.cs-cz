---
title: Začínáme s Visual Studio Tools for Unity | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 9d924ee92258e348d5ffee1551fcde7707d711cf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855206"
---
# <a name="get-started-with-visual-studio-tools-for-unity"></a>Začínáme s Visual Studio Tools for Unity

## <a name="install-visual-studio"></a>Instalace sady Visual Studio

### <a name="unity-bundled-installation"></a>Instalace balíčků Unity

Počínaje Unity 2018.1, Visual Studio je výchozí C# skript editor pro Unity a je součástí Pomocníka pro stáhnout Unity a také nástroj pro instalaci Unity rozbočovače.

- Stáhněte si Unity [store.unity.com](https://store.unity.com/).

Během instalace Ujistěte se, že Visual Studio se změnami seznam součástí k instalaci pomocí Unity:

#### <a name="unity-hub"></a>Centrum Unity

![Centrum instalace Unity](media/vstu_unity-hub.png)

#### <a name="unity-download-assistant"></a>Unity stáhnout Pomocníka s nastavením

![Instalace Pomocníka s nastavením stáhnout Unity](media/vstu_download-assistant.png)

#### <a name="check-for-updates-to-visual-studio"></a>Zkontrolovat aktualizace sady Visual Studio

Tato verze sady Visual Studio je součástí instalace Unity nemusí být na nejnovější verzi. Doporučujeme zkontrolovat aktualizace Ujistěte se, že máte přístup k nejnovější nástroje a funkce.

- [Aktualizace sady Visual Studio](../install/update-visual-studio.md)

### <a name="manual-installation"></a>Ruční instalace

Pokud už máte nainstalovanou sadu Visual Studio 2017, nebo ruční instalaci, spusťte instalační program sady Visual Studio.

1. [Stažení instalačního programu sady Visual Studio](/visualstudio/install/install-visual-studio), nebo pro jeho otevření, pokud už nainstalovaná.

1. Klikněte na tlačítko **změnit** (Pokud je již nainstalováno) nebo **nainstalovat** (pro nové instalace) pro vaši požadovanou verzi sady Visual Studio.

1. Na **úlohy** kartu, přejděte **mobilní aplikace a hry** a vyberte **her pomocí Unity** pracovního vytížení.

    ![Úloha Unity](media/vstu_unity-workload.png)

1. Klikněte na tlačítko **změnit** (Pokud je již nainstalováno) nebo **nainstalovat** (pro nové instalace) v pravém dolním rohu okna instalačního programu.

## <a name="configure-unity-for-use-with-visual-studio"></a>Konfigurace pro použití se sadou Visual Studio Unity

Počínaje Unity 2018.1, Visual Studio by měl být výchozího externí skript editoru Unity. Můžete to ověřit nebo změnit externí skript editoru na konkrétní verzi sady Visual Studio:

1. Vyberte **Předvolby** z **upravit** nabídky.

   ![Vyberte předvolby](media/vstu_unity-preferences.png)

2. V dialogovém okně předvoleb vyberte **externích nástrojů** kartu.

3. Z **externí Editor skriptů** rozevíracího seznamu zvolte vaši požadovanou verzi sady Visual Studio, pokud je hodnota uvedena, v opačném případě vyberte **Procházet...** .

   ![Vyberte Visual Studio](media/vstu_unity-external-tools.png)

4. Pokud **Procházet...**  byla vybrána, přejděte **Common7/IDE** adresáře v sadě Visual Studio Instalační adresář a vyberte **devenv.exe**. Pak klikněte na tlačítko **otevřít**.

   ![Vyberte Otevřít](media/vstu_browse-for-application.png)

5. Po výběru v sadě Visual Studio **externí Editor skriptů** seznamu, ujistěte se, že **Editor připojení** zaškrtávací políčko zaškrtnuto.

6. Zavřít **Předvolby** dialogové okno pro dokončení procesu konfigurace.

## <a name="support-for-older-versions"></a>Podpora pro starší verze

 Stáhněte a nainstalujte Visual Studio Tools for Unity z webu Visual Studio Marketplace. Bude potřeba nainstalovat balíček pravý pro vaši verzi sady Visual Studio.

- Pro Visual Studio 2015 Community, Visual Studio 2015 Professional nebo Visual Studio 2015 Enterprise:

   [Stáhněte si Visual Studio 2015 Tools for Unity](https://marketplace.visualstudio.com/items?itemName=SebastienLebreton.VisualStudio2015ToolsforUnity)

> [!NOTE]
> Visual Studio Tools for Unity vyžaduje Unity 5.2 a vyšší, a také verzi sady Visual Studio, který podporuje rozšíření, jako je například Visual Studio Community, Professional, Premium nebo Enterprise. Chcete-li ověřit, že Visual Studio Tools for Unity jsou povolené v Unity pro vaši instalaci, vyberte **o Unity** z **pomáhají** nabídky a hledejte text "Microsoft Visual Studio Tools for Unity povoleno" v levé dolní části dialogového okna.
> ![o Unity](media/vstu_about-unity.png)

## <a name="next-steps"></a>Další kroky

 Informace o práci s a ladit svým projektem Unity v sadě Visual Studio najdete v tématu [Visual Studio Tools for Unity](../cross-platform/using-visual-studio-tools-for-unity.md).

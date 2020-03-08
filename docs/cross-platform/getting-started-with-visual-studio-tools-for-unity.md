---
title: Začínáme s Visual Studio Tools for Unity | Microsoft Docs
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
ms.openlocfilehash: c22b9c25f95ea26f2cdaf5c2035fb7a373123241
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408788"
---
# <a name="get-started-with-visual-studio-tools-for-unity"></a>Začínáme s Visual Studio Tools for Unity

## <a name="install-visual-studio"></a>Instalace sady Visual Studio

### <a name="unity-bundled-installation"></a>Instalace sady Unity

Od Unity 2018,1 je Visual Studio výchozím C# editorem skriptů pro Unity a je zahrnutý v Pomocníkovi pro stahování Unity a také v nástroji pro instalaci centra Unity.

- Stáhněte si Unity z [Store.Unity.com](https://store.unity.com/).

Během instalace se ujistěte, že je v seznamu komponent, které se mají nainstalovat s Unity, zaškrtnuté políčko Visual Studio:

#### <a name="unity-hub"></a>Centrum Unity

![Centrum instalace Unity](media/vstu_unity-hub.png)

#### <a name="unity-download-assistant"></a>Unity stáhnout Pomocníka s nastavením

![Instalace Pomocníka s nastavením stáhnout Unity](media/vstu_download-assistant.png)

#### <a name="check-for-updates-to-visual-studio"></a>Vyhledat aktualizace sady Visual Studio

Verze sady Visual Studio, která je součástí instalace Unity, nemusí být nejnovější. Doporučujeme zkontrolovat aktualizace Ujistěte se, že máte přístup k nejnovější nástroje a funkce.

- [Aktualizace sady Visual Studio](../install/update-visual-studio.md)

### <a name="manual-installation"></a>Ruční instalace

Pokud už máte nainstalovanou aplikaci Visual Studio 2017 nebo chcete nainstalovat raději ruční instalaci, spusťte instalační program sady Visual Studio.

1. [Stáhněte si instalační program sady Visual Studio](../install/install-visual-studio.md)nebo ho otevřete, pokud už je nainstalovaný.

1. Klikněte na **Upravit** (Pokud je už nainstalovaný) nebo **nainstalujte** (pro nové instalace) pro požadovanou verzi sady Visual Studio.

1. Na kartě **úlohy** se posuňte do části **mobilní & hry** a vyberte úlohu **vývoj her pomocí Unity** .

    ![Zatížení Unity](media/vstu_unity-workload.png)

1. Klikněte na **Upravit** (Pokud je už nainstalovaný) nebo **nainstalujte** (pro nové instalace) v pravém dolním rohu okna instalačního programu.

## <a name="configure-unity-for-use-with-visual-studio"></a>Konfigurace Unity pro použití se sadou Visual Studio

Počínaje Unity 2018.1, Visual Studio by měl být výchozího externí skript editoru Unity. Můžete to potvrdit nebo změnit externí editor skriptu na konkrétní verzi sady Visual Studio:

1. V nabídce **Upravit** vyberte **Předvolby** .

   ![Vyberte předvolby](media/vstu_unity-preferences.png)

2. V dialogovém okně Předvolby vyberte kartu **externí nástroje** .

3. V rozevíracím seznamu **editoru externích skriptů** zvolte požadovanou verzi sady Visual Studio, pokud je uvedena, jinak vyberte **Procházet...** .

   ![Vyberte Visual Studio](media/vstu_unity-external-tools.png)

4. Pokud jste vybrali možnost **Procházet...** , přejděte do adresáře **Common7/IDE** v instalačním adresáři sady Visual Studio a vyberte **devenv. exe**. Pak klikněte na **otevřít**.

   ![Vyberte Otevřít](media/vstu_browse-for-application.png)

5. Jakmile je v seznamu **Editor externích skriptů** vybraná možnost Visual Studio, zkontrolujte, že je zaškrtnuté políčko **připojovat Editor** .

6. Zavřete dialogové okno **Předvolby** a dokončete proces konfigurace.

## <a name="support-for-older-versions"></a>Podpora pro starší verze

 Stáhněte a nainstalujte Visual Studio Tools for Unity z Visual Studio Marketplace. Budete muset nainstalovat správný balíček pro vaši verzi sady Visual Studio.

- Pro Visual Studio 2015 Community, Visual Studio 2015 Professional nebo Visual Studio 2015 Enterprise:

   [Stáhnout Visual Studio 2015 Tools for Unity](https://marketplace.visualstudio.com/items?itemName=SebastienLebreton.VisualStudio2015ToolsforUnity)

> [!NOTE]
> Visual Studio Tools for Unity vyžaduje Unity 5,2 a vyšší a také verzi sady Visual Studio, která podporuje rozšíření, jako je Visual Studio Community, Professional, Premium nebo Enterprise. Pokud chcete ověřit, že je ve vaší instalaci Unity povolený Visual Studio Tools for Unity, vyberte z nabídky **help** možnost **o Unity** a vyhledejte text "Microsoft Visual Studio nástrojů pro Unity Enabled" v levém dolním rohu dialogového okna.
> ![o Unity](media/vstu_about-unity.png)

## <a name="next-steps"></a>Další kroky

 Informace o tom, jak pracovat s projektem Unity a ladit ho v aplikaci Visual Studio, najdete v tématu [Visual Studio Tools for Unity](../cross-platform/using-visual-studio-tools-for-unity.md).

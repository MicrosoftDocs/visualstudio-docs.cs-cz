---
title: Začínáme s Visual Studio Tools for Unity | Microsoft Docs
ms.custom: ''
ms.date: 05/11/2020
ms.technology: vs-unity-tools
ms.topic: how-to
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: indiesaudi
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 32766fdf69136f3882186bbcad08aaf83d2e573e
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815744"
---
# <a name="get-started-with-visual-studio-tools-for-unity"></a>Začínáme s Visual Studio Tools for Unity

## <a name="install-visual-studio"></a>Instalace sady Visual Studio

### <a name="unity-bundled-installation"></a>Instalace sady Unity

Od Unity 2018,1 je Visual Studio výchozím editorem skriptu v jazyce C# pro Unity a je zahrnutý v Pomocníkovi pro stahování Unity a také v nástroji pro instalaci centra Unity.

- Stáhněte si Unity z [Store.Unity.com](https://store.unity.com/).

Během instalace se ujistěte, že je v seznamu komponent, které se mají nainstalovat s Unity, zaškrtnuté políčko Visual Studio:

#### <a name="unity-hub"></a>Centrum Unity

:::moniker range="vs-2017"
![Instalace centra Unity](media/vs-2017/vstu-unity-hub.png)
:::moniker-end
:::moniker range=">=vs-2019"
![Instalace centra Unity](media/vs-2019/vstu-unity-hub.png)
:::moniker-end

:::moniker range="vs-2017"

#### <a name="unity-download-assistant"></a>Pomocník pro stahování Unity

![Instalace pomocníka pro stahování Unity](media/vs-2017/vstu-download-assistant.png)

Verze sady Visual Studio, která je součástí instalace Unity, nemusí být nejnovější. Pokud se zobrazí výzva k instalaci sady Visual Studio 2017, doporučujeme ručně nainstalovat novější verzi sady Visual Studio.
:::moniker-end

### <a name="manual-installation"></a>Ruční instalace

Pokud už máte nainstalovanou aplikaci Visual Studio nebo pokud chcete ručně nainstalovat, spusťte instalační program sady Visual Studio.

1. [Stáhněte si instalační program sady Visual Studio](../install/install-visual-studio.md)nebo ho otevřete, pokud už je nainstalovaný.

1. Klikněte na **Upravit** (Pokud je už nainstalovaný) nebo **nainstalujte** (pro nové instalace) pro požadovanou verzi sady Visual Studio.

1. Na kartě **úlohy** se posuňte do části **mobilní & hry** a vyberte úlohu **vývoj her pomocí Unity** .

   :::moniker range="vs-2017"
   ![Zatížení Unity](media/vs-2017/vstu-unity-workload.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Zatížení Unity](media/vs-2019/vstu-unity-workload.png)
   :::moniker-end

1. Klikněte na **Upravit** (Pokud je už nainstalovaný) nebo **nainstalujte** (pro nové instalace) v pravém dolním rohu okna instalačního programu.


#### <a name="check-for-updates-to-visual-studio"></a>Vyhledat aktualizace sady Visual Studio

Doporučuje se zkontrolovat aktualizace v sadě Visual Studio, abyste měli jistotu, že máte přístup k nejnovějším nástrojům a funkcím. Tím nedojde k přerušení vašeho projektu Unity.

- [Aktualizace sady Visual Studio](../install/update-visual-studio.md)


## <a name="configure-unity-for-use-with-visual-studio"></a>Konfigurace Unity pro použití se sadou Visual Studio

Od Unity 2018,1 by měl být Visual Studio výchozím editorem externích skriptů v Unity. Můžete to potvrdit nebo změnit externí editor skriptu na konkrétní verzi sady Visual Studio:

1. V nabídce **Upravit** vyberte **Předvolby** .

   :::moniker range="vs-2017"
   ![Vybrat předvolby](media/vs-2017/vstu-unity-preferences.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Vybrat předvolby](media/vs-2019/vstu-unity-preferences.png)
   :::moniker-end

2. V dialogovém okně Předvolby vyberte kartu **externí nástroje** .

3. V rozevíracím seznamu **editoru externích skriptů** zvolte požadovanou verzi sady Visual Studio, pokud je uvedena, jinak vyberte **Procházet...**.

   :::moniker range="vs-2017"
   ![Vybrat Visual Studio](media/vs-2017/vstu-unity-external-tools.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Vybrat Visual Studio](media/vs-2019/vstu-unity-external-tools.png)
   :::moniker-end


4. Pokud jste vybrali možnost **Procházet...** , přejděte do adresáře **Common7/IDE** v instalačním adresáři sady Visual Studio a vyberte **devenv.exe**. Pak klikněte na **otevřít**.

   :::moniker range="vs-2017"
   ![Vyberte otevřít.](media/vs-2017/vstu-browse-for-application.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Vyberte otevřít.](media/vs-2019/vstu-browse-for-application.png)
   :::moniker-end

5. Jakmile je v seznamu **Editor externích skriptů** vybraná možnost Visual Studio, zkontrolujte, že je zaškrtnuté políčko **připojovat Editor** .

6. Zavřete dialogové okno **Předvolby** a dokončete proces konfigurace.

## <a name="support-for-older-versions"></a>Podpora pro starší verze

Stáhněte a nainstalujte Visual Studio Tools for Unity z Visual Studio Marketplace. Budete muset nainstalovat správný balíček pro vaši verzi sady Visual Studio.

- Pro Visual Studio 2015 Community, Visual Studio 2015 Professional nebo Visual Studio 2015 Enterprise:

   [Stáhnout Visual Studio 2015 Tools for Unity](https://marketplace.visualstudio.com/items?itemName=SebastienLebreton.VisualStudio2015ToolsforUnity)

> [!NOTE]
> Visual Studio Tools for Unity vyžaduje Unity 5,2 a vyšší a také verzi sady Visual Studio, která podporuje rozšíření, jako je Visual Studio Community, Professional, Premium nebo Enterprise. Pokud chcete ověřit, že je ve vaší instalaci Unity povolený Visual Studio Tools for Unity, vyberte z nabídky **help** možnost **o Unity** a vyhledejte text "Microsoft Visual Studio nástrojů pro Unity Enabled" v levém dolním rohu dialogového okna.
> ![o Unity](media/vs-2019/vstu-about-unity.png)


## <a name="next-steps"></a>Další kroky

 Informace o tom, jak pracovat s projektem Unity a ladit ho v aplikaci Visual Studio, najdete v tématu [Visual Studio Tools for Unity](../cross-platform/using-visual-studio-tools-for-unity.md).

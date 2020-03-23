---
title: Začínáme s nástroji Visual Studio pro jednotu | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302271"
---
# <a name="get-started-with-visual-studio-tools-for-unity"></a>Začínáme s nástroji Visual Studio pro jednotu

## <a name="install-visual-studio"></a>Instalace sady Visual Studio

### <a name="unity-bundled-installation"></a>Unity přibalená instalace

Počínaje Unity 2018.1, Visual Studio je výchozí editor skriptů Jazyka C# pro Unity a je součástí Unity Download Assistant, stejně jako nástroj pro instalaci Unity Hub.

- Stáhnout Unity z [store.unity.com](https://store.unity.com/).

Během instalace se ujistěte, že je visual studio zaškrtnuto v seznamu součástí, které chcete nainstalovat pomocí Unity:

#### <a name="unity-hub"></a>Centrum Unity

![instalace rozbočovače unity](media/vstu_unity-hub.png)

#### <a name="unity-download-assistant"></a>Asistent stahování Unity

![unity download asistent instalace](media/vstu_download-assistant.png)

#### <a name="check-for-updates-to-visual-studio"></a>Kontrola aktualizací sady Visual Studio

Verze sady Visual Studio, která je součástí instalace Unity, nemusí být nejnovější. Doporučujeme vyhledat aktualizace, abyste měli přístup k nejnovějším nástrojům a funkcím.

- [Aktualizace sady Visual Studio](../install/update-visual-studio.md)

### <a name="manual-installation"></a>Ruční instalace

Pokud už máte nainstalovanou Visual Studio 2017 nebo chcete ji nainstalovat ručně, spusťte instalační program Sady Visual Studio.

1. [Stáhněte si instalační program sady Visual Studio](../install/install-visual-studio.md)nebo jej otevřete, pokud jste již nainstalovali.

1. Klikněte na **Změnit** (pokud jste již nainstalovali) nebo **Nainstalovat** (pro nové instalace) pro požadovanou verzi sady Visual Studio.

1. Na kartě **Úlohy** přejděte do části **Mobilní & gaming** a vyberte vývoj hry s pracovní zátěží **Unity.**

    ![Pracovní zátěž Jednoty](media/vstu_unity-workload.png)

1. V pravém dolním rohu okna instalačního programu klikněte na **Změnit** (pokud jste již nainstalovali) nebo **Nainstalovat** (pro nové instalace).

## <a name="configure-unity-for-use-with-visual-studio"></a>Konfigurace unity pro použití s Visual Studio

Počínaje Unity 2018.1, Visual Studio by měl být výchozí externí editor skriptů v Unity. Můžete to potvrdit nebo změnit externí editor skriptů na konkrétní verzi sady Visual Studio:

1. Z nabídky **Úpravy** vyberte **Předvolby.**

   ![Vybrat předvolby](media/vstu_unity-preferences.png)

2. V dialogovém okně Předvolby vyberte kartu **Externí nástroje.**

3. V rozevíracím seznamu **Externí editor skriptů** zvolte požadovanou verzi sady Visual Studio, pokud je v seznamu uvedená, jinak vyberte **Procházet...**.

   ![Výběr sady Visual Studio](media/vstu_unity-external-tools.png)

4. Pokud **je vybrána možnost Procházet...** byla vybrána, přejděte do adresáře **Common7/IDE** uvnitř instalačního adresáře sady Visual Studio a vyberte **devenv.exe**. Potom klepněte na tlačítko **Otevřít**.

   ![Vybrat otevřít](media/vstu_browse-for-application.png)

5. Po výběru sady Visual Studio v seznamu **Externí editor skriptů** zkontrolujte, zda je zaškrtnuté políčko **Připojení editoru.**

6. Chcete-li dokončit proces konfigurace, zavřete dialogové okno **Předvolby.**

## <a name="support-for-older-versions"></a>Podpora starších verzí

 Stáhněte a nainstalujte nástroje Visual Studio pro jednotu z webu Visual Studio Marketplace. Budete muset nainstalovat správný balíček pro vaši verzi sady Visual Studio.

- Pro komunitu Visual Studio 2015, Visual Studio 2015 Professional nebo Visual Studio 2015 Enterprise:

   [Stažení visual studio 2015 nástroje pro jednotu](https://marketplace.visualstudio.com/items?itemName=SebastienLebreton.VisualStudio2015ToolsforUnity)

> [!NOTE]
> Visual Studio Tools for Unity vyžaduje Unity 5.2 a vyšší, stejně jako verze Visual Studio, která podporuje rozšíření, jako je visual studio společenství, professional, premium nebo enterprise. Chcete-li ověřit, že nástroje sady Visual Studio pro jednotu jsou povoleny v instalaci Unity, vyberte **o jednotě** z nabídky **Nápověda** a vyhledejte text "Microsoft Visual Studio Tools for Unity povoleno" v levém dolním rohu dialogového okna.
> ![o jednotě](media/vstu_about-unity.png)

## <a name="next-steps"></a>Další kroky

 Informace o tom, jak pracovat s projektem Unity a ladit ho v sadě Visual Studio, najdete v [tématu Nástroje visual studia pro jednotu](../cross-platform/using-visual-studio-tools-for-unity.md).
